
`fld QWORD PTR __real@40011eb851eb851f`

FLD 代表浮点加载。 该指令将浮点值压入 FPU 栈，该栈从 `ST0` 到 `ST7`。 你可以在运行此指令前后看到调试器输出如下：

**提示**： 你可以在 `main` 的开头插入断点。 要插入断点，请滚动到 `.text` 段的顶部，你会发现与我们的汇编文件 `printfWithFloat.asm` 中的指令集相同的指令。 一旦设置断点，你可以 `step into` 指令逐条执行。

`x32dbg` 在执行此指令之前的输出：

`fld QWORD PTR __real@40011eb851eb851f`

![](images/Figure-7.21.jpg)

**图 7.21：** `ST0` 之前

执行此指令后：

![](images/Figure-7.22.jpg)

**图 7.22：** `ST0` 之后

### 第 38 行

`fstp QWORD PTR [esp]`

`FSTP` 表示浮点存储并弹出。 它将浮点值从 `ST0` 移动到栈顶 `PTR [esp]` 并完全从 `ST0` 弹出该值。

![](images/Figure-7.23.jpg)

**图 7.23：** 浮点存储和弹出

### 第 39 行

`sub esp, 8`

再次在栈上为 `main` 函数的局部变量分配 8 个字节，即传递给 `printf` 函数的第二个参数 `1.0`。 让我们看看它在 `x32dbg` 中的样子。

![](images/Figure-7.24.jpg)

**图 7.24：** 在栈上分配空间

### 第 40 行

`fld1`

此指令在 FPU 栈上加载浮点值 `1.0`。

![](images/Figure-7.25.jpg)

**图 7.25：** 加载浮点值 `1.0`

### 第 41 行

`fstp QWORD PTR [esp]`

`FSTP` 表示浮点存储并弹出，它将浮点值 `1.0` 从 `ST0` 移动到栈顶 `PTR [esp]` 并完全从 `ST0` 弹出该值。

![](images/Figure-7.26.jpg)

**图 7.26：** 浮点存储和弹出

### 第 42 行

`push OFFSET $SG4677`

现在在调用 `printf` 函数之前，我们必须将剩余的字符串常量传递到栈上。 此 `PUSH` 指令将字符串常量 `$SG4677` 压入栈。

![](images/Figure-7.27.jpg)

**图 7.27：** 压入字符串

### 第 43 行

`call _printf`

在调用 `printf` 函数的 `CALL` 指令之前，所有传递给 `printf` 函数的参数都已压入栈。 执行此指令后，两个变量都将打印到控制台上。

### 第 44 行

`add esp, 20 ; 00000014H`

由于我们遵循 CDECL 调用约定，是调用者负责清理栈。 从 `printf` 函数返回时，`main` 通过将栈指针回移 20 字节来清理栈（我们使用了 4 字节来压入字符串常量，8 字节来压入 `1.0` 浮点十六进制值，另外 8 字节用于压入 `2.14` 浮点十六进制值）。

在此指令之前，`x32dbg` 屏幕如下所示：

**提示**： 要直接移动到 `add` 指令，可以使用 `step over` 执行 `print` 函数并在 `add` 指令处停止。 或者你可以在 `add` 指令处插入断点以在 `add` 指令处停止执行。

![](images/Figure-7.28.jpg)

**图 7.28：** 调用 `printf` 之后

此指令之后：

![](images/Figure-7.29.jpg)

**图 7.29：** 栈已清理

### 第 45-52 行

```
; Line 9
xor eax, eax
; Line 10
pop ebp
ret 0
_main ENDP
_TEXT ENDS
END
```

剩余的指令使 `EAX` 为零，因为在 C/C++ 代码中 `main` 返回 0。 最后它调用函数尾声以结束 `main`、`TEXT` 段和代码。

# 使用优化的 printf 打印浮点数

使用优化标志 `/Ox` 编译代码。 在 Windows 命令提示符上运行以下命令为 `cl.exe`（VS 编译器）设置环境，然后使用以下开关编译代码：

* `/Ox`： 启用最大优化
* `/Fa`： 输出汇编列表文件的名称
* `/Fe`： 输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\printfWithFloat\printfWithFloat
cl printfWithFloat.cpp /FaprintfWithFloat-Optimized.asm /Ox /FeprintfWithFloat-Optimized.exe
```

运行上述命令的输出如下：

![](images/Figure-7.30.jpg)

**图 7.30：** 使用优化的函数 `printf` 打印浮点数

生成的汇编代码如下：

![](images/Figure-7.31.jpg)

**图 7.31：** `printfWithFloat-Optimized.asm`

列表中的所有指令都相同，除了第 33 行。 由于代码已优化，函数序言和尾声被移除，我们将在本节中讨论。

### 第 33 行

`fld QWORD PTR __real@40011eb851eb851f`

与之前相同。 此指令将浮点值 `2.14` 压入 FPU 栈，`ST0`。

### 第 34 行

`sub esp, 16 ; 00000010H`

如非优化代码所示，`SUB` 被调用两次以分配 `main` 函数局部变量的内存。 但在优化中，这两个指令合并为从 `ESP` 减去 16 字节，以为浮点变量 `1.0` 和 `2.14` 分配 8+8 字节。

### 第 35 行

`fstp QWORD PTR [esp+8]`

它将浮点值 `2.14` 从 `ST0` 移动到栈顶 `PTR [esp+8]` 并完全从 `ST0` 弹出该值。

### 第 36 行

`fld1`

与之前相同。 此指令在 FPU 栈上加载浮点值 `1.0`。

### 第 37 行

`fstp QWORD PTR [esp]`

它将浮点值 `1.0` 从 `ST0` 移动到栈顶 `PTR [esp]` 并完全从 `ST0` 弹出该值。

### 第 38-39 行

`push OFFSET $SG4677`

`call _printf`

将字符串常量偏移量压入栈以调用 `printf` 函数。

### 第 40-47 行

```
add esp, 20 ; 00000014H
; Line 9
xor eax, eax
; Line 10
ret 0
_main ENDP
_TEXT ENDS
END
```

根据 CDECL 调用约定，调用者清理栈。 剩余的指令通过对 `EAX` 寄存器进行异或操作返回 0，并在第 45-47 行结束 `main` 过程、文本段和代码。

# 函数 printf 使用字符

在这个简单的 C/C++ 代码中，我们在控制台上打印 2 个字符。 我们使用 `printf` 函数来打印字符。

![](images/Figure-7.32.jpg)

**图 7.32：** `printfWithChar.cpp`

# 未优化时函数 printf 打印字符

在同一台 x86 Windows 机器上使用 MSVC 编译器不使用优化编译代码。 在 Windows 命令提示符上运行以下命令为 `cl.exe`（VS 编译器）设置环境，然后使用以下开关编译代码：

* `/Fa`： 输出汇编列表文件的名称
* `/Fe`： 输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\printfWithChar\printfWithChar
cl printfWithChar.cpp /FaprintfWithChar.asm /FeprintfWithChar.exe
```

运行上述命令的输出如下：

![](images/Figure-7.33.jpg)

**图 7.33：** 未优化时函数 `printf` 打印字符

生成的汇编代码如下：

![](images/Figure-7.34.jpg)

**图 7.34：** `printfWithChar.asm`

汇编列表的大部分内容已在前一节中讨论过。 让我们继续到第 25 行。

### 第 25-28 行

```
push 98 ; 00000062H
push 97 ; 00000061H
push OFFSET $SG4677
call _printf
```

在调用 `printf` 函数之前，三个参数被压入栈。 第一个 `PUSH` 指令是 `PUSH 98`，其中 98 是字符 ‘b’ 的 ASCII 值，十六进制等价为 `62H`。 请参阅附录中的 ASCII 表以获取完整的 ASCII 列表。

第二个 `PUSH` 指令是 `PUSH 97`，其中 97 是 ‘a’ 的 ASCII 值，十六进制等价为 `61H`。

而 `printf` 的第三个参数是字符串常量 `$SG4677`，定义在 `CONST SEGMENT` 中。 这是在 `CALL` 指令之前 `x32dbg` 中栈的显示方式。 你可以通过在调用 `printf` 函数的 `CALL` 处插入断点来检查栈状态。
