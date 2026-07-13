# Production files

`Tiny18mini.zip` contains the Gerber and drill files for one reversible Tiny18 PCB. Order two copies to build a complete keyboard.

## Before ordering

- Upload `Tiny18mini.zip` to the PCB manufacturer's Gerber viewer and confirm the board outline, copper, solder mask, and drill layers.
- Do not rename or unpack individual Gerber files unless the manufacturer requires it.
- This is a reversible design. The same PCB is assembled in opposite orientations for the left and right halves.
- The BOM is exported per PCB. A complete split keyboard requires two XIAO nRF52840 controllers, 18 Kailh Choc switches, two power switches, and the corresponding battery hardware.
- The two battery-connector designators represent alternative front/back placements on a reversible PCB. Populate only the footprint appropriate to the assembled side.
- Confirm component orientation and battery polarity against the physical PCB before applying power.

The CSV and IPC files are manufacturing references. They are not firmware and are not needed when flashing an assembled keyboard.

