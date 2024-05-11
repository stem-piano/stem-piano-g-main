# Stem Piano G - Users Manual

Manual for use of Stem Piano G after assembly is complete.

## Quick Start Guide Without Damper Board

For easiest quick start, first get the system working without a separate damper board. Add the damper board later.

The following figure shows the connections and main components for *stem piano*. The 2.8 inch TFT display is not included in the figure.

The quick start setup does not include an Ethernet connection or TFT display option.

![hammer_setup](diagrams/stem_piano_hammer_setup.png)

1. Turn all switches to the OFF position. If switches were not soldered onto the board, the default value is OFF.

2. Connect a sustain pedal to quarter inch connection as shown in figure top right.

3. Connect a 6-pin serial MIDI cable from the *stem piano* to a computer.

4. Run MIDI-based software sound synthesizer software on computer.

5. Connect computer to speakers. Turn on speakers.

6. Connect the +5V power connection to the *stem piano*. Because *stem piano* does not have a power switch, put the power connection on an external switch.

7. Turn on the power switch.

8. Wait until LEDs on the board being blinking. The delay is approximately 5 seconds.

9. Play piano!

## Teensy USB

During normal operation, the Teensy USB is not required and should not be connected. See [./firmware_downloading](./firmware_downloading.md) for information on the USB cable.

## Configuration Switches

Move switch position with a thin wood or plastic utensil. Use something nonconductive.
* Moving switch to right is OFF
* Moving switch to left is ON

The state of an uninstalled switch is OFF. The piano is in normal state with all switches in the OFF position.

![](./diagrams/switches.png)

### ips_sw1_position2 (DAMPER_THRESHOLD)
* Upper left switch next to MIDI connector on the IPS circuit board.
* OFF = Normal damper threshold.
* ON = High damper threshold.
* Normally in the OFF position
* Can use to debug dampers not releasing.

### ips_sw1_position1 (EXTERNAL_DAMPER_BOARD)
* Below ips_sw1_position2
* OFF = No damper board. Dampers are estimated from hammer position.
* ON = The optional external damper board is connected. Damper position is measured by the damper board and then sent to the hammer board.

### ips_sw2_position2 (ENABLE_ETHERNET)
* Below ips_sw1_position1.
* OFF = Ethernet is disabled. No Ethernet cable is needed.
* ON = Ethernet is enabled. Piano will not function unless an Ethernet cable is connected.

### ips_sw2_position1 (ENABLE_TFT)
* Below ips_sw2_position2.
* OFF = TFT displays default message. Normal piano operation.
* ON = TFT displays maximum hammer position and other diagnostic information. MIDI is disabled. Piano does not play sound.

### sca_sw2_position2 (UNUSED)
* Upper switch on SCA card.
* Not used.

### sca_sw2_position1 (DYNAMIC_RANGE_SETUP)
* Below sca_sw2_position2.
* OFF = Normal piano playing.
* ON = Velocity dynamic range setup.

### sca_sw1_position2 (FREEZE_CAL_VALUES)
* Below sca_sw2_position1.
* OFF = Calibration values are updated while piano is played. See below.
* ON = Calibration values are frozen.
* OFF->ON = When move switch from OFF to ON, the present calibration values are stored into nonvolatile memory.
* ON->OFF = No effect on nonvolatile memory.

### sca_sw1_position1 (DELETE_CAL_VALUES)
* Below sca_sw1_position2.
* OFF = Calibration values are applied to signals normally.
* ON = Disable calibration. No calibration values are applied to signals. Most likely the volume will be uneven. See below.
* OFF->ON = When move switch from OFF to ON, the calibration values in nonvolatile memory are deleted.
* ON->OFF = No effect on nonvolatile memory.

## Velocity Dynamic Range Setup

Each piano action is unique and will have slightly different minimum and maximum velocities.

If hammers swing approximately 1.75 inches, the default velocity range may work ok. If not, follow these steps below.

(Turn down speaker volume during these steps. Do this because if the velocity dynamic range is accidentally recorded incorrectly, MIDI output could be maximum volume. If a problem occurs, repeat the following steps until good results are obtained.)

* Make sure calibration is complete (see instructions below).
* Turn the velocity dynamic range switch (sca_sw2_position1) to ON.
* Strike several notes with maximum velocity. Select multiple keys from bass to treble.
* Turn the velocity dynamic range switch (sca_sw2_position1) to OFF.

While the sca_sw2_position1 (DYNAMIC_RANGE_SETUP) switch is ON, previous dynamic range values are used. When the switch is moved back to OFF, new values are applied.

(*FUTURE*) - Velocity dynamic range values are stored in nonvolatile memory and reapplied after a power cycle. To avoid loud notes after changing the frame or sensor positions, turn on power with sca_sw1_position1 (DELETE_CAL_VALUES) in the ON position.

Other scaling values are possible by editing the settings file. See [Firmware Manual](./firmware_manual.md).

## Calibration

### Overview

Each of the 88 CNY-70 sensors on the HPS circuit boards exhibits a slightly different response when measuring the hammer or damper position.

During calibration the *stem piano* firmware measures the maximum and minimum sensor output values and applies those values to calibrate the CNY-70 sensor response in real time.

Without calibration, the piano will likely sound uneven when playing. This is similar to the situation of a poorly voiced piano. Some notes may not make any sound.

### Calibration Control with Switches

When sca_sw1_position2 (FREEZE_CAL_VALUES) and sca_sw1_position1 (DELETE_CAL_VALUES) switches are both OFF, the *stem piano* firmware continuously measures the CNY-70 values, updates the calibration values, and applies calibration values to the CNY-70 measurements.

When sca_sw1_position1 (DELETE_CAL_VALUES) switch is ON:
* Calibration is disabled.
* Values stored in nonvolatile memory are deleted.
* The velocity dynamic range stored values are deleted.

When sca_sw1_position2 (FREEZE_CAL_VALUES) switch is ON:
 * The calibration values are frozen and do not update.
 * The calibration values in nonvolatile memory are re-applied when power is cycled or when new firmware is downloaded.

LED under the TFT:
* When all calibration values are at default the LED flashes quickly.
* When sca_sw1_position1 (DELETE_CAL_VALUES) is ON, the LED flashes quickly.
* When a calibration value is applied to all 88 keys, the LED flashes slowly.

### Calibration Best Results
* Power up the piano.
* Turn ON sca_sw1_position1 (DELETE_CAL_VALUES) then turn it OFF. This ensures old values are deleted from nonvolatile memory.
* Firmly play each piano note once.
* Turn ON sca_sw1_position2 (FREEZE_CAL_VALUES) to freeze calibration values and store them in nonvolatile memory.

If the sensor placement is changed, repeat this process.

## Front LEDs / Test Points

At the front of the piano, next to the Teensy, are four LEDs. Each LED is electrically connected to a test point. The firmware drives with a Teensy pin. Here is the functionality, using names from figure above:

### processing

This test point is high during Teensy main loop processing. The rate is very high and so the LED may be solidly or dimly illuminated. Can monitor with an oscilloscope for debug.

### damper

This LED is ON when any damper is raised by pressing and holding a piano key.

Normally this LED is OFF when no piano keys are pressed. If LED is ON when no piano keys are pressed, this indicates:
* the *damper_threshold_low* or *damper_threshold_high* setting is incorrect or
* a sensor problem or
* not all notes have calibration values (in this case the calibration LED is flashing quickly) or
* distances from sensors to hammer shanks are not uniform between keys.

### strike

This LED is ON when any hammer is close to the string. When a single piano key is pressed quickly, this LED should briefly turn ON then OFF.

Normally this LED is OFF when no piano keys are pressed. If LED is ON when no piano keys are pressed, this indicates:
* the *strike_threshold* setting is incorrect or
* a sensor problem or
* not all notes have calibration values (in this case the calibration LED is flashing quickly) or
* distances from sensors to hammer shanks are not uniform between keys.

### sustain

This LED is ON when any of the pedals is pressed. Probably should be called 'pedal' and not 'sustain'.

## Other LEDs

There are two LEDs under the SCA and two on the Ethernet connector.

The SCA LEDs flash at a fixed rate. They are available for firmware customization.

One Ethernet LED flashes when data is transferred. The other flashes at a fixed rate and is available for firmware customization.

## Serial Monitor

Multiple categories of information is displayed through the Arduino serial monitor. See firmware code for details.

## If Add A Damper Board (optional)

The optional damper board and damper sensors measure the back of each piano key. If not using a damper board, the damper positions are estimated from the hammer positions.

The MIDI connection on damper board is not used. All MIDI data is through the hammer board.

The damper board requires a separate +5 volt input connection.

The damper board Teensy processor is programmed separately from the hammer board Teensy processor.

The damper board has its own 2.8 inch TFT display.

The configuration switches, LEDs, and test points are different on the damper IPS, compared to the hammer IPS.

## Caring for Stem Piano

The CNY-70 have a long, but finite lifetime.

Turn off piano when:
* Not in use.
* Changing any connections.

Protect the circuit boards from electrostatic discharge (ESD) and anything touching them. Build a case or enclose the piano. The circuit boards generate some heat and should be vented.

If the frame is moved it could change the sensor alignment. In this case, clear the calibration values and restart the calibration and velocity processes.

Enjoy!

## Changing Firmware and Software

Now even more fun begins.

You have an open source piano and can add any features and be as creative as you wish.

See the firmware/software manual for details on firmware and firmware settings: [./firmware_manual.md](./firmware_manual.md)

## Important Resources

* Please read the warnings and limitations: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/WARNINGS.md

* Help it doesn't work: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/HELP.md

* Active problems, bugs, and lists of future enhancements:
    * https://github.com/gzweigle/DIY-Grand-Digital-Piano/issues 
    * https://github.com/stem-piano/stem-piano-g-main/issues

## Users Manual, Select Change History
* Add storing calibration values.