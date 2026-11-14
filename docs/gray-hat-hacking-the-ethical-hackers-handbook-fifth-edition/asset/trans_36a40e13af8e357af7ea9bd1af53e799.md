
| 配置文件 | 描述 | 示例应用 |
|---|---|---|
| 应用型 | 这些配置文件中功能最强大的一种。其主要区别特征是 MMU，使其能够运行功能丰富的操作系统，例如 Linux 和 Android。 | 手机 平板电脑 机顶盒 |
| 实时型 | 专为需要实时性能特征的应用而设计。具有低中断延迟和内存保护功能。它不包含 MMU。 | 网络路由器和交换机 摄像头 汽车 |
| 微控制器型 | 专为对尺寸和性能要求较低的高度嵌入式系统而设计。具有低中断延迟、内存保护和嵌入式内存功能。 | 工业控制 可编程灯具 |

表 23-1 ARM 配置文件²

MIPS 目前由 Tallwood MIPS, Inc. 拥有，但已授权给包括 Broadcom、Cavium 等在内的多个制造商。³ 与 ARM 类似，MIPS 有 32 位和 64 位变体，可以以大端或小端模式运行。它通常见于无线接入点和小型家用路由器等网络设备中。

## 串行接口

串行接口通过通信通道一次一位、串行地与对等设备通信。由于一次只传输一位，因此 IC 所需的引脚更少。相比之下，并行接口通信一次传输多位，并需要更多引脚（每位一个引脚）。嵌入式系统中使用多种串行协议，但我们将仅讨论通用异步收发传输器（UART）、串行外设接口（SPI）和集成电路互连（I²C）协议。

## UART

通用异步收发传输器（UART）协议允许两个设备通过通信通道进行串行通信。UART 常用于连接控制台，以便人类与设备交互。尽管大多数设备没有可用于串行通信的外部可用接口，但许多设备在开发和测试期间会使用内部接口。在进行设备测试时，我在内部可访问的串行接口上发现了经过身份验证和未经过身份验证的控制台。UART 通信需要三个引脚，通常以四引脚一组的形式出现（参见图 23-1）。您可能会在板上看到标签，但通常这些焊盘或排针没有标签，需要被发现。尽管图 23-1 显示了一个很好的示例，其中排针作为串行通信的候选项非常突出，但引脚布局可能并不总是那么直观，并可能混杂在大量引脚中。

![](img/5f597c6a70133069118d9e804ace3775_640_0.png)

图 23-1 Ubiquiti ER-X 上未标记的四串口组

定位并连接内部串行端口的主要原因是尝试查找原本不打算向系统用户公开的信息。例如，Web 界面通常无法直接访问文件系统，但基于 Linux 的系统上的串行控制台将使用户能够访问文件系统。当串行端口经过身份验证时，您将不得不暴力破解凭据，或尝试通过修改启动过程（可能使用 JTAG 调试端口）来绕过身份验证。

要发现串行焊盘，可以使用由 Joe Grand 开发的 JTAGulator 等工具对信号进行暴力破解，从而得出焊盘布局和波特率。以下是在图 23-1 所示的 Ubiquiti ER-X 上运行 UART 识别测试的示例，其中使用 JTAGulator 识别了带标签的引脚。涉及的步骤如下：

- 1. 通过检查电路板，定位您认为可能是 UART 的排针或焊盘。
  （在电路板上看到两到四个焊盘/引脚组合在一起是个好迹象，但如前所述，它们可能与其他功能焊盘/引脚混杂在一起。）
- 2. 通过使用万用表探测电路板或识别 IC 并查阅数据手册来发现目标电压。
- 3. 通过测量已知接地点（例如机箱接地）与易于连接的引脚之间的电阻（欧姆）来发现易于连接的地（已知接地点与问题引脚之间的电阻实际上为 0 欧姆）。
- 4. 如果您有幸找到排针，请将电路板连接到 JTAGulator，或将排针焊接到电路板上然后再连接（参见图 23-2）。

![](img/5f597c6a70133069118d9e804ace3775_641_0.png)

图 23-2 JTAGulator 与 Ubiquiti ER-X 之间的连接

- 5. 验证 JTAGulator 固件版本 ①。可以通过 https://github.com/grandideastudio/jtagulator/releases 存储库中的代码检查版本。如果版本不是最新的，请按照 www.youtube.com/watch?v=xlXwy-weG1M 中的说明操作。
- 6. 启用 UART 模式 ② 并设置目标电压 ③。
- 7. 运行 UART 识别测试 ④。
- 8. 成功后，查找合理的响应，例如回车或换行 ⑤（0D 或 0A）。
- 9. 以波特率候选项 ⑦（我们的情况为 57600）运行直通模式 ⑥ 以验证已识别的设置。

```
< ... Omitted ASCII ART ...>
  Welcome to JTAGulator. Press 'H' for available commands.
  Warning: Use of this tool may affect target system behavior!

> h
Target Interfaces:
J   JTAG/IEEE 1149.1
U   UART/Asynchronous Serial
G   GPIO

General Commands:
V   Set target I/O voltage (1.2V to 3.3V)
I   Display version information
H   Display available commands
```

```
①> i
JTAGulator FW 1.4
Designed by Joe Grand, Grand Idea Studio, Inc.
Main: jtagulator.com
Source: github.com/grandideastudio/jtagulator
Support: www.parallax.com/support
②> u
③UART> v
Current target I/O voltage: Undefined
Enter new target I/O voltage (1.2 - 3.3, 0 for off): 3.3
New target I/O voltage set: 3.3
Ensure VADJ is NOT connected to target!

④UART> u
UART pin naming is from the target's perspective.
Enter text string to output: (prefix with \x for hex) [CR]:
Enter starting channel [0]:
Enter ending channel [1]:
Possible permutations: 2
Press spacebar to begin (any other key to abort)...
JTAGulating! Press any key to abort...
-
<... Omitted lower baud rates ...>
TXD: 1
RXD: 0
Baud: 9600
Data: `.]!Hv.Sk..... [ 60 FC 5D 84 21 48 76 AF 53 6B 1A 92 0A EF FF 1F ]

TXD: 1
RXD: 0
Baud: 14400
Data: {...../B+f{.*J.Z. [ 7B 09 DE 8A DA 2F 42 2B 66 7B DB 2A 4A 99 5A 10 ]

TXD: 1
RXD: 0
Baud: 19200
Data: T.W...*.q.Q... [ 54 81 C6 57 B9 19 CE 2A 9A 71 EE 00 51 18 EA 19 ]

TXD: 1
RXD: 0
Baud: 28800
Data: ....[H.g.)oI.L. [ 9D 08 E2 0A 5B 48 88 0C 67 F2 29 6F 31 1D 4C 0C ]

TXD: 1
RXD: 0
Baud: 31250
Data: ..[+t>.6"_. ..z [ F4 C2 5B 2B B9 74 3E 95 36 22 03 5F 20 82 DF 7A ]

TXD: 1
RXD: 0
Baud: 38400
Data: ..9 3SdWV./...h0 [ F9 FC 39 20 33 53 64 57 56 05 2F 8D B5 B7 68 30 ]

TXD: 1
RXD: 0
Baud: 57600
⑤Data: .. [ 0D 0A ]

TXD: 1
RXD: 0
Baud: 76800
Data: . [ 0C ]
```

```
TXD: 1
RXD: 0
Baud: 115200
Data: . [ F8 ]
<... Omitted Higher Baud Rates ...>
```

```
⑥UART> p
UART pin naming is from the target's perspective.
Enter X to disable either pin, if desired.
Enter TXD pin [1]:
Enter RXD pin [0]:
⑦Enter baud rate [0]: 57600
Enable local echo? [y/N]: y
Entering UART passthrough! Press Ctrl-X to abort...
```

## 欢迎使用 EdgeOS ubnt ttyS1

登录、访问或使用 Ubiquiti 产品即表示您已阅读并理解 Ubiquiti 许可协议（默认在 Web UI 中可用，网址为 http://192.168.1.1），并同意受其条款约束。

如果测试成功，现在您应该能够与串行控制台交互。
在连接串行控制台的情况下重置设备通常可以揭示大量信息。文本太长，无法在此处包含，因此我提供了启动消息的片段：

- 处理器是 MT-7621A（MIPS）：
  ASIC MT7621A DualCore（MAC 到 MT7530 模式）
- 可以通过 U-Boot 重新编程：
  请选择操作：
  1: 通过 TFTP 将系统代码加载到 SDRAM。
  2: 加载系统代码，然后通过 TFTP 将其写入 Flash。
  3: 通过 Flash 启动系统代码（默认）。
  4: 进入启动命令行界面。
  7: 加载引导加载程序代码，然后通过串行接口将其写入 Flash。
  9: 加载引导加载程序代码，然后通过 TFTP 将其写入 Flash。
  default: 3
- 正在运行 Linux 版本 3.10.14-UBNT：
  Linux version 3.10.14-UBNT (root@edgeos-builder2) (gcc version 4.6.3 (Buildroot 2012.11.1) ) #1 SMP Mon Nov 2 16:45:25 PST 2015
- MTD 分区有助于理解存储布局：
  在 "MT7621-NAND" 上创建 7 个 MTD 分区：
  0x000000000000-0x000000ff80000 : "ALL"
  0x000000000000-0x0000000080000 : "Bootloader"
  0x0000000080000-0x00000000e0000 : "Config"
  0x00000000e0000-0x0000000140000 : "eeprom"
  0x000000140000-0x0000000440000 : "Kernel"
  0x000000440000-0x0000000740000 : "Kernel2"
  0x000000740000-0x000000ff00000 : "RootFS"
  [mtk_nand] probe successfully!

