
### 图 11.23：堆栈状态在 `ESI` 为 `0x0A` 之后

#### 行 56-66

```
; Line 15
mov ecx, DWORD PTR __$ArrayPad$[esp+48]
pop esi
xor ecx, esp
xor eax, eax
call @__security_check_cookie@4
add esp, 44     ; 0000002cH
ret 0
_main ENDP
_TEXT ENDS
END
```

`MOV` 指令将 `[ESP+0x2C]` 处存储的堆栈 cookie 移动到 `ECX`。

`POP` 指令从堆栈中恢复 `ESI` 的值。

`XOR` 指令将移动到 `ECX` 的堆栈 cookie 与 `ESP` 进行异或，并将异或结果写回 `ECX` 寄存器。在调用 `security_check_cookie` 过程时，此 `ECX` 值会与 `.data` 段中存储的堆栈 cookie 进行比较。

![](images/Figure-11.24.jpg)

### 图 11.24：调用 `security_check_cookie`

由于堆栈 cookie 值未改变，指令指针将返回到 `main`。返回时，`EAX` 与 `EAX` 进行异或以返回 0，`ADD` 指令将清理堆栈以结束 `main` 过程、`TEXT` 段和代码。最终的堆栈状态如下：

```
[ESP-0x3C] 0012FF08  00408140   Now JUNK
[ESP-0x38] 0012FF0C  00000009   Now JUNK
[ESP-0x34] 0012FF10  00000009   Now JUNK
ESP-0x30] 0012FF14  00401087   Now JUNK
[ESP-0x2C] 0012FF18  00000000   Now JUNK
[ESP-0x28] 0012FF1C  00000001   Now JUNK
[ESP-0x24] 0012FF20  00000002   Now JUNK
[ESP-0x20] 0012FF24  00000003   Now JUNK
[ESP-0x1C] 0012FF28  00000004   Now JUNK
[ESP-0x18] 0012FF2C  00000005   Now JUNK
[ESP-0x14] 0012FF30  00000006   Now JUNK
[ESP-0x10] 0012FF34  00000007   Now JUNK
[ESP-0x0C] 0012FF38  00000008   Now JUNK
[ESP-0x08] 0012FF3C  00000009   Now JUNK
[ESP-0x04] 0012FF40  13789938   Now JUNK
[ESP]  0012FF44  0040128B   ESP at the start of main function
```

![](images/Figure-11.25.jpg)

### 图 11.25：最终的堆栈状态

## 结论

本章中，我们讨论了数组在反向工程中的工作原理。我们看到了反汇编代码中的数组代码模式，并理解了数组如何在连续的内存位置中存储。由于一个整数占用 4 字节内存，因此整数数组占用 4 字节乘以数组中元素的数量。我们看到了堆栈中如何分配连续的内存位置。我们还介绍了代码未优化和已优化时数组程序模式。在下一章中，我们将讨论可以处理不同数据类型结构的反向工程。

# 第 12 章

## 反向工程中的结构代码模式

在现实世界中，我们可以用多个属性来描述一个个体。这些属性，或我们可以称之为参数或特征，有助于我们唯一地识别一个个体。可以唯一识别一个个体的属性可以是其姓名、年龄、性别、身高、体重、国籍等。所有这些属性都对应于不同类型的数据。这意味着年龄是一个整数，性别是一个字符串，体重可以是浮点数，国籍是一个字符串。

现在，作为一名计算机程序员，如果我们必须编写一个应用程序来记录某个地理位置中所有个体的详细信息，那么我们必须以一种能够以良好管理且易于的方式处理个体数据的方式编写应用程序。在上一章中，我们已经看到了可以保存单个信息片段的普通变量。我们也看到了数组如何保存相同数据类型的。 但在记录个体数据的情况下，我们必须使用结构，结构用于记录不同数据类型的数据。在本章中，我们将反向分析一种在许多应用程序中使用的结构。

## 结构

本章将涵盖以下主题：

* 结构理解
* 未优化的结构
* 优化的结构

### 目标

在本章中，我们将研究关于反向工程中指向结构的指针。我们将讨论反汇编代码中的结构代码模式以及结构如何在内存中存储。我们还将介绍优化和未优化代码的结构程序。

### 结构理解

在此示例中，让我们演示结构指针。正如我们有一个指向整数的指针或指向字符的指针一样，我们也有指向结构的指针。在 C 语言中，我们有一个箭头运算符来引用结构的元素。

![](images/Figure-12.1.jpg)

**图 12.1：** Structures.cpp

### 未优化的结构

在同一 x86 Windows 机器上使用 `MSVC` 编译器不进行优化编译代码。在 Windows 命令提示符上运行以下命令为 `cl.exe`（VS 编译器）设置环境，然后使用以下开关编译代码：

* `/Fa`：输出汇编列表文件的名称
* `/Fe`：输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\Structures\Structures
cl Structures.cpp /FaStructures.asm /FeStructures.exe
```

以下为运行上述命令的输出：

![](images/Figure-12.2.jpg)

**图 12.2：** 未优化的结构

编译生成 EXE 文件和汇编代码。手动禁用 `ASLR`。要禁用 `ASLR`，请使用 `CFF explorer` 并更改 `DllCharacteristics` 参数以取消选中 `DLL can move`。

现在，让我们继续生成的汇编列表：

![](images/Figure-12.3.jpg)

**图 12.3：** Structures.asm-Part-1

![](images/Figure-12.4.jpg)

**图 12.4：** Structures.asm-Part-2

![](images/Figure-12.5.jpg)

**图 12.5：** Structures.asm-Part-3

让我们继续解释 ASM 代码：

#### 行 30-33

`; Line 9`
```
push ebp
mov ebp, esp
sub esp, 64     ; 00000040H
```

它以 `main` 函数序言开始，其中旧的 `EBP` 被压入堆栈，当前的 `ESP` 被移动到新的 `EBP`。

`SUB` 指令通过从 `ESP` 寄存器中减去 64 字节为安全 cookie 和局部变量创建空间。堆栈上为变量分配的空间可以细分为如下：

`char rgName[40]; = 40 bytes`
`int iAge; = 4 bytes`
`unsigned long long uMobile; = 8 bytes`
`struct SSubscriber *puser; = 4 bytes`
`Stack Cookie = 4 bytes`

#### 行 34-36

```
mov eax, DWORD PTR ___security_cookie
xor eax, ebp
mov DWORD PTR __$ArrayPad$[ebp], eax
```

如以下屏幕截图所示，存储在 `0x0040B000` 的堆栈 cookie 被移动到 `EAX`，其中它与 `EBP` 进行异或。`EAX` 的异或结果被移回 `__$ArrayPad$[ebp]`，即 `[EBP-0x08]`。此时堆栈如下：

```
[ESP]  0012FF00  00000000  Right now JUNK, space for local variables
[ESP+0x04] 0012FF04  00000000  Right now JUNK, space for local variables
[ESP+0x08] 0012FF08  7FFDE000  Right now JUNK, space for local variables
[ESP+0x0C] 0012FF0C  0040345B  Right now JUNK, space for local variables
[ESP+0x10] 0012FF10  0012FEFC  Right now JUNK, space for local variables
[ESP+0x14] 0012FF14  00000004  Right now JUNK, space for local variables
[ESP+0x18] 0012FF18  0012FF78  Right now JUNK, space for local variables
[ESP+0x1C] 0012FF1C  00402500  Right now JUNK, space for local variables
[ESP+0x20] 0012FF20  0185B22A  Right now JUNK, space for local variables
[ESP+0x24] 0012FF24  FFFFFFFE  Right now JUNK, space for local variables
[ESP+0x28] 0012FF28  004054AC  Right now JUNK, space for local variables
[ESP+0x2C] 0012FF2C  004054C0  Right now JUNK, space for local variables
[ESP+0x30] 0012FF30  0040345B  Right now JUNK, space for local variables
[ESP+0x34] 0012FF34  0012FF48  Right now JUNK, space for local variables
[ESP+0x38] 0012FF38  01D7D682  XOR of Stack Cookie and EAX is stored here
```
