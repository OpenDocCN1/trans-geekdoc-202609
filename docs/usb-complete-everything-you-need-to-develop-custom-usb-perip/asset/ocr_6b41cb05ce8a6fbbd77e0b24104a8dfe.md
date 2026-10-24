register and then accesses the data by reading or writing to the Endpoint Data register.

# USB Controller

The ’2272’s USB controller supports full and high speeds and all four transfer types. The controller has three physical endpoints in addition to Endpoint 0. A device that needs more endpoints can use virtual endpoints, where one or more logical endpoints share a physical endpoint’s resources. The device firmware must switch resources between the logical and physical endpoints as needed.

Endpoint 0 has a 128-byte buffer, and the other endpoints share 3 kilobytes of packet buffers. Two of the endpoints can use double buffers. On receiving a Setup packet, the device firmware must read the request and provide any data to return to the host. After a failed IN or OUT transaction, an endpoint automatically recovers and waits for the host to retry.

# FTDI Chip FT232BM and FT245BM

Future Technology Devices International (FTDI) Chip offers controllers that take a different approach to USB design. The FT232BM USB UART and FT245BM USB FIFO are interface chips that manage enumeration and other bus communications completely in hardware. The chips are designed for use with host drivers provided by FTDI Chip. The controllers require no USB-specific firmware at all, though you can use an EEPROM to store values for some items in the descriptors. The device firmware only needs to provide data for the controller to send and retrieve received data. Because the USB communications are handled entirely in hardware and use FTDI Chip’s driver, you can even use FTDI Chips’ Vendor ID in devices you develop and market.

These controllers can be a good solution if your device doesn’t require a standard class driver and you need no more than one bulk or isochronous port in each direction