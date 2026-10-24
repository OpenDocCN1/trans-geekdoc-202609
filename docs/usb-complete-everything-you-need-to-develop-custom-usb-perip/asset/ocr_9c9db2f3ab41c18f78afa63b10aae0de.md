a device with a Vendor ID of 0925h and Product ID or 1234h. Under each of these keys may be one or more hardware keys, with each hardware key identifying an instance of the device. Table 9-1 lists some of the entries under the hardware key.

A device without a USB serial number gets a new hardware key every time the device attaches to a port the device hasn’t been attached to previously. If you physically remove the device and attach a different device with identical descriptors to the same port, the operating system doesn’t know the difference so there is no new hardware key. Devices with USB serial numbers have one hardware key per physical device, without regard to what port the device is attached to.

A USB device may also have one or more keys for additional enumerators such as HID, USBPRINT, and USBSTOR. For example, a UPS back-up device with a HID interface can have a key in the Enum\USB branch to name the HidUsb service and a key in the Enum\HID branch to name the HidBatt service.

# The Class Key

The class key stores information about device setup class and the devices that belong to it. The class keys are under this registry key:

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\
Class
```

The name of a class key is the device setup GUID for the class. This is the same as the value stored in the hardware key for devices in the class, under ClassGUID. Figure 9-5 shows the class key for the HID class. The class key contains a friendly name for the setup class, the class name from the header file that defines the GUID, and an index value that specifies the icon to use in Device Manager and other windows that display setup information. Applications can retrieve the index of the mini-icon for a class by calling SetupDiGetClassBitmapIndex. A vendor-specific class installer or co-installer can provide a vendor-specific icon.