ATA/ATAPI devices include Philips Semiconductor’s ISP1183, Texas Instruments’ TUSB6250, and Cypress Semiconductor’s EZUSB AT2.

# Windows Support

Windows 2000 and later include a driver that supports bulk-only and CBI devices. When a device’s descriptors identify the device as mass-storage class, the operating system loads the USB storage port driver (usbstor.sys). This driver manages communications between the lower-level USB drivers and Windows’ storage-class drivers. When the device is formatted using a supported file system, the operating system assigns a drive letter to the device and the device appears in My Computer.

The mass-storage driver in Windows XP supports bInterfaceSubClass codes 02h, 05h, and 06h. Support for drives with multiple Logical Unit Numbers (LUNs) was added in Windows 2000 SP3.

One point of confusion relating to the mass-storage support under Windows is the difference between removable devices and removable media. All USB drives are removable devices because they’re easily attached and detached from the PC. A removable device may have removable or non-removable media. CD, DVD, and floppy drives have removable media. A hard disk is a non-removable medium because you can’t easily remove the disk from the drive. Windows’ Autorun capability (also called AutoPlay) applies to devices with removable media. Autorun enables the operating system to run a program, play a movie, or perform other actions when a disk or other removable media is inserted.

# Printers

The printer class is for devices that convert received data into text and/or images on paper or other media. The most basic printers print lines of text in a single font. Most laser and inkjet printers understand one or more page description languages (PDLs) and can print text in any font and complex images.