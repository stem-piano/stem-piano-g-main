# Stem Piano G - Assembly Manual

Start here once have acquired all components, accessories, cables, and a piano action (or invented some innovative alternative for the action). The circuit boards are complete and all components soldered into place.

The assembly manual covers the steps of connecting individual components to construct a full piano. The assembly manual ends when *stem piano* as at an "equivalent" of a purchased hybrid piano. Similar to the purchase of a hybrid piano, the steps of connecting power, MIDI, and pedals are covered in the [users manual](users_manual.md).

Video links in documentation below are to *stem piano* historical progress videos on YouTube: https://www.youtube.com/@gzpiano88.

## Circuit Boards

This figure shows the large Integrated Processing System (IPS) circuit board with the Six Channel Analog (SCA) circuit board installed. The SCA is the center rectangular board. To the left is a single Hammer Position Sensor (HPS) board with connections. A total of 88 HPS are required.

![hammer_setup](diagrams/stem_piano_hammer_setup.png)

*Stem Piano* video description of circuit boards:
* https://youtu.be/NmziaIYKS1g?t=75

## Mechanical Assembly

Example piano action with hammer sensors, damper sensors, and hammer stop bar.

![](pictures/mechanical_assembly.jpg)

*Stem Piano* mechanical assembly videos:
* https://www.youtube.com/watch?v=5U7LvOMth28
* https://www.youtube.com/watch?v=xohaQG593e4
* https://www.youtube.com/watch?v=ZMxMio3L9dk
* https://www.youtube.com/watch?v=w0TpXvcRCsM
* https://www.youtube.com/watch?v=NmziaIYKS1g

See the *Action Frame* manual for construction details [./construction_subsections/subsection5_action_frame.md](./construction_subsections/subsection5_action_frame.md).

## Connect SCA Circuit Board to IPS Circuit Board

The small Six Channel Analog (SCA) board connects to the Integrated Processing System (IPS) board.

*Stem Piano* video showing SCA:
* https://youtu.be/NmziaIYKS1g?t=105

## Connecting Hammer Sensors

Connect each HPS sensor to the correct IPS location using the ribbon cable.

![spg_hammer_connections](diagrams/hammer_connections.png)

Hammers are numbered starting at piano note A0 (key number 0), through piano note C8 (key number 87) in the first figure. Connect each set of three pins (power, ground, and signal) to the same three pins on each of the 88 sensors boards.

* Each HPS board is marked with a plus (+) symbol, a minus (-) symbol, and an exclamation point (!) symbol.

* The pins on the IPS board are market with a "3.3v" symbol, a "gnd" symbol, and an "in" symbol.

* Connect (+) to "3.3V", connect (-) to "gnd", and connect (!) to "in".

Connecting all the sensors is very time consuming. A total of 3*88 = 264 wires are required. Gluing into sets makes the connection process much easier. See *stem piano* video https://youtu.be/gNeLMGaxmG0?t=103.

*Stem Piano* video showing top view of wiring:
* https://www.youtube.com/watch?v=TemXGmkoc-g

## Connecting Damper Sensors (Optional)

A second IPS and SCA are required for damper sensors. Damper sensors are optional. If not using damper sensors, the damper location is estimated using the hammer sensors.

Damper keys are numbered starting at piano note A0 (0), through piano note C8 (87).
![spg_damper_connections](diagrams/damper_connections.png)

*Stem Piano* video showing damper wiring:
* https://youtu.be/NmziaIYKS1g?t=167

## Connecting Pedal Header

This figure does not show the small extra PLS 0.0 circuit board (*future*).

Connect jumper wires (short ribbon cable will work) as shown in figure for the IPS mainboard connected to hammer sensors. While it is possible to also use the damper IPS mainboard for pedal connections, the firmware is not presently setup to support this option. Note that with both hammer and damper pedal connections, a total of 6 pedals could be available.

![spg_pedal_connections](diagrams/pedal_connections.png)

Three of the connection wires are optional (sustain connected, sostenuto connected, and una corda connected). Also, in many cases a sostenuto and una corda pedal are not used. Therefore, up to seven keys beyond the traditional 88 keys can be connected (total of 95 keys if using only a single pedal).

Pedal signals are not hardwired on the PCB. Therefore, these jumpers enable connecting pedals in many different configurations.

If noisy pedals or notes, connect unused pins to ground using a short segment of ribbon cable. For example, in this figure pins labeled 88 and 89 in the figure, on J45 (the 'in' row) connect to the adjacent ground pins on J41 (the 'gnd' row).

# PREVIOUS STEP
[./hps_testing.md](./hps_testing.md)

# NEXT STEP
[./firmware_setup.md](./firmware_setup.md)