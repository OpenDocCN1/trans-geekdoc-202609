| Profile | Description | Example Applications |
|---|---|---|
| Application | The most powerful of the profiles. Its main distinguishing feature is the MMU, which allows it to run feature-rich operating systems such as Linux and Android. | Mobile phones Tablets Set-top boxes |
| Real-time | Designed for applications that require real-time performance characteristics. Features low interrupt latency and memory protection. It does not contain an MMU. | Network routers and switches Cameras Cars |
| Microcontroller | Designed for highly embedded systems with lower size and performance requirements. Features low interrupt latency, memory protection, and embedded memory. | Industrial controls Programmable lights |

Table 23-1 ARM Profiles²

MIPS is now owned by Tallwood MIPS, Inc., but has been licensed to several manufacturers such as Broadcom, Cavium, and others.³ Like ARM, MIPS has 32- and 64-bit variants and can be run in either big or little endian mode. It is commonly found in networking devices such as wireless access points and small home routers.

# Serial Interfaces

A serial interface communicates with a peer one bit at a time, serially, over a communication channel. Being that only one bit is being transmitted at a time, fewer pins are required on an IC. In contrast, parallel interface communications transmit multiple bits at a time and require more pins (one pin per bit). Several serial protocols are used in embedded systems, but we will only discuss the Universal Asynchronous Receiver-Transmitter (UART), Serial Peripheral Interface (SPI), and Inter-Integrated-Circuit (I²C) protocols.

# UART

The Universal Asynchronous Receiver-Transmitter protocol allows two devices to communicate serially over a communications channel. UART is commonly used for connecting to a console to allow a human to interact with the device. Although most devices will not have an externally available interface for communicating serially, many will have an internal interface that was used during device development and testing. While performing device testing, I have found both authenticated and unauthenticated consoles on internally accessible serial interfaces. UART requires three pins to communicate and usually comes in a gang of four pins (see