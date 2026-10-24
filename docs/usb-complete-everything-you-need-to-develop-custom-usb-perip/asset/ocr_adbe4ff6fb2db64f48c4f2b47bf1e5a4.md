This is the function's declaration:

```
<DllImport("setupapi.dll")> _
Function SetupDiEnumDeviceInterfaces _
    (ByVal DeviceInfoSet As IntPtr, _
    ByVal DeviceInfoData As Integer, _
    ByRef InterfaceClassGuid As System.Guid, _
    ByVal MemberIndex As Integer, _
    ByRef DeviceInterfaceData As _
        SP_DEVICE_INTERFACE_DATA) _
    As Boolean
End Function
```

This is the code to call the function:

```
Dim MemberIndex As Integer
Dim MyDeviceInterfaceData As SP_DEVICE_INTERFACE_DATA
Dim Result As Boolean

myDeviceInterfaceData.cbSize = _
    Marshal.SizeOf(myDeviceInterfaceData)
MemberIndex = 0

Result = SetupDiEnumDeviceInterfaces _
    (DeviceInfoSet, _
    0, _
    HidGuid, _
    MemberIndex, _
    MyDeviceInterfaceData)
```

# Details

In the SP_DEVICE_INTERFACE_DATA structure, the parameter cbSize is the size of the structure in bytes. Before calling SetupDiEnumDeviceInterfaces, the size must be stored in the structure that the function will pass. The sizeof operator in Visual C++ or the Marshal.SizeOf method in Visual Basic retrieves the size. The other values in the structure should be zero.

The HidGuid and DeviceInfoSet parameters are values retrieved previously. DeviceInfoData is an optional pointer to an SP_DEVINFO_DATA structure that limits the search to a particular device instance. MemberIndex is an index to a structure in the DeviceInfoSet array. MyDeviceInterfaceData is