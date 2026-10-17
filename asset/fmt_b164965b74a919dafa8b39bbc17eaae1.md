
在确定 BIOS 区域的位置后，我们可以开始分析。从高层面看，BIOS 区域被组织为 *firmware volumes*，即用于存储数据和代码的基本存储库。固件卷的精确定义见 EFI Firmware Volume Specification [`www.intel.com/content/www/us/en/architecture-and-technology/unified-extensible-firmware-interface/efi-firmware-file-volume-specification.html`](https://www.intel.com/content/www/us/en/architecture-and-technology/unified-extensible-firmware-interface/efi-firmware-file-volume-specification.html)。每个卷都以包含体积属性的头部开始，例如文件系统类型、体积大小以及校验和。

下面我们来查看本次获取的 BIOS 中可用的固件卷。如果在 UEFITool 窗口中双击 BIOS 区域（如 Figure 19-15），则会显示 BIOS 区域内可用的固件卷列表，如 Figure 19-16 所示。

![image](img/19fig16.jpg)

*Figure 19-16: Browsing the firmware volumes available in the BIOS region*

我们的 BIOS 区域包含四个固件卷，并且会发现两个标记为 *Padding* 的区域。Padding 区域不属于任何固件卷，而是卷之间的空白空间，通常填充为 `0x00` 或 `0xff`，具体取决于 SPI flash 的擦除极性。擦除极性决定擦除操作时写入 flash 内存的值：若极性为 1，擦除后的字节为 `0xff`；若极性为 0，擦除后的字节为 `0x00`。因此，当擦除极性为 1 时，Padding 区域（空白空间）由 `0xff` 值组成。

在 Figure 19-16 右侧的信息选项卡中，可查看所选卷的属性。以下是部分重要字段：

**Offset** ➊ 该固件卷相对于 SPI 映像起始地址的偏移

**Signature** ➋ 固件卷头中的签名字段，用于标识 BIOS 区域中的卷

**Filesystem GUID** ➌ 固件卷使用的文件系统标识符，以 Globally Unique Identifier（GUID）形式出现。该 GUID 在 Structure 窗口中显示为卷的名称；如果 GUID 已被文档记录，UEFITool 会显示其人类可读名称（如 Figure 19-16 中的 `EfiFirmwareFileSystemGuid`）

**Header size** ➍ 固件卷头的大小，卷数据位于头部之后

**Body size** ➎ 固件卷体的大小，即卷中存储的数据大小

### 了解文件系统

- 固件体积是以文件系统的形式组织的，其类型在固件头中的文件系统 GUID 中指示。在固件体积中，最常用的文件系统是 `固件文件系统 (FFS)`，它在 EFI FFS 规范中定义，但固件体积也可能使用其他文件系统，例如 FAT32 或 NTFS。我们将重点关注 FFS，因为它是最常见的。

- FFS 将所有文件存储在根目录中，不支持任何目录层次结构。根据 EFI FFS 规范，每个文件都有一个关联的类型，该类型位于该文件的头部，用于描述该文件中存储的数据。以下是一些在取证分析中常见的文件类型列表：

  - `EFI_FV_FILETYPE_RAW`：一个原始文件——对文件中存储的数据不应做任何假设。
  - `EFI_FV_FILETYPE_FIRMWARE_VOLUME_IMAGE`：一个包含封装固件体积的文件。尽管 FFS 没有目录层次结构的概念，我们仍可以通过将固件模块封装在文件中，利用该文件类型创建类似树状结构。
  - `EFI_FV_FILETYPE_SECURITY_CORE`：包含在系统 (SEC) 启动阶段执行的代码和数据的文件。SEC 阶段是 UEFI 启动过程的第一阶段。
  - `EFI_FV_FILETYPE_PEI_CORE`：一个可执行文件，用于启动预系统初始化 (PEI) 阶段。PEI 阶段紧随 SEC 阶段之后。
  - `EFI_FV_FILETYPE_PEIM`：PEI 模块文件，包含在 PEI 阶段执行的代码和数据。
  - `EFI_FV_FILETYPE_DXE_CORE`：一个可执行文件，用于启动 `Driver Execution Environment` (`DXE`) 阶段。DXE 阶段紧随 PEI 阶段。
  - `EFI_FV_FILETYPE_DRIVER`：在 DXE 阶段启动的可执行文件。
  - `EFI_FV_FILETYPE_COMBINED_PEIM_DRIVER`：包含可在 PEI 和 DXE 阶段均可执行的代码和数据的文件。
  - `EFI_FV_FILETYPE_APPLICATION`：一个 UEFI 应用，是可在 DXE 阶段启动的可执行文件。
  - `EFI_FV_FILETYPE_FFS_PAD`：一个填充文件。

- 与操作系统常用的文件系统不同，FFS 文件不使用人类可读的文件名，而是通过 GUID 进行标识。

### 了解文件段

大多数存储在 FFS 中的固件文件由一个或多个离散部分组成，称为 `段`（尽管某些文件，如 `EFI_FV_FILETYPE_RAW` 文件，不包含任何段）。

段分为两类：叶片段和封装段。`叶片段` 直接包含数据，其类型由段头中的段类型属性决定。`封装段` 包含文件段，文件段可能包含叶片段或嵌套封装段。这意味着一个封装段可以包含另一个封装段。

下面的列表描述了一些常见的叶片段类型：

- `EFI_SECTION_PE32`：包含 PE 映像。
- `EFI_SECTION_PIC`：包含位置独立代码 (PIC)。
- `EFI_SECTION_TE`：包含 terse 可执行 (TE) 映像。
- `EFI_SECTION_USER_INTERFACE`：包含用户界面字符串，通常用于存储文件的人类可读名称，以及文件 GUID。
- `EFI_SECTION_FIRMWARE_VOLUME_IMAGE`：包含封装的固件映像。

下面是 FFS 规范中定义的几种封装段：

- `EFI_SECTION_COMPRESSION`：包含压缩的文件段。
- `EFI_SECTION_GUID_DEFINED`：根据由段 GUID 标识的算法对其他段进行封装。该类型用于签名段，例如。

这些对象构成了现代平台上 UEFI 固件的内容。取证分析师必须考虑固件中的每一个组件，无论是包含可执行代码（如 `PE32`、`TE` 或 `PIC`）的段，还是包含非易失性变量的数据文件。

为了更好地理解这些概念，请参阅 Figure 19-17，该图展示了 `CpuInitDxe` 驱动在固件体积中的位置。该驱动负责在 DXE 阶段初始化 CPU。我们将从下往上遍历 FFS 层次结构，以描述其在固件映像中的位置。

![image](img/19fig17.jpg)

*Figure 19-17: The location of the CpuInitDxe driver in the BIOS region*

驱动的可执行映像位于 `PE32` 图像段 ➐。该段以及包含驱动名称 ➑、版本 ➒ 和依赖项 ➏ 的其他段，都位于 GUID 为 `{62D171CB-78CD-4480-8678-C6A2A797A8DE}` 的文件 ➎ 中。该文件属于封装的固件体积 ➎n。压缩段位于固件体积类型为 `{9E21FD93-9C72-4C15-8C4B-E77F1DB2D792}` 的文件 ➋ 中，该文件存储在顶层固件体积 ➊ 中。

此示例主要用于展示构成 UEFI 固件的对象层次结构，但这只是一种解析方式。

现在我们已经了解了 BIOS 区域的组织方式，接下来能够在其层次结构中导航并查找 BIOS 固件中存储的各种对象。

## 使用 Chipsec 分析固件映像

本节将讨论使用平台安全评估框架 Chipsec（[`github.com/chipsec/`](https://github.com/chipsec/)，如第 15 章所述）进行固件取证分析。本节将深入探讨工具的架构，并提供一些示例，展示 Chipsec 的功能和实用性。

该工具提供多种访问平台硬件资源的接口，如物理内存、PCI 寄存器、NVRAM 变量和 SPI 闪存。这些接口对取证分析师非常有用，后面将更深入地介绍它们。

请遵循 Chipsec 手册（[`github.com/chipsec/chipsec/blob/master/chipsec-manual.pdf`](https://github.com/chipsec/chipsec/blob/master/chipsec-manual.pdf)）中的安装指南进行安装和配置。手册还涵盖了大量功能，但本节仅聚焦于 Chipsec 的取证分析能力。

### 了解 Chipsec 架构

Figure 19-18 展示了工具的高层架构。

![image](img/19fig18.jpg)

*Figure 19-18: The Chipsec tool’s architecture*

最底层是提供对系统资源访问的模块，例如内存映射 I/O 地址范围、PCI 配置空间寄存器以及物理内存。这些模块是平台依赖的，实现为内核模式驱动和 EFI 原生代码。（目前，Chipsec 为 Windows、Linux 和 macOS 提供内核模式驱动。）

大多数模块使用 C 语言编写，旨在在内核模式或 EFI Shell 环境中运行。

> **NOTE**
>
> UEFI Shell 是一个提供命令行界面的 UEFI 应用，用于固件交互，允许我们启动 UEFI 应用并执行命令。我们可以使用 UEFI Shell 检索平台信息、查看和修改启动管理器变量、加载 UEFI 驱动等。

在低层 OS 依赖组件之上，有一个 OS 无关的抽象层，称为 OS Helper，包含多个模块，用于隐藏与内核组件通信的 OS 特定 API，供应用层使用。这些模块实现于 Python。

OS Helper 模块位于底层，与内核组件通信；位于顶层，为硬件抽象层 (HAL) 提供 OS 无关的接口。

The HAL further abstracts the platform’s low-level concepts, like the PCI configuration registers and model-specific registers (MSRs), and it provides an interface for the Chipsec components located at the levels immediately above it: `Chipsec Main` and `Chipsec Util`. The HAL is also written in Python and relies on OSHelper to access the platform-specific hardware resources.

The two remaining components, located at the top of the architecture, provide the main functionality available to users. The first interface, Chipsec Main, is available through the `chipsec_main.py` Python script in the tool’s root folder. It allows us to execute tests that check the security configuration of certain platform aspects, run PoCs to test for the presence of vulnerabilities in system firmware, and more. The second interface, Chipsec Util, is available through the `chipsec_util.py` script. We can use it to run individual commands and access platform hardware resources to read the SPI flash image, dump the UEFI NVRAM variables, and so on.

We’re primarily interested in the Chipsec Util interface because it provides rich functionality for working with UEFI firmware.

### 使用 Chipsec Util 分析固件

You can find out the commands provided by Chipsec Util by running the `chipsec_util.py` script, located in the root directory of the tool’s repository, without specifying any arguments. Generally, commands are grouped into modules based on the platform hardware resources they work with. Here are some of the most useful modules:

- **acpi**：Implements commands for working with *Advanced Configuration and Power Interface* tables.
- **cpu**：Implements commands related to the CPU, such as reading configuration registers and obtaining information about the CPU.
- **spi**：Implements a number of commands for working with the SPI flash, like reading, writing, and erasing data. There is also an option for disabling BIOS write protection on systems with unlocked write protection (as discussed in Chapter 16).
- **uefi**：Implements commands for parsing UEFI firmware (the SPI flash BIOS region) to extract executables, NVRAM variables, and the like.

We can run `chipsec_util.py command_name`, where `command_name` is the name of the command we want to learn about, to output a description and usage information for that command. For instance, Listing 19-2 displays the output of `chipsec_util.py spi`.
