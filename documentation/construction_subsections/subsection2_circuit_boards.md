# Stem Piano G - Manufacturing Circuit Boards

Some released circuit boards also include KiCad project files. Links below are to the Gerber files. The KiCad files are in same directory location.

## Review boards

Before sending to fabrication, make sure each board does not require changes. Changes could be for a component issue, a design issue, or an improvement. Take a look at the *Issues* list
* https://github.com/gzweigle/DIY-Grand-Digital-Piano/issues
* https://github.com/stem-piano/stem-piano-g-main/issues

Make sure the boards comply with your requirements for the piano and environment.

If changes are required, make the changes to the schematic and layout, then purchase boards.

## Verify parts availability

Before making circuit boards, review the bill of materials for each board and verify ability to acquire all components for the boards. For example, if a component has been obsoleted, is unavailable in required time-frame, has restrictions, or if a component has changed, it is better to know this before purchasing the circuit boards.

If changes are required, make the changes to the schematic and layout, then purchase boards.

## Select a circuit board manufacturer

Verify the manufacturer can make the boards as designed. If changes are needed, first make the change to the schematic and layout. Then, send to the manufacturer.

## Send the mainboard (IPS) Gerber files to the PCB manufacturer and order one board

* File location: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/ips20/ips20_gerber

## Send the analog board (SCA) files to the PCB manufacturer and order one board

* File location: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/sca01

## Send the sensor board (HPS) Gerber files to the PCB manufacturer and order 88 boards

Before building the boards, please read the HPS design document https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/design/hps_cny70/hps_cny70.md

Four board options:

* Option #0 (recommended for surface mount) - The surface mount board without trimming resistor. Location: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/hps08

* Option #1 - The board with a trimming resistor. This board is more expensive but may give better control over note accuracy. It is not recommended because it is expensive and because of potential to incorrectly adjust such that the current load exceeds the voltage regulator capability. File location: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/hps07/hps07_gerber

* Option #2 (recommended if do not want surface mount components) - The board without a trimming resistor. File location: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/hps04/hps04_gerber

* Option #3 - Any sensor board that meets the interface specification will work.

## Send the pedal level shift (PLS) Gerber files to the PCB manufacturer and order one board

File location: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/pls00

## Send the optional analog condition equalize A (ACE A) files to the PCB manufacturer and order one board

Original - This has been tested:

https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/aceA00

Updated - This is not yet tested:

https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/aceA01
