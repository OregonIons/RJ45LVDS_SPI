# RJ45LVDS_SPI

Converts from 4x LVDS over ethernet cable (RJ45) to 4x single-ended digital on a 0.1" header.
Small footprint board designed to be panel mounted inside a project case.
Ideal for connecting remote SPI devices to the [Sinara hardware](https://github.com/m-labs/sinara) being designed for [ARTIQ](https://github.com/m-labs/artiq) (specifically the [RJ45_LVDS Kasli module](https://github.com/m-labs/sinara/wiki/EEM_RJ45_LVDS)).


Power
=====

Board requires 3.3V power

1. Apply regulated 3.3V power to 3.3V pin
or
2. Apply unregulated power to UNREG pin and enable the regulator by soldering REG_EN jumper

- Soldering the LED enable jumper ‘LED_EN’ makes the green LED on the RJ45 jack act as a power indicator if desired.
- The default regulator is a MIC39100-3.3WS which requires an UNREG input voltage between 3.7 and 16V.  Datasheet: http://ww1.microchip.com/downloads/en/DeviceDoc/mic39100.pdf
- When applying unregulated power, the 3.3V regulated power becomes an output that can be used to power other things. The MIC39100-3.3WS can 


Channel directions
==================

Each channel can be independently configured as an input or an output.  
The channel directions are set via the solder jumpers on the back of the board.  
Each channel has two jumpers which must both be set the same way.


Digital output level
====================




Switching characteristics
========================

- Max data rate
- Delay


TODO
====

- Add mounting holes
- Provide panel cutout drawing
- Create BOM
- Tidy schematic
- Sprinkle ground vias
- Fix regulator part number