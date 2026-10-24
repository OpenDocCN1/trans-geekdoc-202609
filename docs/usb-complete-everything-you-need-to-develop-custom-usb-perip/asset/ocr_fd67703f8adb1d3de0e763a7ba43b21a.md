# DestinationDirs

The DestinationDirs section names the folder or folders that any CopyFiles, RenFiles, and DelFiles items in the INF file will use. A *dirid* value of 10 specifies the Windows folder. The Windows DDK documentation lists other dirid values. Windows 98 documentation uses the term LDID (logical disk identifier) instead of dirid.

```
```ini
[DestinationDirs]
DefaultDestDir=10,System32\\Drivers
```
```

# SourceDisksNames

The SourceDisksNames section provides a text description for the installation disk(s). In the entry below, there is one source disk whose name is the %SourceDisk% string defined later in the file. An entry can also specify a volume label and serial number for the disk.

```
```ini
[SourceDisksNames]
1=%SourceDisk%,,,.
```
```

# SourceDisksFiles

The SourceDisksFiles section names any file(s) to install from the installation disk. If a file isn't in the disk’s root directory, the entry can specify a subdirectory.

```
```ini
[SourceDisksFiles]
ellex200.sys=1
```
```

# Models

The Manufacturer section names one or more Models sections. Each Models section contains one or more entries that match a device description to a DDInstall section and hardware ID.

In the example, the device description is the %DeviceDesc% string defined later in the file. Install is the name of the INF file’s DDInstall section, which has installation instructions for the device and can add device information to the registry. USB\\VID_0ABA&PID_8001 is the hardware ID that identifies the device by its Vendor ID and Product ID. Following the hardware ID, an entry can provide one or more compatible IDs that provide alternate,