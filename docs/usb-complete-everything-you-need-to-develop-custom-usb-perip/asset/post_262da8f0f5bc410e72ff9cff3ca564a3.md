
## Chapter 6

### USB Controller

The ISP1181B's USB controller supports Endpoint 0 plus up to 14 additional endpoint addresses. All enabled endpoints share 2462 bytes of buffer memory. The control endpoint has 64-byte buffers. The amount of memory allocated to each of the other endpoint addresses is configurable. Isochronous and bulk endpoints are double buffered.

Firmware controls when the chip attaches to the bus. The chip appears detached from the bus until the external CPU sends a command to switch an internal pull-up resistor onto the bus’s D+ line. The firmware-controlled connection can give the chip time to initialize on power up before being enumerated by the host.

A status output can connect to an LED that lights when a USB connection has been established and blinks on data transfers.

### Philips Semiconductors ISP1581

The ISP1581 from Philips Semiconductors is a full/high-speed controller that interfaces to an external CPU over a parallel interface.

### Architecture

The chip has a serial interface engine for handling USB traffic, a 16-bit data bus, and an 8-bit address bus. An external CPU can communicate with the controller by accessing a series of registers. The controller supports multiplexed and non-multiplexed address buses and DMA transfers.

### USB Controller

The USB controller supports full and high speeds. In addition to Endpoint 0, the chip can support up to seven IN endpoint addresses and seven OUT endpoint addresses. All enabled endpoints share 8 kilobytes of buffer memory. The control endpoint has 64-byte buffers. The amount of memory allocated to each of the other endpoint addresses is configurable, and any of these endpoint addresses can use double buffering.

Firmware controls when the chip attaches to the bus. An external pull-up resistor connects to the chip’s RPU pin and to a pull-up voltage. After a hardware reset, the chip appears detached from the bus until the external CPU sets a register bit that causes the chip to switch the pull-up onto the bus's D+ line. This firmware-controlled connection can give the chip time to initialize on power up before being enumerated by the host.

### PLX Technology NET2272

PLX Technology, Inc.’s NET2272 is a full/high-speed chip that interfaces to an external CPU over a parallel interface. PLX Technology acquired Netchip Technology, Inc. and its USB controllers in 2004.

### Architecture

A series of registers hold configuration data and other information. Packet buffers hold USB data that has been received and data that is ready to transmit. The parallel interface has 5 address bits and 16 data bits. Transfers to and from the packet buffers can be 8 or 16 bits.

The registers store status and control information and the data received in the last Setup transaction. The CPU also uses registers to read and write endpoint data from and to the packet buffers.

The ’2272 supports three modes for accessing its registers. In direct address mode, the five address bits specify a register to read or write to. In multiplexed address mode, the CPU places the register address on the data bits and the ’2272 reads the address on the falling edge of the ALE control signal. In indirect address mode, the CPU uses the lowest address bit to distinguish between a register address pointer (0) and data (1). The CPU writes a register address pointer to specify a configuration register and then reads or writes data at the address pointed to. Direct and multiplexed address modes can access only the registers from 00h to 1Fh, which typically contain the information accessed most frequently. Indirect address mode can access all registers. The controller also supports DMA transfers. A CPU can write to the ’2272 at up to 60 Megabytes/sec. and can read from the ’2272 at up to 57 Megabytes/sec (in DMA mode).

To access endpoint data in the packet buffers, the CPU selects an endpoint by writing to the Endpoint Page Select register or the DMA Endpoint Select register and then accesses the data by reading or writing to the Endpoint Data register.

### USB Controller

The ’2272’s USB controller supports full and high speeds and all four transfer types. The controller has three physical endpoints in addition to Endpoint 0. A device that needs more endpoints can use virtual endpoints, where one or more logical endpoints share a physical endpoint’s resources. The device firmware must switch resources between the logical and physical endpoints as needed.

Endpoint 0 has a 128-byte buffer, and the other endpoints share 3 kilobytes of packet buffers. Two of the endpoints can use double buffers. On receiving a Setup packet, the device firmware must read the request and provide any data to return to the host. After a failed IN or OUT transaction, an endpoint automatically recovers and waits for the host to retry.

### FTDI Chip FT232BM and FT245BM

Future Technology Devices International (FTDI) Chip offers controllers that take a different approach to USB design. The FT232BM USB UART and FT245BM USB FIFO are interface chips that manage enumeration and other bus communications completely in hardware. The chips are designed for use with host drivers provided by FTDI Chip. The controllers require no USB-specific firmware at all, though you can use an EEPROM to store values for some items in the descriptors. The device firmware only needs to provide data for the controller to send and retrieve received data. Because the USB communications are handled entirely in hardware and use FTDI Chip’s driver, you can even use FTDI Chips’ Vendor ID in devices you develop and market.

These controllers can be a good solution if your device doesn’t require a standard class driver and you need no more than one bulk or isochronous port in each direction.

### Architecture

Both chips are full speed. The FT245BM has a parallel interface and the FT232BM has an asynchronous serial interface.

Table 6-5 shows the functions of the pins on the ’245BM. The parallel interface has 8 data lines and four handshaking signals. The names of the handshaking signals are from the perspective of the external CPU that interfaces to the chip. The RXF# output is low when the CPU can read a byte received from the host. The CPU strobes RD# to read the byte. In the other direction, the TXE# output goes low when the CPU can write a byte to send to the USB host, and the CPU strobes WR to write the byte into the ’245BM’s buffer. The external CPU can use a data bus or any spare port pins to access the ’245BM.

The ’232BM converts between USB and an asynchronous serial interface. Table 6-6 shows the functions of the pins. The serial interface includes a TXD data output, an RXD data input, and pins for standard RS-232 handshaking signals (RTS, CTS, DTR, DSR, DCD, and RI). A TXDEN output is high when data is transmitting on TXD. This output can interface directly to the transmit-enable input of an RS-485 transceiver, eliminating the need to enable the transmitter using firmware and additional hardware. The ’232BM functions as a DTE as defined by the EIA/TIA-232 standard. (The RS-232 ports on PCs are also DTEs.) On a DTE, the TXD, RTS#, and DTR signals are outputs, and the RXD, CTS#, and DSR signals are inputs. A device that functions as a DCE has complementary signals. (For example, TXD is an input and RXD is an output.) To connect two DTEs to each other, use a null-modem cable that swaps the signal pairs so each output connects to its corresponding input.

To create a USB/RS-232 converter, use a Maxim MAX3245 or similar chip to convert between the ’232BM’s 5V logic signals and RS-232 voltages. In a similar way, you can interface the ’232BM to an RS-485 transceiver. Chapter 7 has more about using the ’232BM to convert devices to USB from these legacy interfaces.

Both chips also support a Bit Bang mode, where the chip operates as a very basic controller without requiring a connection to an external CPU. On the

## Chapter 6

Table 6-5: Pinout of the FT245BM USB FIFO.

| Pin | Name | I/O | Description |
|---|---|---|---|
| 1 | EESK | Output | EEPROM clock |
| 2 | EEDATA | Output | EEPROM data |
| 3 | VCC | Power | +4.35 to 5.25V |
| 4 | RESET# | Input | Reset the chip |
| 5 | RSTOUT# | Output | Output of the Reset Generator |
| 6 | 3V3OUT | Output | Regulated +3.3V output |
| 7 | USBDP | I/O | D+ USB data |
| 8 | USBDM | I/O | D- USB data |
| 9 | GND | Power | Ground |
| 10 | PWREN# | Output | Goes low when device is configured, goes high in Suspend state |
| 11 | SI/WU | IN | Send USB data on next bulk IN/request remote wakeup |
| 12 | RXF# | Output | Goes low when the FIFO contains data that the CPU can read |
| 13 | VCCIO | Power | +3.0 to 5.25V |
| 14 | TXE# | Output | Goes low when the CPU can write data into the FIFO |
| 15 | WR | Input | On H > L transition, writes D0–D7 to the transmit FIFO buffer |
| 16 | RD# | Input | On H > L transition, places a byte from the receive FIFO buffer on D0–D7 for the CPU to read |
| 17 | GND | Power | Ground |
| 18 | D7 | I/O | Data bit 7 |
| 19 | D6 | I/O | Data bit 6 |
| 20 | D5 | I/O | Data bit 5 |
| 21 | D4 | I/O | Data bit 4 |
| 22 | D3 | I/O | Data bit 3 |
| 23 | D2 | I/O | Data bit 2 |
| 24 | D1 | I/O | Data bit 1 |
| 25 | D0 | I/O | Data bit 0 |
| 26 | VCC | Power | +4.35 to 5.25V |
| 27 | XTIN | Input | Crystal oscillator cell input |
| 28 | XTOUT | Output | Crystal Oscillator cell output |
| 29 | AGND | Power | Analog ground |
| 30 | AVCC | Power | Analog power supply |
| 31 | TEST | Input | Bring high to enable Test mode |
| 32 | EECS | I/O | EEPROM Chip Select |
