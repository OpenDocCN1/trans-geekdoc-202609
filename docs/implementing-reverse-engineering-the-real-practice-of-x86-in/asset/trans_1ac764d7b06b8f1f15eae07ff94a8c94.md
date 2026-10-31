
在我们的例子中，自增后 `ESI = 0x02` 的当前值。因此，指令指针将被跳转到 `$LL2@main` 标签。`ESI` 再次在控制台上打印。此循环迭代直到 `ESI` 变为 `0x0B`。当 `ESI` 自增到 `0x0B` 时，`CMP` 指令之后的有符号比较跳转将不会发生。因此，指令指针将移动到汇编代码的末尾。此时堆栈状态为：
```
[ESP-0x8] 0012FF38  00408140  NOW JUNK
[ESP-0x4] 0012FF3C  0000000A  NOW JUNK
[ESP]  0012FF40  00000000  Old value of ESI is preserved
[ESP+0xC] 0012FF44  00401219  return to 0x00401219 from 0x00401000
```
![](images/Figure-10.19.jpg)
**图 10.19：** ESI 自增到 0x0B

### ▼ 第 36-42 行
```
; Line 14
xor eax, eax
pop esi
ret 0
_main ENDP
_TEXT ENDS
END
```
这与在其他章节中解释的内容相同。`EAX` 被 XOR 以返回 0。这里需要注意的一点是，`ESI` 的值使用 `POP ESI` 指令恢复回来。至此，我们的 `main` 过程、`TEXT` 段和代码结束。弹出 `ESI` 后的堆栈状态如下：
```
[ESP-0x8] 0012FF38  00408140  NOW JUNK
[ESP-0x4] 0012FF3C  0000000A  NOW JUNK
[ESP]  0012FF40  00000000  NOW JUNK
[ESP+0xC] 0012FF44  00401219  return to 0x00401219 from 0x00401000
```
![](images/Figure-10.20.jpg)
**图 10.20：** 堆栈已清理

# [For 循环](#toc.xhtml#s210a)
在本节中，我们将在 C/C++ 代码中使用 `for` 循环，它初始化一个整数变量并将其递增 2 以在屏幕或控制台上打印出来。
![](images/Figure-10.21.jpg)
**图 10.21：** for.cpp

# [未优化的 For 循环](#toc.xhtml#s211a)
在同一台 x86 Windows 机器上使用 `MSVC` 编译器不进行优化地编译代码。在 Windows 命令提示符上运行以下命令以设置 `cl.exe`（VS 编译器）的环境，然后使用以下开关编译代码：
*   `/Fa`: 输出汇编列表文件的名称
*   `/Fe`: 输出可执行文件的名称
```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\for\for
cl for.cpp /Fafor.asm /Fefor.exe
```
运行上述命令的输出如下：
![](images/Figure-10.22.jpg)
**图 10.22：** 未优化的 For 循环
编译生成汇编代码和 EXE 文件。要手动禁用 ASLR，请使用 CFF explorer 并更改 `DllCharacteristics` 参数以取消选中 **DLL 可以移动**。
现在，让我们继续查看生成的汇编列表：
![](images/Figure-10.23.jpg)
**图 10.23：** for.asm

### ▼ 第 22-25 行
```
; Line 7
push ebp
mov ebp, esp
push ecx
```
ASM 代码以 `main` 函数序言开始。第一个 `PUSH ECX` 将在堆栈上为 `iNumber` 整数变量创建空间。

### ▼ 第 26-27 行
```
; Line 8
mov DWORD PTR _iNumber$[ebp], 1
```
以下 C/C++ 代码第 8 行将 `iNumber` 变量初始化为 1，这对应于前面的 ASM 代码：
```
int iNumber = 1;
```
在 ASM 代码中，`iNumber` 宏定义为：
```
_iNumber$ = -4; size = 4
```
因此，前面的 ASM 代码在 `x32dbg` 中解析为以下指令：
```
mov dword ptr ss:[ebp-0x4], 0x1
```
`MOV` 将堆栈上 `ss:[ebp-0x4]` 处的 `iNumber` 变量初始化为 `0x01`。这是为创建 `iNumber` 变量空间而推送 `ECX` 的同一内存位置。执行此指令后堆栈状态如下：
```
[ESP]  0012FF3C  00000001  iNumber variable is stored here
[ESP+0x4] 0012FF40  0012FF88  [EBP]
[ESP+0x8] 0012FF44  0040122D  return to for.0040122D from for.00401000
```
![](images/Figure-10.24.jpg)
**图 10.24：** iNumber 在堆栈上

### ▼ 第 28-30 行
```
; Line 9
mov DWORD PTR _iNumber$[ebp], 1
jmp SHORT $LN3@main
```
此 ASM 代码对应于 C/C++ 代码第 9 行，其中 `iNumber` 再次被初始化并且循环开始。
```
for (iNumber = 1 ; iNumber <= 10 ; iNumber = iNumber + 2)
```
在 ASM 中，`MOV` 指令再次初始化 `iNumber` 变量。由于代码未进行优化，编译器不会删除不需要或重复的指令。`JMP` 是对 `$LN3@main` 标签的无条件跳转，在该标签处 `iNumber` 与 10(`0x0A`) 进行比较以进入循环。我们将在下一个 ASM 解释中看到 `$LN3@main` 标签。此无条件跳转后的堆栈状态将相同：
```
[ESP]  0012FF3C  00000001  iNumber variable is stored here
[ESP+0x4] 0012FF40  0012FF88  [EBP]
[ESP+0x8] 0012FF44  0040122D  return to for.0040122D from for.00401000
```

### ▼ 第 35-44 行
```
$LN3@main:
cmp DWORD PTR _iNumber$[ebp], 10  ; 0000000aH
jg SHORT $LN4@main
; Line 10
mov ecx, DWORD PTR _iNumber$[ebp]
push ecx
push OFFSET $SG4681
call _printf
add esp, 8
jmp SHORT $LN2@main
```
前面的 ASM 代码对应于以下 C/C++ 代码第 9-10 行，该行比较 `iNumber` 与 10 (`0x0A`)。
```
for (iNumber = 1 ; iNumber <= 10 ; iNumber = iNumber + 2)
printf ("%d\n", iNumber);
```
让我们逐步分析 ASM 代码。`CMP` 指令将堆栈上存储的 `iNumber` 值与 10 (`0x0A`) 进行比较。如果 `[EBP-0x04]` 处的 `iNumber` 大于 10 (`0x0A`)，它将执行有符号比较跳转。目前 `iNumber` 为 1，因此不会发生跳转，指令指针将移动到汇编列表中第 10 行注释之后的下一部分。`CMP` 指令还设置 `ZF=0`。
第 10 行注释之后的指令将 `[EBP-4]` 处的 `iNumber` 值移动到 `ECX` 寄存器，以便 `ECX` 可以连同字符串常量 `$SG4681` 一起作为 `printf` 的参数推回堆栈。在调用 `printf` 函数时，`iNumber` 值 = 1 将在屏幕上打印出来。
从 `printf` 调用返回时，堆栈通过 `ADD` 指令向 `ESP` 添加 8 个字节来清理。`JMP` 是无条件跳转，使指令指针移动到 `$LN2@main` 标签，在该标签处 `iNumber` 将递增 2。无条件跳转后的堆栈状态如下：
```
[ESP-0x8] 0012FF34  00408140  Now JUNK, "%d\n", parameter to print() was pushed
[ESP-0x4] 0012FF38  00000001  Now JUNK, iNumber parameter to print() was pushed
[ESP]  0012FF3C  00000001  iNumber variable is stored here
[ESP+0x4] 0012FF40  0012FF88  [EBP]
[ESP+0x8] 0012FF44  0040122D  return to for.0040122D from for.00401000
```
![](images/Figure-10.25.jpg)
**图 10.25：** 无条件跳转后的堆栈状态

### ▼ 第 31-34 行
```
$LN2@main:
mov eax, DWORD PTR _iNumber$[ebp]
add eax, 2
mov DWORD PTR _iNumber$[ebp], eax
```
此 ASM 代码对应于以下 C/C++ 代码第 9 行，其中 `iNumber` 递增 2。
```
for (iNumber = 1 ; iNumber <= 10 ; iNumber = iNumber + 2)
```
在 ASM 中，`MOV` 指令将 `[EBP-0x4]` 的 `iNumber` 值取到 `EAX` 寄存器中，其中 `EAX` 使用 `ADD` 指令递增 2 并移回 `[EBP-0x4]`，即 `iNumber` 的内存占位符。随后是之前讨论过的 `iNumber` 与 10 (`0x0A`) 进行比较的相同指令。递增后的堆栈状态如下：
```
[ESP-0x8] 0012FF34  00408140  Now JUNK, "%d\n", parameter to print() was pushed
[ESP-0x4] 0012FF38  00000001  Now JUNK, iNumber parameter to print() was pushed
[ESP]  0012FF3C  00000003  iNumber variable is stored here
[ESP+0x4] 0012FF40  0012FF88  [EBP]
[ESP+0x8] 0012FF44  0040122D  return to for.0040122D from for.00401000
```
![](images/Figure-10.26.jpg)
**图 10.26：** iNumber 在堆栈上递增

### ▼ 第 35-37 行
```
$LN3@main:
cmp DWORD PTR _iNumber$[ebp], 10  ; 0000000aH
jg SHORT $LN4@main
```
此 ASM 代码对应于以下 C/C++ 代码第 9 行，该行比较 `iNumber` 与 10 (`0x0A`)。
```
for (iNumber = 1 ; iNumber <= 10 ; iNumber = iNumber + 2)
```
