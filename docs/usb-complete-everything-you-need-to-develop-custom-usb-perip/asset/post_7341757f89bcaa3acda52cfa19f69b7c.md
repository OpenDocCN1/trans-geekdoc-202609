
## Detecting the Speed of a Dual-Speed Device

A high-speed device must respond to enumeration requests at full speed, and the device may also be completely functional at full speed. As Chapter 1 explained, a high-speed-capable device must use full speed if it has a 1.x host or if there is a 1.x hub between the host and device. Applications and device drivers normally don’t need to know which speed a dual-speed device is using because all of the speed-related details are handled at a lower level. Windows provides no straightforward way to learn a device’s speed. But if a host application wants to know, there are a few techniques that can detect the bus speed for many devices.

If a device has a bulk endpoint, you can learn the current speed by examining the endpoint descriptor in the active configuration. The wMaxPacketSize field must be 512 in a high-speed device and can’t be 512 in a full-speed device. If there is no bulk endpoint, the wMaxPacketSize of an interrupt or isochronous endpoint provides speed information if the endpoint uses a maximum packet size available only at high speed. For an interrupt endpoint, a wMaxPacketSize greater than 64 indicates high speed. If the wMaxPacketSize is 64 or less, the device may be using full or high speed. For isochronous endpoints, a wMaxPacketSize of 1024 indicates high speed. If wMaxPacketSize is 1023 or less, the device may be using full or high speed.

If you’re writing the device firmware, you can provide speed information in the optional strings indexed by the configuration and other_speed_configuration descriptors. For example, the string indexed by the configuration descriptor might contain the text “high speed,” and the string indexed by the other_speed_configuration descriptor might contain the text “full speed.” Applications can then read the configuration string to learn the current speed.

The USBView application in the Windows DDK shows how applications can read descriptors.

## 5

## Control Transfers: Structured Requests for Critical Data

Of USB’s four transfer types, control transfers have the most complex structure. They’re also the only transfer type with functions defined by the USB specification. This chapter looks in greater detail at the structure of control transfers and the requests defined in the specification.

### Elements of a Control Transfer

As Chapter 2 explained, control transfers enable the host and a device to exchange information about the device’s capabilities. Control transfers also offer a way for devices to transfer other class-specific or vendor-specific information. As explained in Chapter 3, a control transfer has a defined format consisting of a Setup stage, a Data stage (optional for some transfers), and a Status stage. Each stage consists of one or more transactions that each contain a token phase, data phase, and handshake phase. Each phase transfers a token, data, or handshake packet.

As described in Chapter 2, low-speed transfers also use PRE packets, high-speed transfers use the PING protocol, and some low- and full-speed transfers use split transactions. Each packet also contains error-checking bits. Application programmers, device-driver writers, and firmware developers don’t have to worry about PREs, PINGs, error-checking, or split transactions because the host controller, hubs, and device hardware handle these protocols.

### Setup Stage

The Setup stage consists of a Setup transaction, which has two purposes: to identify the transfer as a control transfer and to transmit the request and other information that the device will need to complete the request.

Devices must accept and acknowledge every Setup transaction. A device that is in the middle of another control transfer must abandon that transfer and acknowledge the new Setup transaction. Here are more details about each of the packets in the Setup stage’s transaction:

### Token Packet

**Purpose:** identifies the receiver and identifies the transaction as a Setup transaction.

**Sent by:** the host.

**PID:** SETUP

**Additional Contents:** the device and endpoint addresses.

### Data Packet

**Purpose:** transmits the request and related information.

**Sent by:** the host.

**PID:** DATA0

**Additional Contents:** eight bytes in five fields: bmRequestType, bRequest, wValue, wIndex, and wLength.

**bmRequestType** is a byte that specifies the direction of data flow, the type of request, and the recipient.

Bit 7 is a Direction bit that names the direction of data flow for data in the Data stage. Host to device (OUT) or no Data stage is 0; device to host (IN) is 1.

Bits 6 and 5 are Request Type bits that specify whether the request is one of USB’s standard requests (00), a request defined for a specific USB class (01), or a request defined by a vendor-specific driver for use with a particular product or products (10).

Bits 4 through 0 are Recipient bits that define whether the request is directed to the device (00000) or to a specific interface (00001), endpoint (00010), or other element (00011) in the device.

**bRequest** is a byte that specifies the request. Every defined request has a unique bRequest value. When the Request Type bits in bmRequestType = 00, bRequest specifies one of the standard USB requests. When the Request Type bits = 01, bRequest specifies a request defined for the device’s class. When the Request Type bits = 10, bRequest specifies a request defined by a vendor.

**wValue** is two bytes that the host may use to pass information to the device. Each request may define the meaning of these bytes in its own way. For example, in a Set_Address request, wValue contains the device address.

**wIndex** is two bytes that the host may use to pass information to the device. A typical use is to pass an index or offset such as an interface or endpoint number, but each request may define the meaning of these bytes in any way. When passing an endpoint index, bits 0-3 indicate the endpoint number, and bit 7 = 0 for a Control or OUT endpoint or 1 for an IN endpoint. When passing an interface index, bits 0–7 are the interface number. All unused bits are zero.

**wLength** is two bytes containing the number of data bytes in the Data stage that follows. For a host-to-device transfer, wLength is the exact number of bytes the host wants to transfer. For a device-to-host transfer, wLength is a maximum, and the device may return this number of bytes or fewer. If the wLength field is zero, there is no Data stage.

### Handshake Packet

Purpose: transmits the device’s acknowledgement.

Sent by: the device.

PID: ACK.

Additional Contents: none. The handshake packet consists of the PID alone.

Comments: If the device detects an error in the received Setup or Data packet, the device returns no handshake. The device’s hardware typically handles the error checking and sending of the ACK, with no programming required.

### Data Stage

When a control transfer contains a Data stage, the stage consists of one or more IN or OUT transactions. The device descriptor specifies the maximum number of data bytes in a transaction at Endpoint 0.

When the Data stage uses IN transactions, the device sends data to the host. An example is the Get_Descriptor request, where the device sends a requested descriptor to the host. When the Data stage uses OUT transactions, the host sends data to the device. An example is HID-class request Set_Report, where the host sends a report to a device. If the wLength field in the Setup transaction is zero, there is no Data stage. For example, in the Set_Configuration request, the host passes a configuration value to the peripheral in the wValue field of the Setup stage’s data packet, so there’s no need for a Data stage.

If all of the data can’t fit in one packet, the stage uses multiple transactions. The number of transactions required to send all of the data for a transfer equals the value in the Setup transaction’s wLength field divided by the wMaxPacketSize value in the endpoint’s descriptor, rounded up. For exam-
