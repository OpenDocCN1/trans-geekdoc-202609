
You may be able to use or adapt a driver provided by the controller-chip vendor. If you need to provide your own driver, there are toolkits that make the job of writing USB drivers easier.

**Fees.** The USB-IF provides the USB specification, related documents, software for compliance testing, and much more, all for free on its Web site. Anyone can develop USB software without paying a licensing fee.

However, anyone who distributes a device with a USB interface must obtain the rights to use a Vendor ID. At this writing, the administrative fee for obtaining a Vendor ID from the USB-IF is $1500. If you join the USB-IF (currently $2500/year), a Vendor ID is included along with other benefits such as admittance to compliance workshops. The Vendor ID and a Product ID assigned by the vendor are embedded in each device to identify the device to the operating system.

The fee is no problem for developers of high-volume products but can be an impediment to developers who expect to sell small quantities of inexpensive devices. With a few controllers that use the chip vendor’s driver and require no vendor programming for the USB interface, peripheral developers can use the chip manufacturer’s Vendor ID and a Product ID that the chip manufacturer assigns to the peripheral developer.

## Evolution of an Interface

The main reason that new interfaces don’t come around very often is that existing interfaces have the irresistible pull of all of the peripherals that users don’t want to scrap. Using an existing interface also saves the time and expense of designing a new interface. This is why the designers of the original IBM PC chose compatibility with the existing Centronics parallel interface and the RS-232 serial-port interface—to speed up the design process and enable users to connect to printers and modems already on the market. These interfaces proved serviceable for close to two decades. But as computers became more powerful and the number and kinds of peripherals increased, the older interfaces became a bottleneck of slow communications with limited options for expansion.

A break with tradition is justified when the desire for enhancements is greater than the inconvenience and expense of change. This is the situation that prompted the development of USB.

The copyright on the USB 2.0 specification is assigned jointly to seven corporations, all heavily involved with PC hardware or software: Compaq, Hewlett-Packard, Intel, Lucent, Microsoft, NEC, and Philips. The USB-IF’s Web site has the USB 2.0 specification, related documents, and other information for developers and end users.

## Original USB

Version 1.0 of the USB specification was released in January 1996. Version 1.1 is dated September 1998. USB 1.1 added one new transfer type (interrupt OUT). In this book, USB 1.x refers to USB 1.0 and 1.1. April 2000 saw the release of USB 2.0 which added the option to use high speed. Engineering Change Notices (ECNs) contain revisions and additions to the specification, including defining a new mini-B connector, specifying a way for devices to use bus pull-up and pull-down resistors with looser tolerances, and defining a new descriptor type (the Interface Association Descriptor).

USB capability first became available on PCs with the release of Windows 95’s OEM Service Release 2, available only to vendors installing Windows 95 on the PCs they sold. The USB support in these versions was limited and buggy, and there weren’t a lot of USB peripherals available, so use of USB was limited in this era.

Things improved with the release of Windows 98 in June 1998. By this time, many more vendors had USB peripherals available, and USB began to take hold as a popular interface. Windows 98 Second Edition (SE) fixed some bugs and further enhanced the USB support. The original version of Windows 98 is called Windows 98 Gold, to distinguish it from Windows 98 SE.

This book concentrates on PCs running Windows 98 and later Windows editions. Windows NT4 preceded Windows 98 and doesn’t support USB. Windows 2000, Windows Me, Windows XP, and Windows Server 2003 all support USB.

In this book, the term PC includes all of the various computers that share the common ancestor of the original IBM PC. The expression Windows 98 and later means Windows 98, Windows 98 SE, Windows 2000, Windows Me, Windows XP, and Windows Server 2003, and is also likely to apply to any Windows editions that follow. A USB-capable PC is assumed to be using Windows 98 or later. A host computer is any computer that can communicate with USB peripherals.

## USB 2.0

As USB 1.x gained in popularity, it became clear that a faster bus speed would be useful. Investigation showed that a bus speed forty times faster than full speed could remain backwards-compatible with the low- and full-speed interfaces. Version 2.0’s support for a bus speed of 480 Megabits/sec. makes USB much more attractive for peripherals such as printers, scanners, disk drives, and video.

An external USB 2.0 hub must support all three speeds. Other USB 2.0 devices can support low, full, or high speed or a combination. USB 2.0 is backwards compatible with USB 1.1. In other words, USB 2.0 peripherals can use the same connectors and cables as 1.x peripherals, and a USB 2.0 peripheral works when connected to a PC that supports USB 1.x or 2.0. To use high speed, a high-speed-capable device must connect under a 2.0 host computer, and all hubs between the host computer and the device must be 2.0 hubs. Version 2.0 hosts and hubs can also communicate with 1.x peripherals. A 2.0-compliant hub with a slower device attached converts between speeds as needed. This ability increases the complexity of 2.0 hubs but conserves bus bandwidth without requiring different hubs for different speeds.

When USB 2.0 devices first became available, there was confusion among users about whether all USB 2.0 devices supported high speed. In an attempt to reduce the confusion, the USB-IF released naming and packaging recommendations that emphasize speed and compatibility rather than USB version numbers. The recommendations say that a product that supports high speed should be labeled a “Hi-Speed USB” product, and messages on the packaging might include “Fully compatible with Original

common peripherals such as keyboards, printers, and scanners, as well as low- to moderate-speed and cost-sensitive applications. For many devices, such as drives, either interface works well, and in fact some devices include both interfaces.

## USB versus Ethernet

For some applications, the choice is between USB and Ethernet. Ethernet’s advantages include the ability to use very long cables, broadcasting ability, and support for Internet protocols in PCs and Ethernet-capable development systems. Like IEEE-1394, however, the hardware required to support Ethernet is more complex and expensive than typical USB peripheral hardware. USB is also more versatile with four transfer types and a variety of defined classes for different purposes.

## Bus Components

The physical components of the Universal Serial Bus consist of the circuits, connectors, and cables between a host and one or more devices.

The host is a PC or other computer that contains a USB host controller and a root hub. These components work together to enable the operating system to communicate with the devices on the bus. The host controller formats data for transmitting on the bus and translates received data to a format that operating-system components can understand. The host controller also performs other functions related to managing communications on the bus. The root hub has one or more connectors for attaching devices. The root hub, in combination with the host controller, detects attached and removed devices, carries out requests from the host controller, and passes data between devices and the host controller.

The devices are the peripherals and additional hubs that connect to the bus. A hub has one or more ports for connecting devices. Each device must contain circuits and code that know how to communicate with the host. The USB specification defines the cables and connectors that connect devices to hubs.
