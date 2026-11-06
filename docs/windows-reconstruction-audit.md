# Windows reconstruction audit

[Back to the overview](../README.md)

Audit date: **2026-11-06**. This document records what a clean Windows reconstruction still depends on. It is based on the original image and is **not a tested unattended installation recipe**. The supplied Windows image currently has the USB-driver mismatch described in [Windows and USB](windows-and-usb.md).

## Readiness verdict

The repository now captures the central configuration, measured controls, application launch targets, relevant runtime observations and selected user-registry settings. **It is not a self-contained cabinet installer.** Private game/runtime assets, exact original binaries and some unmeasured hardware details remain necessary. Do not discard the raw image just because the configuration is in Git.

Two different goals must be distinguished:

- **Reproduce the historical installation:** reproduce its original versions, paths and recorded configuration, including understanding its existing faults. A blank Windows 7 install would not by itself fix the missing xHCI support.
- **Build a working cabinet on another clean Windows version:** use an OS and drivers appropriate to the hardware, then validate old software and dependencies. That migration has not been tested here; modified Windows 7 boot DLLs/loaders must not be copied onto a different OS version.

## Important gaps closed by this audit

| Area | Newly retained evidence / configuration | Why it matters |
|---|---|---|
| Runtime versions | [Installed-software observations](../evidence/installed-software.json) and [runtime-file presence](../evidence/runtime-file-presence.json) | A directory of EXEs does not reproduce C++/.NET/XNA/OpenAL/legacy graphics components |
| User keyboard state | [Additional Windows observations](../config/windows/additional-observations.json) | Spanish layouts and initial NumLock affect keypad/character interpretation |
| Emulator registry | [Selected emulator HKCU settings](../config/windows/emulator-user-registry.json) | ePSXe and pinball settings are not all stored beside the executable |
| Game launch targets | [36 Windows/MUGEN shortcut records](../metadata/windows-game-shortcut-targets.json) | Target executable, arguments and working directory must be reconstructed, not just game titles |
| Startup shortcuts | [Resolved startup links](../evidence/startup-shortcut-targets.json) | Documents the additional Startup-folder path to tstart.exe |
| Helper launchers | [Embedded-script observations](../evidence/helper-launcher-observations.json) | Desktop HyperSpin shortcut actually uses a wrapper which closes Explorer |
| Additional control profiles | Captured emulator/MUGEN/RetroArch/Project64 profiles under [config/emulators](../config/emulators/) | Global frontend controls do not describe every engine's controls |
| Per-game overrides | [Deduplicated MAME-family override archive](../config/emulators/mame-per-game-overrides.json) | Per-game input/video settings can override default.cfg |

## Runtime components observed in the original image

These are **observations, not a recommendation to install every old package**. Uninstall records can overlap or be stale; their presence does not prove a component is required by every game.

| Component | Recorded version / scope |
|---|---|
| .NET Framework | 4.5.2 / 4.5.51209, including Spanish language components |
| Visual C++ 2008 | x64 9.0.21022 |
| Visual C++ 2010 | x86 and x64 10.0.30319 |
| Visual C++ 2012 | x86 11.0.50727; x64 11.0.61030, with package/component records |
| Visual C++ 2013 | x64 component records 12.0.21005 and bundle record 12.0.30501 |
| Visual C++ 2015 | x64 14.0.23026 |
| Microsoft XNA Framework | 4.0 / 4.0.20823.0 |
| Games for Windows LIVE redistributable | 3.5.88.0 |
| Games for Windows Marketplace | 3.5.50.0 |
| Windows Live ID Sign-in Assistant | 6.500.3165.0 |
| OpenAL | OpenAL entry plus 1.1 Core PC SDK 3.05 |
| Uplay | 15.0 |
| K-Lite Codec Pack Full | 10.2.0 |
| Classic Shell | 4.0.2 |
| 7-Zip | 16.04 x64 and older 9.20 x64 records |
| Java | 7 Update 13; dependency of particular games/tools not established |

`d3dx9_43.dll`, `D3DCompiler_43.dll`, `xinput1_3.dll`, `OpenAL32.dll` and VC++ 2010 runtime DLLs were found in **both System32 and SysWOW64**. On this x64 Windows, these are the native 64-bit and 32-bit component locations respectively. VC++ 2013 msvcr120/msvcp120 files were found in System32 but not in the corresponding SysWOW64 paths examined. The DirectX registry Version string is `4.09.00.0904`; it does not prove every optional legacy DirectX component is installed.

No runtime DLLs or installers are distributed in Git. Use legitimate, version/OS-appropriate redistributables; copying DLLs from the old Windows directory is not a documented reconstruction method.

## Locale, keypad and login details

The original `arcade` HKCU profile contains:

```text
Keyboard Layout\Preload: 1 = 00000c0a, 2 = 00000409
Keyboard Layout\Substitutes: 00000c0a = 0000040a
Control Panel\International: LocaleName = es-ES
Control Panel\Keyboard: InitialKeyboardIndicators = "2"
KeyboardDelay = "1", KeyboardSpeed = "31"
```

This records Spanish and US layout entries, Spanish locale, and initial NumLock enabled. It does not prove the effective layout/LED state at every runtime moment. The other `usuario` profile has a different initial-keyboard-indicator value and must not be substituted for `arcade`.

The source also records `EnableLUA=0` and `ConsentPromptBehaviorAdmin=0`, and empty/disabled AppInit DLL injection. These values are retained as observations of the old setup, **not requirements or instructions to disable security on a new installation**. Which applications actually depend on administrator rights remains untested.

Automatic login requires a deliberate account setup on the new installation. No original password or activation secret is published. Review HKCU settings in the intended cabinet user's account, not an unrelated administrator profile.

## Startup helper behavior

The owner's desktop HyperSpin shortcut targets **Hyperspin Launcher.exe**, not HyperSpin.exe directly. Its embedded script closes explorer.exe, launches `D:\hyperspin1.0\hyperspin.exe`, then exits.

`Task Bar.exe` closes explorer.exe, sends Ctrl+T and Space, then exits. These are observed commands, not runtime-validated behavior. The binaries and extracted third-party source are not included in Git.

In addition to the Winlogon shell replacement, a per-user Startup-folder `TurboSheller.lnk` targets `C:\Program Files (x86)\TSheller\tstart.exe` with its TSheller directory as working directory. A desktop Turbo Sheller shortcut targets TSheller.exe instead. The full shell chain is described in [startup.md](startup.md).

## Per-game configuration archive

`config/emulators/mame-per-game-overrides.json` retains nonempty XML overrides for the examined MAME-family/PinMAME trees, including control/video overrides. Empty configurations after removing bookkeeping are not stored. Coin/ticket counter sections are omitted because these are session/progress data, not required configuration.

The file records source paths/hashes, assignments and deduplicated XML profiles. To reconstruct a recorded override, select its `profiles[profile_sha256]` XML, restore `assignment.system_name` on the `<system>` element, and place it at the corresponding original-relative source path. The original source hash refers to the unmodified private file, not the normalized public XML. This is a documented representation; no deployment script is provided or tested.

The audit examined 18,625 per-game CFG files: 10,744 became empty after removing bookkeeping, 7,829 nonempty assignments were retained as 542 unique XML profiles, and 52 legacy binary CFG files could not be parsed as XML. The inspected legacy PinMAME file begins with `MAMECFG`; retain the original private PinMAME cfg tree for those settings. The archive does not imply every engine uses MAME XML or that the skipped legacy files are included.

## What must remain available outside Git

1. The raw source disk image and extraction/verification manifests.
2. The exact frontend/launcher binaries and DLLs, Modules and Module Extensions, plus helper launchers/TSheller if reproducing the old chain.
3. ROMs, BIOS, CHDs, games, pinball tables, tracks, media, fonts and other payload dependencies.
4. User AppData/My Games/Saved Games, relevant ProgramData and Public Documents/Amiga Files. The earlier 744 GB extraction did not include all of C:.
5. Required legitimate runtime installers and game launchers/account access. Folder copies do not reproduce installations or activation.
6. Original per-user registry hives privately, in case an unexported game-specific setting is needed later. Never import the complete old hive blindly into a new Windows profile.
7. Any Mini-PAC firmware/WinIPAC export and photographs of wiring, if acquired later.

## Clean-install validation sequence

This is an acceptance checklist, not a claim that the rebuild has already succeeded:

- [ ] Identify the target Windows version and install its correct chipset/USB, graphics, LAN and audio drivers for the actual hardware.
- [ ] Verify keyboard, mouse and Mini-PAC before adding cabinet startup automation; reject the old mismatched xHCI package.
- [ ] Establish the intended cabinet user, filesystem paths/drive letters, locale and keypad behavior.
- [ ] Restore the private runtime/payload folders and the reviewed configuration; preserve the originals.
- [ ] Make the frontend work from a normal desktop before enabling automatic login or an alternate shell.
- [ ] Reconstruct Windows/MUGEN shortcuts using the recorded target, arguments and working directory; inspect missing paths rather than guessing from the game title.
- [ ] Install needed runtime components and review emulator-specific HKCU settings.
- [ ] Test one title per engine, then input/video overrides and two-player simultaneous controls, credits, starts, exit, save/load and sound.
- [ ] Validate pinball side buttons, game-specific inputs and any gun/coin hardware separately.
- [ ] Confirm shutdown, restart and return-to-menu behavior before final startup customization.
- [ ] Keep decorative Windows boot customization separate; do not transplant patched Windows 7 loaders onto another Windows version.
- [ ] Capture a new verified reference image only after a successful runtime test of the completed installation.

## Unresolved blockers to an exact replica

The exact current display and audio hardware, Mini-PAC board/firmware/shift functions and terminal wiring are still incomplete. Some historical paths conflict; for example `Settings/MAME/Emulators.ini` references `D:\hyperspin1.0\Emulators\MameUI 0.152 64 bits\mameui64.exe`, whereas the top-level MAME settings identify MAME Arcade 0.190 and the shared MAME Retro ROM directory. The active module/profile precedence has not been traced. A modern Windows version's compatibility with every old executable or launcher is untested. Per-game runtime dependencies/account availability are not fully established. The later NAS transfer has not been fully rehashed.

These limitations prevent an honest promise of a one-click or guaranteed identical reconstruction. The original image remains the complete fallback.
