

表11-2：HID 类描述符包含 7 个或更多字段，占用 9 个或更多字节。

| 偏移量（十进制） | 字段 | 大小（字节） | 说明 |
|---|---|---|---|
| 0 | bLength | 1 | 描述符的大小（以字节为单位）。 |
| 1 | bDescriptorType | 1 | 此描述符的类型：21h 表示 HID 类。 |
| 2 | bcdHID | 2 | HID 规范版本号（BCD）。 |
| 4 | bCountryCode | 1 | 标识本地化硬件的国别的数字表达式（BCD）。 |
| 5 | bNumDescriptors | 1 | 紧随其后的报表描述符和物理描述符的数量。 |
| 6 | bDescriptorType | 1 | 后面跟随的类专用描述符的类型。（报表描述符（必需）的类型为 22h。） |
| 7 | wDescriptorLength | 2 | 上述标识的描述符的总长度。 |
| 9 | bDescriptorType | 1 | 可选。后面跟随的类专用描述符的类型。物理描述符的类型为 23h。 |
| 10 | wDescriptorLength | 2 | 上述标识的描述符的总长度。仅当紧邻其上方存在 bDescriptorType 时才存在。后面可能跟有附加的 bDescriptorType 和 wDescriptorLength 字段，用于标识其他物理描述符。 |

该描述符具有两个或更多 bDescriptorType 字段。其中一个标识 HID 描述符，其他的标识从属描述符的类型。

### 描述符

**bLength。** 描述符的字节长度。

**bDescriptorType。** 值 21h 表示 HID 描述符。

### 类

**bcdHID。** 接口所遵循的 HID 规范版本号，采用 BCD 格式。版本 1.0 为 0100h；版本 1.1 为 0110h。

**bCountryCode。** 如果硬件针对特定国家/地区进行了本地化，该字段是标识国家/地区的代码。HID 规范列出了这些代码。如果硬件未本地化，该字段为 00h。

## 人机接口设备：使用控制传输和中断传输

```text
0x06  0xFFA0      Usage Page (vendor-defined)
0x09  0x01        Usage (vendor-defined)
0xA1  0x01        Collection (Application)

0x09  0x03        Usage (vendor-defined)
0x15  0x00        Logical Minimum (0)
0x26  0x00FF      Logical Maximum (255)
0x95  0x02        Report Count (2)
0x75  0x08        Report Size (8 bits)
0x81  0x02        Input (Data, Variable, Absolute)

0x09  0x04        Usage (vendor-defined)
0x15  0x00        Logical Minimum (0)
0x26  0x00FF      Logical Maximum (255)
0x75  0x08        Report Size (8 bits)
0x95  0x02        Report Count (2)
0x91  0x02        Output (Data, Variable, Absolute)

0x09  0x05        Usage (vendor-defined)
0x15  0x00        Logical Minimum (0)
0x26  0x00FF      Logical Maximum (255)
0x75  0x08        Report Size (8 bits)
0x95  0x02        Report Count (2)
0xB1  0x02        Feature (Data, Variable, Absolute)

0xC0              End Collection
```

清单 11-2：该报表描述符定义了一个输入报表、一个输出报表和一个特征报表。每个报表传输两个厂商自定义的字节。

报表描述符定义了报表可以包含的条目。以下说明示例描述符中每个条目的含义：

Usage Page（用法页）条目由值 06h 标识，指定设备的一般功能，例如通用桌面控制、游戏控制或字母数字显示。在示例描述符中，Usage Page 是厂商定义的值 FFA0h。HID 规范列出了不同 Usage Page 的值，以及为厂商定义的 Usage Page 保留的值。

Usage（用法）条目由值 09h 标识，指定一个报表在某个 Usage Page 中的功能。例如，可用于通用桌面控制的 Usage 包括鼠标、操纵杆和键盘。由于示例中的 Usage Page 是厂商定义的，该 Usage Page 中的所有 Usage 也都是厂商定义的。在示例中，Usage 为 01h。

**Collection (Application)**（集合（应用））条目开启一组条目，这些条目共同执行单一功能，例如键盘或鼠标。每个报表描述符都必须有一个应用集合。

该集合包含三个报表。每个报表具有以下条目：

-   一个厂商定义的 Usage 应用于报表中的数据。
-   Logical Minimum（逻辑最小值）和 Logical Maximum（逻辑最大值）指定报表可以包含的值的范围。
-   Report Count（报表数量）条目指示报表包含多少个数据项。在示例中，每个报表包含两个数据项。
-   Report Size（报表大小）条目指示每个被报告的数据项占多少位。在示例中，每个数据项为 8 位。
-   最后一个条目指定该报表是输入报表 (81h)、输出报表 (91h) 还是特征报表 (B1h)。该条目附带的位包含有关报表数据的附加信息。

End Collection（结束集合）条目关闭应用集合。

第 12 章有更多关于报表格式的内容。

### HID 专用请求

表 11-3：HID 类定义了六个 HID 专用请求。

| 请求编号 | 请求 | 数据源（数据阶段） | wValue（高字节，低字节） | wIndex | 数据长度（字节）(wLength) | 数据阶段内容 | 是否需要？ |
|---|---|---|---|---|---|---|---|
| 01h | Get_Report | 设备 | 报表类型、报表 ID | 接口 | 报表长度 | 报表 | 是 |
| 02h | Get_Idle | 设备 | 0、报表 ID | 接口 | 1 | 空闲持续时间 | 否 |
| 03h | Get_Protocol | 设备 | 0 | 接口 | 1 | 协议 | 对于支持启动协议的 HID 为必需 |
| 09h | Set_Report | 主机 | 报表类型、报表 ID | 接口 | 报表长度 | 报表 | 否 |
| 0Ah | Set_Idle | 无数据阶段 | 空闲持续时间、报表 ID | 接口 | – | – | 否，使用启动协议的键盘除外 |
| 0Bh | Set_Protocol | 无数据阶段 | 0、协议 | 接口 | – | – | 对于支持启动协议的 HID 为必需 |

**Get_Report**

**用途：** 主机使用控制传输从 HID 请求输入报表或特征报表。

**请求编号（bRequest）：** 01h

**数据来源：** 设备

**数据长度（wLength）：** 报表长度

**wValue 字段内容：** 高字节包含报表类型（1=输入，3=特征），低字节包含报表 ID。默认报表 ID 为零。

**wIndex 字段内容：** 该请求所指向的接口编号。

**数据阶段中数据包内容：** 报表

**备注：** 所有 HID 都必须支持此请求。另请参阅 Set_Report。

**Get_Idle**

**用途：** 主机从 HID 读取当前的 Idle（空闲）速率。

**请求编号（bRequest）：** 02h

**数据来源：** 设备

**数据长度（wLength）：** 1

**wValue 字段内容：** 高字节为零。低字节指示此请求所应用的报表 ID。如果低字节为零，此请求应用于 HID 的所有输入报表。

**wIndex 字段内容：** 支持此请求的接口编号。

**数据阶段中数据包内容：** Idle 速率，以 4 毫秒为单位。

**备注：** 更多详情请参阅 Set_Idle。HID 不要求支持此请求。

**Get_Protocol**

**用途：** 主机获知 HID 中当前激活的是启动协议还是报表协议。

**请求编号（bRequest）：** 03h

**数据来源：** 设备

**数据长度（wLength）：** 1

**wValue 字段内容：** 0

**wIndex 字段内容：** 支持此请求的接口编号。

**数据阶段中数据包内容：** 协议（0 = 启动协议，1 = 报表协议）。

**备注：** 启动设备必须支持此请求。另请参阅 Set_Protocol。

