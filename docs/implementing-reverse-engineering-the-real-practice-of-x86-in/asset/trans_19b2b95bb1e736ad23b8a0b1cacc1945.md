
```
[ESP] 0012FF38 00000007 [EBP-8] 7 is stored, Input placeholder for iNumber1
[ESP+0xC] 0012FF3C 0040445A [EBP-4] now JUNK, Input placeholder for iNumber2
[ESP+0x10] 0012FF40 0012FF88 [EBP]
[ESP+0x14] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000
```

![](images/Figure-9.8.jpg)

### 图 9.8：再次调用 printf

### 第 52-57 行

```asm
; Line 13
lea ecx, DWORD PTR _iNumber2$[ebp]
push ecx
push OFFSET $SG4682
call _scanf
add esp, 8
```

第 13 行的 C/C++ 代码从用户处获取输入整数并将其存储在 `&iNumber2` 内存位置：

`scanf("%d", &iNumber2);`

与之前的 `scanf` 代码相同。`LEA` 将有效地将地址 of `_iNumber2$[ebp]`，即 `0x0012FF3C`，加载到 `ECX` 寄存器中。将 `ECX` 加载 `_iNumber2$[ebp]` 地址的目的，是将 `ECX` 寄存器连同字符串常量 `$SG4682` 一起压入栈中。地址 `0x0012FF3C` 和字符串 `$SG4682` 都是 `scanf` 函数的参数。

要检查 `scanf` 函数调用后的堆栈状态，请在 `scanf` 调用后的 `ADD` 指令处设置另一个断点。现在逐条进入指令，并在调用 `scanf` 时执行一次步过。它会提示你在控制台上输入第二个数字。我们将输入数字 8 并按 *ENTER*。按 *ENTER* 后，数字 8 将保存在堆栈中 `iNumber2` 内存位置的输入占位符处，`0x0012FF3C`。通过 `scanf` 调用，用户输入的数字会保存到堆栈上。调用后，是时候再次使用 `ADD` 指令清理堆栈了。`ADD` 将使堆栈指针移动 8 字节以进行清理。堆栈状态显示在以下屏幕截图中：

```
[ESP-0x8] 0012FF30 0040A16C "%d", parameter to 2nd scanf()
[ESP-0x4] 0012FF34 0012FF3C Memory location of placeholder for iNumber2
[ESP] 0012FF38 00000007 [EBP-8] 7 is stored, Input placeholder for iNumber1
[ESP+0xC] 0012FF3C 00000008 [EBP-4] 8 is stored, Input placeholder for iNumber2
[ESP+0x10] 0012FF40 0012FF88 [EBP]
[ESP+0x14] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000
```

![](images/Figure-9.9.jpg)

### 图 9.9：再次进行 scanf 之后

### 第 58-61 行

```asm
; Line 14
mov edx, DWORD PTR _iNumber1$[ebp]
cmp edx, DWORD PTR _iNumber2$[ebp]
jne SHORT $LN2@main
```

第 14 行的 C/C++ 代码比较两个数字：

`if (iNumber1 == iNumber2)`

现在我们有两个数字 `iNumber1` 和 `iNumber2` 分别存储在 `[EBP-8]` 和 `[EBP-4]` 中。为了比较这两个数字，第一个 `MOV` 指令会将存储在 `[EBP-8]` 中的值移动到 `EDX` 寄存器中，即数字 `0x00000007`，然后使用 `CMP` 指令将存储在 `[EBP-4]` 中的值与 `EDX` 寄存器的值进行比较。

在我们的例子中，`EDX` = `0x00000007` 与 `[EBP-8]` = `0x00000008` 进行比较。

`CMP` 指令可以视为 `SUB` 指令，并且由于它是条件 `JMP`，其工作方式如下：

`[EDX] - [EBP-8]`, based on the subtraction result, the control flag is set

`0x00000007 - 0x00000008 != 0`, so it sets `ZF` `Zero Flag` = 0

`CMP` 之后是 `JNE`，即 `Jump if Not Equal`。由于两个数字不相等且 `ZF=0`，跳转将发生到 `JNE` 指令后指定的位置，即 `$LN2@main`。让我们在 `JNE` 指令之前检查堆栈状态和 `x32dbg` 的屏幕截图：

```
[ESP-0x8] 0012FF30 0040A16C "%d", parameter to 2nd scanf()
[ESP-0x4] 0012FF34 0012FF3C Memory location of placeholder for iNumber2
[ESP] 0012FF38 00000007 [EBP-8] 7 is stored, Input placeholder for iNumber1
[ESP+0xC] 0012FF3C 00000008 [EBP-4] 8 is stored, Input placeholder for iNumber2
[ESP+0x10] 0012FF40 0012FF88 [EBP]
[ESP+0x14] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000
```

![](images/Figure-9.10.jpg)

### 图 9.10：JNE 指令之前

在我们的例子中，`JNE` 将指令指针移动到 `$LN2@main` 位置。如果用户输入相同的数字，`CMP` 指令将导致 `ZF` `Zero Flag` = 1。这将使指令指针移动到在控制台上打印 `“Number1 and Number2 are equal”`，随后是第 67 行的无条件跳转指令到 `$LN3@main` `JMP SHORT $LN3@main`，其中 `$LN3@main` 是 `main` 函数和代码的结束。堆栈状态显示在以下屏幕截图中：

### 第 68-72 行

```asm
$LN2@main:
; Line 17
push OFFSET $SG4686
call _printf
add esp, 4
```

C/C++ 等价物是：

`printf("Number1 and Number2 are not equal\n");`

它打印 ‘Number1 and Numver2 are not equal’。ASM 代码将字符串常量 `$SG4686` 压入栈中，供 `printf` 函数作为参数使用。这将在控制台上打印 `‘Number1 and Number2 are not equal’`。接下来是 `ADD` 指令，它将通过 4 字节清理堆栈，这是由 `PUSH` 操作中的字符串常量 `$SG4686` 使用的。之后的堆栈状态如下：

```
[ESP-0x4] 0012FF34 0040A190 "Number1 and Number2 are not equal\n", arg to printf
[ESP] 0012FF38 00000007 [EBP-8] 7 is stored, Input placeholder for iNumber1
[ESP+0xC] 0012FF3C 00000008 [EBP-4] 8 is stored, Input placeholder for iNumber2
[ESP+0x10] 0012FF40 0012FF88 [EBP]
[ESP+0x14] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000
```

![](images/Figure-9.11.jpg)

### 图 9.11：打印 “Number1 and Number2 are not equal”

### 第 73-81 行

```asm
$LN3@main:
; Line 18
xor eax, eax
mov esp, ebp
pop ebp
ret 0
_main ENDP
_TEXT ENDS
END
```

`XOR` 和函数尾声将分别清理 `EAX` 和堆栈。`END` 将通过返回 0 来结束代码。堆栈状态显示在以下屏幕截图中：

```
[ESP-0x10] 0012FF34 0040A190 JUNK
[ESP-0xC] 0012FF38 00000007 JUNK
[ESP-0x8] 0012FF3C 00000008 JUNK
[ESP-0x4] 0012FF40 0012FF88 [EBP] popped up
[ESP] 0012FF44 004012F7 return to ifelse.004012F7 from ifelse.00401000
```

![](images/Figure-9.12.jpg)

### 图 9.12：堆栈已清理

# 使用优化的 if-else 语句

使用优化标志 `/Ox` 编译代码。在 Windows 命令提示符下运行以下命令以设置 `cl.exe` `VS compiler` 的环境，然后使用以下开关编译代码：

* `/Ox`: 启用最大优化
* `/Fa`: 输出汇编列表文件的名称
* `/Fe`: 输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\ifelse\ifelse
cl ifelse.cpp /Faifelse-Optimized.asm /Ox /Feifelse-Optimized.exe
```

运行上述命令的输出如下：

![](images/Figure-9.13.jpg)

### 图 9.13：使用优化的 if-else 语句

这将生成汇编代码和 EXE 文件。为了分析目的，我们将禁用 `ASLR`。它是一种安全机制，通过该机制，使用我们的 `MSVC` 编译器生成的 `PE` 文件在每次加载时其基地址都会被随机化。要禁用 `ASLR`，请使用 `CFF explorer` 按照相同的步骤操作，并更改 `DllCharacteristics` 参数以取消选中 `DLL can move`。有关禁用 `ASLR` 的逐步参考，请参阅附录。

现在，让我们继续查看生成的汇编列表：

![](images/Figure-9.14.jpg)

### 图 9.14：ifelse-Optimized.asm-第 1 部分

![](images/Figure-9.15.jpg)

### 图 9.15：ifelse-Optimized.asm-第 2 部分

此汇编代码通过删除不必要的行来优化，以消耗更少的资源。在此代码中，我们将看不到函数序言和尾声。我们还可以观察到 `ESP` 被用作引用而不是 `EBP`；这是由于缺少函数序言和尾声所致。让我们开始分析，这次我们将输入相同的数字。

### 第 34-35 行

```asm
; Line 7
sub esp, 8
```
