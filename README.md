# Stem Piano G

*Stem Pianos* are open source hybrid MIDI digital pianos.

The Model G version is the first completed piano.

If you build a piano, please share about it in the *Show & Tell* Discussions.

## Piano Documentation

Start here: [documentation/README.md](documentation/README.md)

Status: https://github.com/gzweigle/DIY-Grand-Digital-Piano/blob/main/STATUS.md

## Stem Piano Overview

The following is from the *README.md* file in the *DIY-Grand-Digital-Piano* repository:

"

*A hybrid piano combines the physical action of an acoustic piano with MIDI, sound generation, and other features of a digital keyboard. Some piano manufacturers sell hybrid pianos.*

*This project ("stem piano") is an open-source hybrid digital piano.*

*The qualifier digital is important. It means that signals are sampled with an analog-to-digital converter (ADC) and then all processing is with a microprocessor. Therefore, once the hardware is installed all algorithms, improvements, and new features are with software or firmware.*

*The repository includes schematics, printed circuit board layouts, firmware source files for the real-time processing, optional software source files for Ethernet connected features, and lists of required hardware components.*

*A physical piano action, or other instrument, is required. The electronics and code (stem piano) will work with a grand or upright piano action. Mechanical suggestions are included but not detailed mechanical instructions.*

*The platform and code could also adapt to building a range of other unique and innovative musical instruments.*

"

## Major Features

* Piano Actions:
    * Grand or upright pianos.
    * Action separate from the piano or as a silent system in a full piano.
    * Digital keyboard (sensors may need modification).
    * Or, can use as part of creating innovative new musical instruments.
* Sends data via a single 5-pin serial MIDI.
* Measures and sends hammer velocity and, optionally, damper velocity over MIDI.
* Includes three jacks, quarter-inch, for pedals.
* Accepts up to 96 inputs. Therefore, will work for pianos with more than 88 keys.
* Optional 10/100 Mbit Ethernet port for configuration, status, and debug.
* Optional 2.8" TFT display for configuration, status, and debug.
* 4x2 switches for eight configuration options.

## Links

This repository includes links to:
* Documentation in this repository.
* Files in the original project repository. https://github.com/gzweigle/DIY-Grand-Digital-Piano.
* *Stem Piano* historical progress videos. https://www.youtube.com/@gzpiano88.
* External manufacturer web sites.