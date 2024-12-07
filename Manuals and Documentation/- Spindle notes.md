- 3.7 kW spindle servo at 12k? RPM
    - Incremental magnetic encoder
        - What resolution?
    - 
- Honwin H150-2S3.7GB-MC-ABZ driver
    - Has RS485 Modbus interface
    - Might take HW-EtherCAT expansion card to enable EtherCAT communication
        - I'd REALLY like this to be possible
        - Looks like the incremental encoder card uses the expansion slot that the HW-EtherCAT card would go into


- mb2Hal
    - https://linuxcnc.org/docs/html/drivers/mb2hal.html
    - https://forum.linuxcnc.org/25-classicladder/49895-yl620-a-vfd-rs485-modbus-spindle-control
        - I think this uses classicladder, but not entirely sure

- Example with a different VFD: https://forum.linuxcnc.org/24-hal-components/37715-mb2hal-vacon-vfd



- H150 Modbus
    - Appendix A on Modbus communication: page 167
    - Modbus communication settings: P50 on page 58
    - P01 Start and Stop Control Parameters
        - P01.00 Run command source selection
            - 0: keypad command mode
            - 1: terminal command mode
            - 2: Communication command mode
                - I think I want this mode for use with Modbus
        - P01.02 Running direction selection, register 0x0102
            - 0: forward
            - 1: reverse
        - P00.00 Main frequency reference digital setting, register 0x0000
        - P00.01 Main frequency reference source selection
        - 