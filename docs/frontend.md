# HyperSpin and HyperLaunch configuration

[Back to the repository overview](../README.md)

## Versions

| Component | Verified version evidence |
|---|---|
| HyperSpin | `1.3.2.0` in embedded version-resource strings |
| HyperLaunch | `Version = 2.25c` in its embedded script |
| HyperLaunch's AutoHotkey compiler | `1.1.07.03`; this is not the HyperLaunch version |

[Launcher hashes and version observations](../evidence/launcher-versions.json). No launcher executables or extracted launcher source code are distributed in this repository.

The folder name `hyperspin1.0` is a path, not the actual HyperSpin version.

## Original layout

```text
C:\Program Files (x86)\TSheller\     Windows shell replacement
C:\Users\arcade\                    additional settings and save data
C:\ROMS\                            a few saves, not the main ROM library
D:\hyperspin1.0\
    HyperSpin.exe / HyperHQ.exe      frontend and configuration utility
    HyperLaunch.exe                 game launcher
    Settings\                       global and per-system settings
    Databases\                      XML catalogs and menu definitions
    Modules\ / Module Extensions\   launcher modules and dependencies
    Emulators\                      engines, games, BIOS and configurations
    Media\                          intros, themes, artwork and videos
    HyperTheme\                     theme tools and resources
```

The archived [Settings tree](../config/hyperspin/Settings/) includes global, per-system and nested INI configuration. Original keys, values, casing, encodings and functional paths are retained unless an identified private value was sanitized. Source-language comments are kept verbatim rather than translated inside functional snapshots.

## Main frontend settings

Source: [Settings.ini](../config/hyperspin/Settings/Settings.ini).

| Setting | Recorded value |
|---|---|
| FullScreen | true |
| Width / Height | 1360 / 768 |
| Intro enabled / stop on keypress | true / true |
| Attract mode / delay | true / 120 seconds |
| Master volume / wheel volume | 100 / 20 |
| P1 keyboard Start | 77 = Windows virtual key M |
| P1 keyboard Exit | 27 = Escape |
| P1 Up / Down | 38 / 40 = arrow keys |
| P1 SkipUp / SkipDown | 37 / 39 = left/right arrows |
| Genre / Favorites | 53 / 49 = top-row 5 / 1 |
| P2 keyboard menu controls | Unspecified in this file |
| P1 joystick / P2 joystick menu sections | enabled / disabled |

The captured Mini-PAC exposes keyboard events, so the presence of enabled joystick settings does not prove the frontend used them. The physical P1 service button emits **keypad 1**, whereas frontend Start is configured as **M**, also emitted by P1's top-left action button. This is a real configuration discrepancy to preserve and test, not silently repair in this archive.

## HyperLaunch settings

Sources: [HyperLaunch.ini](../config/hyperspin/Settings/HyperLaunch.ini), [Global Settings.ini](../config/hyperspin/Settings/Global%20Settings.ini).

- Emulator exit: `~Esc`.
- Script exit: `~q & ~s`.
- Navigation: P1 arrows/Enter; P2 numeric-keypad directions/Enter in HyperLaunch.ini.
- Global `Keymapper_Enabled=false` and `7z_Enabled=false`; system-level settings may override them.
- Temporary extraction directory: `C:\Users\arcade\AppData\Local\Temp\Hyperspin\`.
- Several absolute paths assume the original D: library and C: user profile.

Settings.ini, HyperLaunch.ini, global settings and per-system files sometimes disagree on cursor hotkeys, desktop hiding and taskbar hiding. The authoritative runtime combination has not been traced. A reconstruction should preserve originals and establish precedence from the actual launcher/module flow.

## Catalog and menu

The menu references **69 systems/collections**, not 69 independent emulator installations. Several collections share a ROM directory. The archived metadata records the menu and game entries without distributing ROMs. See [game inventory](games.md).

Original visual assets, frontend executables and runtime launcher modules remain in the owner's private disk image. They are intentionally outside this configuration-only repository.
