# Stem Piano G - Assembly Manual

Start here once have all components, accessories, cables, and a piano action (or invented some innovative alternative for the action).

The steps below are for a Grand Piano action.

If using an upright action or another musical idea (perhaps a new invention?) then the Grand Piano instructions give general guidance.

Video links in documentation below are to *stem piano* historical progress videos on YouTube: https://www.youtube.com/@gzpiano88. Useful for general ideas, not specific instructions.

## Circuit Board Overview

This figure shows the large Integrated Processing System (IPS) circuit board with the Six Channel Analog (SCA) circuit board installed. The SCA is the center rectangular board. To the left is a single Hammer Position Sensor (HPS) board with connections. A total of 88 HPS are required.

![hammer_setup](diagrams/stem_piano_hammer_setup.png)

*Stem Piano* video description of circuit boards: https://youtu.be/NmziaIYKS1g?t=75

## Piano Action Frame

Build a frame that holds two (optionall three) bars. All must adjust vertically and horizontally.
* Hammer stop bar.
* Hammer sensor rail.
* Damper sensor rail (option).

Make the frame strong so does not move during piano playing.

Information on the frame: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/mechanical.

Example piano action with hammer sensors, damper sensors, and hammer stop bar.

![](pictures/mechanical_assembly.jpg)

Example ideas from *Stem Piano* mechanical assembly videos:
* https://www.youtube.com/watch?v=5U7LvOMth28 (single-channel audio)
* https://www.youtube.com/watch?v=xohaQG593e4
* https://www.youtube.com/watch?v=ZMxMio3L9dk
* https://www.youtube.com/watch?v=w0TpXvcRCsM
* https://www.youtube.com/watch?v=NmziaIYKS1g

Build an enclosure (not shown) to keep all electronics isolated from contact. Vent for correct temperature range of electronics (instructions not provided).

## Hammer Stop Bar

Use a strip of firm material to absorb the force of shank against the bar. For example, weatherstripping works ok.

Position the hammer shank stop bar horizontally as close to each hammer as possible.

Adjust the hammer shank stop bar vertically until it is approximately 1/8" above the shank drop point. So, when pressing a piano key, move the key down slowly and adjust the bar so the hammer shank does not quite hit the stop bar. Try to get an even distance for all 88 hammer shanks.

See *stem piano* videos
* https://youtu.be/ANJI4KAolEw?t=86
* https://youtu.be/xohaQG593e4?t=48

## Hammer Sensor Rail

See *stem piano* video https://youtu.be/xohaQG593e4?t=60.

Drill 88 holes in the sensor rail. Each hole is located vertically above a hammer shank.

If holes are precise, they can match the machine screw diameter. Otherwise, make holes larger to give room for HPS horizontal adjustment.

Horizontally, the hole is such that the CNY70 on the HPS is close to the place where the shank rotates on the pin adjacent to the drop screw. The shank may get wider at this location.

Install all 88 HPS sensors. The nut is on top. If put nut on bottom, it could hit the piano hammer shank.

Another option is aluminum extrusion. See https://github.com/stem-piano/stem-piano-g-main/issues/1

Adjust the sensor rail up and down until the hammer shanks are approximately one millimeter from the CNY70 sensors when hammer hits the stop bar. If the distance is too much smaller than one millimeter, the CNY70 response loses sensitivity. If the distance is too much larger than one millimeter, the output voltage can be too low. Better for a distance too large than too small. See *Piano Regulation* subsection below in this file.

The following picture shows the measurement location. This picture shows no white stickers. For best results, use a white sticker or white paint on the hammer shank underneath each CNY70 sensor.

![](./pictures/hammer2sensor.jpg)

Good note-to-note consistency depends on the consistency of shank-to-sensor distances for each sensor. It is a good idea to spend extra time making these distances as consistent as possible. One approach is using thin paper shims to adjust distances when connecting the sensors to the sensor rail.

If the hammer shank wood is not strongly reflective, place white stickers on each shank under the CNY70 location. Another option is white paint. Use the same kind of surface as use in the CNY70 voltage level tests: [./hps_testing.md](./hps_testing.md).

## Connecting Hammer Sensors

Connect each HPS sensor to the correct IPS location using the ribbon cable.

Tests indicate that standard ribbon cable can introduce coupling errors in the sensor signal output as high as 5% on adjacent keys. Typical errors are 0% to 3% depending on the ribbon cable arrangement. One approach for reducing errors is interleaving ground signals. Or, physically separating the cables.

![spg_hammer_connections](diagrams/hammer_connections.png)

Hammers are numbered starting at piano note A0 (key number 0), through piano note C8 (key number 87) in the first figure. Connect each set of three pins (power, ground, and signal) to the same three pins on each of the 88 sensors boards.

* Each HPS board is marked with a plus (+) symbol, a minus (-) symbol, and an exclamation point (!) symbol.

* The pins on the IPS board are market with a "3.3v" symbol, a "gnd" symbol, and an "in" symbol.

* Connect (+) to "3.3V", connect (-) to "gnd", and connect (!) to "in".

Connecting all the sensors is very time consuming. A total of 3*88 = 264 wires are required. Gluing into sets makes the connection process much easier. See *stem piano* video: https://youtu.be/gNeLMGaxmG0?t=103.

*Stem Piano* video showing wiring top view:
* https://www.youtube.com/watch?v=TemXGmkoc-g
* https://youtu.be/tyN7v7L9VIQ?t=135

## Connecting Damper Sensors (Optional)

A second IPS and SCA are required for damper sensors. Damper sensors are optional. If not using damper sensors, the damper location is estimated using the hammer sensors.

Damper keys are numbered starting at piano note A0 (0), through piano note C8 (87).

![spg_damper_connections](diagrams/damper_connections.png)

*Stem Piano* video showing damper wiring https://youtu.be/NmziaIYKS1g?t=167

## Using the Analog Condition Equalize (ACE) Interposer Board (Optional)

### Purpose of ACE If Not Using HPS Sensor Boards
* If not using HPS sensor boards, and the custom sensor board being used in place of the HPS does not match the interface requirements. In this case, use an ACE interposer board to interface sensor to mainboard signals so that the sensor output matches the mainboard input requirements.

### ACE Optional Use, Independent of Sensor Board Type

* It is possible (future) that an ACE interposer board could improve the performance of sensor signals.
* The ACE interposer board simplifies wiring connections. This is a useful purpose for an ACE even if using the HPS sensor boards. If using ACE A for this with HPS then do not solder on the ACE A resistors.
* Here is another case where the ACE interposer board could be useful, even if using the HPS sensor boards. This is the case for if unsure about HPS R2 value. An option is to not install R2 on the HPS circuit boards. Use the ACE resistors instead. The advantage of this approach is that changing R2 requires replacing 6 ACE boards instead of replacing 88 HPS boards.

### ACE General Information

ACE comes in several versions. Presently one version is done: ACE A. This version is a set of load resistors.

Each ACE A connects to 16 sensors. A total of six ACE A interposer boards are required for 88 sensors (88 piano keys).

See the hardware source readme for details on each board. The values in parts list at this directory are for example. Select resistor values according to the requirements to match the custom sensor being used in place of HPS sensors.
Link: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/hardware/releases/aceA00

### Sensor Connections with ACE

When using an ACE interposer board, connect wires to sensors exactly as described above for the case without ACE interposer boards.

### ACE Assembly Pictures

Below is a picture of ACE connection to IPS 2.0 main board. The ACE snaps into place. 

![aceA00_connection0](pictures/aceA00_connection0.jpg)

Picture of ACE connection next to a location without the ACE interposer board.
![aceA00_connection3](pictures/aceA00_connection3.jpg)

The ACE A interposer can also be used to simplify connecting sensor wires to the IPS 2.0 mainboard. In this case, if the load resistors are not required, simply do not install them. Without installing resistors, the ACE A is a straight-through wire connection. Without resistors installed, it does not change the signal values.

The advantage of using ACE A in this way is that the wiring can be done separate from the main board and then sets of 16 wires snap into place.

![aceA00_connection1](pictures/aceA00_connection1.jpg)
![aceA00_connection2](pictures/aceA00_connection2.jpg)

## Connecting Pedal Signals

### Without PLS (Pedal Level Shift)

The first figure does not show the small extra PLS 0.0 circuit board.

Connect jumper wires (short ribbon cable will work) as shown in figure for the IPS mainboard connected to hammer sensors. While it is possible to also use the damper IPS mainboard for pedal connections, the firmware is not presently setup to support this option. Note that with both hammer and damper pedal connections, a total of 6 pedals could be available.

![spg_pedal_connections](diagrams/pedal_connections.png)

### With PLS (Pedal Level Shift)
The next figure includes the PLS 0.0. circuit board. For illustration purposes the PLS circuit board is shown offset from J46.

The purpose of PLS is level shifting the pedal signals so they stay within the analog-to-digital converter (ADC) maximum voltage, when the optional IPS resistors R23, R25, and R28 are installed. These resistors are needed for passive pedals. Most pedals are passive. Without PLS the pedal signals may be clipped by the ADC.

![spg_pedal_connections](diagrams/pedal_connections_with_pls.png)

The Pedal Level Shift (PLS) circuit board headers:
* J1 is a socket header that is soldered onto the bottom of the PLS board.
* J2 is a pin header that is soldered onto the top of the PLS board.

Connect the PLS J1 socket to the IPS J46 pin header. Then, connect wires as shown from the J2 pin header of PLS.

Following the previous diagram, below is a picture. For illustration in the picture the PLS socket header J1 is resting against the IPS pin header J46. Install with PLS fully seated. 

In this picture the pedal quarter inch jacks are visible in the background (red and black).

Note that the far right pin (for ground) on the PLS socket header does not have an associated pin on IPS J46. This is by design. Connections in picture:

* blue wire connects to J45 for input 90 (una corda).
* violet wire connects to J45 for input 91 (una corda connected).
* grey wire connects to J45 for input 92 (sostenuto).
* white wire connects to J45 for input 93 (sostenuto connected).
* black wire connects to J45 for input 94 (sustain).
* brown wire connects to J45 for input 95 (sustain connected).
* red wire connects to any ground pin of J41.

![pls_connection](pictures/pls00_connection.jpg)

*Stem Piano* video pedal wiring with PLS https://youtu.be/tyN7v7L9VIQ?t=120 

### General

Three of the connection wires are optional (sustain connected, sostenuto connected, and una corda connected). Also, in many cases a sostenuto and una corda pedal are not used. Therefore, up to seven keys beyond the traditional 88 keys can be connected (total of 95 keys if using only a single pedal).

Pedal signals are not hardwired on the PCB. Therefore, these jumpers enable connecting pedals in many different configurations.

If noisy pedals or notes, connect unused pins to ground using a short segment of ribbon cable. For example, in this figure pins labeled 88 and 89 in the figure, on J45 (the 'in' row) connect to the adjacent ground pins on J41 (the 'gnd' row).

## Piano Regulation

In addition to the piano action, the mechanical structure and electronics all contribute together to result in the most consistent, accurate, and precise piano possible.

See this *Stem Piano* video for details on sources of note-to-note inconsistency and how to improve each: https://www.youtube.com/watch?v=yqkRKSGX6kw

**Things to consider:**

Each is rated low effect (L), medium effect (M), high effect (H).

1. (H) Piano Action. Use the final mechanical setup during piano action regulation.

2. (L) Sensor Rail Horizontal Position.

3. (M) Sensor Rail Vertical Position. See instructions above.

4. (H) Sensor Nonlinearity. The piano includes an automatic calibration feature. See the *Users Manual* in this repository.

5. (H) Sensor Tolerance. Some CNY70 may result in an output voltage that is very low or very high. It is best to select a different CNY70 in these cases.

6. (M) Crosstalk. The sensor spacing is large enough to keep crosstalk small.

7. (L) Shank Angle.

8. (L) Analog Front End. For the *Stem Piano G* design, the analog processing does not contribute significant note-to-note errors.

9. (H) Reflective Material. The reflective surface under each CNY70 should be identical for all keys and dampers.

10. (H) Ambient Light. If the sensors are exposed to ambient light it can cause uneven notes when the ambient light changes. One option to fix is rerun the automatic calibration when lighting conditions change. Avoid bright light as this could cause loud notes to sound.