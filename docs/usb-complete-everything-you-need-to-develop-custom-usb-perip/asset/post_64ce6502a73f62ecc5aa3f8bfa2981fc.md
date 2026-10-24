
## Enumeration: How the Host Learns about Devices

Bits 11 and 12 specify the number of additional transactions the endpoint can support per microframe: 00 = no additional transactions (total of 1 transaction per microframe), 01 = 1 additional (total of 2 transactions per microframe), 10 = 2 additional (total of 3 transactions per microframe), 11 = reserved. In USB 1.x, these bits were reserved and set to zero. Bits 13 through 15 are reserved and must be zero.

**bInterval.** Can indicate the maximum latency for polling interrupt endpoints, the interval for polling isochronous endpoints, or the maximum NAK rate for high-speed bulk OUT or control endpoints. The allowed range and how the value is used varies with the device speed, the transfer type, and whether or not the device complies with USB 2.0.

For low-speed interrupt endpoints, the maximum latency equals bInterval in milliseconds. The value may range from 10 to 255.

For all full-speed interrupt endpoints and for full-speed isochronous endpoints on 1.x devices, the interval equals bInterval in milliseconds. For interrupt endpoints, the value may range from 1 to 255. For isochronous endpoints in 1.x devices, the value must be 1. For isochronous endpoints in full-speed 2.0 devices, values from 1 to 16 are allowed, and the interval is calculated as 2^{bInterval-1}, allowing a range from 1 millisecond to 32.768 seconds.

For full-speed bulk and control transfers, the value is ignored.

For high-speed endpoints, the value is in units of 125 microseconds, which is the width of a microframe. The value for interrupt and isochronous endpoints may range from 1 to 16, and the interval is calculated as 2^{bInterval-1} to allow a range from 125 microseconds to 4.096 seconds.

For high-speed bulk OUT and control endpoints, the value indicates the endpoint's maximum NAK rate. This value is relevant when the device has received data and returned ACK, and the host has more data to send in the transfer. By returning ACK, the device is saying that it expects to be able to accept the next transaction's data. (Otherwise the device would return NYET.) If the next data packet arrives and for some reason the device can't accept the packet, the endpoint returns NAK. The bInterval value says that the endpoint will return NAK no more than once in each period specified by bInterval. The value can range from 0 to 255 microframes. A value of zero means the endpoint will never NAK. The host isn't required to use the maximum-NAK-rate information.

### String Descriptor

A string descriptor contains descriptive text. The USB 2.0 specification defines descriptors that can contain indexes to various strings, including strings that describe the manufacturer, product, serial number, configuration, and interface. Class- and vendor-specific descriptors can contain indexes to additional string descriptors. Support for string descriptors is optional, though a class may require them. A host retrieves a string descriptor by sending a Get_Descriptor request with the high byte of the Setup transaction's wValue field equal to 3. Table 4-11 shows the descriptor's fields and their purposes.

**Table 4-11:** A string descriptor has three or more fields.

| Offset (decimal) | Field | Size (bytes) | Description |
|---|---|---|---|
| 0 | bLength | 1 | Descriptor size in bytes |
| 1 | bDescriptorType | 1 | The constant STRING (03h) |
| 2 | bString or wLANGID | varies | For string descriptor 0, an array of 1 or more Language Identifier codes. For other string descriptors, a Unicode string. |

#### The Descriptor

bLength. The number of bytes in the descriptor.

bDescriptorType. The constant STRING (03h).

#### The String

When the host requests a String descriptor, the low byte of the wValue field is an index value. An index value of zero has the special function of requesting language IDs, while other index values request strings that may contain any text.

wLANGID[0...n]. Used in string descriptor 0 only. String descriptor 0 contains one or more 16-bit language ID codes that indicate the languages that the strings are available in. The code for English is 0009h, and the subcode for U.S. English is 0004h. These are likely to be the only codes supported by an operating system. The wLANGID value must be valid for any of the other strings to be valid. Devices that return no string descriptors must not return an array of language IDs. The USB-IF's web site has a list of defined USB language IDs.

bString. For values 1 and higher, the String field contains a Unicode string. Unicode uses 16 bits to represent each character. With a few exceptions, ANSI character codes 00h through 7Fh correspond to Unicode values 0000h through 007Fh. For example, a product string for a product called "Gizmo" would contain five 16-bit Unicode values that represent the characters in the product name: 0047 0069 007A 006D 006F. The strings are not null-terminated.

### Other Standard Descriptors

The USB 2.0 specification lists three additional descriptor codes for interface_power, OTG, and debug descriptors.

The interface_power descriptor is defined in a proposed Interface Power Management specification to enable interfaces to manage their power consumption individually. The specification was proposed by Microsoft in 1998 but hasn't been approved or implemented. The document describing this descriptor's structure and use is USB Feature Specification: Interface Power Management.

The OTG descriptor is required for devices that support On-The-Go's Host Negotiation Protocol (HNP) or Session Request Protocol (SRP). The descriptor indicates the supported protocols. Chapter 20 has more about this descriptor.

The debug descriptor is defined in a proposed specification for USB 2.0 Debug Devices. A debug device connects to the optional debug port defined in the EHCI specification for high-speed host controllers. The debug port and device are intended to replace the RS-232 port that PCs have long used for debugging purposes.

### The Microsoft OS Descriptor

Microsoft has defined its own Microsoft OS descriptor for use with devices in vendor-defined classes. The descriptor is intended to assist in providing Windows-specific data such as icons and registry settings.

The descriptor consists of a special String descriptor and one or more Microsoft OS feature descriptors. The String descriptor must have an index of EEh and contains an embedded signature. Windows XP SP1 and later request this string descriptor on first attachment. A device that doesn't support this descriptor should return a STALL.

If a device contains a Microsoft OS String descriptor, Windows requests additional Microsoft-specific descriptors. Future editions of the Windows DDK will have more documentation about these descriptors.

### Descriptors in 2.0-compliant Devices

If you're upgrading a 1.x-compliant device to 2.0, what changes are required in the descriptors? In a dual-speed device, can you detect whether a device is using full or high speed by reading its descriptors? This section answers these questions.

#### Making 1.x Descriptors 2.0-compliant

Table 4-12 lists the descriptor fields whose contents may require changes to enable a 1.x device to comply with the USB 2.0 specification. For all except some devices that have isochronous endpoints, the one and only required change is this: in the device descriptor, the bcdUSB field must be 0200h.

As Chapter 3 explained, a USB 2.0 device's default interface(s) must request no isochronous bandwidth. And because the default interface is of no use for transferring isochronous data, a device that wants to do isochronous transfers must support at least one alternate interface setting, and the alternate interface descriptor will have at least one subordinate endpoint descriptor. Some 1.x devices meet this requirement already.

**Table 4-12:** The descriptors in a 1.x-compliant device require very few changes to comply with USB 2.0.

| Descriptor | Field | Change |
|---|---|---|
| Device | bcdUSB | Set to 0200h. |
| Endpoint | wMaxPacketSize | Isochronous only: must be 0 in the default configuration. |

The USB 2.0 specification also adds two new descriptors and functions for bits in existing fields, but the new descriptors are used only in dual-speed devices and the other descriptors are backwards compatible with 1.x.

Full-speed isochronous endpoints have a few new, optional abilities. The endpoint descriptor can specify synchronization and usage types (bmAttributes field), and the interval can be greater than 1 millisecond (bInterval field). In 1.x descriptors, these bits default to 0 (no synchronization) and 1 (one millisecond).

When selecting bInterval values for interrupt and isochronous endpoints, don't forget that the relation between bInterval and the interval time will vary depending on the transfer type and speed. For low- and full-speed interrupt endpoints, the interval equals bInterval in milliseconds. For full-speed isochronous endpoints, the interval equals 2^{bInterval-1} in milliseconds. For high-speed interrupt and isochronous endpoints, the interval equals 2^{bInterval-1} in units of 125 microseconds. Note that if bInterval = 1, the full-speed interval is 1 millisecond in both USB 1.x and USB 2.0. So a 1.x isochronous endpoint, which must have bInterval = 1, requires no changes to comply with USB 2.0.

If you upgrade a full-speed device to support high speed as well, the device needs a device_qualifier descriptor, an other_speed_configuration descriptor, and a set of descriptors for the high-speed configuration. Any interrupt endpoints in the default interface must have a maximum packet size of 64 or less. A USB 2.0 device that supports only low speed or only full speed must return STALL in response to requests for the device_qualifier and other_speed_configuration descriptors.
