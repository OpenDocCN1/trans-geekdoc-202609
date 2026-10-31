
类似地，计算机也被编程为基于条件做出决策。C/C++ 编程也提供了决策语句，帮助程序员编写涉及基于条件决策的代码。不同的条件与结果相连，以自然的方式表现。本章将帮助你从逆向工程的角度理解这些条件在组装列表中的模式。

# [结构](#toc.xhtml#s199a)

本章将涵盖以下主题：

* If-else 语句
* 未优化的 If-else 语句
* 带优化的 If-else 语句

## [目标](#toc.xhtml#s200a)

本章的目标是理解程序流程中用于决策的汇编指令的概念。我们将在汇编代码中学习 `CMP` 和 `Jump` 指令。正如我们在日常生活中为一个问题做出多个决策一样，为了处理汇编中的问题或条件，我们在汇编中有 `CMP` 和 `jump` 指令。我们还将理解决策控制结构的优化与非优化汇编代码之间的差异。

## [If-else 语句](#toc.xhtml#s201a)

在本节中，我们将介绍带有 if-else 语句的简单 C/C++ 代码，其中我们将要求用户输入两个整数。如果两个数字相等，则在控制台上打印出两个数字相等的信息。但如果输入的两个数字不相等，代码将使用 else 语句打印数字不相等。此代码还包括我们的 C/C++ 代码中的 `scanf` 和 `printf`。建议阅读 *[第 7 章，Printf 程序的逆向工程模式](#c07.xhtml)*，以便更好地理解。

![](images/Figure-9.1.jpg)

**图 9.1：** `ifelse.cpp`

## [未优化的 If-else 语句](#toc.xhtml#s202a)

在同一台 x86 Windows 机器上，使用 MSVC 编译器在不进行优化的情况下编译代码。在 Windows 命令提示符上运行以下命令以设置 `cl.exe`（VS 编译器）的环境，然后使用以下开关编译代码：

* `/Fa`：输出汇编列表文件名
* `/Fe`：输出可执行文件名

| `cd C:\Program Files\Microsoft Visual Studio 10.0\VC` `vcvarsall.bat` `^` `cd C:\JitenderN\REBook\ifelse\ifelse` `^` `cl ifelse.cpp /Faifelse.asm /Feifelse.exe` |
| --- |

运行前述命令的输出如下：

![](images/Figure-9.2.jpg)

**图 9.2：** If-else 语句未优化

这将生成汇编代码和 EXE 文件。为分析目的，我们将禁用 **地址空间布局随机化** (**ASLR**)。这是一种安全机制，通过它使用我们的 MSVC 编译器生成的 **可移植可执行** (**PE**) 文件在每次加载时其基地址都会随机化。要禁用 ASLR，请使用 `CFF explorer` 遵循相同的步骤并更改 `DllCharacteristics` 参数以取消选中 **DLL 可移动**。有关更多详细信息，请参阅附录。

现在，让我们继续查看生成的汇编列表：

![](images/Figure-9.3.jpg)

**图 9.3：** `ifelse.asm-Part-1`

![](images/Figure-9.4.jpg)

**图 9.4：** `ifelse.asm-Part-2`

让我们逐行浏览汇编代码。正如我们在前几章中讨论了大部分初始汇编列表，我们将从 `main` 过程的开始处继续指令。

▼**行 34-37**

`; Line 7`

`push ebp`

`mov ebp, esp`

`sub esp, 8`

它以 `main` 函数序言开始。使用 `SUB` 指令，我们为 `main` 的局部变量创建空间，这些变量是 `iNumber1` 和 `iNumber2`。每个数字将占用 4 字节空间，总共 8 字节。

为了分析栈状态，让我们在 `x32dbg` 中打开生成的 PE 文件，并在 `main` 过程的开始处设置断点。我们将逐步进入代码以查看 `SUB` 指令后的栈状态。

`[ESP] 0012FF38 004038DD [EBP-8] now JUNK, Input placeholder for iNumber1`

`[ESP+0x4] 0012FF3C 0040445A [EBP-4] now JUNK, Input placeholder for iNumber2`

`[ESP+0x8] 0012FF40 0012FF88 [EBP]`

`[ESP+0xC] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000`

可以使用 `_iNumber1$` 宏访问 `iNumber1`，其等于 -8。因此，`iNumber1` 可以通过将 `EBP` 与 `_iNumber1$` 宏相加来访问，等于 `[EBP-8].`

![](images/Figure-9.5.jpg)

**图 9.5：** 为我们的局部变量创建空间

▼**行 38-41**

`; Line 10`

`push OFFSET $SG4679`

`call _printf`

`add esp, 4`

第 10 行的 C/C++ 代码在控制台上打印字符串：

`printf("Input Number1 : ");`

在我们的汇编代码中，`printf` 函数的参数首先被压入栈。`printf` 的参数是一个存储在 `.rdata` 段中的字符串常量，内部定义为 `$SG4679`。对 `printf` 的调用将在控制台上打印 `$SG4679`，而调用 `printf` 后的 `ADD` 指令通过 4 字节清理栈。

`[ESP-0x4] 0012FF34 0040A140 "Input Number1 : ", parameter to 1st printf()`

`[ESP] 0012FF38 004038DD [EBP-8] now JUNK, Input placeholder for iNumber1`

`[ESP+0x4] 0012FF3C 0040445A [EBP-4] now JUNK, Input placeholder for iNumber2`

`[ESP+0x8] 0012FF40 0012FF88 [EBP]`

`[ESP+0xC] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000`

![](images/Figure-9.6.jpg)

**图 9.6：** 调用 printf

▼**行 42-47**

`; Line 11`

`lea eax, DWORD PTR _iNumber1$[ebp]`

`push eax`

`push OFFSET $SG4680`

`call _scanf`

`add esp, 8`

第 11 行的 C/C++ 代码从用户处获取输入整数并将其存储在 `&iNumber1` 内存位置：

`scanf("%d", &iNumber1);`

在我们的汇编代码中，`LEA` 将有效地将 `_iNumber1$[ebp]` 的地址，即 `0x0012FF38`，加载到 `EAX` 寄存器中。将 `EAX` 加载 `_iNumber1$[ebp]` 地址的目的是将 `EAX` 寄存器与字符串常量 `$SG4680` 一起压入栈。地址（`0x0012FF38`）和字符串 `$SG4680` 都是 `scanf` 函数的参数。

要检查 `scanf` 函数调用后的栈状态，请在 `scanf` 调用后的 `ADD` 指令处设置另一个断点。现在逐条逐步进入指令，并在调用 `scanf` 时执行一步跳过。它将在控制台上提示你输入第一个数字。我们将输入数字 7 并按 *ENTER*。按 *ENTER* 后，数字 7 将保存在栈上 `iNumber1` 内存位置的输入占位符处，`0x0012FF38`。使用 `scanf` 调用，用户输入的数字将保存在栈上。调用后，是时候再次使用 `ADD` 指令清理栈了。`ADD` 将栈指针移动 8 字节进行清理。栈状态显示在以下屏幕截图中：

`[ESP-0x8] 0012FF30 0040A154 "%d", parameter to 1st scanf()`

`[ESP-0x4] 0012FF34 0012FF38 Memory location of placeholder for iNumber1`

`[ESP] 0012FF38 00000007 [EBP-8] 7 is stored, Input placeholder for iNumber1`

`[ESP+0xC] 0012FF3C 0040445A [EBP-4] now JUNK, Input placeholder for iNumber2`

`[ESP+0x10] 0012FF40 0012FF88 [EBP]`

`[ESP+0x14] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000`

![](images/Figure-9.7.jpg)

**图 9.7：** scanf 之后

▼**行 48-51**

`; Line 12`

`push OFFSET $SG4681`

`call _printf`

`add esp, 4`

第 12 行的 C/C++ 代码在控制台上打印字符串：

`printf("Input Number2 : ");`

它与之前相同。`printf` 函数的参数首先被压入栈。`printf` 的参数是一个存储在 `.rdata` 段中的字符串常量，内部定义为 `$SG4681`。对 `printf` 的调用将在控制台上打印 `$SG4681`，而调用 `printf` 后的 `ADD` 指令将通过 4 字节清理栈。栈状态显示在以下屏幕截图中：

`[ESP-0x4] 0012FF34 0040A158 "Input Number2 : ", parameter to 2nd printf()`

