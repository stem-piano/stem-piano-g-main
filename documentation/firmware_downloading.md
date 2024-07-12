# Stem Piano G - Firmware Downloading

## USB Cable And +5 Volt Power - The Problem

A USB cable connects from an external computer to the Teensy 4.1 processing system.

The USB cable has three purposes:
- Send firmware from computer to the Teensy 4.1
- Provide +5 volt power from a computer to the Teensy and all *stem piano* circuit boards.
- Serial monitor connection.

When 8 or less HPS are connected to the IPS mainboard, the computer can probably deliver enough current for all *stem piano* circuits through the USB cable.

With a full 88 sensor setup, the computer probably cannot deliver enough current for all *stem piano* circuits through the USB cable.

When the computer cannot deliver enough current, the IPS board has a +5 volt power input, J1. However, using an external +5 volt power at J1 presents a problem because the USB cable is also sending +5 volts power.

See the warnings document in the *DIY-Grand-Digital-Piano* repository:

https://github.com/stem-piano/stem-piano-top/blob/main/WARNINGS.md

## USB Cable And +5 Volt Power - Solution

See figure of power connections below.

One option is to never connect the external +5 volt power source (at J1) and the USB cable simultaneously. The IPS includes a jumper, J12, as a reminder. When the jumper is disconnected, the external +5 volt power supply is disconnected. Also, the circuit board includes warnings printed on the circuit board.

![](./diagrams/usb_power.png)

The problem with this option is that powering all 88 sensors requires using the external +5 volt power source. In this case, the USB is unusable. So, the Teensy cannot be reprogrammed.

For sending firmware to the Teensy while also connected to the external +5 volt power input at J1, the Teensy manufacturer's website https://www.pjrc.com/ explains solutions to this problem https://www.pjrc.com/teensy/external_power.html

The recommended option is cutting the "5V" pad.


## Initial Download

When initially downloading firmware to the Teensy, may need to push the download button on the Teensy.

## Strategy When Using Hammer and Damper Boards

If running Arduino software for both hammer and damper Teensy simultaneously, use the serial monitor to keep track of which USB is connected to each Teensy. The serial monitor can display the Teensy connection.