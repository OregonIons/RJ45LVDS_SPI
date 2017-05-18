# RJ45LVDS_SPI

Converts from 4x LVDS over ethernet cable (RJ45) to 4x single-ended digital on a 0.1" header.  
Small footprint board designed to be panel mounted inside a project case.  
Ideal for connecting remote SPI devices to the [Sinara hardware](https://github.com/m-labs/sinara) being designed for [ARTIQ](https://github.com/m-labs/artiq) (specifically the [RJ45_LVDS Kasli module](https://github.com/m-labs/sinara/wiki/EEM_RJ45_LVDS)).  
Voltage translation allows connection to 1.8, 2.5, 3.3, or 5V voltage node logic.


Power
=====

Board requires 3.3V (max current draw is ~200mA). Two options:

1. Apply regulated 3.3V power to 3.3V pin.  
or
2. Apply unregulated power to UNREG pin and enable the regulator by soldering REG_EN jumper.

- The default regulator is a MIC39100-3.3WS which requires an UNREG input voltage between 3.7 and 16V.  [Datasheet](http://ww1.microchip.com/downloads/en/DeviceDoc/mic39100.pdf)
- When applying unregulated power, the 3.3V pin on the power header becomes an output that can be used to power other things, such as an SPI device. The MIC39100-3.3WS is capable of providing 1A (minus the current required by the board). 
- Adding the optional resistor R5 makes the green LED on the RJ45 jack act as a power indicator.


Channel directions
==================

- Each channel can be independently configured as an input or an output.  
- The channel directions are set via the solder jumpers on the back of the board.  You must set all four directions before powering the board.  
- Each channel has two jumpers which must both be set the same way.


LVDS interface
==============

- Uses Texas Instruments SN65MLVD206 Line Driver and Receiver [Datasheet](http://www.ti.com/lit/ds/symlink/sn65mlvd206.pdf)
- Signalling rates up to 200 Mbps
- Driver has 1.5ns of propagation delay
- Receiver has 4ns of propagation delay


Single-ended digital interface
==============================

- Uses Texas Instruments SN74LVC1T45DBVR Bus Transceiver With Configurable Voltage Translation [Datasheet](http://http://www.ti.com/lit/ds/symlink/sn74lvc1t45.pdf)
- The voltage level of interface must be configured using one of the two V_LOGIC solder jumpers:
1. 3.3V - uses the board’s 3.3V rail
2. EXT - uses voltage supplied at V_LOGIC pin.  Must be in range 1.65-5.5V.
- EXT can be supplied at 'EXT V_LOGIC' pin or the 'UNREG to EXT V_LOGIC' jumper can be used to connect EXT to UNREG.  This would typically be done when powering the board from a regulated +5V supply.
- Propagation delays and data rates depend on V_LOGIC voltage level.  At 3.3V though they are ~4ns and 210Mbps.


RJ45 Connectors
================

Either a vertical or right-angled connector can be mounted as required. 
The panel cutouts are the same for both and can be found in the datasheets:
- MRJ-5481-01 (vertical): https://www.amphenolcanada.com/ProductSearch/drawings/AC/MRJ548XX1.pdf
- MRJ-5381-01 (right-angled): https://www.amphenolcanada.com/ProductSearch/drawings/AC/MRJ53xxx1.pdf


Release Notes
=============

v0.1 - Initial board fab run.

v0.2 - Second board fab run. Fixed some routing errors that made v0.1 untestable.

v0.3 - Changed the RJ45 connector to allow for both vertical and right-angled versions.  Fixed a few silkscreen mistakes.

