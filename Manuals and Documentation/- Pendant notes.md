


<h3>Pendant notes</h3>

- Need to create rules file
	- /etc/udev/rules.d/99-xhc-whb04b-6.rules should be created with the single line:
		- ATTR{idProduct}=="eb93", ATTR{idVendor}=="10ce", MODE="0666", OWNER="root", GROUP="plugdev"
- sudo apt-get install usbutils
	- lsusb
- Need HAL file for config