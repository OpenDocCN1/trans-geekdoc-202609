
如 bash、telnetd、ls、cp 等，通常会使用一个名为 busybox 的更小的单体程序。Busybox 14 通过将第一个参数用作所需程序，在单个可执行文件中提供相应功能。虽然我很想说未使用的服务被移除是为了减小攻击面，但它们很可能只是为了节省空间而被移除。

虽然大多数设备并非故意向用户提供控制台访问权限，但许多设备在板上确实有一个用于控制台访问的串行端口。一旦您通过控制台或从存储中提取镜像而获得根文件系统的访问权限，您将希望查看应用程序和库的版本、全局可写目录、任何持久存储以及初始化过程。Linux 的初始化过程位于 /etc/inittab 和 /etc/init.d/rcS，它将让您了解应用程序在启动时是如何启动的。

## 摘要

在本章中，我们简要讨论了不同 CPU 封装（微控制器、微处理器和 SoC）、几种感兴趣的串行接口、JTAG 和嵌入式软件之间的差异。在我们讨论串行接口时，您通过发现 UART（串行）端口的示例了解了 JTAGulator。JTAGulator 还可用于发现 JTAG 调试端口以及潜在的其他几种接口。我们还简要讨论了不同的软件用例，包括引导加载程序、无操作系统、RTOS 和通用操作系统。此时，您应该已掌握嵌入式系统的通用词汇，以及在尝试深入了解时需要关注的几个领域。

## 进一步阅读

- ARM:
  - https://developer.arm.com/products/architecture/a-profile
  - https://www.arm.com/products/processors/cortex-a?tab=Resources
  - https://developer.arm.com/products/architecture/r-profile
  - https://www.arm.com/products/processors/cortex-r?tab=Resources
  - https://developer.arm.com/products/architecture/m-profile
  - https://www.arm.com/products/processors/cortex-m?tab=Resources

- Bus Pirate http://dangerousprototypes.com/docs/Bus_Pirate

- 嵌入式 Linux https://www.elinux.org/Main_Page

- 固件提取与重构 https://www.j-michel.org/blog/2013/09/16/firmware-extraction-and-reconstruction

- 固件安全信息 https://github.com/advanced-threat-research/firmware-security-training

- Free RTOS https://www.freertos.org/

- I2C https://learn.sparkfun.com/tutorials/i2c

- JTAG:
  - http://blog.senr.io/blog/jtag-explained
  - https://developer.arm.com/docs/dui0499/latest/arm-dstream-target-interface-connections/signal-descriptions/serial-wire-debug

- JTAGulator www.grandideastudio.com/jtagulator/

- MT-7621A:
  - https://www.mediatek.com/products/homeNetworking/mt7621n-a
  - https://wikidevi.com/wiki/MediaTek_MT7621

- OpenOCD http://openocd.org/

- 逆向工程 VxWorks 固件 www.devttys0.com/2011/07/reverse-engineering-vxworks-firmware-wrt54gv8/

- SPI https://www.maximintegrated.com/en/app-notes/index.mvp/id/3947

- 了解 ARM 硬件调试选项 https://elinux.org/images/7/7f/Manderson5.pdf

- VxWorks https://www.windriver.com/products/vxworks/

## 参考文献

- 1. 或门，Wikipedia, https://en.wikipedia.org/wiki/OR_gate.
- 2. “ARM 架构配置文件”，ARM 开发者，http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0471i/BCFDF FGA.html.
- 3. “MIPS 出售完成”，Imagination，2017 年 10 月 25 日，https://www.imgtec.com/news/press-release/completion-of-sale-of-mips/.
- 4. “串行外设接口 (SPI)”，Sparkfun，https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi.
- 5. “串行外设接口总线，SPI 标准”，Wikipedia，https://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus#Standards.
- 6. “SPI”，https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi.
- 7. “I2C—这是什么？”，Wikipedia，I2C，https://www.i2c-bus.org/.
- 8. 联合测试行动组，Wikipedia，https://en.wikipedia.org/wiki/JTAG.
- 9. “JTAG 引脚图”，JTAG 测试，www.jtagtest.com/pinouts/.
- 10. “JTAG 引脚描述”，ARM DS-5 DSTREAM 系统与接口设计参考指南第 5 版，https://developer.arm.com/docs/dui0499/latest/arm-dstream-target-interface-connections/the-arm-jtag-20-connector-pinouts-and-interface-signals/arm-jtag-20-interface-signals.
- 11. “SWJ-DP 的结构”（JTAG/SWD 作为 SWJ-DP 共存），ARM 开发者，http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.ddi0314h/Chdjjbcb.html.
- 12. “10 路连接器引脚图”（SWD/JTAG 10 针），ARM 开发者，http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.ddi0314h/Chdhbiad.html.
- 13. “包含追踪的 20 路连接器引脚图”（SWD/JTAG 20 针），ARM 开发者，http://infocenter.arm.com/help/topic/com.arm.doc.ddi0314h/Chdfccbi.html.
- 14. “BusyBox：嵌入式 Linux 的瑞士军刀”，BusyBox，https://busybox.net/about.html.

## 利用嵌入式设备

本章介绍利用嵌入式设备的主题。随着物联网（IoT）的出现，这一主题变得越来越重要，如前几章所述。从电梯到汽车、烤面包机以及一切“智能”设备，嵌入式设备正在变得无处不在，安全漏洞和威胁也在变得数不胜数。正如 Bruce Schneier 所观察到的，这就像 20 世纪 90 年代的“西部荒野”重现；无论我们看向哪里，这些嵌入式设备中都存在漏洞。Schneier 解释说，这是因为许多因素造成的，包括设备自身的资源有限，以及在生产嵌入式设备这一低利润领域中，制造商的资源有限。¹ 希望更多的道德黑客能够迎接这一挑战，在嵌入式设备漏洞的洪流中占据一席之地。为此，在本章中，我们将讨论以下主题：

- 嵌入式设备漏洞的静态分析
- 基于硬件的动态分析
- 基于仿真的动态分析

## 嵌入式设备漏洞的静态分析

漏洞的静态分析涉及在不需要为待评估设备通电的情况下，通过检查系统的更新包、文件系统和二进制文件来查找漏洞。事实上，在大多数情况下，攻击者不需要拥有设备即可进行大部分静态分析。在本节中，您将接触到一些用于对嵌入式设备进行静态分析的工具和技术。

## 实验 24-1：分析更新包

在大多数情况下，设备的更新包可以从厂商网站下载。目前，大多数更新未加密，因此可能可以使用 unzip、binwalk 和 Firmware Mod Kit 等各种工具进行解构。出于教学目的，我们将查看基于 Linux 的系统，因为您很可能已经熟悉这些系统。

在基于 Linux 的嵌入式系统中，更新包通常包含运行系统所需的所有基本文件和目录的新副本。所需的目录和文件被称为根文件系统 (RFS)。如果攻击者能够访问 RFS，他们将拥有初始化例程、Web 服务器源代码、运行系统所需的任何二进制文件，以及可能为攻击者在尝试利用系统时提供优势的一些二进制文件。例如，如果系统使用 Busybox 并包含 telnetd 服务器，攻击者可能能够利用 Telnet 服务器为系统提供远程访问。具体来说，Busybox 中包含的 telnetd 服务器提供一个参数，允许它在无需身份验证的情况下被调用，并绑定到任何程序 (/usr/sbin/telnetd -l /bin/sh)。

作为示例，我们将调查 D-Link DAP-1320 无线信号扩展器固件更新的旧版本（A 硬件版本 1.1）。选择此更新是因为它是一个较旧的、已打补丁的更新，且漏洞披露 (www.kb.cert.org/vuls/id/184100) 由多位作者报告。

![](img/5f597c6a70133069118d9e804ace3775_660_0.png)

第一步是创建固件解构环境。在我们的情况中，我们将使用固件修改工具包。我们分析的基础主机系统是 Kali Linux 2017.1。为了安装固件修改工具包，必须先使用包管理器 apt-get ① 安装先决条件。满足先决条件后，安装只需从 GitHub ② 克隆项目。首次运行 extract-firmware.sh 时，它会编译必要的工具并产生大量输出（示例中省略了首次运行）。然后我们尝试提取固件 ③，如果工具知道包和内容类型，它们将被提取以供进一步分析。从输出中，我们可以看到该工具已找到 MIPS Linux 内核镜像 ④ 和 squashfs 文件系统 ⑤，并且它们已成功提取到 fmk 目录 ⑥。通过浏览提取内容，我们将其识别为 rootfs ⑦，并验证二进制文件是为 MIPS ⑧ 编译的。
