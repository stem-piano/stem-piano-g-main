# Stem Piano G - Firmware Downloading

## USB Cable And +5 Volt Power - The Problem

A USB cable connects from an external computer to the Teensy 4.1 processing system.

The USB cable has two purposes:
- Send firmware from computer to the Teensy 4.1
- Serial monitor connection.

Also, it can provide +5 volt power from a computer to the Teensy and all *stem piano* circuit boards.

When 8 or less HPS are connected to the IPS mainboard, the computer can probably deliver enough current for all *stem piano* circuits through the USB cable.

With a full 88 sensor setup, a computer cannot deliver enough current for all *stem piano* circuits through the USB cable.

When the computer cannot deliver enough current, the IPS board has a +5 volt power input, J1. However, using an external +5 volt power at J1 presents a problem because the USB cable is also sending +5 volts power.

See the warnings document in the *DIY-Grand-Digital-Piano* repository:

https://github.com/stem-piano/stem-piano-top/blob/main/WARNINGS.md

## USB Cable And +5 Volt Power - Solution

See figure of power connections below.

![](./diagrams/usb_power.png)

For sending firmware to the Teensy while also connected to the external +5 volt power input at J1, the Teensy manufacturer's website https://www.pjrc.com/ explains solutions to this problem https://www.pjrc.com/teensy/external_power.html

Do not connect jumper J12 or external +5V power until the "5V" pad is cut according to PJRC instructions.

## Initial Download

When initially downloading firmware to the Teensy, may need to push the download button on the Teensy.

## Strategy When Using Hammer and Damper Boards

If running Arduino software for both hammer and damper Teensy simultaneously, use the serial monitor to keep track of which USB is connected to each Teensy. The serial monitor can display the Teensy connection.