# Sanitized Linux inventory

These nine text files were captured from the cabinet using SystemRescue (rescue-medium label `RESCUE1302`). They preserve the detailed observations behind the documentation, rather than only its summary.

| File | Captured information |
|---|---|
| cpu.txt | CPU model, cores, feature flags, caches, reported clocks and vulnerability/mitigation status |
| pci.txt | Full PCI device enumeration, subsystem IDs, addresses and bound Linux drivers |
| usb.txt | USB device IDs and names |
| usb-tree.txt | USB topology, link speeds and interface drivers |
| input.txt | Linux input interfaces, event handlers and supported event/key bitmaps |
| hardware.txt | SMBIOS firmware, motherboard and processor descriptors |
| disks.txt | Block devices, filesystems, labels and rescue mount points |
| partitions.txt | Sector sizes, partition starts, sector counts and disk layout |
| kernel.txt | Captured boot/device messages, USB initialization, audio codec detection and diagnostics |

## Publication changes

Hardware/USB unit serials, nonempty input unique values, MAC addresses and private IP addresses are redacted. Firewall packet-log lines are omitted because they describe local network traffic rather than the cabinet configuration. PCI topology addresses, VID/PID values, model names, driver names and the disk's MBR signature are retained. The generic rescue hostname is retained.

The original archive was not modified. `provenance.json` records source/published file hashes and redaction counts without disclosing removed values. No game data, registry hives or firmware images are included.

The original private archive is only needed if the removed identifying information or original packet logs matter to a later investigation. This sanitized copy contains the remaining captured technical observations. It does not fill gaps that were never measured, such as the installed monitor label, speaker references or Mini-PAC firmware.
