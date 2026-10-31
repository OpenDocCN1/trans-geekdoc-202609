
现在，假设我们对指令迭代了 9 次，并且 `iLoop` 的值已变为 `10 (0x0A)`。此时，`CMP` 指令将执行有符号比较跳转，因为位于 `[EBP-0x04]` 的 `iLoop` 等于 `10(0x0A)`，并且它还会设置 `ZF=1`。由于 `iLoop` 为 `10(0xA),` 因此跳转将发生到 `$LN1@main` 标签。`JGE` 之后的堆栈状态如下：

```
[ESP-0x0C] 0012FF04  00408140  [EBP-0x40] NOW JUNK
[ESP-0x8] 0012FF08  00000009  [EBP-0x38] NOW JUNK
[ESP-0x4] 0012FF0C  00000009  [EBP-0x34] NOW JUNK
[ESP]  0012FF10  00000000  [EBP-0x30] iArray first element
[ESP+0x4] 0012FF14  00000001  [EBP-0x2C] iArray second element
[ESP+0x8] 0012FF18  00000002  [EBP-0x28] iArray third element
[ESP+0xC] 0012FF1C  00000003  [EBP-0x24] iArray forth element
[ESP+0x10] 0012FF20  00000004  [EBP-0x20] iArray fifth element
[ESP+0x14] 0012FF24  00000005  [EBP-0x1C] iArray sixth element
[ESP+0x18] 0012FF28  00000006  [EBP-0x18] iArray seventh element
[ESP+0x1C] 0012FF2C  00000007  [EBP-0x14] iArray eighth element
[ESP+0x20] 0012FF30  00000008  [EBP-0x10] iArray ninth element
[ESP+0x24] 0012FF34  00000009  [EBP-0x0C] iArray tenth element
[ESP+0x28] 0012FF38  ED59748F  [EBP-0x08] Stack Cookie xor EBP value placed
[ESP+0x2C] 0012FF3C  0000000A  [EBP-0x04] iLoop placeholder here
[ESP+0x30] 0012FF40  0012FF88  [EBP]
[ESP+0x34] 0012FF44  00401299  return to array.00401299 from array.00401000
```

**图 11.12：** `JGE` 之后的堆栈状态

### 第 65-77 行

```
$LN1@main:
; Line 14
xor eax, eax
; Line 15
mov ecx, DWORD PTR __$ArrayPad$[ebp]
xor ecx, ebp
call @__security_check_cookie@4
mov esp, ebp
pop ebp
ret 0
_main ENDP
_TEXT ENDS
END
```

在此标签处，`EAX` 使用 `XOR` 置零，以根据 C/C++ 代码第 14 行返回 0。

在函数尾声之前会检查 Security Cookie，首先将存储在 `[EBP-0x08]` 的 Security Cookie 移动到 `ECX`，然后用 `EBP` 对 `ECX` 进行 `XOR`。会调用 `security_check_cookie` 过程以防止缓冲区溢出攻击。

存储在 `[EBP-0x08]` 的 Security Cookie = `0xED59748F`

`EBP` = `0x0012FF40`

`ECX XOR EBP` = `0xED59748F` XOR `0x0012FF40` = `0xED4B8BCF`

结果将保存在 `ECX` 中。

如我们所见，此值与生成并存储在 `0x0040B000` 内存位置的值相同。由于我们处理的是小端模式，因此该值以反转顺序存储。此时的堆栈状态与之前相同：

```
[ESP-0x0C] 0012FF04  00408140  [EBP-0x40] NOW JUNK
[ESP-0x8] 0012FF08  00000009  [EBP-0x38] NOW JUNK
[ESP-0x4] 0012FF0C  00000009  [EBP-0x34] NOW JUNK
[ESP]  0012FF10  00000000  [EBP-0x30] iArray first element
[ESP+0x4] 0012FF14  00000001  [EBP-0x2C] iArray second element
[ESP+0x8] 0012FF18  00000002  [EBP-0x28] iArray third element
[ESP+0xC] 0012FF1C  00000003  [EBP-0x24] iArray forth element
[ESP+0x10] 0012FF20  00000004  [EBP-0x20] iArray fifth element
[ESP+0x14] 0012FF24  00000005  [EBP-0x1C] iArray sixth element
[ESP+0x18] 0012FF28  00000006  [EBP-0x18] iArray seventh element
[ESP+0x1C] 0012FF2C  00000007  [EBP-0x14]  iArray eighth element
[ESP+0x20] 0012FF30  00000008  [EBP-0x10] iArray ninth element
[ESP+0x24] 0012FF34  00000009  [EBP-0x0C] iArray tenth element
[ESP+0x28] 0012FF38  ED59748F  [EBP-0x08] Stack Cookie xor EBP value placed
[ESP+0x2C] 0012FF3C  0000000A  [EBP-0x04] iLoop placeholder here
[ESP+0x30] 0012FF40  0012FF88  [EBP]
[ESP+0x34] 0012FF44  00401299  return to array.00401299 from array.00401000
```

**图 11.13：** 调用 `security_check_cookie`

如果我们进入 `call` `@__security_check_cookie@4`，我们可以看到保存在 `ECX` 中的 `XOR` 结果与存储在 `0x0040B000` 的安全 cookie 进行比较。

**图 11.14：** `Security_check_cookie` 函数

由于我们存储在 `0x0040B000` 的安全 cookie 与 `ECX` 中的相同，`ZF=1`，指令指针将返回到 `main` 函数。返回时，会调用函数尾声以结束 `main` 函数、`TEXT` 段和代码。下面是在返回指令之前解释的堆栈状态：

```
[ESP-0x34] 0012FF10  00000000  NOW JUNK
[ESP-0x30] 0012FF14  00000001  NOW JUNK
[ESP-0x2C] 0012FF18  00000002  NOW JUNK
[ESP-0x28] 0012FF1C  00000003  NOW JUNK
[ESP-0x24] 0012FF20  00000004  NOW JUNK
[ESP-0x20] 0012FF24  00000005  NOW JUNK
[ESP-0x1C] 0012FF28  00000006  NOW JUNK
[ESP-0x18] 0012FF2C  00000007  NOW JUNK
[ESP-0x14] 0012FF30  00000008  NOW JUNK
[ESP-0x10] 0012FF34  00000009  NOW JUNK
[ESP-0x0C] 0012FF38  ED59748F  NOW JUNK
[ESP-0x08] 0012FF3C  0000000A  NOW JUNK
[ESP-0x04] 0012FF40  0012FF88  NOW JUNK
[ESP]  0012FF44  00401299  return to array.00401299 from array.00401000
```

**图 11.15：** 堆栈已清理

## 数组循环优化

使用优化标志 `/Ox` 编译代码。在 Windows 命令提示符上运行以下命令以设置 `cl.exe`（VS 编译器）的环境，然后使用以下开关编译代码：

* `/Ox`：启用最大优化
* `/Fa`：输出汇编列表文件的名称
* `/Fe`：输出可执行文件的名称

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\Array\Array
cl Array.cpp /FaArray-Optimized.asm /Ox /FeArray-Optimized.exe
```

以下是在运行上述命令后的输出：

**图 11.16：** 数组循环优化

编译生成 EXE 文件和汇编代码。手动禁用 ASLR。要禁用 ASLR，请使用 CFF explorer 并更改 `DllCharacteristics` 参数以取消选中 `DLL can move`。有关禁用 ASLR 的详细步骤，请参阅 *附录*。

现在，让我们继续查看生成的汇编列表：

**图 11.17：** Array-Optimized.asm-Part-1

**图 11.18：** Array-Optimized.asm-Part-2

启用优化后，ASM 列表中删除了所有不需要的代码。在浏览 ASM 代码时，我们看到标准函数序言和尾声不在优化代码中。因此，所有指令中的 `EBP` 引用都被 `ESP` 替换。

我们将直接跳转到指令，因为我们在前一节中已经介绍了一些常见的 ASM 列表。

### 第 26-31 行

```
; Line 7
sub esp, 44     ; 0000002cH
mov eax, DWORD PTR ___security_cookie
xor eax, esp
mov DWORD PTR __$ArrayPad$[esp+44], eax
push esi
```

`SUB` 指令通过向 `ESP` 添加 `44 (0x2C)` 字节为堆栈上的局部变量创建空间。44 字节来自 `iArray` 的 10 个元素，其中每个元素为 4 字节，以及 4 字节用于在堆栈上存储堆栈 cookie 以防止缓冲区溢出，如前所述。

`MOV` 指令将存储在 `.data` 段中的堆栈 cookie 移动到 `EAX` 寄存器，其中它与 `ESP` 进行 `XOR`。`XOR` 的结果被放置在堆栈上以防止缓冲区溢出利用发生。此 `XOR` 值将在 `main` 函数尾声之前进行检查。

`ESI` 将用于 `iLoop` 变量的占位符；`ESI` 的旧值使用 `PUSH` 指令保存在堆栈上。推送 `ESI` 寄存器后的堆栈状态如下：

```
[ESP]  0012FF14  00000000  old ESI value is preserved here
[ESP+0x04] 0012FF18  0012FF78  JUNK
[ESP+0x08] 0012FF1C  004024D0  JUNK
[ESP+0x0C] 0012FF20  132AFDF8  JUNK
[ESP+0x010] 0012FF24  FFFFFFFE  JUNK
[ESP+0x014] 0012FF28  0040547C  JUNK
[ESP+0x18] 0012FF2C  00405490  JUNK
[ESP+0x1C] 0012FF30  0040342B  JUNK
[ESP+0x20] 0012FF34  0012FF48  JUNK
[ESP+0x24] 0012FF38  004028AE  JUNK
[ESP+0x28] 0012FF3C  0040342B  JUNK
```
