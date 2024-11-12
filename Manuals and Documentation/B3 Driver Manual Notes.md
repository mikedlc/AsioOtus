# AsioOtus - Digital IO Setup Notes from PDFs

<h3>From 'B3 Driver Manual.pdf'</h3>

- Section pages 8-73 and 8-190 in the software manual
- Page 8-13 has the Ditgital Input and Output functional planning parameters (Parameter Numbers P1.XXX, P2.XXX, P3.XXX, etc...)
- The eStop and limit assignments are on 8-195
	- 0x21 is EMGS (estop)
	- 0x22 is NL (CWL) Negative inhibit limit (normally closed contact)
	- 0x23 is PL (CCWL) Positive inhibit limit (normally closed contact)
- brake output is on 8-199
	- 0x08 is BRKR Output signal of the magnetic brake control. Set MBT1 P1.042 and MBT2 P1.043 to adjust the delay time before and after the brake control is activated and deactivated..
	- Notes to refer to the note in P1.042
- Physical/software control option is 3.006 on page 8-108
- DI functional planning
	- Page 8-73
	- P2.010 - P2.013 are DI1 - DI4, the 4 digital inputs with physical pin assignments
	- P2.014 - P2.017 are DI4 - DI8 and don't have physical pins but are addressable in software
- DI pin assignments on page 3-52, wiring on 3-62
	- COM+ - pin 5
		- Gets +24V from external power supply
	- Digital Inputs, get negative terminal from external power supply, normally closed (NC) switched
		- DI1- - pin 6 - 0021 (eStop)
		- DI2- - pin 7 - 0022 (CW Limit)
		- DI3- - pin 8 - 0023 (CCW Limit)
		- DI4- - pin 9 - 0000 (disabled)