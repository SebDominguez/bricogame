# Hardware

[Back to the repository overview](../README.md)

## Cabinet

Owner-reported Bricogame upright cabinet with two players, two four-direction joysticks, six action buttons per player, four front service buttons and two side buttons. Counting each joystick direction separately gives **26 physical actions**. The supplied [control-panel diagram](../assets/control-panel.png) documents their positions and test order.

| Component | Identification | Evidence / outstanding detail |
|---|---|---|
| Cabinet | Bricogame | Commercial model, serial number and manufacturing year: **TBD** |
| Motherboard | **MSI A320M-A PRO, MS-7C51, revision 1.0** | Linux SMBIOS capture |
| Chipset / socket | AMD A320 / AM4 | Hardware inventory |
| CPU | **AMD Ryzen 3 3200G with Radeon Vega Graphics**, 4 cores / 4 threads | Linux and SMBIOS; 3,600 MHz observed, 4,000 MHz maximum reported by SMBIOS |
| GPU | Integrated AMD Radeon Vega, PCI `1002:15d8` | Linux `amdgpu`; no discrete graphics card identified in this capture |
| RAM | **8 GB / 8,192 MB**, 2,666 MHz observed in BIOS | Owner-reported; module count, manufacturer and part numbers: **TBD** |
| Disk examined | **Seagate ST1000DM010-2EP102**, SATA, 1 TB | SATA port 3 owner-reported; this is the replacement disk, not necessarily the failed original disk |
| Display | **Exact installed reference TBD** | LG 22MK600M was discussed from a multi-model product sheet, not confirmed from the installed monitor |
| Display dimensions | About 46.5 × 27 cm, owner-reported | Measurement boundary (panel/case), full enclosure dimensions, VESA, cable, native resolution and refresh rate: **TBD** |
| Speakers | **TBD** | Make, model, count, impedance, power, amplifier and volume control: **TBD** |
| Onboard audio | **Realtek ALC892**, plus AMD HDMI audio | ALC892 identified in the Linux kernel log; this does not identify the physical speakers |
| Input encoder | **Ultimarc Mini-PAC**, USB `d209:0440` | Keyboard mode in the captured Linux enumeration; board revision, firmware, terminal wiring and WinIPAC export: **TBD** |
| Joysticks / switches | 2 joysticks, 12 action buttons, 4 service buttons, 2 side buttons | Make, restrictor plates, switch models and wiring photographs: **TBD** |
| Ethernet | Realtek RTL8111/8168/8211/8411 family, PCI `10ec:8168` | Linux `r8169` |
| Other parts | **TBD** | ATX supply, monitor/audio supplies, fans, marquee lighting, main switch and any gun/coin hardware |

Linux exposes roughly 6 GiB of addressable RAM in the capture, while 8 GB is reported in BIOS. Memory reserved for integrated graphics is a possible explanation, but its allocation was not measured. Do not infer a missing RAM module from that discrepancy.

Several EDID records in the disk's Windows registry refer to LG, Acer, Samsung and other monitors. They are historical records from an image used with multiple systems; they do not establish the currently installed display. HyperSpin's configured **1360×768** resolution is also not evidence of the monitor's native resolution.

## BIOS

| Item | Observed / reported value |
|---|---|
| Vendor | American Megatrends / AMI |
| Earlier version | Owner-reported `E7C51AMS.130`, 2019-11-08 |
| Updated version | Owner-reported `E7C51AMS.196`; SMBIOS reports `1.96`, release date 2026-08-14 |
| Windows boot mode | CSM, owner-reported |
| XHCI Hand-off | Enabled |
| Legacy USB Support | Enabled |
| DRAM Frequency | Auto |
| Memory Fast Boot | Enabled |
| Memory Failure Retry | Enabled |

The BIOS reportedly detects two keyboards and one USB mouse. The M-FLASH update completed but did not resolve Windows USB failure. These are recorded settings, not a recommendation to force CSM on another OS installation.

## Disk image and partitions

The source is a **raw disk image**, not a Windows installation ISO:

- Size: **1,000,204,886,016 bytes**.
- MBR/DOS partition table; disk signature `0x1652460c`.
- Logical sectors: 512 bytes; physical sectors reported by the disk: 4,096 bytes.

| Partition | Start sector | Sector count | Size in bytes | Role in the installed setup |
|---|---:|---:|---:|---|
| 1, active, NTFS | 206848 | 102207527 | 52330253824 (~48.7 GiB) | Windows and `C:\` paths |
| 2, NTFS | 102414375 | 1851110793 | 947768726016 (~882.7 GiB) | HyperSpin/game data and `D:\` paths; label `Nuevo vol` |

Linux enumerated these as `/dev/sda1` and `/dev/sda2` in the supplied capture. Device names can change on another boot.

## Rescue environment

The inventory was captured using **SystemRescue**, with label `RESCUE1302` and boot path `/sysresccd/boot/x86_64/vmlinuz`, identifying a **13.02** rescue medium. The captured inventory includes CPU, PCI, USB, input, SMBIOS, disk and kernel observations. A [sanitized copy of all nine captured files](../evidence/linux-inventory/README.md) is included. Unit serials and network identifiers are redacted; firewall packet lines are omitted.
