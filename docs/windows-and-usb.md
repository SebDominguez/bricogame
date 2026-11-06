# Installed Windows and USB failure

[Back to the repository overview](../README.md)

## OS identified in the image

| Registry field | Value |
|---|---|
| ProductName | Windows 7 Professional |
| CSDVersion | Service Pack 1 |
| Architecture | x64 / AMD64 |
| CurrentVersion | 6.1 |
| CurrentBuild | 7601 |
| BuildLabEx | `7601.18247.amd64fre.win7sp1_gdr.130828-1532` |

The BuildLabEx string alone does not establish the patch level of every installed component. Parts of the interface and paths are Spanish. The configured automatic-login account is `arcade`; another profile named `usuario` exists.

## Why this particular supplied image is unsuitable as delivered

MSI lists Windows 10 x64 and limits Windows 7 x64 support on this board to **Summit Ridge / Pinnacle Ridge** CPUs. The installed **Ryzen 3 3200G** is outside those two families. Thus the precise finding is that this Windows 7/driver image is unsuitable **as delivered for this hardware**. It would be inaccurate to say the motherboard can never support Windows 7 with any CPU. [MSI specification](https://us.msi.com/Motherboard/A320M-A-PRO/Specification).

The stronger, image-specific evidence is the controller-ID mismatch below.

| Actual USB controller, captured under Linux | PCI ID | Linux driver |
|---|---|---|
| AMD A320 USB 3.1 xHCI | `1022:43bc` | `xhci_hcd` |
| AMD Raven USB 3.1 | `1022:15e0` | `xhci_hcd` |
| AMD Raven USB 3.1 | `1022:15e1` | `xhci_hcd` |

The Windows image contains AMD `amdxhc.sys` and `amdhub30.sys`, described by `oem9.inf` and `oem8.inf` as version **1.1.0.167, 2015-01-21**. The xHCI INF only declares:

```text
PCI\VEN_1022&DEV_7812
PCI\VEN_1022&DEV_7814
PCI\VEN_1022&DEV_7914
```

**None of the actual three controllers is covered by that INF.** No suitable Ryzen/Promontory USB package was identified in the inspected driver store. The text INFs are retained as [xHCI evidence](../evidence/amd-xhci-oem9.inf) and [hub evidence](../evidence/amd-usb-hub-oem8.inf); driver binaries are excluded.

The image also contains standard Microsoft USB/HID drivers and AMD `usbfilter`, registered as a USB-class upper filter. Its contribution, if any, has not been isolated. The xHCI service has `Start=3` (demand start), which is not by itself evidence that the service is disabled.

All connected devices in the Linux USB-tree capture, including low/full/high-speed devices, are attached through xHCI. A missing controller driver can therefore affect the keyboard, mouse and Mini-PAC together. Windows 7 depends on third-party USB 3 driver stacks. [Microsoft USB driver FAQ](https://learn.microsoft.com/en-us/windows-hardware/drivers/usbcon/usb-faq--introductory-level).

**Main diagnosis:** missing/incompatible xHCI support in the replacement image. No repaired clone has yet been tested to prove a particular corrective driver or procedure.

## Owner-reported failure timeline

1. The cabinet operated with its earlier disk, which failed.
2. Support supplied a paid, preconfigured replacement disk.
3. After installation and Ethernet connection, Windows displayed a restart request.
4. USB controls were already unavailable when attempting to confirm that dialog; the cabinet was restarted physically.
5. USB remains unavailable in this Windows installation, while the same devices work in BIOS and live Linux.
6. A later BIOS update did not resolve the problem.

An automatic update or forced restart has **not been proven to cause the failure**. The restart prompt is a chronological observation, not a diagnosis. The BIOS update occurred after the initial problem and therefore cannot explain its onset.

Passive USB-to-PS/2 adapters were also tried unsuccessfully. That does not prove PS/2 hardware failure: such adapters require devices that support both protocols.
