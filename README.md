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
The PCB was designed in current KiCad version. All necessary files are in the documentation folder.
## Setup
The gadget uses the AP33771 chip as a Pawer Delivery sink. The output voltage and delivered power is configured using resistors. For the resistor values shown in the schematic, the controller delivers 9V at a maximum power of 20W. Such settings worked well in my implementation of the board. With no load in the form of a mug of beer, the board heats up to 70 degrees in 30 seconds. Keep in mind that my PD sink circuit configuration depends on the resistance of the load. In the JLCPCB board design, the load resistance was about 4.3 Ohms at an ambient temperature of 21 degrees, and was in accordance with the calculations of the Saturn PCB Design calculator. If the load resistance of the manufactured boards will differ from the intended one, the voltage and power settings provided by the PD source should be adjusted accordingly. On the first page of the schematic diagram there are two tables from which you can read the desired values of the voltage and power configuration resistors. For 9V, R28 and R29 must not be soldered in. To get 20W R30 must be 26k Ohm. After checking the value of the load resistance and selecting the appropriate PD sink configuration resistors, the two solder bridges (JP1 and JP2) should be soldered together. This will lead the current to the load. Two additional resistors should not be soldered on the PCB: R13 and R32.

To program the STM32 microcontroller, use the ST Link programmer, the SWDIO and SWCLK pins are brought out on the popular DF13A socket. The program is trivial and its listing can be found in the documentation folder. Digital and one analog outputs from all temperature sensors and a proximity sensor have been fed to the microcontroller. The microcontroller has a large percentage of unused memory resources. There is a huge room for maneuver and for expanding the functionality of the software. By changing the software, the number of temperature sensors can be reduced, thus reducing the cost of the board.

The AND gate is used to protect the circuit from overheating and against software or microcontroller errors. When any of the inputs is low, the current from the load is disconnected. The inputs of the gate are:
- 85 degree sensor output
- touch sensor output
- output from the microcontroller

After checking the fucnition of the board, I suggest you desolder the DF13A socket and put conformal coating on both sides of the board.
## Status
Closed
## License
MIT


