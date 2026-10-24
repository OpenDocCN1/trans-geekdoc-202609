
![](img/3955d77b6be34048e3bc722d0b15c2a9_37_0.png)

Figure 1-1: USB uses a tiered star topology, where each hub is the center of a star that can connect to peripherals or additional hubs.

## Topology

The topology, or arrangement of connections, on the bus is a tiered star (Figure 1-1). At the center of each star is a hub. Each point on a star is a device that connects to a port on a hub. The number of points on each star can vary, with a typical hub having two, four, or seven ports. When there are multiple hubs in series, you can think of them as connecting in a tier, or series, one above the next.

The tiered star describes only the physical connections. In programming, all that matters is the logical connection. To communicate, the host and device don’t need to know or care how many hubs the communication passes through.

Only one device at a time can communicate with a host controller. To increase the available bandwidth for USB devices, a PC can have multiple host controllers.

Figure 1-2 shows a few possible configurations for a PC with two USB connectors. Some devices are compound devices that contain both a peripheral and a hub. You can cascade up to five external hubs in series, up to a total of 127 peripherals and hubs including the root hub. However, it may be impractical to have this many devices communicating with a single host controller.

![](img/3955d77b6be34048e3bc722d0b15c2a9_39_0.png)

Figure 1-2: There are many possible configurations for connecting USB devices to a host PC. These are a few of the options for a host with two ports.

In some cases, especially with compound devices where the hubs are hidden inside the peripherals, the peripherals may appear to be using a daisy-chain type of connection, where each new peripheral hooks to the last one in a chain. But the USB’s topology is more flexible and complicated than a daisy chain. Each peripheral connects to a hub that manages communications with the host, and the peripherals and hubs aren’t limited to connecting in a single chain.

## Defining Terms

In the universe of USB, several everyday words have specific meanings. Along with *host*, defined earlier as the computer that controls the interface, three other such terms are *function*, *hub*, and *device*. It’s also important to understand the concept of a USB port and how it differs from other ports such as RS-232.

### Function

The USB specification defines a function as a device that provides a capability to the host. Examples of functions are a mouse, a set of speakers, or a data-acquisition unit. A single physical device can contain more than one function.

### Hub

A hub has one upstream connector for communicating with the host and one or more downstream connectors or internal connections to embedded devices. Each downstream connector or internal connection represents a USB port.

A 1.x hub repeats received USB traffic in both directions, manages power, and sends and responds to status and control messages. A 2.0 hub does all of this and also supports high speed, converting as needed between speeds.

### Device

The USB specification’s definition of a device is a function or a hub, except for the special case of the compound device, which contains a hub and one or more functions. The host treats a compound device in much the same way as if the hub and its functions were separate physical devices. Every device on the bus has a unique address, except again for a compound device, whose hub and functions each have unique addresses.

A composite device is a multi-function device with multiple, independent interfaces. The interfaces are defined by interface descriptors stored in the device. A composite device has one address on the bus but each interface has a different function and specifies its own device driver on the host. For example, a composite device could have one interface for an audio device and another interface for a control panel. Some Microsoft documentation uses the term composite device to refer to any device whose function is defined by its interface descriptor, rather than its device descriptor, whether or not there is more than one active interface.

### Port

In a general sense, a computer port is an addressable location that is available for attaching additional circuits. Usually the circuits terminate at a connector that enables attaching a cable to a peripheral. Some peripheral circuits are hard-wired to a port. Software can monitor and control the port circuits by reading and writing to the port’s address. Computer memory also consists of addressable locations, but the CPU typically accesses memory with different machine instructions than are used for accessing ports.

USB ports differ from many other ports because all of the ports on a bus share a single path to the host and aren’t directly addressable. With the RS-232 interface, each port is on the PC and independent from the others. If you have two RS-232 ports, each has its own data path, and each cable carries its own data and no one else’s. The two ports can send and receive data at the same time.

With USB, each host controller manages a single bus, or data path. Each connector on a bus represents a USB port, but unlike RS-232, all devices share the bus’s bandwidth. So even though a USB host controller can communicate with multiple ports, each with its own connector and cable, one data path serves all. Only one device or the host may transmit at a time. A single computer can have multiple USB host controllers, however, each with its own bus. Other interfaces where multiple devices can share a data path include IEEE-1394, SCSI, and Ethernet.

Another difference with USB is that a bus can have ports on hubs that are external to the host controller’s PC.

## Division of Labor

The host and its devices each have defined responsibilities. The host bears most of the burden of managing communications, but a device must have the intelligence to respond to communications and other bus events from the host and the hub the device attaches to.

### The Host’s Duties

To communicate with USB devices, a computer needs hardware and software support that enable the computer to function as a USB host. The hardware consists of a USB host controller and a root hub with one or more USB ports. The software support is an operating system that provides a mechanism for drivers to communicate with the USB hardware.

Just about any recent PC will have a USB host controller and two or more USB-port connectors. Many PCs have multiple host controllers. If a computer doesn’t have USB support built into its motherboard, you can add a host controller on an expansion card that plugs into a slot on the PCI bus. For portable computers, USB controllers on PC cards are available.

The host is in charge of the bus. The host has to know what devices are on the bus and the capabilities of each device. The host must also do its best to ensure that all devices on the bus can send and receive data as needed. A bus may have many devices, each with different requirements, and all wanting to transfer data at the same time. The host’s job is not trivial.

Fortunately, the host-controller hardware and the host-controller drivers in Windows do much of the work of managing the bus. Each device attached to the host must also have a device driver that enables applications to communicate with the device. Some peripherals can use device drivers included with Windows. Other devices use drivers provided by the device manufacturer. Various system-level software components manage communications between the device driver and the host-controller and root-hub hardware.

Applications don’t have to worry about the USB-specific details of communicating with devices. All the application has to do is send and receive data using standard operating-system functions that are accessible from just about all programming languages. Often the application doesn’t have to know or care whether the device uses USB or another interface.

The host performs the tasks below. The descriptions are in general terms. Later chapters have more specifics.

### Detect Devices

On power-up, the hubs make the host aware of all attached USB devices. In a process called enumeration, the host assigns an address and requests additional information from each device. After power-up, whenever a device is removed or attached, the host learns of the event and enumerates any newly attached device and removes any detached device from its list of devices available to applications.
