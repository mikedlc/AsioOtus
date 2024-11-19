# AsioOtus - Digital IO Setup Notes from PDFs

- LinuxCNC Docs
	- https://linuxcnc.org/docs/stable/html/


<h3>From 'B3 Driver Manual.pdf'</h3>

- Section pages 8-73 and 8-190 in the software manual
- Page 8-13 has the Ditgital Input and Output functional planning parameters (Parameter Numbers P1.XXX, P2.XXX, P3.XXX, etc...)
	- The eStop and limit DI assignments are on 8-195
		- 0x21 is EMGS (estop)
		- 0x22 is NL (CWL) Negative inhibit limit (normally closed contact)
		- 0x23 is PL (CCWL) Positive inhibit limit (normally closed contact)
- Brake - page 2-28
	- Wiring diagram on page 2-29
	- brake output is value 0x08 on page 8-199
	- 0x08 is BRKR Output signal of the magnetic brake control. Set MBT1 P1.042 and MBT2 P1.043 to adjust the delay time before and after the brake control is activated and deactivated.
	- Notes to refer to the note in P1.042
	- Need a reverse polarity shottky doide across the relay solenoid to protect the driver from reverse voltage
- DI functional planning
	- Page 8-73
	- P2.010 - P2.013 are DI1 - DI4, the 4 digital inputs with physical pin assignments
	- P2.014 - P2.017 are DI4 - DI8 and don't have physical pins but are addressable in software
	- Physical/software control option is 3.006 on page 8-108

- DI pin assignments on page 3-52, wiring on 3-62
	- COM+ - pin 5
		- Gets +24V from external power supply
	- Digital Inputs, get negative terminal from external power supply, normally closed (NC) switched
		- DI1- - pin 6 -
		- DI2- - pin 7 -
		- DI3- - pin 8 
		- DI4- - pin 9 
	- DI values: (P2.010 - 2.017 for DI 1-8)
		- 0021 - eStop
		- 0022 - CW Limit
		- 0023 - CCW Limit
	- Digital Outputs
		- DO1+ - pin 15
		- DO1- - pin 16 
		- DO2+ - pin 17
		- DO2- - pin 18
	- DO values: (P2.018 - 2.022 for DI 1-5)
		- 0x08 - brake output
			- 0108 for NO (correct?)
			- 0008 for NC

	- Currently all inputs are unassigned (0000) so that the drive doesn't use them but LinuxCNC does

- Homing within driver - Page 7-9
	- DI value 0x027 - SHOM ('during homing, when this DI is on, the servo starts to search for the origin. refer to the setting of P5.004)
	- "Homing method is specified by P5.004 and the homing definition is determiend by P6.000"
	- Can home with 3 methods:
		- Home to limit switch - P5.004: 0000 (forward) or 0001 (reverse)
			- As it sounds, move until switch is tripped, back off switch, move to z pulse, set that as origin
			- Need to consider velocity and acceleration to ensure axis can be stopped fast enough upon triggering limit switch
		- Home to origin switch
			- Move until origin switch between limits is triggered
			- If limit is encountered, move in other direction until origin switch is triggered
			- Probably not useful for my application
		- Home to torque limit - P5.004: 0109 (forward) or 010A (reverse)
			- Set motor torque to a low % and run it into a hard stop
			- When torque rises above specified % for the prescribed duration, back off to z pulse and set origin
			- Scary, because it's hard-limit homing, but very attractive because no switches, maximizes travel, easy once set up

- Integrating driver homing into LinuxCNC
	- https://github.com/rodw-au/cia402_homecomp/tree/main
	- Haven't tried any of it, but doesn't seem imposisble
	- The goal would be to relinquish motion control to the driver, let it home to establish the origin, then use the absolute encoder to always know where the servo is.

- Absolute Encoder
	- P2.069 = 0001 to enable absolute encoder then power cycle (page 8-94)
	- If AL06A, then origin is not established
	- P0.049 - update encoder absolute position
	- P2.071 or handshake with LinuxCNC to establish absolute origin
		- To set current location as origin:
			- Set P2.008 to 271, then set P2.071 to 1. When P2.071 is set to 1, the current position is set as the origin

- EMC IO
	- http://www.linuxcnc.org/docs/html/man/man1/io.1.html
	- 

- To Do
	- 