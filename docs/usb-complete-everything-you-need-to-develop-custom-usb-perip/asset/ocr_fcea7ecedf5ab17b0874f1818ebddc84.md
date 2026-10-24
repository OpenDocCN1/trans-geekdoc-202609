A call to HidD_SetOutputReport works much the same way to send an Output report using a control transfer. The function passes a handle to the HID, a pointer to a byte array containing an Output report, and the number of bytes in the report plus one byte for the report ID.

# Reading a Feature Report from a Device

To read a Feature report from a device, use the HidD_GetFeature API function. The function sends a Get_Feature request in a control transfer. The device returns the report in the Data stage.

# Visual C++

This is the function's declaration:

```
BOOLEAN
    HidD_GetFeature(
        IN HANDLE HidDeviceObject,
        OUT PVOID ReportBuffer,
        IN ULONG ReportBufferLength
    );
```

This is the code to call the function:

```
BOOLEAN Result;
CHAR    InFeatureReportBuffer[3];

// The first byte in the report buffer is the report
// ID:

InFeatureReportBuffer[0]=0;

Result = HidD_GetFeature
    (DeviceHandle,
    InFeatureReportBuffer,
    Capabilities.FeatureReportByteLength)
```