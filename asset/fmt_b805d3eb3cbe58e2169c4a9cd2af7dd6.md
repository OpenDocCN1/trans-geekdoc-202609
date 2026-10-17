
Table 14-2 列出了 GPT 头中所包含值的描述。

**表 14-2:** GPT 头

| **名称** | **偏移量** | **长度** |
| --- | --- | --- |
| 签名 “EFI PART” | 0x00 | 8 字节 |
| 适用于 GPT 版本的修订 | 0x08 | 4 字节 |
| 头大小 | 0x0C | 4 字节 |
| 头 CRC32 | 0x10 | 4 字节 |
| 保留 | 0x14 | 4 字节 |
| 当前 LBA（逻辑块寻址） | 0x18 | 8 字节 |
| 备份 LBA | 0x20 | 8 字节 |
| 分区表可用的第一个 LBA | 0x28 | 8 字节 |
| 最后可用 LBA | 0x30 | 8 字节 |
| 磁盘 GUID | 0x38 | 16 字节 |
| 分区条目数组的起始 LBA | 0x48 | 8 字节 |
| 分区条目数组中的条目数量 | 0x50 | 4 字节 |
| 单个分区条目的大小 | 0x54 | 4 字节 |
| 分区条目数组的 CRC32 | 0x58 | 4 字节 |
| 保留 | 0x5C | * |

如上所示，GPT 头仅包含常数字段，而非代码。从取证角度来看，最重要的字段是 `分区条目数组的起始 LBA` 和 `分区条目数组中的条目数量`，它们分别定义分区表在硬盘上的位置和大小。

GPT 头中的另一个有趣的字段是 `备份 LBA`，它提供了 GPT 头备份副本的位置。这在主 GPT 头损坏时可用于恢复主 GPT 头。我们在讨论 Petya 勒索软件时（第 13 章），提到了备份 GPT 头，因为 Petya 同时加密了主备份 GPT 头，使得系统恢复更加困难。

如图 14-4 所示，分区表中的每一项都提供了硬盘上分区属性和位置的信息。

![image](img/14fig04.jpg)

*图 14-4: GUID 分区表*

两个 64 位字段 `First LBA` 和 `Last LBA` 分别定义分区的第一个和最后一个扇区的地址。`分区类型 GUID` 字段包含一个 GUID 值，用于标识分区类型。例如，前文提到的 EFI 系统分区的类型为 `C12A7328-F81F-11D2-BA4B-00A0C93EC93B`。

GPT 方案中不存在任何可执行代码，这为引导程序感染带来了问题：在 GPT 方案中，恶意软件开发者如何将控制权转移到其恶意代码中？一个思路是修改 EFI 引导加载程序，使其在转移控制权给操作系统内核之前执行恶意代码。在此之前，我们先了解一下 UEFI 固件架构和启动过程的基本概念。

### UEFI 固件的工作原理

在了解完 GPT 分区方案后，我们现在知道操作系统引导加载程序的位置以及 UEFI 固件如何在硬盘上找到它。接下来，我们来看 UEFI 固件如何加载并执行操作系统加载程序。我们将按顺序介绍 UEFI 启动过程的各个阶段，以准备执行加载程序的环境。

UEFI 固件会解释 GPT 表中的数据结构，以定位操作系统加载程序，该固件存储在主板的闪存芯片中（也称为 `SPI 闪存`，其中 “SPI” 指的是连接芯片与芯片组其余部分的总线接口）。系统启动时，芯片组逻辑会将闪存芯片的内容映射到特定的 RAM 区域，其起始和结束地址由硬件芯片组本身配置，并取决于 CPU 具体配置。一旦映射到的 SPI 闪存芯片代码在通电后获得控制权，它会初始化硬件并加载各种驱动、操作系统启动管理器、操作系统加载程序，最后加载操作系统内核本身。该序列的步骤可以概括为：

1. UEFI 固件执行平台初始化，完成 CPU 和芯片组初始化，并加载 UEFI 平台模块（即 UEFI 驱动；这些模块与后续加载的设备特定代码不同）。
2. UEFI 启动管理器枚举外部总线上的设备（如 PCI 总线），加载 UEFI 设备驱动，然后加载启动应用。
3. Windows 启动管理器（`bootmgfw.efi`）加载 Windows 启动加载程序。
4. Windows 启动加载程序（`winload.efi`）加载 Windows 操作系统。

负责步骤 1 和 2 的代码位于 SPI 闪存；负责步骤 3 和 4 的代码则从硬盘的特殊 UEFI 分区的文件系统中提取，仅在步骤 1 和 2 完成后才能读取硬盘。

UEFI 规范将固件进一步划分为负责硬件初始化或启动过程不同部分的组件，如图 14-5 所示。

操作系统加载程序本质上依赖于 UEFI 固件提供的 EFI 启动服务和 EFI 运行服务来启动并管理系统。我们将在“操作系统加载程序内部”的第 245 页进一步说明，加载程序利用这些服务建立一个能够加载操作系统内核的环境。当操作系统加载程序接管启动流程后，启动服务即被移除，不再对操作系统可用。然而，运行服务在操作系统运行时仍然可用，并提供读取/写入 NVRAM UEFI 变量、通过 `Capsule Update` 进行固件更新以及重启或关闭系统的接口。

![image](img/14fig05.jpg)

*图 14-5: UEFI 框架概览*

#### 固件胶囊更新

`Capsule Update` 是一种用于安全更新 UEFI 固件的技术。操作系统将胶囊固件更新镜像加载到内存中，并通过运行时服务向 UEFI 固件发出胶囊已存在的信号。因此，UEFI 固件在下次启动时重新启动系统并处理更新胶囊。`Capsule Update` 旨在标准化并改进 UEFI 固件更新过程的安全性。我们将在第 15 章中更深入地讨论它。

#### The UEFI Specification

与传统 BIOS 启动不同，UEFI 规范覆盖了从硬件初始化开始的每一个步骤。在此之前，硬件厂商在固件开发过程中拥有更大的自由度，但这种自由度也导致了混乱和漏洞。规范列出了引导过程的四个主要连续阶段，每个阶段都有其各自的责任：

**Security (SEC)** 初始化使用 CPU 缓存的临时内存并定位 PEI 阶段的加载器。SEC 阶段执行的代码从 SPI 闪存中运行。

**Pre-EFI Initialization (PEI)** 配置内存控制器，初始化芯片组，并处理 S3 休眠恢复过程。PEI 阶段执行的代码在内存控制器初始化之前运行于临时内存中，完成后会从永久内存中执行。

**Driver Execution Environment (DXE)** 初始化系统管理模式 (SMM) 与 DXE 服务（核心、分发器、驱动等），以及启动和运行时服务。

**Boot Device Selection (BDS)** 发现操作系统可从中启动的硬件设备，例如通过枚举 PCI 巴士上的外设，这些外设可能包含兼容 UEFI 的启动加载器（如操作系统加载器）。

启动过程中使用的所有组件均位于 SPI 闪存中，除了操作系统加载器，它位于磁盘文件系统中，由 SPI 闪存基于的 DXE/BDS 阶段代码通过存储在 NVRAM UEFI 变量中的文件系统路径找到（如前所述）。

SMM 与 DXE 初始化阶段是植入根套件的最有趣的区域。SMM 在环 –2，是最受信任的系统模式——比环 –1 的超级盾更受信任。从该模式，恶意代码可以完全控制系统。

同样，DXE 驱动为实现引导套件功能提供了另一个强大的入口点。Hacking Team 的固件根套件实现就是 DXE 驱动的一个典型例子，详见第 15 章。

**SYSTEM MANAGEMENT MODE**

System Management Mode 是 x86 CPU 的一种特殊模式，以特殊的更高“环 –2”特权（即“减二”）执行，这比“环 –1”更低且更有权力，而“环 0”则是历史上最受信任的特权（不是吗？）。SMM 最初在 Intel 386 处理器中引入，主要用于电源管理，但现代 CPU 的复杂度和重要性已大幅提升。SMM 如今是固件的组成部分，负责启动过程中的所有初始化和内存分离设置。SMM 的代码运行在与正常操作系统地址空间（包括 OS 内核空间）隔离的独立地址空间中。我们将在第 15 章和第 16 章中进一步探讨 UEFI 根套件如何利用 SMM。

我们现在来探讨最后一个阶段以及操作系统内核获得控制的过程。我们将在下一章更详细地讨论 DXE 与 SMM。

#### Inside the Operating System Loader

当 SPI 存储的 UEFI 固件代码完成工作后，它将控制权交给存储在磁盘上的操作系统加载器。加载器代码是 64 位或 32 位（取决于操作系统版本），启动过程不再包含 MBR 或 VBR 的 16 位加载器代码。

操作系统加载器由多个文件组成，存放在 EFI 系统分区中，包括 `bootmgfw.efi` 与 `winload.efi` 两个模块。前者被称为 *Windows Boot Manager*，后者称为 *Windows Boot Loader*。这些模块的位置也由 NVRAM 变量指定。特别是，UEFI 路径变量（由 UEFI 标准定义的端口和总线枚举方式决定）指示包含 ESP 的磁盘路径，存储在启动顺序 NVRAM 变量 `BOOT_ORDER`（用户通常可以通过 BIOS 配置修改）；ESP 文件系统内的路径则存储在另一个变量 `BOOT`（通常为 `\\EFI\\Microsoft\\Boot\\`）。

##### Accessing the Windows Boot Manager

UEFI 固件启动管理器查询 NVRAM UEFI 变量以找到 ESP，然后在 Windows 情况下，查找其中的 OS 专用启动管理器 `bootmgfw.efi`。启动管理器随后在内存中创建该文件的运行时镜像。为此，它依赖于 UEFI 固件读取启动硬盘并解析其文件系统。在其他操作系统下，NVRAM 变量会包含相应 OS 加载器的路径，例如 Linux 指向 GRUB 启动加载器 (`grub.efi`)。

当 `bootmgfw.efi` 加载完成后，UEFI 固件启动管理器跳转到 `bootmgfw.efi` 的入口点 `EfiEntry`。此时，SPI 闪存中存储的固件将控制权交给硬盘上的代码。

##### Establishing an Execution Environment

`EfiEntry` 的原型如 Listing 14-2 所示，它调用 Windows Boot Manager `bootmgfw.efi`，并用于配置 UEFI 固件回调，以便在 `winload.efi`（Windows Boot Loader）之后被调用。这些回调将 `winload.efi` 代码与 UEFI 运行时服务关联，用于对外设（如硬盘）进行操作。这些服务在 Windows 完全加载后仍会通过硬件抽象层（HAL）包装继续使用，我们稍后会看到它们的设置过程。

```
EFI_STATUS EfiEntry (
    EFI_HANDLE ImageHandle,      // UEFI image handle for loaded application
    EFI_SYSTEM_TABLE *SystemTable // Pointer to UEFI system table
);
```

*Listing 14-2: Prototype of the EfiEntry routine (EFI_IMAGE_ENTRY_POINT)*

`EfiEntry` 的第一个参数 ➊ 指向负责继续启动过程并调用 `winload.efi` 的 `bootmgfw.efi` 模块。第二个参数 ➋ 包含指向 UEFI 配置表（`EFI_SYSTEM_TABLE`）的指针，这是访问大多数 EFI 环境服务配置数据的关键（Figure 14-6）。

![image](img/14fig06.jpg)

*Figure 14-6: EFI_SYSTEM_TABLE high-level structure*

`winload.efi` 加载器使用 UEFI 服务加载操作系统内核，并通过启动设备驱动堆栈初始化 `EFI_RUNTIME_TABLE`，以便内核通过 HAL 库模块 (`hal.dll`) 在未来访问。`hal.dll` consumes the `EFI_SYSTEM_TABLE` 并导出包装 UEFI 运行时函数的函数，供内核调用，例如读取 NVRAM 变量和通过 `Capsule Update` 向 UEFI 固件提交固件更新。

请注意，多层包装的模式在启动过程中由每一层 progressively 配置的 UEFI 硬件特定代码实现。一次系统调用可能会跨越 UEFI 的“兔子洞”多深！

`hal.dll` 中使用的 `EFI_RUNTIME_SERVICES` 结构体在 Figure 14-7 中有所表示。

![image](img/14fig07.jpg)

*Figure 14-7: EFI_RUNTIME_SERVICES in* `hal.dll`*’s representation*

`HalEfiRuntimeServiceTable` holds a pointer to `EFI_RUNTIME_SERVICES`, which in turn contains the addresses of entry points of service routines that will do things like get or set the NVRAM variable, perform a `Capsule Update`, and so on.

In the next chapters, we’ll analyze these structures in the context of firmware vulnerabilities, exploitation, and rootkits. For now, we simply want to stress that `EFI_SYSTEM_TABLE` and (especially) `EFI_RUNTIME_SERVICES` within it are the keys to finding the structures responsible for accessing UEFI configuration information and that some of this information is accessible from the kernel mode of the operating system.

Figure 14-8 shows the disassembled `EfiEntry` routine. One of its first instructions triggers a call to the function `EfiInitCreateInputParametersEx()`, which converts the `EfiEntry` parameters to the format expected by `bootmgfw.efi`. Inside `EfiInitCreateInputParametersEx()`, a routine called `EfiInitpCreateApplicationEntry()` creates an entry for the `bootmgfw.efi` in the Boot Configuration Data (BCD), a binary storage of configuration parameters for a Windows bootloader. After `EfiInitCreateInputParametersEx()` returns, the `BmMain` routine (highlighted in Figure 14-8) receives control. Note that at this point, to properly access hardware device operations, including any hard drive input and output, and to initialize memory, the Windows Boot Manager must use only EFI services, as the main Windows driver stacks are not yet loaded and thus are unavailable.

![image](img/14fig08.jpg)

*Figure 14-8: Disassembled EfiEntry routine*

##### Reading the Boot Configuration Data

As the next step, `BmMain` calls the following routines:

`BmFwInitializeBootDirectoryPath` Routine used to initialize the boot application’s path (`\\EFI\\Microsoft\\Boot`)

`BmOpenDataStore` Routine used to mount and read the BCD database file (`\\EFI\\Microsoft\\Boot\\BCD`) via UEFI services (disk I/O)

`BmpLaunchBootEntry` **and** `ImgArchEfiStartBootApplication` Routines used to execute boot application (`winload.efi`)

Listing 14-3 shows Boot Configuration Data as output by the standard command line tool `bcdedit.exe`, which is included in all recent versions of Microsoft Windows. The paths to the Windows Boot Manager and Windows Boot Loader modules are marked with ➊ and ➋ respectively.

```
PS C:\WINDOWS\system32> bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
➊ path                  \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {c68c4e64-6159-11e8-8512-a4c49440f67c}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
➋ path                  \WINDOWS\system32\winload.efi
description             Windows 10
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {f5b4c688-6159-11e8-81bd-8aecff577cb6}
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \WINDOWS
resumeobject            {c68c4e64-6159-11e8-8512-a4c49440f67c}
nx                      OptIn
bootmenupolicy          Standard
```

*Listing 14-3: Output from the bcdedit console command*

The Windows Boot Manager (`bootmgfw.efi`) is also responsible for the boot policy verification and for the initialization of the Code Integrity and Secure Boot components, covered in the following chapters.

At the next stage of the boot process, `bootmgfw.efi` loads and verifies the Windows Boot Loader (`winload.efi`). Before starting to load `winload.efi`, the Windows Boot Manager initializes the memory map for transition to the protected memory mode, which provides both virtual memory and paging. Importantly, it performs this setup via UEFI runtime services rather than directly. This creates a strong layer of abstraction for the OS virtual memory data structures, such as the GDT, which were previously handled by a legacy BIOS in 16-bit assembly code.

##### Transferring Control to Winload

In the final stage of the Windows Boot Manager, the `BmpLaunchBootEntry()` routine loads and executes `winload.efi`, the Windows Boot Loader. Figure 14-9 presents the complete call graph from `EfiEntry()` to `BmpLaunchBootEntry()`, as generated by the Hex-Rays IDA Pro disassembler with the IDAPathFinder script ([`www.devttys0.com/tools/`](http://www.devttys0.com/tools/)).

![image](img/14fig09.jpg)

*Figure 14-9: Call graph flow from EfiEntry() to BmpLaunchBootEntry()*

The control flow preceding the `BmpLaunchBootEntry()` function chooses the right boot entry, based on the values from the BCD store. If Full Volume Encryption (BitLocker) is enabled, the Boot Manager decrypts the system partition before it can transfer control to the Boot Loader. The `BmpLaunchBootEntry()` function followed by `BmpTransferExecution()` checks the boot options and passes execution to `BlImgLoadBootApplication()`, which then calls `ImgArchEfiStartBootApplication()`. The `ImgArchEfiStartBootApplication()` routine is responsible for initializing the protected memory mode for `winload.efi`. After that, control is passed to the function `Archpx64TransferTo64BitApplicationAsm()`, which finalizes the preparation for starting `winload.efi` (Figure 14-10).

![image](img/14fig10.jpg)

*Figure 14-10: Call graph flow from BmpLaunchBootEntry() to Archpx64TransferTo64BitApplicationAsm()*

After this crucial point, all execution flow is transferred to `winload.efi`, which is responsible for loading and initializing the Windows kernel. Prior to this moment, execution happens in the UEFI environment over boot services and operates under the flat physical memory model.

**NOTE**

*If Secure Boot is disabled, malicious code can make any memory modifications at this stage of the boot process, because kernel-mode modules are not yet protected by the Windows Kernel Patch Protection (KPP) technology (also known as PatchGuard). PatchGuard will initialize only in the later steps of the boot process. Once PatchGuard is activated, though, it will make malicious modifications of kernel modules much harder.*

#### The Windows Boot Loader

The Windows Boot Loader performs the following configuration actions:

*   Initializes the kernel debugger if the OS boots in debug mode (including the hypervisor debug mode).
*   Wraps UEFI Boot Services into HAL abstractions for later use by the Windows kernel-mode code and calls Exit Boot Services.
*   Checks the CPU for the Hyper-V hypervisor support features and sets them up if supported.
*   Checks for Virtual Secure Mode (VSM) and DeviceGuard policies (Windows 10 only).
*   Runs integrity checks on the kernel itself and on the Windows components, then transfers control to the kernel.

The Windows Boot Loader starts execution from the `OslMain()` routine, as shown in Listing 14-4, which performs all the previously described actions.

```
__int64 __fastcall OslpMain(__int64 a1)
{
    __int64 v1; // rbx@1
    unsigned int v2; // eax@3
    __int64 v3; //rdx@3
    __int64 v4; //rcx@3
    __int64 v5; //r8@3
    __int64 v6; //rbx@5
    unsigned int v7; // eax@7
    __int64 v8; //rdx@7
    __int64 v9; //rcx@7
    __int64 v10; //rdx@9
    __int64 v11; //rcx@9
    unsigned int v12; // eax@10
    char v14; // [rsp+20h] [rbp-18h]@1
    int v15; // [rsp+2Ch] [rbp-Ch]@1
    char v16; // [rsp+48h] [rbp+10h]@3
    v1 = a1;
    BlArchCpuId(0x80000001, 0i64, &v14);
    if ( !(v15 & 0x100000) )
        BlArchGetCpuVendor();
    v2 = OslPrepareTarget (v1, &v16);
    LODWORD(v5) = v2;
    if ( (v2 & 0x80000000) == 0 && v16 )
    {
        v6 = OslLoaderBlock;
        if ( !BdDebugAfterExitBootServices )
            BlBdStop(v4, v3, v2);
        ➊ v7 = OslFwpKernelSetupPhase1(v6);
        LODWORD(v5) = v7;
        if ( (v7 & 0x80000000) == 0 )
        {
            ArchRestoreProcessorFeatures(v9, v8, v7);
            OslArchHypervisorSetup(1i64, v6);
        ➋ LODWORD(v5) = BlVsmCheckSystemPolicy(1i64);
            if ( (signed int)v5 >= 0 )
            {
                if ( (signed int)OslVsmSetup(1i64, 0xFFFFFFFFi64, v6) >= 0
        ➌ || (v12 = BlVsmCheckSystemPolicy(2i64), v5 = v12, (v12 & 0x80000000) == 0 ) )
                {
                    BlBdStop(v11, v10, v5);
            ➍ OslArchTransferToKernel(v6, OslEntryPoint);
                    while ( 1 )
                        ;
                }
            }
        }
    }
}
```

*Listing 14-4: The decompiled OslMain() function (Windows 10)*

The Windows Boot Loader starts with configuring the kernel memory address space by calling the `OslBuildKernelMemoryMap()` function (Figure 14-11). Next, it prepares for loading the kernel with the call to the `OslFwpKernelSetupPhase1()` function ➊. The `OslFwpKernelSetupPhase1()` function calls `EfiGetMemoryMap()` to get the pointer to the `EFI_BOOT_SERVICE` structure configured earlier, and then stores it in a global variable for future operations from kernel mode, via the HAL services.

![image](img/14fig11.jpg)

*Figure 14-11: Call graph flow from OslMain() to OslBuildKernelMemoryMap()*

After that, the `OslFwpKernelSetupPhase1()` routine calls the EFI function `ExitBootServices()`. This function notifies the operating system that it is about to receive full control; this callback allows for making any last-minute configurations before jumping into the kernel.

The VSM boot policy checks are implemented in the routine `BlVsmCheckSystemPolicy` ➋ ➌, which checks the environment against the Secure Boot policy and reads the UEFI variable `VbsPolicy` into memory, filling the `BlVsmpSystemPolicy` structure in memory.

Finally, execution flow reaches the operating system kernel (which in our case is the `ntoskrnl.exe` image) ➍ via `OslArchTransferToKernel()` (Listing 14-5).
