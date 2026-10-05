# Basics of Arduino

![](bbox=[0.218, 0.131, 0.781, 0.319])

FIGURE 4.2

Arduino Mega board.

# TABLE 4.2

Pin Description

| Pin | Description |
| --- | --- |
| Vin | The external voltage to the Arduino board |
| +5V | Output a regulated 5 V |
| 3.3 V | Onboard 3.3 V supply |
| GND | Ground |
| IOREF | It is to select the appropriate power source by providing the voltage reference |
| Serial0 | It can transmit and receive serial data with 0(Rx) and 1(Tx) |
| Serial1 | It can transmit and receive serial data with 19(Rx) and 18(Tx) |
| Serial2 | It can transmit and receive serial data with 14(Rx) and 16(Tx) |
| External Interrupts | It triggers an external interrupt at low value 2 (interrupt 0), 3 (interrupt 1), 18 (interrupt 5), 19 (interrupt 4), and 20 (interrupt 2) |
| PWM | 8 bit PWM (pins: 2-13 and 44-46) |
| SPI | It supports SPI communication [10 (SS), 11 (MOSI), 13 (M)] |
| LED | Driven by pin 13 |
| TWI | Supports TWI communication [pins: 20 (SDA), 21 (SCL)] |
| AREF | It is a reference voltage for analog inputs |
| Reset | It is used to reset the microcontroller by board |

# 4.1.3 Arduino Nano

The Arduino/Genu Nano has an onboard ATmega328 microcontroller. It has 8 analog inputs, 14 digital I/O ports, and 6 PWM. It has 32 KB flash memory, 1 KB EEPROM, 2 KB SRAM, and operates at 16 MHz of frequency. Figure 4.3 shows the Arduino Nano (Tables 4.3 and 4.4).