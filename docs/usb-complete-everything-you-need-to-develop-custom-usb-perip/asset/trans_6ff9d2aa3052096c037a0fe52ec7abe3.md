

应用程序可以将此设备路径名与目标设备的设备路径名进行比较。如果匹配，应用程序可以采取任何所需的操作。

## Visual C++

以下代码用于检索设备路径名并查找匹配项：

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

应用程序对 `DEV_BROADCAST_DEVICEINTERFACE` 结构使用两个声明。第一个声明（前面已介绍）在调用 `RegisterDeviceNotification` 时使用。第二个声明 `DEV_BROADCAST_DEVICEINTERFACE_1` 可以对 `dbcc_name` 和 `classguid` 中的数据进行封送处理：

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

以下代码用于检索设备路径名并查找匹配项：

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

`Marshal.PtrToStructure` 会将消息的 `lParam` 属性复制到 `DEV_BROADCAST_HDR` 结构中。如果 `lParam` 指示该消息与设备接口相关，应用程序就会检索设备路径名。

该名称位于非托管内存中的 `Char` 数组中。应用程序需要检索该 `Char` 数组并将其转换为 `String`。

`DEV_BROADCAST_HDR` 的 `dbch_size` 成员包含整个 `DEV_BROADCAST_INTERFACE` 结构中的字节数。若要获取存储在 `dbcc_name` 中的设备路径名的字符数，请减去结构中不属于名称部分的 32 个字节，然后除以 2，因为每个字符占 2 个字节。

`DevBroadcastDeviceInterface` 是一个 `DEV_BROADCAST_DEVICEINTERFACE_1` 结构，用于对 `classguid` 和 `dbcc_name` 成员中的数据进行封送处理。`ReDim` 语句会修剪 `dbcc_name`，使其与设备路径名的大小匹配。`Marshal.PtrToStructure` 会将 `lParam` 中非托管块的数据复制到 `DevBroadcastDeviceInterface` 结构中。包含设备路径名的 `Char` 数组随后作为 `String` 存储在 `DeviceNameString` 中，并通过 `String.Compare` 方法查找匹配项。

## 停止设备通知

要停止接收设备通知，应用程序会调用 `UnregisterDeviceNotification`。应用程序应在关闭之前调用该函数。

### Visual C++

这是该函数的声明：

```
BOOL UnregisterDeviceNotification(
    HDEVNOTIFY Handle
);
```

这是调用该函数的代码：

```
UnregisterDeviceNotification(
    DeviceNotificationHandle);
```

### Visual Basic

这是该函数的声明：

```
<DllImport("user32.dll")> Function
UnregisterDeviceNotification _
    (ByVal Handle As IntPtr) _
    As Boolean
End Function
```

这是调用该函数的代码：

```
UnregisterDeviceNotification _
    (DeviceNotificationHandle)
```

## 11 人机接口设备：使用控制和中断传输

人机接口设备（HID）类是 Windows 最早支持的 USB 类之一。在运行 Windows 98 或更高版本的 PC 上，应用程序可以使用操作系统内置的驱动程序与 HID 通信。因此，许多厂商专用的 USB 设备都使用 HID 类。

第 7 章介绍了该类。本章说明如何确定某个特定设备是否能归入人机接口类，详细介绍了将设备定义为 HID 并使其能够与主机交换数据的固件要求，介绍了六个 HID 专用的控制请求，并给出了一个 HID 固件示例。第 12 章介绍 HID 用于交换信息的报告，第 13 章说明如何从应用程序访问 HID。

## 什么是 HID？

名称中的*人机接口*表示 HID 直接与人交互，许多 HID 也确实如此。鼠标可以检测到有人按下按键或移动鼠标，主机也可以发送一条消息，转换为用户体验到的操纵杆效果。除了键盘、鼠标和操纵杆之外，HID 类还包括带有旋钮、开关、按钮和滑块的前面板；遥控器；电话键盘；以及数据手套和方向盘等游戏控制设备。

但 HID 不一定非要有人机接口。设备只需能够在 HID 类规范的限制内运行即可。以下是 HID 类设备的主要能力和限制：

- 所有交换的数据都存放在称为报告（report）的结构中。主机通过控制传输或中断传输发送和请求报告来发送和接收数据。报告格式灵活，几乎可以处理任何类型的数据，但每个定义的报告都有固定大小。
- HID 接口必须有一个中断 IN 端点用于发送输入报告。
- HID 接口最多只能有一个中断 IN 端点和一个中断 OUT 端点。如果需要更多中断端点，可以创建一个包含多个 HID 的复合设备。应用程序必须为复合设备中的每个 HID 获取独立的句柄。
- 中断 IN 端点使 HID 能够在不可预测的时间向主机发送信息。例如，计算机无法知道用户何时会按下键盘上的按键，因此主机驱动程序使用中断事务定期轮询设备以获取新数据。
- 数据交换速率受到限制，尤其是在低速和全速下。如第 3 章所述，主机可以保证低速中断端点不超过 800 字节/秒。对于全速端点，最大为 64 千字节/秒；对于高速端点，如果主机支持高带宽端点，最大约为 24 兆字节/秒，否则约为 8 兆字节/秒。控制传输没有保证带宽，但总线上为所有控制传输保留的带宽除外。
- Windows 98 Gold（原始版本）支持 USB 1.0，因此不支持中断 OUT 传输，所有主机到设备的报告都必须使用控制传输。

任何能在该类别限制内运行的设备都可以成为 HID。HID 规范提到了条形码阅读器、温度计和电压表作为可能没有传统人机接口的 HID 示例。这些设备都会向计算机发送数据，也可能接收配置设备的请求。主要接收数据的设备示例包括远程显示器、远程设备的控制面板、机器人，以及任何会从主机接收偶发或定期命令的设备。

HID 接口可能只是设备支持的多个 USB 接口之一。例如，使用等时传输进行音频传输的 USB 扬声器也可能有一个 HID 接口，用于控制音量、平衡、高音和低音。HID 接口通常比设备上的传统物理控件更便宜。

## 硬件要求

要符合 HID 规范，接口的端点和描述符必须满足若干要求。

### 端点

所有 HID 传输要么使用控制端点，要么使用中断端点。每个 HID 都必须有一个中断 IN 端点用于向主机发送数据。中断 OUT 端点是可选的。表 11-1 显示了 HID 中的传输类型及其典型用途。

