# Table 14.1 Comparison of Microcontrollers/Microprocessors Used in Healthcare Applications

| Name | Arduino | NodeMCU | Raspberry pi |
|---|---|---|---|
| Processor/controller | ATMEGA328 microcontroller | ESP8266 | ARM |
| Analog input | 6 pins | 1 pin | — |
| Digital I/O | 14 pins | 16 pins | 17 pins |
| Memory | 32 kB of flash memory, 2 kB of SRAM | 4 MB of flash memory, 64 kB of SRAM | 32 GB of SD card, 1 GB of DDR2 |
| Ethernet | — | — | Yes |
| Wi-Fi | — | Yes | Yes |
| Programming environment | Arduino IDE, C and C++ | Arduino IDE | Raspbian OS, Python |

# 14.3.3 Challenges

Cyber-physical system enables the continuous and non-expansive monitoring of health data by using WBAN sensors, networks and cloud.

# 14.3.3.1 Sensitivity

In harsh environments like fire situation, the device sensitivity is considered as an important one. Sweat and water droplets also affect the performance of the sensors. Care should be given for designing high sensitivity and requiring less maintenance devices.

# 14.3.3.2 Energy

Sensors are battery-powered and energy consumption devices. It is very difficult to recharge the batteries. The design requires low power and green energy enabled devices.