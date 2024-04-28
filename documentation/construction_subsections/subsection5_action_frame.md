# Stem Piano G - Piano Action Frame

* The steps below are for a Grand Piano action.

* If using an upright action or another musical idea (perhaps a new invention?) then the Grand Piano instructions give general guidance.

* Information on the frame: https://github.com/gzweigle/DIY-Grand-Digital-Piano/tree/main/mechanical.

## Top view of mechanical system

![](../pictures/mechanical_assembly.jpg)

## Acquire a piano action.

Perhaps the most challenging step!

... or ... build something innovative.

## Build a frame that holds two bars

One is for the hammer stop and one is for the sensors.

Both must adjust vertically and horizontally.

See the following *stem piano* videos for examples:
* https://www.youtube.com/watch?v=xohaQG593e4
* https://www.youtube.com/watch?v=NmziaIYKS1g
* https://www.youtube.com/watch?v=5U7LvOMth28 (audio accidentally recorded single-channel).

## Install a heavy bar for the hammer shank stop

Use a strip of firm material to absorb the force of shank against the bar. For example, weatherstripping works ok.

Position the hammer shank stop bar horizontally as close to each hammer as possible.

Adjust the hammer shank stop bar vertically until it is approximately 1/8" above the shank drop point. So, when pressing a piano key, move the key down slowly and adjust the bar so the hammer shank does not quite hit the stop bar. Try to get an even distance for all 88 hammer shanks.

See *stem piano* videos
* https://youtu.be/ANJI4KAolEw?t=86
* https://youtu.be/xohaQG593e4?t=48

## Install a rail for the HPS sensors

See *stem piano* video https://youtu.be/xohaQG593e4?t=60.

Drill 88 holes in the sensor rail. Each hole is located vertically above a hammer shank.

If holes are precise, they can match the machine screw diameter. Otherwise, make holes larger to give room for HPS horizontal adjustment.

Horizontally, the hole is such that the CNY-70 on the HPS is close to the place where the shank rotates on the pin adjacent to the drop screw. The shank may get wider at this location.

Install all 88 HPS sensors. The nut is on top. If put nut on bottom, it could hit the piano hammer shank.

Another option is aluminum extrusion. See https://github.com/stem-piano/stem-piano-g-main/issues/1

Adjust the sensor rail up and down until the hammer shank is between 0.5 millimeters 1.5 millimeter from the CNY-70 sensor when hammer hits the stop bar. If the distance is smaller than 0.5 millimeters, the CNY-70 response loses sensitivity. If the distance is larger than 1.5 millimeters, the output voltage can be too low. Better for the distance to be too large than too small.

The following picture shows the measurement location. In this picture there are no white stickers. For best results, use a white sticker or white paint on the hammer shank underneath the CNY-70 sensor.

![](../pictures/hammer2sensor.jpg)

Good note-to-note consistency depends on the consistency of shank-to-sensor distances for each sensor. It is a good idea to spend extra time making these distances as consistent as possible. One approach is using thin paper shims to adjust distances when connecting the sensors to the sensor rail.

If the hammer shank wood is not strongly reflective, place white stickers on each shank under the CNY-70 location. Another option is white paint. Use the same kind of surface as use in the CNY-70 voltage level tests: [../hps_testing.md](../hps_testing.md).

## Piano action regulation

For best results, get the piano action adjusted while in the configuration described above

Consistent shank height at location of sensor.