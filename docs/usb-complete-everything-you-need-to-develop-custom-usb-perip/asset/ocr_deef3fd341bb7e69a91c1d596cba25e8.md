# Visual Basic

This is the function's declaration:

```
<DllImport("hid.dll")> _
Function HidD_GetPreparsedData _
    (ByVal HidDeviceObject As Integer, _
    ByRef PreparsedData As IntPtr) _
    As Boolean
End Function
```

This is the code to call the function:

```
Dim PreparsedData As IntPtr

HidD_GetPreparsedData _
    (DeviceHandle, _
    PreparsedData)
```

# Details

DeviceHandle is the handle returned by CreateFile. PreparsedData is a pointer to the buffer containing the data. The application doesn’t need to access the data in the buffer directly. The code just needs to pass the pointer to another API function.

When finished using the PreparsedData buffer, the application should free system resources by calling HidD_FreePreparsedData as described later in this chapter.

# Getting the Device’s Capabilities

The HidP_GetCaps function returns a pointer to a structure that contains information about the device’s capabilities. The structure contains the HID’s Usage Pages, Usages, report lengths, and the number of button-capabilities structures, value-capabilities structures, and data indexes that identify specific controls and data items in Input, Output, and Feature reports. An application can use the capabilities information to identify a particular HID and learn about its reports and report data. Not every item in the structure applies to all devices.