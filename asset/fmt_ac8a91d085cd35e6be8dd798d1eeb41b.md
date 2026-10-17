
# chipsec_main.py -m common.bios_wp

```
=====================================================================
 Module: BIOS Region Write Protection
=====================================================================

- BC = `0x00000A88` << BIOS 控制 (b:d.f 00:31.5 + 0xDC)
- BIOSWE = `0` << BIOS 写入使能
- BLE = `0` << BIOS 锁定使能
- SRC = `2` << SPI 读取配置
- TSS = `0` << 顶端交换状态
- SMM_BWP = `0` << SMM BIOS 写入保护
- BBS = `0` << 引导 BIOS 跳线
- BILD = `1` << BIOS 接口锁定

BIOS 区域写入保护已禁用！

- BIOS 区域：基址 = `0x00A00000`，上限 = `0x00FFFFFF`

SPI 受保护范围
------------------------------------------------------------
PRx (偏移) | 值 | 基址 | 上限 | WP? | RP?
------------------------------------------------------------
PR0 (84) | 00000000 | 00000000 | 00000000 | 0 | 0
PR1 (88) | 00000000 | 00000000 | 00000000 | 0 | 0
PR2 (8C) | 00000000 | 00000000 | 00000000 | 0 | 0
PR3 (90) | 00000000 | 00000000 | 00000000 | 0 | 0
PR4 (94) | 00000000 | 00000000 | 00000000 | 0 | 0

SPI 受保护范围未对 BIOS 区域进行写入保护

BIOS 应启用所有可用的 SMM 基于写入保护机制，或配置 SPI 受保护范围以保护整个 BIOS 区域

FAILED: BIOS 未完全受保护
```

`Listing 15-1: common.bios_wp 模块的 chipsec 工具输出`

输出显示 BLE ➊ 未启用，这意味着攻击者可以直接在常规操作系统的内核模式下，通过 SPI 闪存芯片修改 BIOS 内存的任意区域。此外，SMM_BWP ➋ 和 PRx ➌ 完全未被使用，表明该平台根本没有启用任何 SPI 闪存保护机制。

如果 `Listing 15-1` 中测试的平台的 BIOS 更新未进行签名，或硬件厂商未正确验证更新，攻击者可以轻易篡改固件。这种情况看似偶然，但此类简单错误实际上相当常见。原因各异：有些厂商对安全毫不在意，另一些虽知晓安全问题，却不愿为低成本硬件开发复杂的更新方案。下面我们来看看其他感染 BIOS 的方式。

## 感染 BIOS 的方式

我们在 `Chapter 14` 中详细审查了复杂且多层次的 UEFI 启动过程。该章节的核心要点是，在 UEFI 固件将控制权交给操作系统加载器，操作系统开始启动之前，攻击者有大量隐藏或感染系统的位置。

事实上，现代 UEFI 固件愈发像一个独立的操作系统。它拥有自己的网络栈和任务调度器，并且可以在启动过程之外直接与物理设备通信——例如，许多设备通过 UEFI DXE 驱动程序与操作系统通信。`Figure 15-3` 展示了固件感染可能通过不同启动阶段实现的情形。

![image](img/15fig03.jpg)

*Figure 15-3: UEFI 固件启动流程中的攻击指针*

多年来，安全研究人员发现了许多漏洞，使攻击者能够在启动过程前注入恶意代码。截至目前，大多数漏洞已被修复，但即使是新硬件，也可能仍受到这些旧问题的影响。以下是通过多种方式在 UEFI 固件中植入持久化根套件或植入程的方式：

**修改未签名的 UEFI 选项 ROM** 攻击者可以修改某些添加卡（如网络卡、存储卡等）中的 UEFI DXE 驱动程序，以在 DXE 阶段执行恶意代码。

**添加/修改 DXE 驱动** 攻击者可以修改已有的 DXE 驱动，或在 UEFI 固件映像中添加恶意 DXE 驱动。结果是，添加或修改后的 DXE 驱动将在 DXE 阶段被执行。

**替换 Windows 引导管理器（回退启动器）** 攻击者可以替换硬盘的 EFI 系统分区 (ESP) 上的启动管理器（回退启动器），例如 `ESP\\EFI\\Microsoft\\Boot\\bootmgfw.efi` 或 `ESP\\EFI\\BOOT\\bootx64.efi`，在 UEFI 固件将控制权交给操作系统加载器时接管代码执行。

**添加新启动器 (*bootkit.efi*)** 攻击者可以通过修改 BootOrder/Boot#### EFI 变量（决定操作系统启动器顺序的变量）来向已有的启动器列表中添加另一个启动器。

在这些方法中，前两种在本章语境下最具吸引力，因为它们在 UEFI DXE 阶段执行恶意代码；我们将重点研究这两种。其余两种方法虽然与 UEFI 启动过程相关，但侧重于攻击操作系统启动器，并在固件执行完毕后运行恶意代码，故本文不进一步展开。

### 修改未签名的 UEFI 选项 ROM

*Option ROM* 是 PCI/PCIe 扩展固件（ROM）的 x86 代码，位于 PCI 兼容设备上。Option ROM 在启动过程中的加载、配置和执行阶段被加载、配置并执行。John Heasman 首先在 2007 年的 Black Hat 会议上揭示了选项 ROM 作为隐蔽根套件感染入口（参见 `Table 15-1`）。2012 年，黑客 Snare 引入多种技术，包括通过选项 ROM 感染 Apple 笔记本电脑（参见 *[`ho.ax/downloads/De_Mysteriis_Dom_Jobsivs_Black_Hat_Slides.pdf`](http://ho.ax/downloads/De_Mysteriis_Dom_Jobsivs_Black_Hat_Slides.pdf)*）。2015 年的 Black Hat 会议上，Trammell Hudson、Xeno Kovah 和 Corey Kallenberg 展示了名为 *Thunderstrike* 的攻击，该攻击通过修改 Apple 以太网适配器的固件加载恶意代码（参见 *[`www.blackhat.com/docs/us-15/materials/us-15-Hudson-Thunderstrike-2-Sith-Strike.pdf`](https://www.blackhat.com/docs/us-15/materials/us-15-Hudson-Thunderstrike-2-Sith-Strike.pdf)*）。

选项 ROM 包含一个特定的 DXE 驱动程序的 PE 镜像，用于 PCI 设备。在 Intel 的开源 EDK2 套件（参见 *[`github.com/tianocore/edk2/`](https://github.com/tianocore/edk2/)*）中，可以找到加载这些 DXE 驱动的代码；在源码中，`PciBusDxe` 文件夹下的 *PciOptionRomSupport.h* 实现了选项 ROM 加载器。`Listing 15-2` 展示了该代码中的 `LoadOpRomImage()` 函数。

```
EFI_STATUS LoadOpRomImage (

➊ IN PCI_IO_DEVICE *PciDevice,   // PCI 设备实例

➋ IN UINT64 RomBase   // 选项 ROM 的地址

);
```

*Listing 15-2: EDK2 中的 `LoadOpRomImage()` 例程*

可以看到，`LoadOpRomImage()` 函数接受两个参数：一个指向 PCI 设备实例的指针 ➊ 和选项 ROM 的地址 ➋。由此可推断该函数会将 ROM 镜像映射到内存并为其执行做准备。随后，`ProcessOpRomImage()` 函数（`Listing 15-3`）负责进一步处理。

```
EFI_STATUS ProcessOpRomImage (

IN PCI_IO_DEVICE *PciDevice   // Pci 设备实例

);
```

*Listing 15-3: EDK2 中的 `ProcessOpRomImage()` 例程*

`ProcessOpRomImage()` 负责启动包含在选项 ROM 中的特定设备驱动程序的执行过程。Thunderstrike 攻击的创建者利用选项 ROM 作为入口点，通过修改 Thunderbolt 以太网适配器，使其能够连接外部外设。该适配器由 Apple 和 Intel 开发，基于 GN2033 芯片，并提供 Thunderbolt 接口。类似于 Thunderstrike 利用的 Thunderbolt 以太网适配器的拆解版本如图 15-4 所示（参考链接 Figure 15-4）。

![image](img/15fig04.jpg)

*Figure 15-4: A disassembled Apple Thunderbolt Ethernet adapter*

具体来说，Thunderstrike 加载了原始选项 ROM 驱动并添加了额外代码，这些代码在固件启动时未对选项 ROM 的扩展驱动进行身份验证，从而被执行（此攻击在 Apple Macbook 上得到验证，但同样适用于其他硬件）。Apple 通过硬件解决了此问题，但许多其他供应商仍可能受到此类攻击的威胁。

Table 15-1 中列出的许多 BIOS 漏洞已在现代硬件和操作系统中得到修复，例如较新版本的 Windows 默认在硬件和固件支持时启用 Secure Boot。我们将在 `Chapter 17` 中详细讨论 Secure Boot 的实现方法和弱点，但目前只需说明，任何缺乏严格身份验证要求的加载固件或扩展驱动都可能成为安全问题。在现代企业级硬件中，第三方选项 ROM 通常默认被阻止，但可以在 BIOS 管理界面中重新启用，如图 15-5 所示（参考链接 Figure 15-5）。

![image](img/15fig05.jpg)

*Figure 15-5: Blocking third-party Option ROMs in the BIOS management interface*

在 Thunderstrike PoC 发布后，包括 Apple 在内的部分供应商加强了对所有未经签名或第三方选项 ROM 的阻止。我们认为这是正确的政策：加载第三方选项 ROM 的情形非常罕见，阻止第三方设备的所有选项 ROM 能显著降低安全风险。如果你在设备上使用带有选项 ROM 的外设扩展，请确保从与设备同一供应商处购买，随意购买的随机选项 ROM 不值得冒险。

### Adding or Modifying a DXE Driver

让我们来看列表中的第二种攻击方式：在 UEFI 固件映像中添加或修改 DXE 驱动。本质上，这种攻击相当直接：通过修改合法的 DXE 驱动，攻击者可以在预启动环境的 DXE 阶段注入恶意代码。但这类攻击最有趣（也是最复杂）的部分在于，添加或修改 DXE 驱动需要绕过固件、操作系统和用户模式应用程序中存在的复杂漏洞链。

一种修改 UEFI 固件中 DXE 驱动的方法是绕过本章前文提到的 SPI 闪存保护位，利用特权提升漏洞实现。提升权限后，攻击者可以关闭保护位，从而禁用 SPI 闪存保护。

另一种方法是利用 BIOS 更新过程中的漏洞，绕过更新身份验证，直接在 SPI 闪存中写入恶意代码。下面我们来看看这些方法是如何用于在 BIOS 中植入恶意代码的。

> **NOTE**
>
> 这两种方法并非唯一用于修改受保护 SPI 闪存内容的手段，但我们在此聚焦于它们，以展示恶意 BIOS 代码如何在受害者计算机上持久化。更完整的 UEFI 固件漏洞列表请参阅 `Chapter 16`。

## Understanding Rootkit Injection

大多数用户的秘密和攻击者感兴趣的敏感信息存储在操作系统的内核级别，或受到运行在该级别的代码保护。因此，根套件长期致力于 compromise kernel-mode（即“Ring 0”）：从该级别，根套件可以观察所有用户活动或针对特定用户模式（“Ring 3”）应用程序，包括其加载的任何组件。

然而，Ring 0 根套件在一个方面存在劣势：缺乏用户模式上下文。当根套件从内核态查看 Ring 3 应用程序持有的数据时，由于设计上内核态不应感知用户级数据抽象，它无法获得最自然的视图，必须通过某种技巧重构数据，尤其是当数据跨越多个内存页时。因此，内核态根套件常需重用实现用户级抽象的代码。即便如此，由于仅有一层分离，这种代码重用并不算困难。

SMM 增加了另一个更佳的目标，但也引入了与用户级抽象更进一步的分离。SMM 根套件可以通过控制任意物理内存页，同时掌控内核级和用户级内存，但其优势同样是劣势 —— 必须可靠地重实现上层抽象（如虚拟内存），并处理相关复杂性。

好在攻击者可以利用 SMM 根套件以类似 bootkits 的方式在操作系统启动时或之后注入恶意 Ring 0 根套件模块，而非仅在启动阶段。随后，它可以依赖这段代码在内核态上下文中使用内核结构，同时躲避内核级安全工具的检测。关键的是，SMM 代码可以选择注入 implant 的时机。

具体而言，固件植入甚至可以绕过某些 Secure Boot 实现 —— 这在启动时直接植入的 rootkit 无法做到的，因为它会在完整性检查完成后才进行感染。如图 15-6 所示，我们展示了加载 Ring 0 根套件的可能方式演变：从最初的简单方案 —— 使用用户模式（Ring 3）加载器利用漏洞提升权限，安装恶意内核驱动（Ring 0），到后来因 Microsoft kernel-mode signing 政策失效而出现的 bootkit 时代，随后 Secure Boot 被引入以抵御此类威胁，再到 SMM 威胁削弱 Secure Boot 的能力。

![image](img/15fig06.jpg)

*Figure 15-6: Possible ways of loading a Ring 0 rootkit*

截至本文撰写时，SMM 威胁已在大多数 Intel 平台上成功绕过 Secure Boot。SMM 根套件和植入再次将安全边界向更底层的物理硬件靠近。

随着 SMM 威胁的流行，固件取证分析成为一个新兴且极其重要的研究方向。

#### Injecting Malicious Code via SMM Privilege Escalation

要提升权限至 SMM 级以修改 SPI 闪存内容，攻击者必须利用操作系统的回调接口 —— 这些接口由系统管理中断处理程序（SMI handler）处理（详见 `Chapter 16`）。负责硬件与操作系统交互的 SMI 处理程序在 SMM 中执行，因此如果攻击者能够利用 SMM 驱动中的漏洞，就有可能获得 SMM 执行权限。具备 SMM 权限的恶意代码可以禁用 SPI 闪存保护位，并在部分平台上修改或添加 DXE 驱动到 UEFI 固件中。

- 了解此类攻击，我们需要从操作系统层面思考持久性感染的攻击战术。攻击者需要在 SPI 闪存中修改内容吗？[Figure 15-7 描绘了必要的步骤。

![image](img/15fig07.jpg)

*Figure 15-7: 通用的 UEFI 根包感染方案*

如图所示，利用路径相当复杂，涉及多层次的漏洞利用。我们将该过程分解为以下阶段：

**第 1 阶段，用户模式** 客户端漏洞利用，例如浏览器 *远程代码执行 (RCE)*，会在系统上丢弃恶意安装程序。随后，安装程序利用特权提升漏洞获取 **LOCALSYSTEM** 访问权限，并在此新权限下继续执行。

**第 2 阶段，内核模式** 安装程序绕过代码签名策略（详见 第 6 章），在内核模式下执行其代码。内核模式负载（驱动）运行一个漏洞利用，以获取 SMM 特权。

**第 3 阶段，系统管理模式** *SMM 代码* 成功执行后，特权提升至 SMM。*SMM 负载* 关闭 SPI 闪存修改的保护措施。

**第 4 阶段，SPI 闪存** 所有 SPI 闪存保护均已禁用，闪存对任意写入保持开放。*根包/植入体* 随后被安装到固件中写入 SPI 芯片。此漏洞实现了系统极高的持久性。

Figure 15-8 中的通用感染方案实际上展示了一个真实的 SMM 勒索软件 PoC，该 PoC 在 2017 年黑帽亚洲会议上发表。演示文稿名为 “UEFI 固件根包：神话与现实”，我们建议感兴趣的读者阅读（*[`www.blackhat.com/docs/asia-17/materials/asia-17-Matrosov-The-UEFI-Firmware-Rootkits-Myths-And-Reality.pdf`](https://www.blackhat.com/docs/asia-17/materials/asia-17-Matrosov-The-UEFI-Firmware-Rootkits-Myths-And-Reality.pdf)*）。

#### 利用 BIOS 更新进程 (In)Security

另一种在 BIOS 中注入恶意代码的方式是利用 BIOS 更新验证过程。BIOS 更新验证旨在防止未经验证真实性的 BIOS 更新安装，确保仅由平台供应商发布的更新镜像被授权安装。如果攻击者成功利用该验证机制的漏洞，他们可以在更新镜像中注入恶意代码，随后写入 SPI 闪存。
