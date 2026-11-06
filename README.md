# Bricogame arcade cabinet: configuration and reverse engineering

Documentation of one **Bricogame two-player arcade cabinet**, its Windows installation, launcher configuration and Ultimarc Mini-PAC controls. The inspected hardware is an **MSI A320M-A PRO (MS-7C51 rev. 1.0), Ryzen 3 3200G and 8 GB RAM**. The supplied disk contains **Windows 7 Professional SP1 x64, HyperSpin 1.3.2.0 and HyperLaunch 2.25c**.

This repository contains **configuration and documentation only**. There are no ROMs, BIOS images, emulator executables, Windows binaries, game installations or activation secrets. Game titles and file hashes are inventory metadata, not game content.

## Why this repository exists

I started this work after a very poor customer-service experience with **bricogame.es**, including what I consider questionable commercial practices and poor build quality in my cabinet. Following a hard-drive failure, I paid for a replacement disk that arrived with a Windows/driver configuration unsuitable for my hardware.

What particularly motivated me was the effort to keep the setup closed: according to my experience with support, they refused to send me an ISO or disk image so I could correct the configuration problem, and instead required me to return the physical drive for another replacement. Inspecting the disk revealed a preconfigured Windows installation using HyperSpin and existing emulators. The image examined here runs Windows 7; this is not a claim about every cabinet the company has sold.

This project is intended for other customers who want control over their own system: understanding how it works, repairing configuration errors, improving it, and retaining the option to move to another system such as Batocera. The support history and quality assessment above are my account and opinion; the technical findings below are tied to the specific inspected image and hardware.

**Work in progress.** I am considering a future cabinet auto-configuration script for Batocera. Nothing in this repository currently implements or validates that migration. Development pace will depend in part on community interest. If this would be useful to you, please let me know through [my contact page](https://sebastien.bio.link/).

## Documentation

| Document | Contents |
|---|---|
| [Hardware](docs/hardware.md) | Components, BIOS, display/audio unknowns and disk layout |
| [Windows and USB failure](docs/windows-and-usb.md) | Installed OS, actual controllers, driver mismatch and failure timeline |
| [Startup and customization](docs/startup.md) | Automatic login, TurboSheller, replacement boot animation and black login resources |
| [HyperSpin and HyperLaunch](docs/frontend.md) | Versions, folder layout, launch settings and configuration precedence |
| [Mini-PAC and control mapping](docs/controls.md) | Diagram, 26 measured actions, raw evtest capture and MAME bindings |
| [Emulator configuration](docs/emulators.md) | Launchers, shared ROM paths and archived configuration entry points |
| [Game inventory](docs/games.md) | Catalog counts, Windows/MUGEN titles and links to inventory metadata |
| [Evidence and backup scope](docs/evidence-and-backup.md) | What was extracted, what remains in the private image and evidence limits |
| [Configuration index](config/README.md) | Where each captured configuration came from and how it was handled |
| [Contributing](CONTRIBUTING.md) | Reporting corrections and sharing configuration safely |

## Read the evidence correctly

- **Verified** means a captured Linux observation, registry value or file was inspected.
- **Owner-reported** means a physical observation or support-history statement supplied by the owner.
- **Inference** means an interpretation that has not been established by a runtime test.
- **TBD** means an important detail is still missing.

The original image was opened read-only. Programs extracted from it were not executed during analysis. Configuration files describe recorded settings, which can differ from the settings actually loaded at runtime. The Linux controller test is not a firmware or EEPROM dump. The [sanitized SystemRescue inventory](evidence/linux-inventory/README.md) retains the detailed hardware observations behind the summary.

Start with [the USB mismatch](docs/windows-and-usb.md) and [the measured controls](docs/controls.md): both matter when trying to understand the original setup. Do not apply registry observations or old startup patches blindly to a different Windows installation.
