# Stem Piano G - Firmware and Software Manual

## Firmware and Software Relationships

![](./diagrams/firmware_and_software_overview.png)

## Firmware Setup and Compiling

[./firmware_setup.md](./firmware_setup.md)

## Firmware Downloading

[./firmware_downloading.md](./firmware_downloading.md)

## Hammer - Settings and Runtime

The two most important firmware files are
* The settings file: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/ips2_hammer/hammer_settings.cpp
* The runtime file: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/ips2_hammer/src_hammer.cpp

### Hammer Settings: hammer_settings.cpp

To change a setting:
* Modify the value in downloaded code.
* Compile the firmware using Arduino software. See [./firmware_setup.md](./firmware_setup.md)
* Download the firmware to the Teensy. See [./firmware_downloading.md](./firmware_downloading.md).

Most settings are unlikely to change and are not listed here. The following settings may need adjustment for various reasons:

* debug_level - controls information displayed on Arduino serial monitor.

* calibration_threshold, calibration_match_gain, calibration_match_offset - calibration control values.

* damper_threshold_using_damper - threshold for sustain, when using optional damper board.

* damper_threshold_using_hammer - threshold for sustain, without optional damper board.

* strike_threshold, release_threshold, min_repetition_seconds, min_strike_velocity, hammer_travel_meters - piano key strike algorithm. Note that the algorithm does not use thresholds for calculating hammer velocity. The threshold is simple to disable the algorithm when a hammer is at rest. When at rest the signal can be noisy and lead to false strikes.

* pedal_threshold - when to decide a pedal is pressed.

* connected_channel[*] - for any unused or unconnected sensor, set to false to avoid electrical noise causing a note to play.

* teensy_ip, computer_ip, udp_port - For the copy of code on computer, edit *hammer_settings.cpp* and put values into the Teensy and computer IP addresses. If not using Ethernet, any numbers are ok.

## Hammer Runtime: src_hammer.cpp

The firmware consists of a Class for each major item of functionality. The firmware *src_hammer.cpp* declares and instantiates all classes.

The firmware *src_hammer.cpp* consists of two functions: setup() and loop().

* The setup() function runs once and initializes each Class.

* The loop() function runs repeatedly and calls methods of Class instances.

Within the loop() function is this statement:

*if (Tmg.AllowProcessing() == true)*

Everything within this if() statement runs at the ADC sample rate.

## Damper - Settings and Runtime

The two important firmware files are
* The settings file: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/ips2_damper/damper_settings.cpp
* The runtime file: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/firmware/releases/ips2_damper/src_damper.cpp

### Damper Settings: damper_settings.cpp

To change a setting:
* Modify the value in downloaded code.
* Compile the firmware using Arduino software. See [./firmware_setup.md](./firmware_setup.md)
* Download the firmware to the Teensy. See [./firmware_downloading.md](./firmware_downloading.md).

The damper IPS circuit board sends damper position values to the hammer IPS circuit board using CAN bus (see https://en.wikipedia.org/wiki/CAN_bus). The hammer IPS circuit board processes the damper values, combines with hammer position values, and sends results using MIDI. The damper processing is simpler than the hammer processing. Therefore, the settings file is smaller.

The setting called adc_sample_period_microseconds must be the same as for the hammer setting.

## Software

*documentation will be added in the future*