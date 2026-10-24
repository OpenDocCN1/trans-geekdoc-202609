

通常更通用的方法是识别使用同一驱动程序的设备。本章后面的*使用设备标识字符串*部分将详细介绍硬件 ID 和兼容 ID。

```
[Models]
%DeviceDesc%=Install,USB\VID_0ABA&PID_8001
```

示例 INF 文件有两组 Install 节。一组（Install、Install.CopyFiles 和 Install.AddReg）用于 Windows 98 和 Windows Me。另一组（Install.NT、Install.CopyFiles、Install.NT.Services 和 Install.NT.AddService）用于 Windows 2000 和 Windows XP。两组都使用相同的 Install.CopyFiles 节。名称中包含 .NT 的节被称为*修饰*节：

```
[Install]
CopyFiles=Install.CopyFiles
AddReg=Install.AddReg

[Install.CopyFiles]
ellex200.sys,,,2

[Install.AddReg]
HKR,,DevLoader,,*ntkern
HKR,,NTMPDriver,,ellex200.sys

[Install.NT]
CopyFiles=Install.CopyFiles

[Install.NT.Services]
AddService=ellex200,2,Install.NT.AddService

[Install.NT.AddService]
DisplayName=%SvcDesc%
ServiceType=1
StartType=3
ErrorControl=1
ServiceBinary=%10%\system32\drivers\ellex200.sys
```

在示例的 Install 节中，CopyFiles 指令指定了 Install.CopyFiles 节，该节指定了要复制的驱动程序文件（*ellex200.sys*）。标志值 2 告诉 Windows 不允许用户跳过复制该文件。AddReg 指令命名了 Install.AddReg 节，该节提供要添加到注册表中的信息。在 Install.AddReg 节中，DevLoader 指定与设备关联的设备加载器，NTMPDriver 指定驱动程序。

Windows 2000 和 Windows XP 的 DDInstall 节是 Install.NT。CopyFiles 指令指定了与 Windows 98 和 Windows Me 相同的 Install.CopyFiles 节。这些 Windows 版本不需要 DevLoader 和 NTMPDriver 条目，因此没有 AddReg 节。

Windows 2000 和 Windows XP 需要两个额外的节：Install.NT.Services 和 Install.NT.AddService。Services 节为驱动程序指定服务名称（*ellex200*），将该服务指定为设备的即插即用功能驱动程序（flags = 2），并命名一个 AddService 节，该节指定如何以及何时加载驱动程序的服务（Install.NT.AddService）。

示例中的 AddService 节有五个条目。DisplayName 为服务指定一个友好名称。ServiceType = 1 表示该条目用于内核模式设备驱动程序。StartType = 3 表示在枚举时启动驱动程序。ErrorControl = 1 表示在加载或初始化设备时如果出现错误，则显示警告并继续。ServiceBinary 指定 CopyFiles 节中命名的驱动程序的位置。此节可以包含许多附加指令，这些指令是可选的，或者仅对某些设备和驱动程序是必需的。

## 字符串

Strings 节定义了其他节引用的所有字符串。

```ini
[Strings]
ClassName="Ellisys protocol analyzers"
Provider="Ellisys "
Manufacturer="Ellisys"
SourceDisk="USB Explorer 200 Installation Disk"
DeviceDesc="USB Explorer 200"
SvcDesc="USB Explorer 200 Driver (ellex200.sys)"
```

## 使用设备标识字符串

为了识别设备的可能驱动程序，Windows 会搜索系统上的 INF 文件，查找与设备描述符中的信息所生成的字符串相匹配的设备标识字符串。设备标识字符串分为三类：设备 ID、硬件 ID 和兼容 ID。

### 从设备获取的标识字符串

每个 USB 设备至少有一个设备 ID，该 ID 由集线器驱动程序根据设备描述符中的 Vendor ID、Product ID 和修订号创建。USB 设备的设备 ID 有以下形式之一：

```text
USB\VID_xxxx&PID_yyyy&REV_zzzz
USB\VID_xxxx&PID_yyyy
```

xxxx、yyyy 和 zzzz 中的值各为四个字符：xxxx 是 idVendor 值，yyyy 是 idProduct 值，zzzz 是 bcdDevice 值。idVendor 和 idProduct 值是十六进制值，但 Windows Me 除外，它使用十进制，而 bcdDevice 使用 BCD 格式。

例如，VID = 0925h、PID = 1234h、bcdDevice = 0310 的设备具有以下设备 ID：

```text
USB\VID_0925&PID_1234&REV_0310
```

具有多个接口的设备可以为每个接口指定一个驱动程序。在这种情况下，设备有多个设备 ID，每个接口一个。接口的设备 ID 有以下形式之一：

```text
USB\VID_xxxx&PID_yyyy&REV_zzzz&MI_ww
USB\VID_xxxx&PID_yyyy&MI_ww
```

xxxx、yyyy 和 zzzz 中的值与之前的设备 ID 相同。

ww 中的 2 字符值等于设备某个接口的接口描述符中的 bInterfaceNumber。例如，一个充当鼠标和键盘的复合设备可能在两个 Models 节中有条目，一个用于键盘（接口 00），一个用于鼠标（接口 01）：

```text
[LAKEVIEW_KEYBOARD]
%USB\VID_0925&PID_0801&MI_00.DeviceDesc%=
HID_Inst,, USB\VID_0925&PID_0801&MI_00
```

### 将驱动程序与设备匹配

```text
[LAKEVIEW_MOUSE]
%USB\VID_0925&PID_0801&MI_01.DeviceDesc%=
HID_Inst,, USB\VID_0925&PID_0801&MI_01
```

HID 类设备的报告描述符如果包含多个顶级集合，则每个集合可以有一个设备 ID。集合的设备 ID 可以采用以下任何形式，其中 bb 表示集合编号：

```text
USB\VID_xxxx&PID_yyyy&REV_zzzz&Colbb
USB\VID_xxxx&PID_yyyy&Colbb
USB\VID_xxxx&PID_yyyy&REV_zzz&MI_ww&Colbb
USB\VID_xxxx&PID_yyyy&MI_ww&Colbb
```

除了设备 ID 之外，一些驱动程序还会为设备创建一个或多个兼容 ID 字符串。兼容 ID 可以通过设备描述符中的类代码以及任何子类和协议代码来标识设备。兼容 ID 使用以下形式之一：

```text
USB\CLASS_aa&SUBCLASS_bb&PROT_cc
USB\CLASS_aa&SUBCLASS_bb
USB\CLASS_aa
```

aa、bb 和 cc 的值与设备描述符中的值匹配，每个值都是两个字符：aa 是 bDeviceClass 值，bb 是 bDeviceSubclass 值，cc 是 bDeviceProtocol 值。这些值用十六进制表示，但 Windows Me 除外，它使用十进制。

例如，HID 的类代码是 03h，因此 HID 类设备具有以下兼容 ID：

```text
USB\Class_03
```

对于某些兼容 ID，Windows 会定义描述性名称，例如 USBSTOR_BULK 或 GENERIC_USB_PRINTER。

INF 文件中的兼容 ID 表示不太理想但可以接受的匹配。兼容 ID 使 Windows 能够在 INF 文件不包含匹配的设备 ID 时找到并加载驱动程序。供应商的 INF 文件不应包含兼容 ID。

### 从 INF 文件获取标识字符串

在 INF 文件中，Models 节中的每个条目都有一个硬件 ID 和零个或多个兼容 ID。硬件 ID 列在最前面，后面跟任何兼容 ID，ID 之间用逗号分隔。

硬件 ID 可以有多种形式。它可以采用上面描述的设备、接口或 HID 集合的设备 ID 形式之一。Windows 附带的 INF 文件可能包含使用上述兼容 ID 格式来标识设备的硬件 ID，这些格式通过类或描述性名称标识设备。

### 查找匹配

为了在从设备检索的信息与 INF 文件中的信息之间寻找最佳匹配，Windows 会为找到的每个匹配分配一个等级，等级越低表示匹配越好（表 9-3）。基于 NT 的操作系统，包括 Windows 2000 和 Windows XP，会给予“受信任”的驱动程序更低的等级。这些驱动程序的目录（.cat）文件具有数字签名，表示该驱动程序已通过 Windows 硬件质量实验室（WHQL）测试。第 17 章有更多关于 WHQL 测试的内容。受信任的驱动程序也称为已签名驱动程序。Windows 98 不检查受信任的驱动程序。

在基于 NT 的操作系统中，最佳匹配是设备 ID 与受信任 INF 文件中的硬件 ID 匹配。次佳匹配是设备 ID 与受信任 INF 文件中的兼容 ID 匹配。再次是设备中的兼容 ID 与受信任 INF 文件中的硬件 ID 匹配，然后是设备中的兼容 ID 与受信任 INF 文件中的兼容 ID 匹配。只有当与受信任 INF 文件完全没有匹配时，基于 NT 的操作系统才会考虑来自不受信任 INF 文件的 ID。

如果 Windows 找不到匹配，它会启动“找到新硬件”向导，让用户有机会指定位置（例如 CD 驱动器）来查找 INF 文件。

复合设备（具有多个接口）是一个特例。由于每个接口可能需要不同的驱动程序，因此在选择使用哪个驱动程序时

