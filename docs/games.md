# Detected game inventory

[Back to the repository overview](../README.md)

**69 main-menu entries and 30,233 catalog entries.** These counts include clones, variants and overlapping collections. They are not counts of distinct or tested games.

- [Complete title/identifier metadata](../metadata/game-catalog.csv).
- [System, configured path and launcher metadata](../metadata/systems.csv).

Only metadata is published. No ROMs, BIOS images, game binaries, table files or downloads are provided.

## Menu collections

| Menu collection | Catalog entries | Files at configured directory level* | Windows executable |
|---|---:|---:|---|
| MAME | 7668 | 8578 | `mamearcade64.exe` |
| MAME Retro | 7668 | 8578 | `mamearcade64.exe` |
| AAE | 33 | 39 | `aae.exe` |
| cave | 74 | 83 | `mameuifx64.exe` |
| CPS1 | 33 | 8578 | `mamearcade64.exe` |
| CPS2 | 41 | 8578 | `mamearcade64.exe` |
| Capcom Play System III | 6 | 8578 | `mamearcade64.exe` |
| Mugen | 16 | 16 | `PCLAUNCHER.exe` |
| Namco sistem 22 | 15 | 26 | `mamep64.exe` |
| BOR | 9 | 9 | `BOR.exe` |
| Full Sega ST-V | 37 | 8578 | `mamearcade64.exe` |
| Sega Model 2 | 54 | 60 | `EMULATOR.EXE` |
| Sega Model 3 | 22 | 41 | `Supermodel.exe` |
| Sega Naomi | 90 | 104 | `demul.exe` |
| Atomiswave | 21 | 27 | `demul.exe` |
| Neo Geo MVS | 139 | 8578 | `mamearcade64.exe` |
| Technos Arcade | 22 | 23 | `mamep64.exe` |
| Technos Nintendo | 18 | 19 | `nestopia.exe` |
| Zinc | 64 | 78 | `ZiNc.exe` |
| Daphne | 23 | 26 | `daphne.exe` |
| Amstrad GX4000 | 25 | 25 | `WinApe.exe` |
| Atari 2600 | 648 | 963 | `Retroarch.exe` |
| Atari 5200 | 72 | 75 | `mess.exe` |
| Atari 7800 | 59 | 67 | `Retroarch.exe` |
| Atari Lynx | 75 | 75 | `retroarch.exe` |
| Atari Jaguar | 47 | 50 | `Retroarch.exe` |
| Bandai WonderSwan | 110 | 112 | `retroarch.exe` |
| Bandai WonderSwan Color | 91 | 91 | `retroarch.exe` |
| ColecoVision | 140 | 173 | `Retroarch.exe` |
| Commodore Amiga | 1954 | 2888 | `WinUAELoader.exe` |
| Emerson Arcadia 2001 | 55 | 48 | `mess.exe` |
| Microsoft MSX | 585 | 585 | `Retroarch.exe` |
| Microsoft MSX2 | 167 | 177 | `Retroarch.exe` |
| Microsoft MSX2+ | 26 | 50 | `Retroarch.exe` |
| NEC PC Engine | 301 | 301 | `retroarch.exe` |
| NEC PC Engine CD | 120 | 120 | `retroarch.exe` |
| TurboGrafx 16 | 94 | 94 | `retroarch.exe` |
| TurboGrafx CD | 45 | 45 | `retroarch.exe` |
| NEC SuperGrafx | 5 | 5 | `retroarch.exe` |
| Gameboy | 1798 | 1799 | `retroarch.exe` |
| Nintendo Gameboy Color | 535 | 589 | `Retroarch.exe` |
| Gameboy Advance | 1129 | 1315 | `retroarch.exe` |
| Nintendo Famicom | 1239 | 1239 | `Retroarch.exe` |
| Famicom Disk System | 91 | 91 | `Retroarch.exe` |
| Nintendo Entertainment System | 199 | 199 | `Retroarch.exe` |
| Super Nintendo Entertainment System | 812 | 819 | `retroarch.exe` |
| Nintendo 64 | 303 | 311 | `retroarch.exe` |
| Nintendo 64DD | 8 | 12 | `retroarch.exe` |
| SG-1000 | 69 | 81 | `retroarch.exe` |
| Sega Game Gear | 249 | 253 | `Retroarch.exe` |
| Sega Master System | 273 | 286 | `Retroarch.exe` |
| Sega Genesis | 813 | 816 | `Retroarch.exe` |
| Sega CD | 162 | 161 | `retroarch.exe` |
| Sega 32X | 33 | 33 | `retroarch.exe` |
| Sega Saturn | 303 | 303 | `SSF.exe` |
| Sega Dreamcast | 36 | 0 | `nullDC_Win32_Release-NoTrace.exe` |
| Neo Geo Pocket | 8 | 10 | `retroarch.exe` |
| Neo Geo Pocket Color | 40 | 40 | `retroarch.exe` |
| Neo Geo AES | 140 | 8578 | `mamearcade64.exe` |
| Neo Geo CD | 90 | 90 | `neoraine32.exe` |
| Sony Playstation | 188 | 0 | `ePSXe.exe` |
| Psp | 14 | 14 | `PPSSPPWindows64.exe` |
| Sony Playstation Minis | 298 | 299 | `PPSSPPWindows64.exe` |
| Panasonic 3DO | 225 | 225 | `Retroarch.exe` |
| PC GAMES | 20 | 20 | `PCGAMES.exe` |
| Future Pinball | 386 | 306 | `Future Pinball.exe` |
| Pinball FX2 | 1 | 0 | `Game.exe` |
| Pinball Arcade | 52 | 0 | `Game.exe` |
| Visual Pinball | 47 | 51 | `VPinball915.exe` |

\* Direct-directory counts use the extensions declared in the existing configuration. A shared directory is counted again for each collection pointing to it. A zero does not prove there are no games: PlayStation and Dreamcast use subdirectories/tracks, and some systems launch through shortcuts. A catalog entry, matching basename or .lnk file does not establish a complete installation.

## Payload observations from the private image

- Main shared MAME directory: **8,578 ZIP archives and 149 CHDs**.
- PlayStation tree: **181 CUEs, 3 CCDs and 3 ISOs**, with accompanying tracks and Windows shortcuts.
- Dreamcast tree: **35 GDIs** with accompanying track data.
- Visual Pinball tree: **51 .vpt table files**, while its catalog has 47 entries.
- Cataloged pinball content: **386 Future Pinball entries, 47 Visual Pinball entries, 52 Pinball Arcade table entries and one Pinball FX2 launcher entry**. These represent different kinds of content, not 486 separate applications.

## Windows game titles in the menu

- Another World – 20th Anniversary Edition
- BRAWL
- Crazy Taxi 2-in-1
- Crazy Taxi 3
- Double Dragon Neon
- DuckTales
- Fix-it Felix Jr
- hurrican
- limbo
- Metal Slug Collection PC
- Naruto Shippuden - Ultimate Ninja Storm Revolution
- One Piece Pirate Warriors 3
- outrun 2006
- PAC-MAN
- Rayman Legends
- Shank
- Shank2
- streets of rage remake
- VT4
- ZackZero

## MUGEN game titles in the menu

- Cartoon Fighters 2010
- Coruscation Mugen
- Dragon Ball Z Sagas
- DragonBall Z M.U.G.E.N Edition 2011
- Hokuto no Ken
- King Of Fighters Shining
- Marvel vs Capcom 3 - Last Rise of Heroes
- Megaman Battle - Robot Master Mayhem
- Mortal Kombat Project 4.8
- Mortal Kombat vs Street Fighter
- Shades of Manhattan
- Super Marvel vs Capcom Eternity of Heroes
- Super Street Fighter 2 Turbo HD Remix
- Ultimate Mugen 2009
- World Heroes
- World Warriors X

Catalog XML was parsed locally; recoverable malformed XML was normalized only for metadata extraction, never in the source disk image. The `name_found_in_configured_directory` field is a basename-level observation, not an archive integrity check or a compatibility result. Existing references can point to missing or obsolete folders.
