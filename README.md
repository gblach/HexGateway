# HexGateway
An internet gateway for Bluetooth LE, OpenThread and/or Zigbee devices.

It employs three chips:
- nrf52840 - has support for Bluetooth LE, OpenThread and Zigbee networks.
- esp32-c3 - has support for WiFi at 2.4GHz.
- enc28j60 - has support for Ethernet network.

![HexGateway image](HexGateway.png)

## Hardware
To build your own board you need this [gerber file](HexGateway.zip) and [bill of materials](HexGateway.csv).

Note that U102 is required only if your are using esp32-c3 (U101) without built-in flash memory. 

## Programmers
nrf52840 (U1) can be programmed using the standalone [Segger J-Link](https://www.segger.com/products/debug-probes/j-link/) or the on-board Segger J-Link (this can be found for e.g. on [nrf52840dk](https://www.nordicsemi.com/Products/Development-hardware/nRF52840-DK) board). This programmer must be connected to J1 (TagConnect) or J2 (IDC 10) connector.

esp32-c3 (U101) can be programmed using [ESP-Prog](https://docs.espressif.com/projects/espressif-esp-iot-solution/en/latest/hw-reference/ESP-Prog_guide.html). This programmer must be connected to J101 (TagConnect) or J102 (IDC 6) connector.

enc28j60 (U201) does not need to be programmed.

## Software
For the nrf52840 chip you have to write your own software that will meet your requirements. The best way is to use [Zephyr RTOS](https://www.zephyrproject.org/). The board definition for Zephyr can be found in [boards/arm/hexgw1](boards/arm/hexgw1) directory.

esp32-c3 can be controlled with AT commands. To do this, you need to upload [ESP-AT](https://github.com/espressif/esp-at) firmware.