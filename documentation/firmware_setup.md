# Stem Piano G - Firmware and Software Setup

## External Software

### Arduino

See internet for details of installing and using the Arduino software.

### Teensy Development Board

See https://www.pjrc.com/ for instructions related to the Teensy 4.1 Arduino setup.

### Adafruit 2.8" TFT Display

The display is optional. The firmware default is not including the display.

Go to the manufacturer web site and follow instructions for installing Arduino libraries. The manufacturer is listed in the IPS2 part file. Link: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/hardware/releases/ips20/ips20_bill_of_materials_0.txt

Adafruit 2.8" TFT display and Teensy library conflict:
* The Adafruit 2.8" TFT display requires an AdaFruit library for the SD card that conflicts with the library for the SD card on the Teensy.
* As a temporary fix, after all libraries are installed, delete the SdFat/ directory from the Teensy library location (instead of deleting, it is probably better to move the directory to another location in case the directory is needed for another project in future). Deleting SdFat/ will cause warnings when building the project.
* If libraries update in the future, may need to delete SdFat/ again.
* The SdFat/ directory is likely in the Teensy library directory location, not the Arduino library directory location.

If not using the optional Adafruit 2.8" TFT display, comment out the TFT display #define in *stem_piano_ip2.h*. Then the Adafruit 2.8" TFT display is not required and deleting the Teensy SD library is not required.

* Link to code: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/StemPianoIPS2/src/stem_piano_ips2.h.

The default in code is TFT display commented out (disabled).

For simplest initial board bring up, it is easiest to skip the TFT display. Can add later.

## Stem Piano Firmware and Software Overview
![fw_and_sw](./diagrams/firmware_and_software_overview.png)

## Getting Source Files from GitHub

* https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/firmware/releases/StemPianoIPS2
* https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/firmware/releases/ips2_hammer
* https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/firmware/releases/ips2_damper

Damper is optional.

For the copy of code on computer, rename *src_hammer.cpp* to *src_hammer.ino*.

## Edit Ethernet Address in Hammer Settings

Link: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/ips2_hammer/hammer_settings.cpp

For the copy of code on computer, edit *hammer_settings.cpp* and put values into the Teensy and computer IP addresses. If not using Ethernet, any numbers are ok. To avoid a syntax error, comment out or remove the line about needing to edit the Ethernet values.

## Compilation Configuration

For the TFT display.

Open *stem_piano_ips2.h*.
Link: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/StemPianoIPS2/src/stem_piano_ips2.h

* If not using the TFT, comment out the line *#define TFT_INSTALLED*. This is the default.
* If using the TFT, keep the line *#define TFT_INSTALLED*.

For simplest initial board bring up, it's best to not use the TFT display.

## Compile

Use the Arduino software.

Select Teensy 4.1 as the board in the board manager.

Compile the project without selecting the download step.

If it does not compile, see the https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/HELP.md file and the repository *Issues* list. Also, check Arduino and Teensy web pages.

Another source of help is the https://www.pjrc.com/ website.

If it does compile, the boards are now ready to install firmware.