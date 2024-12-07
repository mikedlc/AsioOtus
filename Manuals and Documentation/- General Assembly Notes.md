# AsioOtus - Callum's Assembly Notes

- Computer:
	- user: callum (case sensitive)
	- password: address, capital E

<h3>Servo Wiring</h3>

- B3 servo drivers connected in series, upper port to upstream servo/computer, lower port daisy-chained downstream
	- First driver is x, then y and z
- Drivers are powered with single phase 240V via the first and third input power terminals 
	- (Use all 3 terminals w/ 3 phase power)
	- Driver power and servo power are separated so servo power can be cut with a contactor if desired
		- I don't plan on doing this; I want the servos to regeneratively brake to decelerate quicker when eStopped


<h3>Parts List</h3>

- Servos
	- B3 Servos
	- B3 Servo Drivers
	- Power cables
	- Encoder cables
	- 18 AWG wire for axis servo driver wiring
- 30A switch
- Limit switches, normally closed
- ETFE wiring for limit switches
- eStop button, normally closed
- 5-port Wago connectors
- MeanWell 24V 50W power supply (for switches and z brake)

- Spindle issue: how to control servo driver that isn't ethercat compatible
	- Best option looks like modbus over RS485
		- Would use USB to RS485 adapter
			- Ordered
		- Would require figuring out both how to program drive to talk over RS485/Modbus as well as how to get LinuxCNC to talk over the same interface
	- Another option would be http://store.mesanet.com/index.php?route=product/product&product_id=408&search=7I76U which would require a way to connect to it, probably necessitating a larger computer with a PCIe slot


- Musings
	- I/O board
		- https://www.aliexpress.us/item/3256805154534518.html?spm=a2g0o.productlist.main.11.66c45Pg25Pg2Ka&algo_pvid=88a4c406-91c2-41de-b4fb-fbb3ffdee25c&algo_exp_id=88a4c406-91c2-41de-b4fb-fbb3ffdee25c-5&pdp_npi=4%40dis%21USD%21112.00%2186.70%21%21%21112.00%2186.70%21%402103209b17319410423355792e5fac%2112000032670056316%21sea%21US%210%21ABX&curPageLogUid=b54gui9J0vKQ&utparam-url=scene%3Asearch%7Cquery_from%3A
		- 