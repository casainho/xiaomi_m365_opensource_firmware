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
  * to flash and debug the firmware, a STLinkV2 clone can be bought on Aliexpress for 3€
  * software tools do flash, debug, edit and build the firmware: OpenOCD, GCC and Visual Code Studio
  * there are many motor controllers based on STM32F103C8T6, like the ones on hoverboard, electric unicycles, ebikes
  * there are OpenSource firmware to implement motor control FOC on STM32F103 or other similar STM32:
    *  [EBike motor controller Lishui)(https://github.com/EBiCS/EBiCS_Firmware)

* JTAG pins to flash and debug the firmware are available on the board and 3 wires must be soldered:
* GND
* 34 | DIO
* 37 | DCLK
