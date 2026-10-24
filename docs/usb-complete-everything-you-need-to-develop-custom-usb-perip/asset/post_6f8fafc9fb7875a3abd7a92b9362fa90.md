
## Chapter 9

![](img/3955d77b6be34048e3bc722d0b15c2a9_278_0.png)

Figure 9-4: A hardware key contains information about an instance of a device with a specific Vendor ID and Product ID.

The current copy becomes unusable. Be extremely careful about making changes to the registry. Windows’ System Restore utility can restore the registry to an earlier state. Just viewing the registry is safe, however.

The registry’s data has a tree structure. Each node on the tree is a registry key. Each key can have entries with assigned values and subkeys that in turn may have entries and subkeys. Information about the system’s hardware and installed software is under the HKEY_LOCAL_MACHINE key, with information about USB devices under several subkeys: the hardware key, the class key, the driver key, and the service key.

### The Hardware Key

The hardware key, also called the instance key or device key, stores information about an instance of a specific device. Hardware keys are under the enumerator (Enum) key:

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Enum
```

Under the Enum key is a USB key. Each subkey of the USB key contains the Vendor ID and Product ID of a USB device. Figure 9-4 shows the entry for a device with a Vendor ID of 0925h and Product ID of 1234h. Under each of these keys may be one or more hardware keys, with each hardware key identifying an instance of the device. Table 9-1 lists some of the entries under the hardware key.

A device without a USB serial number gets a new hardware key every time the device attaches to a port the device hasn’t been attached to previously. If you physically remove the device and attach a different device with identical descriptors to the same port, the operating system doesn’t know the difference so there is no new hardware key. Devices with USB serial numbers have one hardware key per physical device, without regard to what port the device is attached to.

A USB device may also have one or more keys for additional enumerators such as HID, USBPRINT, and USBSTOR. For example, a UPS back-up device with a HID interface can have a key in the Enum\USB branch to name the HidUsb service and a key in the Enum\HID branch to name the HidBatt service.

### The Class Key

The class key stores information about device setup class and the devices that belong to it. The class keys are under this registry key:

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Class
```

The name of a class key is the device setup GUID for the class. This is the same as the value stored in the hardware key for devices in the class, under ClassGUID. Figure 9-5 shows the class key for the HID class. The class key contains a friendly name for the setup class, the class name from the header file that defines the GUID, and an index value that specifies the icon to use in Device Manager and other windows that display setup information. Applications can retrieve the index of the mini-icon for a class by calling SetupDiGetClassBitmapIndex. A vendor-specific class installer or co-installer can provide a vendor-specific icon.

![](img/3955d77b6be34048e3bc722d0b15c2a9_280_0.png)

Figure 9-5: The class key for the HID class includes a friendly name for the class and an index to an icon.

Optional entries in the class key can affect what users see on device installation. If NoInstallClass is present and not equal to zero, users will never need to manually install devices in the class. If SilentInstall is present and not equal to zero, the Plug and Play manager will install devices in the class without displaying dialog boxes or requiring user interaction. If NoDisplayClass is present and not equal to zero, the Device Manager doesn't display devices of the class.

UpperFilters and LowerFilters entries can specify upper filter and lower filter drivers that apply to all devices in the class.

### The Driver Key

Under the class key, each device in a class has a driver key, also called a software key. In the hardware key for a device instance, the Driver entry names a device setup GUID that matches a class key and a device instance number that matches a driver subkey under the class key. Figure 9-6 shows the key for a generic HID-class device. Table 9-2 lists some of the entries for a driver key.

The driver key contains the name of the INF file that in turn names the driver files for the device.

### Matching a Driver to a Device

Table 9-1: These are some of the entries in a USB device’s hardware key.

| Key | Description | Source of Information |
|---|---|---|
| Class | Name of the device’s setup class | INF file (from devguid.h) |
| ClassGUID | GUID of the device’s setup class | INF file (from devguid.h) |
| DeviceDesc | Device Description | INF file, Models section, device description entry |
| HardwareID | ID string containing the device’s Vendor ID and Product ID | Device descriptor |
| CompatibleIDs | ID string(s) containing the device’s class and (optional) subclass and protocol | Device and interface descriptors |
| Mfg | Device manufacturer | INF file, Manufacturer section, manufacturer name entry |
| Driver | Name of the device’s driver key | System registry, under CurrentControlSet\Control\Class |
| Location Information | “USB Device” or iProduct string | Bus driver or string descriptor |
| Service | Name of the device’s Service key | System registry, under HKLM\System\CurrentControlSet\Services |

![](img/3955d77b6be34048e3bc722d0b15c2a9_281_0.png)

Figure 9-6: The driver keys under each class key have information about the drivers assigned to instances of devices in the class.

Table 9-2: The driver key contains information about the driver assigned to a device.

| Key | Description | Source of Information |
|---|---|---|
| DriverDate | Date of the driver file | INF file, Version section, DriverVer directive |
| DriverDesc | Driver description | INF file |
| DriverVer | Driver version | INF file, Version section, DriverVer directive |
| InfPath | Name of INF file | INF file name |
| InfSection | Name of the driver’s DDInstall section | INF file |
| InfSectionExt | “Decorated” extension used in INF file (.NT, etc.) | INF file |
| MatchingDeviceID | The hardware or compatible ID used to assign the driver | Device descriptor and INF file |
| ProviderName | The provider of the driver | INF file, Provider string |

### The Service Key

A service key has information about a driver’s files, including where they are stored and how to load them. Service keys are in this branch:

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services
```

There are service keys for each host controller type, hubs, and classes such as storage (USBSTOR), printers (USBPRINT), and HIDs (HidBatt, HidServ, HidUsb). Figure 9-7 shows the Service key for HidUsb.

![](img/3955d77b6be34048e3bc722d0b15c2a9_283_0.png)

Figure 9-7: The service key names a driver's file.

### Inside INF Files

A device setup information file, or INF file, is a text file that contains information about one or more devices in a device setup class. The devices may be from one or more manufacturers. The file tells Windows what driver or drivers to use and contains information to store in the registry. Windows includes INF files for the drivers provided with the operating system. The files are in the %SystemRoot%\inf folder. Any new INF files for added devices are copied to this folder as well. By default, the folder is hidden. If you don’t see it in Windows Explorer, select Tools > Folder Options > View, then under Hidden Files, select *Show hidden files and folders*. Do not select *Hide file extensions for known file types*.

On first attachment, after retrieving descriptors from a USB device, Windows looks for a match between the information in the descriptors and the information in the system's INF files.

This section doesn't attempt to document every nuance of INF-file creation. Instead, I use an example INF file to show the kinds of information an INF file can contain. The Windows DDK documentation has more details. Examining the INF files included with Windows is another way to learn about the kinds of things contained in the files and how the information is structured.

Listing 9-1 shows an INF file for the Ellisys USB Explorer protocol analyzer, which uses a vendor-specific driver. (The analyzer has a USB interface that communicates with the PC running the analyzer software.) This INF file is suitable for use under Windows 98, Windows Me, Windows 2000, and Windows XP.
