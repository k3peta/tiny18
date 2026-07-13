# Tiny18

Tiny18 is a compact, 18-key wireless split keyboard designed for Japanese input. Each half uses a Seeed Studio XIAO nRF52840 and ZMK firmware.

日本語の説明は [`README.ja.md`](README.ja.md) を参照してください。

[Download the latest firmware](https://github.com/k3peta/zmk-config-tiny18/releases/latest) · [Firmware source](https://github.com/k3peta/zmk-config-tiny18) · [Keymap](https://github.com/k3peta/zmk-config-tiny18#default-keymap)

## Features

- 18 keys total (9 per half)
- Wireless split using Bluetooth Low Energy
- Seeed Studio XIAO nRF52840 controllers
- Kailh Choc (PG1350) switch footprints
- Diodeless, direct-pin wiring
- Reversible PCB: the same board is used for both halves
- Battery connector and hardware power switch on each half
- ZMK Studio support on the right/central half over USB

## Repository contents

This repository contains the production outputs for the PCB. The ZMK source and downloadable UF2 firmware are kept in the separate [zmk-config-tiny18](https://github.com/k3peta/zmk-config-tiny18) repository so that firmware builds remain small and reproducible.

| Path | Purpose |
| --- | --- |
| [`production/Tiny18mini.zip`](production/Tiny18mini.zip) | Gerber and drill files for PCB fabrication |
| [`production/bom.csv`](production/bom.csv) | Bill of materials exported from KiCad |
| [`production/positions.csv`](production/positions.csv) | Component placement data |
| [`production/designators.csv`](production/designators.csv) | Reference designator data |
| [`production/netlist.ipc`](production/netlist.ipc) | IPC-D-356 netlist for fabrication checks |

See [`production/README.md`](production/README.md) before ordering boards.

## Firmware

Prebuilt firmware is distributed from the [firmware Releases page](https://github.com/k3peta/zmk-config-tiny18/releases/latest). A release contains:

- `tiny18-right.uf2` — right half and Bluetooth central
- `tiny18-left.uf2` — left half and Bluetooth peripheral
- `settings-reset.uf2` — clears saved Bluetooth and split settings
- `SHA256SUMS` — checksums for the UF2 files

The right and left files are not interchangeable. Flashing the wrong file will not normally damage the controller; enter the bootloader again and flash the correct file.

### Flashing

1. Turn the keyboard's battery power switch off. Connect one half to the computer with a USB data cable.
2. Double-press the XIAO reset button. A drive named `XIAO-SENSE` should appear.
3. Copy the matching UF2 file to that drive:
   - right half: `tiny18-right.uf2`
   - left half: `tiny18-left.uf2`
4. Repeat for the other half, then disconnect USB and turn both halves on.
5. Pair the Bluetooth device named `tiny18` from the host computer.

For first-time setup, or when the halves no longer pair, flash `settings-reset.uf2` to both halves first. Enter the bootloader again, then flash the matching right and left firmware.

After clearing settings, remove the old `tiny18` entry from the host's Bluetooth settings before pairing again.

## Safety and scope

- Verify battery polarity before connecting a LiPo battery. Reversed polarity can damage the controller or battery.
- Turn battery power off while flashing over USB.
- These files are provided as-is. PCB fabrication, assembly, battery selection, and physical testing remain the builder's responsibility.
- The repository does not currently include a case or switch plate.

## License

The hardware production files in this repository are licensed under [CERN-OHL-P-2.0](LICENSE); see [`NOTICE`](NOTICE). Firmware is licensed separately under the MIT License in the firmware repository. Third-party components retain their own licenses.
