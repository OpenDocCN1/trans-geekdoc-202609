This is the code to call the function the first time:

```
```c
BOOLEAN Result;
PSP_DEVICE_INTERFACE_DETAIL_DATA DetailData;
ULONG Length;

Result = SetupDiGetDeviceInterfaceDetail
    (DeviceInfoSet,
    &MyDeviceInterfaceData,
    NULL,
    0,
    &Length,
    NULL);
```
```

The code then allocates memory for the DetailData structure, sets the cbSize property of DetailData, and calls the function again, passing the returned buffer size in Length:

```
```c
DetailData =
    (PSP_DEVICE_INTERFACE_DETAIL_DATA)malloc(Length);

DetailData -> cbSize =
    sizeof(SP_DEVICE_INTERFACE_DETAIL_DATA);

Result = SetupDiGetDeviceInterfaceDetail
    (DeviceInfoSet,
    &MyDeviceInterfaceData,
    DetailData,
    Length,
    &Length,
    NULL);
```
```