
当你在编写使用共享库的 C/C++ 代码时，代码调用约定变得很重要，因为你交互的代码超出了你的控制范围。如果你是一名编写 C/C++ 代码的程序员，那么作为程序员，你不必担心，因为编译器会为你处理调用约定。编译器通常会根据语言自动采用默认的代码约定。在本章中，我们将了解代码调用约定的差异。

## 结构
本章将涵盖以下主题：
* 了解调用约定的类型
* 不同调用约定背后的概念

## 目标
学习完本章后，你将能够根据调用约定区分不同的汇编代码。如果收到一些汇编代码，那么通过查看汇编列表，你将能够评估所使用的调用约定。为了理解不同的代码调用约定，我们将采用一段伪代码来详细阐述每种调用约定背后的概念。

## 了解调用约定的类型
为了理解调用约定，让我们取一段基本的伪代码。在此代码中，函数 `funcA` 调用另一个函数（`funcB`）。在这种情况下，`funcA` 被称为 `caller`，而 `funcB` 被称为 `callee`。

```
FuncA()
{
Arg1;
Arg2;
FuncB(Arg1, Arg2);
}
```

现在当 `FuncB` 被调用时，它带 2 个参数（`Arg1`，`Arg2`）被调用。当此代码用不同的编译器编译时，它会生成不同的汇编代码。调用约定是一组规则，指定 C 或 C++ 函数如何转换为汇编代码。因此，调用约定基本上定义：
* 如何将参数传递给函数
* 函数如何返回值
* 调用者如何调用被调用者
* 当一个函数调用另一个函数时堆栈如何管理
* 如何清空堆栈

所有这些都由编译器使用的调用约定方法定义。在 C/C++ 语言中，主要使用三种调用约定：`CDECL`、`STDCALL` 和 `FASTCALL`。我们将逐一介绍这些调用约定。

### CDECL
`CDECL` 也可读作 C Declaration。当使用 `CDECL` 调用约定时：
* 参数按从右到左的顺序传递。在同一伪代码中，从右到左的顺序意味着 `Arg2` 首先被压入堆栈，然后 `Arg1` 被压入堆栈。
```
FuncA()
{
Arg1;
Arg2;
FuncB(Arg1, Arg2);
}
```
* 函数返回值传递到 `EAX` 寄存器中。
* 调用函数，`caller` 清理堆栈。

### STDCALL
`STDCALL` 代表 Standard Call。此调用约定由 Microsoft 定义为 Win32 API 的标准调用约定。当使用 `STDCALL` 时：
* 第一点与 `CDECL` 相同。参数按从右到左的顺序传递。
* 函数返回值传递到 `EAX` 寄存器中。这一点也与 `CDECL` 相同。
* 这一点与 `CDECL` 不同，被调用函数 `callee` 清理堆栈。

### FASTCALL
`CDECL`/`STDCALL` 与 `FASTCALL` 的主要区别在于初始参数不是压入堆栈，而是通过寄存器传递。将数据保存在寄存器中比在内存中更快，因此命名为 `FASTCALL`。在 `FASTCALL` 中，使用调用约定时：
* 前两个或三个参数通过寄存器 `EDX`、`ECX` 或 `EAX` 传递。附加参数传递到堆栈。参数按从右到左的顺序传递。
* 函数返回值传递到 `EAX` 寄存器中。
* 调用函数，`caller` 在需要时清理堆栈。

## 不同调用约定背后的概念
现在为了理解不同调用约定背后的概念，我们将用 C/C++ 编写一段简单代码。然后使用 `cl.exe`（VS 编译器），我们将用不同的调用约定编译代码并了解生成的汇编代码之间的差异。

下图显示了一段将进行加法的简单 C/C++ 代码：

![](images/Figure-5.1.jpg)

**图 5.1：** `AddNumber.cpp`

`AddNumber.cpp` 代码是一个简单的加法代码。以下是对前述程序需要注意的几点：
* `main` 函数是程序的入口点。
* `main` 函数正在调用一个 `addition` 函数。因此，`main` 函数是 `caller`，而 `addition` 函数是 `callee`。
* 在 `main` 函数和 `addition` 函数中定义的局部变量的类型为整数。
* 传递给 `callee` 的两个参数为 4 和 5。

编写代码后，我们将使用 `cl.exe` 编译代码，并使用不同的开关强制编译器更改调用约定。
* `/Gd`：使用此开关用于 `CDECL` 调用约定。
* `/Gz`：使用此开关用于 `STDCALL` 调用约定。
* `/Gr`：使用此开关用于 `FASTCALL` 调用约定。

我们将逐一介绍每种调用约定并了解它们之间的差异。

### CDECL
我们将不进行优化并使用 `CDECL` 调用约定编译 `AddNumber.cpp` 代码。我们将为此使用 `/Gd` 开关。在 Windows 命令提示符上运行以下命令以设置 `cl.exe`（VS 编译器）的环境，然后使用以下开关编译代码。
* `/Gd`：使用此开关用于 `CDECL` 调用约定。
* `/Fa`：输出汇编列表文件的名称
* `/Fe`：输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\AddNumber\AddNumber
cl AddNumber.cpp /FaAddNumber-CDECL.asm /Gd /FeAddNumber-CDECL.exe
```

运行上述命令的输出如下：

![](images/Figure-5.2.jpg)

**图 5.2：** `CDECL`

这将生成 `AddNumber-CDECL.asm`。现在我们将继续分析 `AddNumber-CDECL.asm` 中生成的汇编代码：我们的 C++ 代码分为两个函数，一个是 `main` 函数（`caller`），另一个是 `addition` 函数（`callee`）。为了理解 `CDECL` 调用约定，我们将采用 `main` 函数代码从 C++ 代码到汇编的转换。

![](images/Figure-5.3.jpg)

**图 5.3：** `AddNumber.cpp` 中的主函数代码

主函数的汇编代码变为：

![](images/Figure-5.4.jpg)

**图 5.4：** `AddNumber-CDECL.asm` 中 Main proc 的汇编代码

让我们分析 `asm` 文件中主函数的汇编代码：
* 第 20-21 行是函数序言。这些是一系列用于开始函数的指令。
* 在第 22 行，函数序言后 `PUSH ECX` 的目的不是将 `ECX` 保存到堆栈上，而是为存储局部变量 `add` 在堆栈上分配 4 个字节。
* `Add` 变量可以通过 `_add$` 宏访问，该宏等于 -4。因此，`Add` 可以在 `[EBP - 0x4]` 处访问。
* 从第 24 行开始，我们将理解 `CDECL` 的概念。让我们逐一回顾 `CDECL` 调用约定的要点，以便在实践中理解概念：
  * 参数按从右到左的顺序传递。
    * 在 `AddNumber.cpp` 的第 12 行，即 `int add=addition(4,5);`，我们将 4、5 参数传递给 `addition` 函数。现在，从右到左意味着 5 将首先被压入堆栈，然后 4 被压入堆栈，正如在 `AddNumber-CDECL.asm` 代码第 24-25 行所做的那样。参数压入堆栈后，`addition` 函数在 `AddNumber-CDECL.asm` 的第 26 行被调用。
  * `Calling function`，`caller` 清理堆栈。
