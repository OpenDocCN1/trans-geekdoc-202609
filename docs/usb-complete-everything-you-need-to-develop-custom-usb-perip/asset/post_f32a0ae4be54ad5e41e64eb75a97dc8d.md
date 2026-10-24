
The Philips Transfer Descriptor (PTD) defines a format for exchanging information with the host controller's driver. The descriptor consists of a header that contains information such as the endpoint number, transaction type (Setup, IN, OUT), bus speed, toggle-bit value, and a completion code, followed by data.

The chip contains two USB ports. One port can function as the OTG port in an OTG device or as a host or device port for a non-On-The-Go host or device. The second port can function only as a host port and is not recommended for use in On-The-Go devices.

Philips provides host, peripheral, and OTG drivers for PCI platforms running Linux, Windows CE, DOS, and the FlexiUSB real-time operating system and for Intel PXA250/ARM architecture platforms running Linux or Windows CE.

If you need high speed, the ISP1761 is an OTG controller that supports high speed and can use a 16-bit or 32-bit CPU interface.

## TransDimension TD242LP

TransDimension Inc.'s TD242LP is a physically small, low-power interface chip especially suited for compact and inexpensive dual-role products.

The controller interfaces to an external CPU using a 16-bit data bus that can transfer data at up to 22 Megabytes/sec.

The chip has two USB ports that can be configured in any of four modes. In Hardware HNP mode, one port is an OTG device port, the other is a non-OTG host port, and HNP is handled in hardware. Software HNP mode is the same except that HNP is handled in software. In Host Only mode, there is a single non-OTG host with two ports. In Function Host mode, one port is for a non-OTG host and the other is for a peripheral-only device. Both ports can operate at low and full speeds.

For reduced EMI, the chip can be clocked at 6 Megahertz rather than 48 Megahertz.

The Host Endpoint Transfer Descriptor defines a format for sending and receiving USB data. Information in the descriptor includes the endpoint number, transfer type, bus speed, direction, and a completion code.

TransDimension supplies a host-controller driver for Linux and Windows CE. Other operating systems can use USBLink drivers from SoftConnex.

## Cypress CY7C67200 EZ-OTG

As the name suggests, Cypress Semiconductor's CY7C67200 EZ-OTG controller is designed for use in OTG devices. The chip contains a 16-bit CPU and can function in two modes. In stand-alone mode, the controller is the device's main CPU. Firmware can be stored in an I²C EEPROM or the controller can download its firmware from a USB host using the same method used by the EZ-USB chips described in Chapter 6. In coprocessor mode, the controller interfaces to an external CPU that manages USB communications and other tasks. The CPU can communicate via either a parallel Host Peripheral Interface at up to 16 Megabytes/sec., a high-speed asynchronous serial interface at up to 2 Megabaud, or a Serial Peripheral Interface (SPI) at up to 2 Megabits/sec.

The EZ-OTG has two USB ports and two serial interface engines that support low and full speeds. One port can function as an OTG device, a non-OTG host, or a peripheral-only device port. The other port can function as a non-OTG host or peripheral-only device port.

The controller contains a ROM BIOS that executes an Idle task consisting of an endless loop that waits for an interrupt, executes the tasks in the Idle chain, and repeats. Firmware can add tasks to the Idle chain or replace the entire Idle task with device-specific programming.

Firmware development can use the free GNU Toolset, which supports many CPUs and includes a C compiler, assembler, make utility, linker, debugger and other utilities. Cypress provides Frameworks C code for performing USB-related tasks and accessing other components in the controller.

A tutorial and many examples are in the free e-book, *USB Multi-Role Device Design By Example*, by John Hyde, available from www.usb-by-example.com.

A related chip, the CY7C67300 EZ-HOST, includes an interface to external memory, two ports for each of the two SIEs, memory expansion capabilities, and additional I/O features.

## Philips ISP1261 Bridge Controller

Philips Semiconductor's ISP1261 is a bridge controller that takes a different approach to OTG design. With this controller and some additional firmware, an ordinary USB device can function as a "pseudo host" that can communicate with USB devices.

The ISP1261 adds some overhead, so it doesn't provide the most efficient communications, but the chip can offer a quick way to add host capability to a device. The controller can be integrated into a device or implemented as a separate dongle that attaches to a device's USB port. When implemented as a dongle, the bridge requires no hardware changes on the device, though the device must be able to store and run new firmware that communicates with the bridge controller.

The bridge contains a host port and host controller and an OTG port and OTG controller. The host port connects to the local device, and the OTG port connects to the remote host or device that the local device wants to communicate with. The host controller communicates with the local device, and the OTG controller communicates with the remote device. A Software Emulated OTG Controller (SEOC) Protocol Engine manages communications between the host controller and the OTG controller. A state machine implements the SEOC Protocol.

I hope you've found *USB Complete* to be useful. For more about USB developing, including device and host example code and links to product information, tutorials, articles, news, and updates, please visit my Web site at *www.Lvr.com*.

Jan Axelson

## Index

Page numbers in italics indicate figures and tables.

- A
- ACK (acknowledge) handshake code, 48, 52, 53, 55, 56, 56, 57
- ACPI (Advanced Configuration and Power Interface) specification, 467
- Address field, 500, 500
- Advanced Configuration and Power Interface (ACPI) specification, 467
- Agere Systems, 166, 533
- AMD chips, 155
- AnywhereUSB, 525, 534
- API (Applications Programming Interface). See Windows API functions
- Apple Macintosh, support for USB, 7–8
- Applications Programming Interface (API). See Windows API functions
- assemblers, as necessary tool for USB device development, 30
- Atmel chips, 155
- audio class
  - about, 181–2, 182
  - chips, 188
  - descriptors, 182–8
  - documentation, 181
  - INF file, 276
  - types of Unit descriptor, 184, 187
  - where declared, 179
  - Windows support, 189
- AudioControl interface, 183, 183
- AudioStreaming interface, 184, 185
- B
- B & B Electronics, 530
- babble, 444
- bandwidth
  - for bulk transfers, 71
  - for control transfers, 66, 67, 321
  - for interrupt transfers, 72, 74, 75, 81
  - for isochronous transfers, 78, 79, 80, 81
  - role in data transfer, 24
  - role of transaction translator, 71
  - as speed-limiting factor, 81
- batteries. See self-powered devices
- Battery Devices device setup class, 251
- BIOS, 10–11
- bit stuffing, 496–7
- bridges, wireless, 534
- broadcasting, 11
- buffers, in USB controllers, 143–4
- bulk endpoints, 54, 58
- bulk transfers
  - about, 41–2, 46, 68
  - asynchronous serial interface example, 408, 409, 410, 411–13, 414
  - availability, 69
  - vs. control transfers, 41, 46
  - data size, 69, 71
  - data toggles in, 58
  - error handling, 71–2
  - vs. interrupt transfers, 41, 46
  - vs. isochronous transfers, 41, 46
  - maximum data-transfer rate per endpoint, 62
  - parallel interface example, 414, 415, 416, 417, 418–21, 421
  - speed, 71
  - and stream pipes, 43
  - structure, 69, 70
  - transactions, 36, 46
- bus drivers, 234, 237, 238, 239, 239, 240, 246, 257
- bus power
  - about, 24, 26–7, 455–6
- Freescale MCF5482 ColdFire, 164
- Microchip Technology PIC16C745/65, 155, 157
- Microchip Technology PIC16F877 microcontroller in FT232BM device controller example, 408, 410, 411–13, 414
- Microchip Technology PIC16F877 microcontroller in FT245BM device controller example, 414, 415, 416, 417, 418–21, 421
- Microchip Technology PIC18F4550, 155, 156–7, 338
- National Semiconductor USBN9603, 165–7
- for OTG devices, 545–9
- Philips ISP1181B, 166, 167–8
- Philips ISP1261, 549
- Philips ISP1362, 546–7
- Philips ISP1581, 166, 168–9
- Philips PDIUSBD12, 166
- PLX Technology NET2272 controller, 166, 169–70
- TransDimension TD242LP, 547–8
- chip/smart card interface class, 179, 189–91, 251, 276
- Chirp J bus state, 493
- Chirp K bus state, 493
- ChkInf tool, 266, 277
- class descriptor, HID, 326–8, 327
- class drivers
  - advantages of using, 226–7
  - vs. custom drivers, 226–7
- classes
  - about, 177–80
  - audio class, 179, 181–9
  - chip/smart card interface class, 179, 189–91, 251, 276
  - communication class, 179, 191–8, 251
  - Content Security class, 179, 198–200
  - Device Firmware Upgrade (DFU) class, 179, 200–2
  - device setup, 250–1
  - and Device Working Groups, 178
  - Human Interface Device (HID) class, 179, 203–6, 251, 276, 319
  - IrDA Bridge class, 179, 206–8, 534
  - mass-storage class, 179, 208–13, 251
  - printer class, 179, 213–17, 251
  - specification elements, 178–80, 180
  - standard vs. custom drivers, 226–7
  - still-image class, 179, 217–20, 251
  - test-and-measurement class, 179, 220–1
  - video class, 179, 221–6
- class installers, 279
- class keys, Windows registry, 250, 259–60, 260
- class specifications, 178–80, 179, 180
- class-specific requests
  - about, 140
  - audio class, 188
  - chip/smart card interface, 191
  - communication-device class, 196
  - Content Security class, 199–200
  - Device Firmware Upgrade class, 202
  - HIDs, 204–5
  - hub class, 451, 452–3
  - IrDA interface, 207
  - mass-storage devices, 212
  - printer class, 215
  - still-image class, 219
  - test-and-measurement class, 221
  - video class, 225
- Clear_Feature request, 128, 130, 452
- Clear_Hub_Feature request, 451, 452, 453
- Clear_Port_Feature request, 451, 452, 454
- Clear_TT_Buffer request, 451, 452
- client drivers, in layered driver model, 238–40, 239, 240, 245
- clocks, in USB controllers, 145
- CloseHandle API function
  - about, 306
  - defined, 304
  - in Visual Basic code, 306
  - in Visual C++ code, 306
- CLR (common language runtime), 282
- code, managed vs. unmanaged, 282–4
- co-installers, 279
- Collection items, 360–1, 361
- Command Block Wrapper (CBW), 209–10, 210
