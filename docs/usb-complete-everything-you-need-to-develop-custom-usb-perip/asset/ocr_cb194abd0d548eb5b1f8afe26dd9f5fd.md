which provides information to add to the registry. In the Install.AddReg section, DevLoader names the device loader associated with the device and NTMPDriver names the driver.

The DDInstall section for Windows 2000 and Windows XP is Install.NT. The CopyFiles directive names the same Install.CopyFiles section used for Windows 98 and Windows Me. These Windows editions don’t require the DevLoader and NTMPDriver entries, so there is no AddReg section.

Windows 2000 and Windows XP require two additional sections: Install.NT.Services and Install.NT.AddService. The Services section specifies a ServiceName for the driver (*ellex200*), assigns the service as the Plug-and-Play function driver for the device (flags = 2), and names an AddService section that specifies how and when the driver’s services are loaded (Install.NT.AddService).

The AddService section in the example has five entries. DisplayName specifies a friendly name for the service. ServiceType = 1 indicates that the entry is for a kernel-mode device driver. StartType = 3 to start the driver on enumeration. ErrorControl = 1 to display a warning and proceed if there is an error when loading or initializing the device. ServiceBinary specifies the location of the driver named in the CopyFiles section. This section can have many additional directives that are optional or required only for some device and drivers.

# Strings

The Strings section defines all of the strings that other sections refer to.

```
```ini
[Strings]
ClassName="Ellisys protocol analyzers"
Provider="Ellisys "
Manufacturer="Ellisys"
SourceDisk="USB Explorer 200 Installation Disk"
DeviceDesc="USB Explorer 200"
SvcDesc="USB Explorer 200 Driver (ellex200.sys)"
```
```