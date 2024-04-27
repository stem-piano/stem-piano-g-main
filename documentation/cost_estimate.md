# Stem Piano G - Cost Estimates (2023)

Each bill of materials file in the hardware directories includes parts cost estimates. USD units.

The estimates assume purchasing single quantities and prototype boards. It should be possible to lower these costs.

Here is a summation of all the parts costs in the bill of materials files:

## Component costs

* IPS mainboard - minimal options (no TFT display, no LED, no test points, no Can bus, no Ethernet, no config switches) - $120.
* IPS mainboard fully populated - $175.
* SCA data acquisition card - minimal options - $45.
* SCA data acquisition card fully populated - $50.
* HPS 0.6 or HPS 0.7 (with trimmer resistor) - $7.50 (not recommended for normal use cases).
* HPS 0.8 or HPS 0.4 (without trimmer resistor) - $2.15.

## Total cost for the least expensive system
* No display, LEDs, test points, Ethernet, or configuration switches.
* No separate IPS and SCA for damper processing.
* No damper sensors. Damper position is estimated in firmware from hammer position.
* No trimmer resistors on HPS hammer sensors.
* Total = $120 + $45 + 88 * $2.15 = $354.20.

## Total cost for the most expensive system
* All features - boards are fully populated.
* Separate processing for dampers.
* Total = 2 * ($175 + $50 + 88 * $2.15) = $828.40.
 
## Trimmer resistors will slightly improve accuracy
* Total = 2 * ($175 + $50 + 88 * $7.50) = $1770.

## Other costs

The above estimates do not include the mechanical equipment cost (sensor bars and hammer stop bar), the pedal cost, the external power supply cost, or the piano action cost. Also, a sturdy table is required.

The above estimates do not include cost for time of construction, soldering, assembly, sleepless nights debugging and troubleshooting.