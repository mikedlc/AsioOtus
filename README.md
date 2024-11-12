# AsioOtus

This is a repo created to house the config files and other build information for the Asio Otus mill project

Kinematics (Joint) explanation:
https://linuxcnc.org/docs/html/motion/kinematics.html

Example ethercat servo configs:
https://github.com/gchesney/linuxcnc-asda-b3-e-configs

More example configs from rodw-au:
https://github.com/rodw-au/linuxcnc-cia402

Original how-to step by step from rodw:
https://forum.linuxcnc.org/ethercat/45336-ethercat-installation-from-repositories-how-to-step-by-step

On what HAL is and examples, from https://github.com/dbraun1981/hal-cia402:
- this component acts as a glue layer between hardware to Hal modules like Ethercat, CAN-Bus or others.
- HARDWARE INPUT-->--CiA402_read-->--Motion-->--CiA402_write-->--Hardware Output
- Code examples in the git repo.
