the returned SP_DEVICE_INTERFACE_DATA structure that identifies a device interface of the requested type.

# Requesting a Structure Containing the Device Path Name

The SetupDiGetDeviceInterfaceDetail function returns a structure that contains a device path name for a device interface identified in an SP_DEVICE_INTERFACE_DATA structure.

Before calling this function for the first time, there’s no way to know the value of the DeviceInterfaceDetailDataSize parameter, which must contain the size in bytes of the DeviceInterfaceDetailData structure. Yet the function won’t return the structure unless the function call contains this information. The solution is to call the function twice. The first time, GetLastError returns the error The data area passed to a system call is too small, but the RequiredSize parameter contains the correct value for DeviceInterfaceDetailDataSize. The second time, you pass the returned size value and the function returns the structure.

# Visual C++

This is the declaration for DeviceInterfaceDetailData’s structure:

```
typedef struct _SP_DEVICE_INTERFACE_DETAIL_DATA {
    DWORD cbSize;
    TCHAR DevicePath[ANYSIZE_ARRAY];
} SP_DEVICE_INTERFACE_DETAIL_DATA,
*PSP_DEVICE_INTERFACE_DETAIL_DATA;
```

This is the function’s declaration:

```
BOOLEAN
SetupDiGetDeviceInterfaceDetail(
    IN HDEVINFO DeviceInfoSet,
    IN PSP_DEVICE_INTERFACE_DATA DeviceInterfaceData,
    OUT PSP_DEVICE_INTERFACE_DETAIL_DATA
        DeviceInterfaceDetailData, OPTIONAL
    IN DWORD DeviceInterfaceDetailDataSize,
    OUT PDWORD RequiredSize, OPTIONAL
    OUT PSP_DEVINFO_DATA DeviceInfoData OPTIONAL
);
```