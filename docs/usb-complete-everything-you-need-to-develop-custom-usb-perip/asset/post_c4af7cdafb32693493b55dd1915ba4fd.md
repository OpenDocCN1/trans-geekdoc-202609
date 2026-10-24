
![](img/3955d77b6be34048e3bc722d0b15c2a9_250_0.png)

Figure 7-10: To enable two USB hosts to communicate with each other, two USB serial interface engines can share a buffer. Each SIE copies received USB data into the shared buffer, and the other device retrieves the data from the buffer and sends the data to the other host.

A host-to-host bridge cable that contains two serial interface engines. Each PC has a USB connection to one of the SIEs, and the two devices communicate with each other via a shared buffer (Figure 7-10). Data sent by a PC travels to one of the SIEs, through the shared buffer, and out the other SIE to the remote PC.

Prolific Technology’s PL-2501 Hi-Speed USB Host to Host Bridge Controller is a single chip designed for this type of host-to-host application. The chip contains an 8032 microcontroller and two USB SIEs that can access a common buffer. The PL-2301 is a full-speed version. Many commercial “data-link file-transfer cables” contain one of these chips. Typically, the drivers enable each PC to see the other as a network-connected computer.

An alternate approach is to use two FTDI Chip USB UARTs and cross-connect the asynchronous interfaces in a “null modem” configuration. The PCs then see each other as COM-port devices. Yet another option is to establish a network connection by attaching a USB/Ethernet converter to each PC and connecting each converter to a local network.

## Using a Generic Driver

For devices that don’t fit into a standard class, a generic driver can be a solution. Generic drivers typically enable applications to request control, interrupt, bulk, and isochronous transfers using a driver-specific API. Two such options are the DriverX USB toolkit from Tetradyne Software, Inc. and the USBIO Development Kit from Thesycon Systemsoftware & Consulting GmbH. (Yes, that spelling is correct.)

The DriverX USB toolkit includes a generic driver, header and library files for use with Visual C++ and Borland C++ Builder, and additional support for Delphi and Visual Basic.

To communicate with the driver included with the USBIO Development Kit, applications can use standard Windows API functions (ReadFile, WriteFile, DeviceIoControl), a C++ class library, native Delphi and Java interfaces, or a USBIO COM interface based on Microsoft’s Component Object Model (COM) technology.

## 8

## How the Host Communicates

Under Windows, an application that wants to access a USB peripheral must communicate with a device driver that knows how to manage communications with the system's USB drivers. This chapter explains how Windows manages USB communications and explores the options for device drivers.

### Device Driver Basics

A device driver is a software component that enables applications to access a hardware device. The hardware device may be a printer, modem, keyboard, video display, data-acquisition unit, or just about anything controlled by circuits that the CPU can access. Some devices, such as internal disk drives, are inside the box with the CPU. Others, including just about all USB devices, are external devices that connect to the system via cables (or wireless links). As Chapter 7 explained, some device drivers are class drivers that handle communications with a variety of devices that perform similar functions.

### Insulating Applications from the Details

Applications are the programs that users run, including everything from word processors and databases to special-purpose applications that access custom hardware. A device driver insulates applications from having to know details about the physical connections, signals, and protocols required to communicate with a device.

A device driver can enable application code to access a peripheral when the application knows only the peripheral’s name (such as HP LaserJet 2300) or the device’s function (joystick, drive, scanner). The application doesn’t have to know the physical address of the port the peripheral attaches to or monitor and control handshaking signals. Applications don’t even have to know whether a device uses USB or another interface. The application code can be the same for devices that perform similar functions but have different interfaces, with the hardware-specific details handled at a lower level.

The device driver translates between application-level and hardware-specific code. Applications communicate with device drivers using functions supported by the operating system. The hardware-specific code handles the protocols needed to access the peripheral’s circuits, including detecting the states of status signals and toggling control signals at appropriate times.

The Windows drivers for USB devices use a layered driver model where each driver in a series performs a portion of the communication. The top layer contains a client device driver (or client driver for short) that manages communications between applications and lower-level bus drivers. Another term for client driver is function driver. The bottom layer contains bus drivers that manage communications between the client driver and the hardware. One or more filter drivers may supplement the client and bus drivers.

The layered driver model simplifies the job of writing drivers. Devices can share code for tasks they have in common. The drivers that handle communications with the system’s USB hardware are included with Windows, so writers of client drivers don’t have to handle these details. Note also that the layered driver model means that applications can’t access USB ports directly. Windows doesn’t allow it. All application communications must be with a driver assigned to a device.

### Options for USB Devices

There are several approaches to obtaining a driver for a USB device that you’re developing. Many devices can use a driver that’s included with Windows or provided by a chip vendor or other source. Other devices may require custom drivers. When a custom driver is necessary, toolkits are available to simplify and speed up the task of driver writing. Sometimes more than one way will work, and the choice depends on what’s easier, cheaper, or offers better performance.

As Chapter 7 showed, many peripherals fit into standard classes such as disk drives, printers, modems, keyboards, and mice. Each of these devices is available with a choice of interfaces, including USB. For example, a disk drive may use ATA/ATAPI, SCSI, IEEE-1394, or USB. When the devices in a class may have any of multiple hardware interfaces, supplemental drivers can support different interfaces. If a device has features or capabilities beyond what a class driver supports, a device-specific filter driver may be able to support these as needed.

### User and Kernel Modes

To understand what the device driver has to do, you need to understand where the driver fits in the communications path of a data transfer. Even if you don’t need to write a driver for your device, understanding the driver’s role will help in understanding the application-level code that you do write.

In the most general sense, a device driver is any code that handles communication details for a hardware device that interfaces to a CPU. Even a short subroutine in an application can be considered a device driver. Under Windows, the code for most drivers, including USB drivers, differs from application code because the operating system allows the driver code a greater level of privilege than applications are allowed.

Program code in a Windows system runs in one of two modes: user or kernel. Each allows a different level of privilege in accessing memory and other system resources. Applications must run in user mode. Most drivers, including all USB drivers, run in kernel mode, though a driver for a USB device

![](img/3955d77b6be34048e3bc722d0b15c2a9_256_0.png)

Figure 8-1: USB uses a layered driver model under Windows, with separate drivers for devices and the buses they connect to.

may have a supplementary user-mode driver. Figure 8-1 shows the major components of user and kernel modes in a USB communication.

In user mode, Windows limits access to memory and other system resources. Windows doesn’t allow an application to access memory that the operating system has designated as protected. Managing memory in this way enables a PC to run multiple applications at the same time. If an application crashes, other applications shouldn’t be affected. On x86 processors, user mode corresponds to the CPU’s Ring 3 mode.
