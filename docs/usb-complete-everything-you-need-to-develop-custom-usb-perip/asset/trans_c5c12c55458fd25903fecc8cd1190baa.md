
USB IrDA 桥使用批量管道与主机交换数据。主机和桥在报头中放置状态和控制信息，其格式在 IrDA 桥规范中定义。在从 IrDA 链路接收数据时，IrDA 桥提取 IrLAP 有效载荷，添加报头，并将数据和报头传递给主机。报头可以包含 IrDA 链路的 Media_Busy 和 Link_Speed 参数的值。在从主机接收 IrDA 数据时，IrDA 桥移除主机添加的报头。报头可以指定 Link_Speed 的新值和帧开始标记的数量。然后桥将 IrDA 有效载荷置于 IrDA 帧中以进行传输。

## Descriptors

IrDA 桥功能在接口子类级别定义。在接口描述符中，bInterfaceClass = FEh 表示应用特定接口和 bInterfaceSubclass 02h 表示 IrDA Bridge Device。类特定描述符包含 IrDA 特定信息，例如 IrDA 帧中的最大字节数和支持的波特率。

## Class-specific Requests

有五个类特定控制请求：

| 请求 | bRequest | 描述 |
|---|---|---|
| Receiving | 1 | 设备当前是否正在接收 IrLAP 帧？ |
| Check_Media_Busy | 3 | 是否存在红外流量？ |
| Set_IrDA_Rate_Sniff | 4 | 以任意速度或单一速度接受帧。 |
| Set_IrDA_Unicast_List | 5 | 仅接受来自指定地址的帧。 |
| Get_Class_Specific_Descriptors | 6 | 返回类特定描述符。 |

## Chips

SigmaTel, Inc.’s STIR4000 是一款 IrDA USB 桥芯片，包含全速 USB 收发器和 IrDA 收发器的接口。主机通过访问一系列寄存器与芯片通信，这些寄存器可用于配置、获取状态信息和交换数据。该芯片支持用于读取和写入寄存器的厂商特定控制请求。STIR4200 是该芯片的高速版本。

将 IrDA 添加到 USB 主机的另一种方法是使用带 IrDA 接口的 USB/异步串行转换器。Texas Instruments’ TUSB3410 是一款用于有线和 IrDA 串行接口的 USB/异步串行转换器。对于有线链路，芯片内部的 UART 接口到串行数据引脚。对于 IrDA 链路，UART 接口到内部 IrDA 编解码器，后者再连接到外部 IrDA 收发器。

## Windows Support

Windows XP 通过两种软件配置文件支持 IrDA 通信。拨号网络配置文件可启用使用 IrDA 连接 PC 和移动电话。LAN 访问配置文件可启用使用点对点协议 (PPP)、直接点对点网络连接或直接连接到网络接入点。Windows XP 不包含 USB-IrDA 桥功能的通用驱动程序，但 SigmaTel 为其芯片提供了驱动程序。

## Mass Storage

大容量存储类用于在单向或双向传输文件的设备。典型设备包括软盘、硬盘、CD、DVD 和闪存驱动器。相机可以使用大容量存储类来访问相机内存中的图片文件。在 Windows 计算机中，使用大容量存储驱动程序的设备在“我的电脑”中显示为驱动器，文件系统使用户能够复制、移动和删除设备中的文件。

## Documentation

大容量存储设备的 USB 规范包含在四份文档中：概述（版本 1.2）、仅批量传输协议规范（版本 1.0）和控制/批量/中断（CBI）传输协议规范（版本 1.1）以及通用软盘接口（UFI）命令（版本 1.0）。

每种媒体类型都有一个行业标准的命令块集，用于控制设备和读取状态信息。以下规范定义了大容量存储类支持的设备类型的命令块集：

ATAPI CD/DVD 设备使用来自 *www.t13.org* 的 *ATA/ATAPI* 规范和来自 *www.t10.org* 的 *MultiMedia Command (MMC) Set*。 （ATA/ATAPI 规范的早期版本称为 *SFF 8020i*。）

ATAPI 可移动媒体使用来自 *www.sffcommittee.com* 的 *SFF-8070i: ATAPI Removable Rewritable Media Devices*。该文档是 ATA/ATAPI 规范的补充。软盘驱动器通常属于此类子类。

通用 SCSI 媒体使用来自 *www.t10.org* 的 *SCSI Primary Command (SPC) Set* 和 *SCSI Block Command (SBC) Set* 中的强制命令。

QIC-157 磁带驱动器使用来自 *www.qic.org* 的 *Common SCSI/ATAPI Command Set for Streaming Tape*。

UFI 使用来自 *www.usb.org* 的 *UFI Command Specification*。命令基于 SCSI-2 和 SFF-8070i 命令集。

## Overview

大容量存储设备使用批量传输交换数据。控制传输发送类特定请求并可以清除批量端点的 Stall 条件。用于交换其他信息，设备可以使用两种传输协议之一：仅批量或控制/批量/中断（CBI）。CBI 仅批准用于全速软盘驱动器。仅批量传输推荐用于所有类型的新设备。

在仅批量协议中，成功的数据传输有三个阶段：命令传输、数据传输和状态传输。在命令传输阶段，主机在称为命令块包装器（CBW）的结构中发送命令。在数据传输阶段，主机或设备发送请求的数据。在状态传输阶段，设备在称为命令状态包装器（CSW）的结构中发送状态信息。有些命令没有数据传输阶段。

### 表 7-7：CBW 包含命令块和其他有关命令的信息。

| 名称 | 位 | 描述 |
|---|---|---|
| dCBWSignature | 32 | 值 43425355h，用于标识该结构为 CBW。 |
| dCBWTag | 32 | 一个标签，将此 CBW 与设备响应时发送的 CSW 关联起来。 |
| dCBWDataTransferLength | 32 | 主机在数据传输阶段期望传输的字节数。 |
| bmCBWFlags | 8 | 指定数据传输阶段的方向。位 7 = 0 表示 OUT（主机到设备）传输。位 7 = 1 表示 IN（设备到主机）传输。所有其他位均为零。如果没有数据传输阶段，则忽略位 7。 |
| Reserved | 4 | 0 |
| bCBWLUN | 4 | 对于具有多个 LUN 的设备，指定命令块指向的 LUN。否则值为零。 |
| Reserved | 3 | 0 |
| bCBWCBLength | 5 | 命令块的长度（以字节为单位，1–16） |
| CBWCB | 128 | 设备要执行的命令块。 |

表 7-7 显示了 CBW 中的字段，共 31 字节。CBWCB 字段中命令块值的含义随接口描述符的 bInterfaceSubClass 字段指定的命令集而变化。

在接收到 CBW 后，设备必须检查该结构是否有效且内容有意义。如果在 CSW 或复位后接收到 CBW，且为 31 字节，并在 dCBWSignature 中具有正确的值，则 CBW 有效。如果未设置保留位、bCBWLUN 包含受支持的 LUN 值，并且 bCBWCBLength 和 CBWCB 对接口的子类有效，则内容被视为有意义。

表 7-8 显示了 CSW 中的字段，共 13 字节。在接收到 CSW 后，设备必须检查该结构是否有效且内容有意义。CSW 有效如果它有 13 字节，具有正确的值在

### 表 7-8：CSW 包含有关命令的状态和相关信息。

| 名称 | 位 | 描述 |
|---|---|---|
| dCSWSignature | 32 | 值 53425355h，用于标识该结构为 CSW。 |
| dCSWTag | 32 | 从主机接收到的 CBW 中的 dCBWTag 的值。 |
| dCSWDataResidue | 32 | 对于 OUT 传输，dCBWDataTransferLength 与设备处理的字节数之差。对于 IN 传输，dCBWDataTransferLength 与设备发送的字节数之差。 |
| bCSWStatus | 8 | 00h = 命令通过
01h = 命令失败
02h = 阶段错误 |

dCSWSignature 中，并且具有与相应 CBW 的 dCBWTag 匹配的 dCSWTag 值。如果 bCSWStatus 等于 02h，或者 bCSWStatus 等于 00h 或 01h 且 dCSWDataResidue 小于或等于 dCBWDataTransferLength，则内容被视为有意义。

## Descriptors

大容量存储功能在接口级别定义。在设备的接口描述符中，bInterfaceClass = 08h 表示接口属于大容量存储类。

bInterfaceSubClass 字段指示受支持的命令块集：

| bInterfaceSubClass | 子类描述 |
|---|---|
| 02h | ATAPI CD/DVD 设备 |
| 03h | QIC-157 磁带设备 |
| 04h | USB 软盘接口（UFI） |
| 05h | ATAPI 可移动媒体 |
| 06h | 通用 SCSI 媒体 |

