# Stem Piano G - Initial Testing

Video links in documentation below are to the *stem piano* historical progress videos on YouTube: https://www.youtube.com/@gzpiano88.

## Setup

Do not connect the +5V external power supply for this step. The board is powered through the Teensy 4.1 USB cable.

Do not install jumper J12 on IPS2 printed circuit board.

Make sure all DIP switches on IPS2 are in their off position. If switches were not installed, this step is not necessary.

There is no need to connect a MIDI or Ethernet cable for this step.

## Connect a single HPS board

### Check HPS Voltages

Before connecting the HPS, verify correct voltage level following this procedure: [../hps_testing.md](../hps_testing.md)

### Connect a single HPS board

For simple initial test, connect a single HPS board to the IPS board.

Each HPS board is marked with a plus (+) symbol, a minus (-) symbol, and an exclamation point (!) symbol.

The pins on the IPS board are market with a "3.3V" symbol, a "gnd" symbol, and an "in" symbol.

Select the triplet of pins on the IPS board that are closest to the +5V power input and connect (+) to "3.3V", connect (-) to "gnd", and connect (!) to "in". The connection in this initial test is for the lowest note on a piano, A0. It is data index 0 in the firmware.

Modify the firmware settings to disable unused inputs.

## Connect USB to Teensy and power up

Connect a USB cable to the Teensy. Because the board is powered through the USB cable, use a normal USB cable without modification (later steps may require modifying a cable to remove the power connections).

Connect the opposite side of the USB cable to a computer.

The IPS, SCA, and a single HPS board are now powered!

## Download

Please follow steps in the [../firmware_downloading.md](../firmware_downloading.md) manual. Then return to this step.

If LED are installed on the IPS circuit board, they should begin blinking.

Optionally measure the voltage at the 3.3 volt pin on lower right of IPS board with a multimeter to check that it reads 3.3 volts.

If no LED are not blinking or no voltage is measured, disconnect USB cable from computer and see the https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/HELP.md file and also the https://github.com/gzweigle/DIY-Grand-Digital-Piano/issues.

## Test it works?

Open a serial monitor in Arduino. A set of startup messages should display from the firmware running on the Teensy. If not, the problem could be with the Arduino serial connection. Or, the problem could be with the board.

Example startup message:

![](../pictures/startup_example.jpg)

Use a rectangle of white cardboard and try to "play a note" by quickly moving the cardboard toward the CNY-70 sensor. See *stem piano* video https://youtu.be/NmziaIYKS1g?t=115.

A message should appear in the Arduino serial monitor that a note was sent to MIDI.

## Test with a MIDI cable

Power down.

Connect a MIDI cable from IPS to a computer.

Run software on an external computer that converts MIDI to sound. Before using with *stem piano*, check that the external software is working by using an existing MIDI keyboard or source.

Turn the speaker volume to a low level.

Power up.

"Play the note" again. Using the cardboard. Should hear a sound.

## Celebrate, just a little

If at this step, congratulations, most of the project risk is eliminated. See *stem piano* video https://youtu.be/M1_228-ClXM?t=321.

To eliminate even more risk, test other HPS boards and other IPS input pins. Test several simultaneously.

As more HPS sensor boards are connected to the IPS board, the total current draw of the system increases. Do not connect more than eight HPS while powering the system with the USB cable to Teensy processor.

## Disconnect the USB cable

For future steps, a modified USB connection is required.