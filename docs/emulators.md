# Existing emulator configuration

[Back to the repository overview](../README.md)

## Identified launchers

| Existing content | Recorded engine / executable |
|---|---|
| Main arcade, CPS, Neo Geo and shared collections | **MAME Arcade 0.190**, read from version resources of both MAME/mamearcade64.exe and MAME Retro/mamearcade64.exe |
| Multiple consoles | RetroArch; exact core versions **TBD** |
| Cave | mameuifx64.exe |
| Namco System 22 / Technos Arcade | mamep64.exe |
| Naomi / Atomiswave | Demul |
| Sega Model 2 / Model 3 | Model 2 Emulator / Supermodel |
| Dreamcast / Saturn | nullDC / SSF |
| PlayStation / PSP | ePSXe / PPSSPP |
| Neo Geo CD / Amiga | neoraine32 / WinUAELoader |
| OpenBOR / MUGEN | BOR engine and separately packaged MUGEN games |
| Pinball | Future Pinball, VPinball915.exe, Pinball FX2 and Pinball Arcade |
| PC games | Windows programs, often reached through .lnk shortcuts and helper launchers |

These names identify recorded files and launch settings, not proof that every title ran on the examined cabinet. VPinball915.exe's filename suggests Visual Pinball 9.15; a resource-version check of that executable has not been documented here.

## Shared paths

The frontend settings for MAME, MAME Retro, CPS1/CPS2/CPS3, Neo Geo AES/MVS and Sega ST-V point to the same `D:\hyperspin1.0\Emulators\MAME Retro\Roms\` directory. These are overlapping collections, not independently installed game libraries.

An installed MAME 0.190 executable does not prove every archive belongs to a complete, homogeneous 0.190 ROM set. Parent/clone, BIOS and CHD completeness has not been audited against a DAT file. No emulator was executed as part of the read-only inspection.

## Configuration retained here

[config/emulators](../config/emulators/) contains captured global bindings, MAME INIs, standalone emulator INIs and selected global/per-platform RetroArch configuration files. [config/hyperspin/Settings](../config/hyperspin/Settings/) contains frontend launch settings for the cataloged systems, including systems whose referenced payload paths may be stale or absent.

The archive preserves original names and source structure, including spaces and case. It does not merge conflicting profiles. Standalone emulator folders may contain several alternate GPU or control profiles; retaining an INI does not establish that it was active.

## External dependencies recorded or observed

The Windows installation contains or references DAEMON Tools Lite, Visual C++/.NET-related components, OpenAL, Games for Windows LIVE and Ubisoft software. A directory copy alone does not reproduce registry entries, runtime libraries, account access or game activation. Private user profiles and installed runtime components are not included here.

Additional global/control profiles and a deduplicated MAME-family per-game override archive were added during the [Windows reconstruction audit](windows-reconstruction-audit.md). Selected [emulator HKCU settings](../config/windows/emulator-user-registry.json) cover ePSXe, Visual Pinball, Future Pinball, Visual PinMAME and other inspected engine keys. Exact secondary engine/core versions, active module precedence and effective runtime behavior still require confirmation.
