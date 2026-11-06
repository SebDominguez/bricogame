# Configuration archive

These files document the inspected installation. They are **not an automated installer** and should not be applied blindly to a different system.

| Directory | Source and contents |
|---|---|
| hyperspin/Settings | Text configuration from D:\hyperspin1.0\Settings, including nested INIs |
| emulators | Global/default MAME bindings and selected standalone/RetroArch configuration entry points |
| windows | Selected startup, login-background and keyboard-remapping registry observations |

Documentation is in English. Functional source configurations retain their original language, casing, encoding, directory names and values unless sanitized. Translating a literal path or changing a key name could change behavior, so those files are not editorial translations.

Source data may contain redundant profiles and conflicting overrides. Original absolute C:/D: paths are part of the recorded setup. Values from generic examples and inactive profiles must not be assumed to be active.

Potential credentials in recognized fields are removed when populated. Private LAN IP/MAC values are replaced with placeholders. Any altered file is identified by differing source/published hashes and the `sanitized` flag in [the provenance record](../metadata/config-provenance.json). Such placeholders may require local adjustment before a file can be used.

The repository excludes executable code extracted from launchers, emulator binaries, driver binaries, BIOS, ROMs, media themes, saved progress and raw registry hives. The two USB INFs in evidence are text descriptions of the installed driver packages, not a working driver installation.
