
The application can compare this device path name with the device path name of the device of interest. On a match, the application can take any desired actions.

## Visual C++

This is the code to retrieve the device path name and look for a match:

```
PDEV_BROADCAST_HDR lpdb = (PDEV_BROADCAST_HDR)lParam;

if (lpdb->dbch_devicetype ==
    DBT_DEVTYP_DEVICEINTERFACE)
{
    PDEV_BROADCAST_DEVICEINTERFACE lpdbi =
        (PDEV_BROADCAST_DEVICEINTERFACE)lParam;

    CString DeviceNameString;

    DeviceNameString = lpdbi->dbcc_name;

    if
        ((DeviceNameString.CompareNoCase
          (DetailData->DevicePath)) == 0)
    {
        // The names match.
    }
    else
    {
        // It's a different device.
    }
}
```

## Visual Basic

The application uses two declarations for the DEV_BROADCAST_DEVICEINTERFACE structure. The first declaration, presented earlier, is used when calling RegisterDeviceNotification. The second declaration, DEV_BROADCAST_DEVICEINTERFACE_1, enables marshaling the data in dbcc_name and classguid:

```
<StructLayout _
    (LayoutKind.Sequential, _
        CharSet:=CharSet.Unicode)> _
Public Class DEV_BROADCAST_DEVICEINTERFACE_1
    Public dbcc_size As Integer
    Public dbcc_devicetype As Integer
    Public dbcc_reserved As Integer
    <MarshalAs _
        (UnmanagedType.ByValArray, _
        ArraySubType:=UnmanagedType.U1, _
        SizeConst:=16)> _
        Public dbcc_classguid() As Byte
    <MarshalAs _
        (UnmanagedType.ByValArray, SizeConst:=255)> _
        Public dbcc_name() As Char
End Class
```

This is the code to retrieve the device path name and look for a match:

```
Dim DevBroadcastDeviceInterface As _
    New DEV_BROADCAST_DEVICEINTERFACE_1()
Dim DevBroadcastHeader As New DEV_BROADCAST_HDR()

Marshal.PtrToStructure(m.LParam, DevBroadcastHeader)

If (DevBroadcastHeader.dbch_devicetype = _
    DBT_DEVTYP_DEVICEINTERFACE) Then
    Dim StringSize As Integer = _
        CInt((DevBroadcastHeader.dbch_size - 32) / 2)
    ReDim DevBroadcastDeviceInterface.dbcc_name _
        (StringSize)

    Marshal.PtrToStructure _
        (m.LParam, DevBroadcastDeviceInterface)
```

```
Dim DeviceNameString As New String _
    (DevBroadcastDeviceInterface.dbcc_name, _
    0, _
    StringSize)

If (String.Compare _
    (DeviceNameString, _
    DevicePathName, _
    True) = 0) Then
    'The name matches.
Else
    'It's a different device.
End If
End If
```

Marshal.PtrToStructure copies the message's lParam property into a DEV_BROADCAST_HDR structure. If lParam indicates that the message relates to a device interface, the application retrieves the device path name.

The name is in a Char array in unmanaged memory. The application needs to retrieve the Char array and convert it to a String.

The dbch_size member of DEV_BROADCAST_HDR contains the number of bytes in the complete DEV_BROADCAST_INTERFACE structure. To obtain the number of characters in the device path name stored in dbcc_name, subtract the 32 bytes in the structure that are not part of the name and divide by 2 because there are 2 bytes per character.

DevBroadcastDeviceInterface is a DEV_BROADCAST_DEVICEINTERFACE_1 structure that marshals the data in the classguid and dbcc_name members. A ReDim statement trims dbcc_name to match the size of the device path name. Marshal.PtrToStructure copies the data from the unmanaged block in lParam to the DevBroadcastDeviceInterface structure. The Char array containing the device path name is then stored as a String in DeviceNameString, and the String.Compare method looks for a match.

## Stopping Device Notifications

To stop receiving device notifications, an application calls UnregisterDeviceNotification. The application should call the function before closing.

### Visual C++

This is the function's declaration:

```
BOOL UnregisterDeviceNotification(
    HDEVNOTIFY Handle
);
```

This is the code to call the function:

```
UnregisterDeviceNotification(
    DeviceNotificationHandle);
```

### Visual Basic

This is the function's declaration:

```
<DllImport("user32.dll")> Function
UnregisterDeviceNotification _
    (ByVal Handle As IntPtr) _
    As Boolean
End Function
```

This is the code to call the function:

```
UnregisterDeviceNotification _
    (DeviceNotificationHandle)
```

## 11 Human Interface Devices: Using Control and Interrupt Transfers

The human interface device (HID) class was one of the first USB classes supported under Windows. On PCs running Windows 98 or later, applications can communicate with HIDs using the drivers built into the operating system. For this reason, many vendor-specific USB devices use the HID class.

Chapter 7 introduced the class. This chapter shows how to determine whether a specific device can fit into the human-interface class, details the firmware requirements that define a device as a HID and enable it to exchange data with its host, introduces the six HID-specific control requests, and presents an example of HID firmware. Chapter 12 describes the reports that HIDs use to exchange information and Chapter 13 shows how to access HIDs from applications.

## What is a HID?

The *human interface* in the name suggests that HIDs interact directly with people, and many HIDs do. A mouse may detect when someone presses a key or moves the mouse, or the host may send a message that translates to a joystick effect that the user experiences. Besides keyboards, mice, and joysticks, the HID class encompasses front panels with knobs, switches, buttons, and sliders; remote controls; telephone keypads; and game controls such as data gloves and steering wheels.

But a HID doesn’t have to have a human interface. The device just needs to be able to function within the limits of the HID class specification. These are the major abilities and limitations of HID-class devices:

- All data exchanged resides in structures called reports. The host sends and receives data by sending and requesting reports in control or interrupt transfers. The report format is flexible and can handle just about any type of data, but each defined report has a fixed size.
- A HID interface must have an interrupt IN endpoint for sending Input reports.
- A HID interface can have at most one interrupt IN endpoint and one interrupt OUT endpoint. If you need more interrupt endpoints, you can create a composite device that contains multiple HIDs. An application must obtain a separate handle for each HID in the composite device.
- The interrupt IN endpoint enables the HID to send information to the host at unpredictable times. For example, there’s no way for the computer to know when a user will press a key on the keyboard, so the host’s driver uses interrupt transactions to poll the device periodically to obtain new data.
- The rate of data exchange is limited, especially at low and full speeds. As Chapter 3 explained, a host can guarantee a low-speed interrupt endpoint no more than 800 bytes/sec. For full-speed endpoints, the maximum is 64 kilobytes/sec., and for high-speed endpoints, the maximum is about 24 Megabytes/sec. if the host supports high-bandwidth endpoints and about 8 Megabytes/sec. if not. Control transfers have no guaranteed bandwidth except for the bandwidth reserved for all control transfers on the bus.
- Windows 98 Gold (original edition) supports USB 1.0, so interrupt OUT transfers aren’t supported and all host-to-device reports must use control transfers.

Any device that can live within the class’s limits is a candidate to be a HID. The HID specification mentions bar-code readers, thermometers, and voltmeters as examples of HIDs that might not have a conventional human interface. Each of these sends data to the computer and may also receive requests that configure the device. Examples of devices that mostly receive data are remote displays, control panels for remote devices, robots, and devices of any kind that receive occasional or periodic commands from the host.

A HID interface may be just one of multiple USB interfaces supported by a device. For example, a USB speaker that uses isochronous transfers for audio may also have a HID interface for controlling volume, balance, treble, and bass. A HID interface is often cheaper than traditional physical controls on a device.

## Hardware Requirements

To comply with the HID specification, the interface’s endpoints and descriptors must meet several requirements.

### Endpoints

All HID transfers use either the control endpoint or an interrupt endpoint. Every HID must have an interrupt IN endpoint for sending data to the host. An interrupt OUT endpoint is optional. Table 11-1 shows the transfer types and their typical uses in HIDs.
