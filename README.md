# Xiaomi M365 scooter OpenSource firmware (my notes, working in progress)

# System overview
* there are 3 main blocks:
  * user interface board (with Bluetooth)
  * motor controller
  * battery BMS

## Connections
* battery BMS -> motor controller: 3 wires (GND, UART TX and UART RX)
* motor controller -> user interface board: 4 wires (GND, 5V, UART TX and UART RX)
* motor controller -> motor: 3 power wires (motor phase wires) + 5 wires (GND, 5V, hall sensor A, B and C) 

## Motor controller
* microcontroller STM32F103C8T6 (48 pins)
* 3 power resistors of 2 milliohms each, to measure motor phase currents and implement FOC motor control
* 2 LM5025 working as stepdown converters (??)
* 3 MT8006 power mosfet drivers

# Firmware development
* the STM32F103C8T6 is very popular
  * to flash and debug the firmware a STLinkV2 clone can be bought 

JTAG pins on STM32F103
* 34 | DIO
* 37 | DCLK
