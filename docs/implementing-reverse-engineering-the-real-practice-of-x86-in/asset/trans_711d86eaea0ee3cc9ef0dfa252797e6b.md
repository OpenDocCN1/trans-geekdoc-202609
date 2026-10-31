
The stack state and the screenshot of x32dbg when `iNumber` is incremented by 1 will be as follows:

`[ESP] 0012FF3C 00000002 iNumber is stored here, now its incremented by 1`

`[ESP+0x4] 0012FF40 0012FF88 [EBP]`

`[ESP+0x4] 0012FF44 00401224 return to while.00401224 from while.00401000`

![](images/Figure-10.7.jpg)

**图 10.7：** 当 `iNumber` 增加 1 时

### Line 42-43

`; Line 13`

`jmp SHORT $LN2@main`

这是一个无条件跳转到 `$LN2@main` 标签，在那里存储在 `[EBP-4]` 中的值将再次与值 10 (0x0A) 进行比较。如果该值小于或等于 10，则相同的指令将把 `iNumber` 打印到屏幕上，同时将 `[EBP-4]` 处的 `iNumber` 值递增 1。

在 `JMP` 之后，堆栈状态将与之前相同。

`[ESP] 0012FF3C 00000002 iNumber is stored here, now its incremented by 1`

`[ESP+0x4] 0012FF40 0012FF88 [EBP]`

`[ESP+0x4] 0012FF44 00401224 return to while.00401224 from while.00401000`

指令指针将被指向 `0x0040100B`，如下所示：

![](images/Figure-10.8.jpg)

**图 10.8：** 无条件跳转到 `$LN2@main`

现在，我们将看到当 `iNumber` 变为 10 (0x0A) 时会发生什么。分析代码有两种方法：

1. 手动 **单步进入** 代码逐条指令。这是一个耗时过程。
2. 在存储在 `[EBP-4]` 中的值变为 `0x0A` 或 `ECX == 0x0A` 时设置断点。我们将在 x32dbg 中设置条件断点，当 `ECX == 0x0A` 时。

* 现在，要设置条件断点，首先在以下位置设置软件断点（按 `F2` 键）：

`0x00401025 add ecx, 1`

* 然后右键单击该指令并从上下文菜单中选择 **编辑断点** 命令。填写以下条件表达式，然后确认并关闭对话框，如以下屏幕截图所示：

![](images/Figure-10.9.jpg)

**图 10.9：** 在条件上设置断点

* 运行代码直到命中条件断点。从那里，我们可以手动 **单步进入** 指令。此时的堆栈状态和 x32dbg 的屏幕截图如下：

`[ESP] 0012FF3C 0000000A iNumber is stored here, now its incremented to 0xA`

`[ESP+0x4] 0012FF40 0012FF88 [EBP]`

`[ESP+0x4] 0012FF44 00401224 return to while.00401224 from while.00401000`

![](images/Figure-10.10.jpg)

**图 10.10：** 当 `iNumber` 递增到 0x0A 时

* 当我们 **单步进入** 时，`ECX` 和 `[EBP-4]` 将变为 0x0B。

![](images/Figure-10.11.jpg)

**图 10.11：** 当 `iNumber` 递增到 0x0B 时

* 在下一次迭代中，`JG` 指令将跳转指令指针到 `$LN3@main` 标签，我们将在下一部分讨论它。

### Line 44-52

```
$LN3@main:
; Line 14
xor eax, eax
mov esp, ebp
pop ebp
ret 0
_main ENDP
_TEXT ENDS
END
```

这将清零 `EAX` 并调用 `main` 函数的尾声。至此，`TEXT` 段和代码结束。

# 使用优化的 While 条件

使用优化标志 `/Ox` 编译代码。在 Windows 命令提示符下运行以下命令为 `cl.exe`（VS 编译器）设置环境，然后使用以下开关编译代码：

* `/Ox`: 启用最大优化
* `/Fa`: 输出汇编列表文件的名称
* `/Fe`: 输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\while\while
cl while.cpp /Fawhile-Optimized.asm /Ox /Fewhile-Optimized.exe
```

运行上述命令的输出如下：

![](images/Figure-10.12.jpg)

**图 10.12：** 使用优化的 While 条件

它将生成汇编代码和 EXE 文件。按照相同的过程手动禁用 ASLR。要禁用 ASLR，请使用 CFF explorer 按照相同的步骤操作，并更改 `DllCharacteristics` 参数以取消选中 **DLL 可以移动**。有关禁用 ASLR 的逐步过程，请参阅 *附录*。

现在，让我们继续查看生成的汇编列表：

![](images/Figure-10.13.jpg)

**图 10.13：** `while-Optimized.asm`

我们将逐条指令 walk through 生成的汇编代码：

### Line 21-22

`; Line 7`

`push esi`

`main` 过程首先推送 `ESI` 寄存器。通过将 `ESI` 压入堆栈，我们保留了 `ESI` 寄存器的值。`ESI` 在 `main` 过程结束时使用 `POP ESI` 指令恢复。因此，它基本上是在函数的开始和结束时使用 `PUSH` 和 `POP` 指令分别保存和恢复寄存器值。

### Line 23-25

`; Line 8`

`mov esi, 1`

`npad 10`

C/C++ 代码第 8 行初始化 `iNumber` 变量：

`int iNumber = 1 ;`

在 ASM 代码中，`ESI` 寄存器将用于保存 `iNumber` 值并进行后续操作。`MOV` 指令通过将 0x01 移动到 `ESI` 寄存器来初始化 `iNumber`。

接下来是 `npad` 宏，它插入非破坏性和非操作指令。这意味着它将插入一条不执行任何操作的指令。有关 `npad` 的信息，请参阅 *附录* 部分。我们的汇编列表使用 `npad 10`，它在 `LISTING.INC` 中定义为 `jmp .+A; .npad 7; .npad 1`，其中

`npad 10` is

![](images/Figure-10.14.jpg)

**图 10.14：** `npad 10`

`npad 7` is

![](images/Figure-10.15.jpg)

**图 10.15：** `npad 7`

`npad 1` is

![](images/Figure-10.16.jpg)

**图 10.16：** `npad 1`

Together, `npad 10` makes:

`jmp .+A -> It will add 0x0A to instruction location (0x00401006 + 0x0A)`

`lea esp, [esp+00000000]`

`nop`

让我们看看 `npad 10` 宏在 x32dbg 屏幕截图中是如何解析的：

![](images/Figure-10.17.jpg)

**图 10.17：** x32dbg 中的 `npad 10`

标记为 RED 的三条指令对代码流程没有任何影响；它们只是相当于大小为 10 字节的一系列 NOP。编译器在 `mov esi,1` 指令和标签 `$LL2@main`（接下来定义）之间填充了 10 个字节。

### Line 26-30

```
$LL2@main:
; Line 11
push esi
push OFFSET $SG4681
call _printf
```

`$LL2@main` 标签在注释为第 11 行后定义。C/C++ 代码的第 11 行使用 `printf` 函数将 `iNumber` 打印到屏幕上。

`printf("%d\n", iNumber);`

在 ASM 代码中，在调用 `printf` 函数之前，两个 `printf` 参数被压入堆栈。第一个是保存 `iNumber` 的 `ESI`，另一个是由 `$SG4681` 定义的字符串常量。`printf` 调用后的堆栈状态如下所示，同时附有 x32dbg 屏幕截图以便更好地理解：

`[ESP] 0012FF38 00408140 "%d\n", parameter to printf()`

`[ESP+0x4] 0012FF3C 00000001 iNumber is pushed as a parameter to printf()`

`[ESP+0x8] 0012FF40 00000000 Old value of ESI is preserved`

`[ESP+0xC] 0012FF44 00401219 return to 0x00401219 from 0x00401000`

![](images/Figure-10.18.jpg)

**图 10.18：** `printf` 之后

### Line 31-35

`; Line 12`

`inc esi`

`add esp, 8`

`cmp esi, 10 ; 0000000aH`

`jle SHORT $LL2@main`

第 12 行的 C/C++ 代码将 `iNumber` 递增 1。

`iNumber = iNumber + 1 ;`

在 ASM 中，我们使用 `INC` 指令递增存储在 `ESI` 中的 `iNumber`。`INC` 将 1 加到 `ESI` 并将结果写回 `ESI` 寄存器。`ADD` 指令通过向 `ESP` 添加 8 个字节来清理堆栈。堆栈清理后，`ESI` 中的值与 10 (0x0A) 进行比较。如果 `ESI` 中的值小于或等于 10 (0x0A)，则在 `CMP` 指令后执行有符号比较跳转。
