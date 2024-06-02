# bEEr_warmer
A simple PCB as a beer mug warmer powered by The USB type C Power Delivery source
## Table of contents
* [General info](#general-info)
* [Topology](#topology)
* [Technologies](#technologies)
* [PCB](#pcb)
* [Setup](#setup)
* [Main components selection](#main-components-selection)
* [Status](#status)
* [License](#license)
## General info
Gadget built for my colleague - PCB board as a heat keeper for hot drinks like mulled wine, beer or regular tea.
The board requires electronic configuration (selection of resistors) and uploading software to the microcontroller.
## Topology
![Diagram](./Documentation/Diagram.svg)
## PCB
The PCB was designed in current KiCad version. All necessary files are in the documentation folder
## Setup
The gadget uses the AP33771 chip as a Pawer Delivery sink. The output voltage and delivered power is configured using resistors. For the resistor values shown in the schematic, the controller delivers 9V at a maximum power of 20W. Such settings worked well in my implementation of the board. With no load in the form of a mug of beer, the board heats up to 70 degrees in 30 seconds. Keep in mind that my PD sink circuit configuration depends on the resistance of the load. In the JLCPCB board design, the load resistance was about 4.3 Ohms at an ambient temperature of 21 degrees, and was in accordance with the calculations of the Saturn PCB Design calculator. If the load resistance of the manufactured boards will differ from the intended one, the voltage and power settings provided by the PD source should be adjusted accordingly. On the first page of the schematic diagram there are two tables from which you can read the desired values of the voltage and power configuration resistors. For 9V, R28 and R29 must not be soldered in. To get 20W R30 must be 26k Ohm. After checking the value of the load resistance and selecting the appropriate PD sink configuration resistors, the two solder bridges (JP1 and JP2) should be soldered together. This will lead the current to the load.

To program the STM32 microcontroller, use the ST Link programmer, the SWDIO and SWCLK pins are brought out on the popular DF13A socket.



