# Evidence and private backup scope

[Back to the repository overview](../README.md)

## What was preserved privately

The owner retains a raw disk image of **1,000,204,886,016 bytes** and a payload/configuration extraction completed on **2026-11-04 at 09:13:25 Europe/Madrid**:

- **235,167 files**.
- **743,873,138,049 bytes** (~743.87 GB / 692.79 GiB).
- No extraction errors recorded.
- Each output file was re-read locally and SHA-256 checked against the hash computed during extraction.

The image was opened read-only. Source size and modification timestamp were unchanged at the end. This is not a full-image SHA-256 verification: a hash of the entire image has not been recorded. The extracted tree was later found relocated to the owner's NAS; the subsequent transfer has not been independently hash-audited in full.

The initial extraction covered C:\ROMS and D:\hyperspin1.0\Emulators, Settings, Databases, Modules and Module Extensions. It did not extract every file in Windows or every frontend resource. “Complete” means complete for that extraction plan.

## Files intentionally outside this repository

| Private content | Reason it remains useful |
|---|---|
| Raw image and extraction manifest | Complete source and per-file verification metadata |
| Frontend root executables and DLLs | Original runtime versions and helper launchers |
| Media / HyperTheme trees | Original appearance, videos, logos and intros |
| Game, ROM, BIOS, table and CHD payloads | Actual playable data and dependencies |
| User profiles, My Games and AppData | Saves and settings not located beside games |
| Windows registry hives and installed applications | Shell configuration, runtime registrations and potentially private activation/account data |
| Boot DLLs, loaders and stored alternatives | Original customization evidence; binary hashes only are shared here |
| TSheller and supporting tools | Original shell replacement and boot customization utilities |
| Public Documents / Amiga Files | Additional WinUAE resources/settings |
| AimTrak installer folder | Possible gun-related tools; directory presence is not proof of installed gun hardware |

C:\ROMS contains only desktop.ini, VirtuaTennis2009/vt2009_save.bin and Zen Studios/Profile backup/226980/Profile.dat (Pinball FX2 profile). It is not the main game library.

## Public evidence

- [Raw Mini-PAC event capture](../evidence/minipac-evtest.txt).
- [Physical panel diagram](../assets/control-panel.png), supplied by the owner.
- [Launcher resource/script version observations and hashes](../evidence/launcher-versions.json).
- [Boot/authentication file hashes](../evidence/windows-boot-file-hashes.json).
- [Installed AMD USB hub INF](../evidence/amd-usb-hub-oem8.inf) and [xHCI INF](../evidence/amd-xhci-oem9.inf).
- [Selected registry observations](../config/windows/registry-observations.json), with no login password.
- [Configuration provenance](../metadata/config-provenance.json): original/published SHA-256, source-relative location and sanitization status.
- [Credential-field redaction record](../metadata/redactions.json), containing field names rather than removed values.

Full registry hives, raw kernel logs, hardware serial numbers, network addresses and activation material are intentionally excluded. The publication review is not a substitute for reviewing future contributions.

## Remaining unknowns

Installed monitor reference and EDID, audio hardware, RAM module references, power supplies, physical wiring, Mini-PAC board/firmware and WinIPAC export, shifted inputs and simultaneous-player behavior, exact secondary emulator/core versions, effective launcher overrides, and the precise binary patches applied to Windows loaders.

Historical Windows device records must not be substituted for current physical identification. Recorded configuration is not proof of effective runtime behavior. No broad game-compatibility or repaired-Windows test has been performed on this cabinet during this investigation.
