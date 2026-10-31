
本章的目标是了解安装逆向工程框架 `Cutter` 所涉及的步骤。安装后，我们将分析二进制文件以生成伪代码来提取加密密钥。该加密密钥用于加密二进制文件中的 URL。我们还将看到这种 URL 加密是如何用于逃避逆向工程的。

# Cutter 安装

`Cutter` 可以从 GitHub 仓库下载。它可以从源代码编译，也可以作为二进制文件下载。它适用于不同的平台（Windows、Linux、macOS）。我们将使用 Windows 10 64 位版本来进行 `Cutter` 安装。以下是安装 `Cutter` 的逐步操作流程：

1. 从 GitHub 仓库下载并解压 zip 文件：
   [`https://github.com/rizinorg/cutter/releases/download/v1.12.0/Cutter-v1.12.0-x64.Windows.zip`](https://github.com/rizinorg/cutter/releases/download/v1.12.0/Cutter-v1.12.0-x64.Windows.zip)

2. 在解压后的文件夹中，运行 `cutter.exe` 以打开 `Cutter` 的首屏。这是我们需要选择并打开要分析的二进制文件的屏幕。
   ![](images/Figure-17.1.jpg)
   图 17.1：Cutter 首屏

3. 从以下链接下载此 `CrackMe.exe`：
   [`https://github.com/bpbpublications/Implementing-Reverse-Engineering`](https://github.com/bpbpublications/Implementing-Reverse-Engineering)

4. 选择好要分析的二进制文件后，点击 `Open` 以获取 `Cutter` 的 `Load Options`。我们保持所有设置默认。如果您有符号文件，可以选择 `Load PDB` 选项。
   ![](images/Figure-17.2.jpg)
   图 17.2：Cutter 加载选项

5. 点击 `Ok` 后，您将看到二进制文件的反汇编视图。同时，我们可以看到窗口底部的多个标签页。
   ![](images/Figure-17.3.jpg)
   图 17.3：二进制反汇编视图

6. 至此，我们已成功启动 `Cutter` 进行进一步分析。但在开始分析之前，我们将介绍 `Cutter` 图形用户界面中的不同功能和术语。

# 使用 Cutter 进行二进制分析

`Cutter` 用户界面有许多标签页。我们将逐一介绍每个标签页并解释其在分析任何二进制文件中的相关性。

## Dashboard

`Dashboard` 标签页显示二进制路径、架构、字节序以及许多其他详细信息。我们的二进制文件是可移植可执行文件（`PE`）格式文件，并且按如下方式编译为 32 位架构。`Hashes` 部分中的值用于确保文件未被损坏或被未经授权的用户篡改。一些杀毒软件公司使用这些值来判断文件是否具有恶意性。他们维护已知恶意软件的哈希数据库，并在扫描时评估文件哈希以与数据库中的进行比较。如果哈希值与数据库中的值匹配，则会触发文件感染。
![](images/Figure-17.4.jpg)
图 17.4：Dashboard 视图

## Strings

`Strings` 标签页显示二进制文件中找到的文本字符串。它是任何二进制文件的第一层分析，因为有时它会提供有关二进制内部的许多线索。想象一下，如果某些 IP 地址或 URL 以明文格式用于恶意代码中，那么该 IP 或 URL 将会反映在 `Strings` 标签页中。
![](images/Figure-17.5.jpg)
图 17.5：Strings 视图

## Imports

此标签页显示二进制文件导入的库。如果二进制文件使用互联网连接到某些服务，则可以通过用于连接互联网的相关函数来确定。
![](images/Figure-17.6.jpg)
图 17.6：Imports 视图

## Disassembly

此标签页显示二进制文件的反汇编视图。我们在前几章中学到的概念和指令将帮助我们理解此流程。第一次查看可能会让您感到不知所措，但不用担心，我们将以逐步的方式理解它。
![](images/Figure-17.7.jpg)
图 17.7：反汇编视图

## Graph

如前一图所示，此标签页命名为 Graph（Empty）。后缀 Empty 是因为我们尚未选择任何函数。选择此标签页后，我们会看到一个空屏幕，并显示相同的消息提示选择一个函数。

## Hexdump

这显示了二进制文件的十六进制转储，并由 3 列表示。第一列显示偏移量，第二列显示十六进制输出，第三列是数据的 ASCII 格式表示。
![](images/Figure-17.8.jpg)
图 17.8：Hexdump 视图

## Decompiler

要填充此标签页，我们首先进入 Windows 菜单并选择 `Functions` 以获取二进制文件中的函数列表。在过滤器中，搜索 `main` 函数，因为它是二进制文件的起点。双击 `main` 函数后，反编译器将分析二进制文件以在 `Decompiler` 标签页中显示汇编代码的高级表示。`Cutter` 支持多个反编译器的插件，例如 `RetDec` 和 `Ghidra`。
![](images/Figure-17.9.jpg)
图 17.9：Decompiler 视图

# 解密隐藏的 URL

现在我们将返回到 Graph 部分，该部分显示 `main` 函数的视觉流程图。此图形视图可以使用 `Ctrl++` 或 `Ctrl—` 快捷键进行缩放。我们将以逐步的方式理解执行路径，以了解二进制文件实际在做什么。以下是在 `main` 函数的图形视图中获得的屏幕截图。在图形视图中，我们看到由箭头连接的块。箭头代表不同的跳转，例如 `JMP`、`JGE`、`JE`。绿色箭头显示跳转发生时发生的情况。红色箭头显示如果不发生跳转。蓝色箭头显示循环。
![](images/Figure-17.10.jpg)
图 17.10：main 的导出图形

让我们逐一查看反汇编的代码块以了解代码流程：
![](images/Figure-17.11.jpg)
图 17.11：main 的导出图形-块-1

在函数序言之后，`SUB` 指令通过将 `ESP` 减去 0x3C（十进制 60 字节）为局部变量创建空间。在 `[EBP-0x08]` 处，通过 `XOR` `EAX` 和 `EBP` 存储栈 cookie。在随后的 `MOV` 指令中，文本字符串“`yyy0kke{dgtugewtkv{0eqo`”字符串长度为 24（十进制）被复制到栈上。此文本字符串似乎是某物的加密版本。我们称之为加密文本字符串。在栈上的 60 字节（十进制）中，我们已消耗 24 字节（十进制）用于加密文本字符串和 4 字节用于栈 cookie。栈上剩余的内存位置在 `XOR` `EAX` 指令后使用 `MOV` 指令清除。这以 `JMP` 指令结束块。让我们继续查看块中的剩余指令。
![](images/Figure-17.12.jpg)
图 17.12：main 剩余块的导出图形

我们看到由蓝色箭头表示的循环箭头。它表示 `ECX` 被初始化为 0x32（十进制 50）以使用 `CMP` 和 `JGE` 指令进行循环。右侧的绿色箭头表示 `ECX` 达到十进制 50 的计数。此绿色箭头移动到代码块的末尾。红色箭头表示我们处于循环内部。
