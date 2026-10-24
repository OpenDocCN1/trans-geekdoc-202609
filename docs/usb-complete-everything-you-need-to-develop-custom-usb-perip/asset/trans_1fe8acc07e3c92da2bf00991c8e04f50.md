
next call. But before calling the function again, we need to take care of a few things.

下一次调用。但在再次调用函数之前，我们需要处理一些事情。

The function will return a pointer (DetailDataBuffer) to an SP_DEVICE_INTERFACE_DETAIL_DATA structure in unmanaged memory. The Marshal.AllocHGlobal method uses the returned BufferSize value to reserve memory for the structure:

函数将返回一个指针（DetailDataBuffer）指向非托管内存中的 SP_DEVICE_INTERFACE_DETAIL_DATA 结构。Marshal.AllocHGlobal 方法使用返回的 BufferSize 值来为该结构预留内存：

```
Dim DetailDataBuffer As IntPtr
DetailDataBuffer = Marshal.AllocHGlobal(BufferSize)
```

The cbSize member of the structure passed in DetailDataBuffer equals four bytes for the cbSize integer plus the length of one character for the device path name (which is empty when passed to the function). The Marshal.WriteInt32 method copies the cbSize value into the first member of DetailDataBuffer:

传递到 DetailDataBuffer 中的结构的 cbSize 成员等于 cbSize 整数的四个字节加上设备路径名称的一个字符的长度（在传递给函数时为空）。Marshal.WriteInt32 方法将 cbSize 值复制到 DetailDataBuffer 的第一个成员中：

```
Marshal.WriteInt32 _
    (DetailDataBuffer, _
    4 + Marshal.SystemDefaultCharSize)
```

The second call to SetupDiGetDeviceInterfaceDetail passes the DetailDataBuffer pointer and sets the DeviceInterfaceDetailDataSize parameter equal to the BufferSize value returned previously in RequiredSize:

对 SetupDiGetDeviceInterfaceDetail 的第二次调用传递 DetailDataBuffer 指针，并将 DeviceInterfaceDetailDataSize 参数设置为之前在 RequiredSize 中返回的 BufferSize 值：

```
Success = SetupDiGetDeviceInterfaceDetail _
    (deviceInfoSet, _
    MyDeviceInterfaceData, _
    DetailDataBuffer, _
    BufferSize, _
    BufferSize, _
    IntPtr.Zero)
```

When the function returns, DetailDataBuffer points to a structure containing a device path name.

当函数返回时，DetailDataBuffer 指向包含设备路径名称的结构。

## Extracting the Device Path Name

提取设备路径名称

The device path name is in the DevicePath member of the SP_DEVICE_INTERFACE_DETAIL_DATA structure returned by SetupDiGetDeviceInterfaceDetail.

设备路径名称位于 SetupDiGetDeviceInterfaceDetail 返回的 SP_DEVICE_INTERFACE_DETAIL_DATA 结构体的 DevicePath 成员中。

### Visual C++

Visual C++

The device path name is in DetailData -> DevicePath.

设备路径名称位于 DetailData -> DevicePath 中。

### Visual Basic

Visual Basic

The string containing the device path name is stored beginning at byte 5 in DetailDataBuffer. (The first four bytes are the cbSize member.) The pDevicePathName variable points to this location:

包含设备路径名称的字符串从 DetailDataBuffer 的第 5 字节开始存储。（前四个字节是 cbSize 成员。）pDevicePathName 变量指向此位置：

```
Dim DevicePathName(127) As String
Dim pDevicePathName As IntPtr = _
    New IntPtr(DetailDataBuffer.ToInt32 + 4)
```

The Marshal.PtrToString method retrieves the string from the buffer:

Marshal.PtrToString 方法从缓冲区检索字符串：

```
DevicePathName = _
    Marshal.PtrToStringAuto(pDevicePathName)
```

We’re finished with DetailDataBuffer, so we should free the memory previously allocated for it:

我们已经完成了对 DetailDataBuffer 的使用，因此应释放为其先前分配的内存：

```
Marshal.FreeHGlobal(DetailDataBuffer)
```

## Closing Communications

关闭通信

When finished using the DeviceInfoSet returned by SetupDiGetClassDevs, the application should call SetupDiDestroyDeviceInfoList.

使用 SetupDiGetClassDevs 返回的 DeviceInfoSet 完成后，应用程序应调用 SetupDiDestroyDeviceInfoList。

### Visual C++

Visual C++

This is the function’s declaration:

这是函数的声明：

```cpp
BOOL SetupDiDestroyDeviceInfoList(
    HDEVINFO DeviceInfoSet);
```

This is the code to call the function:

这是调用函数的代码：

```cpp
SetupDiDestroyDeviceInfoList(DeviceInfoSet);
```

### Visual Basic

Visual Basic

This is the function’s declaration:

这是函数的声明：

```vb
<DllImport("setupapi.dll")> Function
SetupDiDestroyDeviceInfoList _
        (ByVal DeviceInfoSet As IntPtr) _
        As Integer
        End Function
```

This is the code to call the function:

这是调用函数的代码：

```vb
SetupDiDestroyDeviceInfoList (deviceInfoSet)
```

## Obtaining a Handle

获取句柄

An application can use a retrieved device path name to obtain a handle that enables communicating with the device. Table 10-2 shows the API functions related to requesting a handle.

应用程序可以使用检索到的设备路径名称获取一个句柄，从而能够与设备通信。表 10-2 显示了与请求句柄相关的 API 函数。

## Requesting a Communications Handle

请求通信句柄

After retrieving a device path name, an application is ready to open communications with the device. The CreateFile function requests a handle to an object, which can be a file or another resource managed by a driver that supports handle-based operations. For example, applications can request a handle to use in exchanging reports with HID-class devices.

检索到设备路径名称后，应用程序即可准备好打开与设备的通信。CreateFile 函数请求对对象的句柄，该对象可以是文件或由支持基于句柄操作的驱动程序管理的其他资源。例如，应用程序可以请求一个句柄以用于与 HID 类设备交换报告。

### Visual C++

Visual C++

This is the function’s declaration:

这是函数的声明：

```cpp
HANDLE CreateFile(
    LPCSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile
);
```

Table 10-2: Applications can use CreateFile to request a handle to a device and CloseHandle to free the resources used by a handle.

表 10-2：应用程序可以使用 CreateFile 请求对设备的句柄，并使用 CloseHandle 释放句柄使用的资源。

| API Function | DLL | Purpose |
|---|---|---|
| CloseHandle | kernel32 | Free resources used by CreateFile. |
| CreateFile | kernel32 | Retrieve a handle for communicating with a device. |

This is the code to call the function:

这是调用函数的代码：

```
HANDLE DeviceHandle;

DeviceHandle=CreateFile
(DetailData->DevicePath,
GENERIC_READ|GENERIC_WRITE,
FILE_SHARE_READ|FILE_SHARE_WRITE,
(LPSECURITY_ATTRIBUTES)NULL,
OPEN_EXISTING,
0,
NULL);
```

### Visual Basic

Visual Basic

This is a declaration for the SECURITY_ATTRIBUTES structure:

这是 SECURITY_ATTRIBUTES 结构体的声明：

```
<StructLayout(LayoutKind.Sequential)> _
Public Structure SECURITY_ATTRIBUTES
    Dim nLength As Integer
    Dim lpSecurityDescriptor As Integer
    Dim bInheritHandle As Integer
End Structure
```

This is the function's declaration:

这是函数的声明：

```
<DllImport("kernel32.dll", CharSet:=CharSet.Auto)>
Function CreateFile _
    (ByVal lpFileName As String, _
    ByVal dwDesiredAccess As Integer, _
    ByVal dwShareMode As Integer, _
    ByRef lpSecurityAttributes As _
        SECURITY_ATTRIBUTES, _
    ByVal dwCreationDisposition As Integer, _
    ByVal dwFlagsAndAttributes As Integer, _
    ByVal hTemplateFile As Integer) _
    As Integer
End Function
```

This is the code to call the function:

这是调用函数的代码：

```
Public Const GENERIC_READ = &H80000000
Public Const GENERIC_WRITE = &H40000000
Public Const FILE_SHARE_READ = &H1
Public Const FILE_SHARE_WRITE = &H2
Public Const OPEN_EXISTING = 3
Dim DeviceHandle As Integer
Dim Security As SECURITY_ATTRIBUTES

Security.lpSecurityDescriptor = 0
Security.bInheritHandle = CInt(True)
Security.nLength = Len(Security)

DeviceHandle = CreateFile _
    (DevicePathName, _
    GENERIC_READ Or GENERIC_WRITE, _
    FILE_SHARE_READ Or FILE_SHARE_WRITE, _
    Security, _
    OPEN_EXISTING, _
    0, _
    0)
```

## Details

详细信息

The function passes a pointer to the device-path-name string returned by SetupDiGetDeviceInterfaceDetail. The dwDesiredAccess parameter requests read/write access to the device. The dwShareMode parameter allows other processes to access the device while the handle is open. The lpSecurityAttributes parameter is a pointer to a SECURITY_ATTRIBUTES structure. The dwCreationDisposition parameter must be OPEN_EXISTING for devices. The final two parameters are unused in this example.

该函数传递一个指向由 SetupDiGetDeviceInterfaceDetail 返回的设备路径名称字符串的指针。dwDesiredAccess 参数请求对设备的读/写访问。dwShareMode 参数允许在句柄打开时其他进程访问设备。lpSecurityAttributes 参数是指向 SECURITY_ATTRIBUTES 结构的指针。dwCreationDisposition 参数对于设备必须为 OPEN_EXISTING。此示例中最后两个参数未使用。

## Closing the Handle

关闭句柄

Chapter 13 shows how to use a handle to exchange information with a HID-class device. For other device classes, the details will vary with the driver. When finished communicating with a device, the application should call CloseHandle to free the resources used by CreateFile.

第 13 章展示了如何使用句柄与 HID 类设备交换信息。对于其他设备类，细节将因驱动程序而异。与设备通信完成后，应用程序应调用 CloseHandle 以释放 CreateFile 使用的资源。

### Visual C++

Visual C++

This is the function's declaration:

这是函数的声明：

```
BOOL CloseHandle(
    HANDLE hObject);
```

This is the code to call the function:

这是调用函数的代码：

```
CloseHandle(DeviceHandle);
```

### Visual Basic

Visual Basic

This is the function's declaration:

这是函数的声明：

```
<DllImport("kernel32.dll")> Function CloseHandle _
    (ByVal hObject As Integer) _
    As Integer
End Function
```

This is the code to call the function:

这是调用函数的代码：

```
CloseHandle(DeviceHandle)
```

## Detecting Attachment and Removal

检测附加和移除

Many applications find it useful to know when a device has been attached or removed. An application that detects when a device has been attached can begin communicating automatically on attachment. An application that detects when a device has been removed can stop attempting to communicate, notify the user, and wait for reattachment. Windows provides device-notification functions for this purpose.

许多应用程序发现知道设备何时被附加或移除很有用。能够检测到设备已附加的应用程序可以在附加时自动开始通信。能够检测到设备已移除的应用程序可以停止尝试通信、通知用户并等待重新附加。Windows 为此目的提供了设备通知函数。

## About Device Notifications

关于设备通知

To request to be informed when a device is attached or removed, an application’s form can register to receive notification messages for devices in a device interface class. The messages are WM_DEVICECHANGE messages that the operating system passes to the form’s WindowProc (WndProc in Visual Basic) method. An application can override the WindowProc method in a form’s base class with a method that processes the messages and then passes them to the base class’s WindowProc method. Each notification contains a device path name that the application can use to identify the device the notification applies to. Table 10-3 lists the API functions used in registering for device notifications. The example that follows shows how to use the functions.

为了在设备附加或移除时收到通知，应用程序的窗体可以注册以接收设备接口类中设备的通知消息。这些消息是 WM_DEVICECHANGE 消息，操作系统将其传递给窗体的 WindowProc（Visual Basic 中的 WndProc）方法。应用程序可以用一种处理消息然后将其传递给基类 WindowProc 方法的方法来重写窗体基类中的 WindowProc 方法。每个通知都包含一个设备路径名称，应用程序可使用它来标识通知适用的设备。表 10-3 列出了用于注册设备通知的 API 函数。下面的示例展示了如何使用这些函数。

## Registering for Device Notifications

注册设备通知

Applications use the RegisterDeviceNotification function to request to receive notification messages. The function requires a pointer to a handle for the window or service that will receive the notifications, a pointer to a DEV_BROADCAST_DEVICEINTERFACE structure that holds information about the request, and flags to indicate whether the handle is for a window or service status.

应用程序使用 RegisterDeviceNotification 函数请求接收通知消息。该函数需要一个指向将接收通知的窗口或服务的句柄的指针、一个指向保存请求信息的 DEV_BROADCAST_DEVICEINTERFACE 结构的指针，以及指示句柄是用于窗口还是服务状态的标志。

In the DEV_BROADCAST_DEVICEINTERFACE structure passed to RegisterDeviceNotification, the dbcc_devicetype member is set to DBT_DEVTYP_DEVICEINTERFACE to specify that the application wants to receive notifications about a device interface class, and classguid is the GUID of the device interface class (HidGuid in the examples).

传递给 RegisterDeviceNotification 的 DEV_BROADCAST_DEVICEINTERFACE 结构中，dbcc_devicetype 成员设置为 DBT_DEVTYP_DEVICEINTERFACE，以指定应用程序希望接收有关设备接口类的通知，而 classguid 是设备接口类的 GUID（示例中为 HidGuid）。

When the WM_DEVICECHANGE messages are no longer of interest, the application should call UnregisterDeviceNotification, as described later in this chapter.

当 WM_DEVICECHANGE 消息不再感兴趣时，应用程序应调用 UnregisterDeviceNotification，如本章后面所述。

