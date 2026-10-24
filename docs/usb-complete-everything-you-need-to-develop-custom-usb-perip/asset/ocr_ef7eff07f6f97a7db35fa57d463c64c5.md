used by applications that use the Windows Telephony Application Programming Interface (TAPI) must have its own INF file. Microsoft provides a Modem Development Kit with tools, sample INF files, and information for creating and testing INF files for modems.

Devices other than modems can use the *usbser.sys* driver as well. To enable host applications to access a device using COM-port functions (a virtual COM port), bInterfaceSubClass must be set to the Abstract Control Model. For better performance, however, most device developers use a driver from another source.

Under Windows 2000 and later, the *usb8023.sys* driver maps Remote NDIS to USB.

# Content Security

The Content Security class defines a way for content owners to control access to files, music, video, or other data transmitted on the bus. The control can use either of two defined Content Security Methods: Basic Authorization or Digital Transmission Content Protection (DTCP).

# Documentation

In addition to the main Content Security specification, each content security method (CSM) has its own specification document. At this writing, the latest edition of the specifications is 1.0. The DTCP specification and license information are available from the Digital Transmission Licensing Administrator (*www.dtcp.com*).

# Overview

The class defines a protocol for activating and deactivating a content security method and for associating a content security method to a channel. A channel represents a relationship between an interface or endpoint and one or more CSMs. Only one CSM can be active on a channel at a time.

Basic Authorization, also known as Content Security Method 1, or CSM-1, consists only of the class-specific request Get_Unique_ID, which enables a host to request an ID value from a device.