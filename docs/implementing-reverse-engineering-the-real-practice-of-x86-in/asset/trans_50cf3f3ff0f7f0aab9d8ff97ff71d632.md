
```
[ESP+0x2C] 0012FF40  13789938  XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B  ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.19.jpg)

### 图 11.19：旧 ESI 值被保留

## 第 32-44 行

```
; Line 8
xor esi, esi
mov DWORD PTR _iArray$[esp+48], esi
mov DWORD PTR _iArray$[esp+52], 1
mov DWORD PTR _iArray$[esp+56], 2
mov DWORD PTR _iArray$[esp+60], 3
mov DWORD PTR _iArray$[esp+64], 4
mov DWORD PTR _iArray$[esp+68], 5
mov DWORD PTR _iArray$[esp+72], 6
mov DWORD PTR _iArray$[esp+76], 7
mov DWORD PTR _iArray$[esp+80], 8
mov DWORD PTR _iArray$[esp+84], 9
npad 3
```

第 8 行的 C/C++ 代码初始化 `iArray`：
`int iArray[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};`

在 ASM 代码中，`XOR` 指令将 `ESI` 寄存器重置为 `0x00`，然后将 `ESI` 移动到 `[ESP+0x04]` 位置作为 `iArray` 的第一个元素。所有其他 `MOV` 指令将 `iArray` 的剩余元素推送到堆栈上。

我们看到 `npad` 宏，它插入非破坏性和非操作指令，而不是一系列 NOP 指令。`Npad 3` 对应于 `lea ecx, [ecx+00]`。有关 `npad` 的更多详细信息，请参阅附录。`npad` 宏执行后立即的堆栈状态如下：

```
[ESP]  0012FF14  00000000   old ESI value is preserved here
[ESP+0x04] 0012FF18  00000000   iArray first element pushed here
[ESP+0x08] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x0C] 0012FF20  00000002   iArray third element pushed here
[ESP+0x010] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x014] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x18] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x1C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x20] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x24] 0012FF38  00000008   iArray ninth element pushed here
[ESP+0x28] 0012FF3C  00000009   iArray tenth element pushed here
[ESP+0x2C] 0012FF40  13789938   XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B   ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.20.jpg)

### 图 11.20：npad 之后的堆栈状态

## 第 45-55 行

```
$LL3@main:
; Line 12
mov eax, DWORD PTR _iArray$[esp+esi*4+48]
push eax
push esi
push OFFSET $SG4682
call _printf
inc esi
add esp, 12     ; 0000000cH
cmp esi, 10     ; 0000000aH
jl SHORT $LL3@main
```

C/C++ 代码的第 12 行在屏幕上打印 `iArray` 的元素以及索引。
`printf ("iArray[%d]=%d\n", iLoop, iArray[iLoop]);`

同样的概念在上一节中已在未优化的情况下讨论过。`printf` 函数接受三个参数来打印屏幕上的 `iArray` 元素和索引。因此，在调用 `printf` 函数之前，这三个参数都需要被压入堆栈。

在 ASM 代码中，第一个被压入堆栈的参数将是 `iArray[iLoop]`。为了将该值压入堆栈，存储在 `ESI` 寄存器中的 `iLoop` 值乘以 4（整数的大小），然后加上 `_iArray$` 宏和 48 字节的偏移量，以计算为特定 `iLoop` 值存储的元素的内存位置。因此，在第一次迭代时，当存储在 `ESI` 中的 `iLoop` = 0 时，第一个 `MOV` 指令的结果为：
`mov eax, DWORD PTR _iArray$[esp+esi*4+48]`
`mov eax, dword ptr ss:[esp+esi*4+0x4], as ESI = 0`
`mov eax, dword ptr ss:[esp+0x4]`

这将使我们得到 `EAX` 寄存器中的第一个数组元素的值。因此，通过将 `EAX` 压入堆栈，我们将 `printf` 的第一个参数压入了堆栈。

`printf` 的下一个参数是 `iLoop` 值。它是通过压入 `ESI` 寄存器来压入堆栈的。

最后一个参数，即字符串常量，是由 `push OFFSET $SG4682` 压入的。

现在三个参数都在堆栈上，`printf` 被调用。此时堆栈如下：

```
[ESP]  0012FF08  00408140   "iArray[%d]=%d\n", string argument to printf
[ESP+0x04] 0012FF0C  00000000   iLoop value, ESI is pushed as printf argument
[ESP+0x08] 0012FF10  00000000   iArray first element is pushed as printf argument
[ESP+0x0C] 0012FF14  00000000   old ESI value is preserved here
[ESP+0x10] 0012FF18  00000000   iArray first element pushed here
[ESP+0x14] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x18] 0012FF20  00000002   iArray third element pushed here
[ESP+0x1C] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x20] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x24] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x2C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x30] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x34] 0012FF38  00000008   iArray ninth element pushed here
```
![](images/Figure-11.21.jpg)

### 图 11.21：printf 的参数在堆栈上

`INC` 指令将递增 `ESI` 寄存器。这意味着它递增存储在 `ESI` 中的 `iLoop` 值。

`ADD` 指令通过 12 字节清理堆栈。接下来，`ESI` 与 `10 (0x0A)` 进行比较。此时，`CMP` 指令将执行有符号比较跳转到标签 `$LL3@main`，因为 `ESI` 处的 `iLoop` 小于 `10(0x0A)`。小于时跳转 `JL` 后的堆栈状态如下：

```
[ESP-0x0C] 0012FF08  00408140   Now JUNK
[ESP-0x08] 0012FF0C  00000000   Now JUNK
[ESP-0x04] 0012FF10  00000000   Now JUNK
[ESP]  0012FF14  00000000   old ESI value is preserved here
[ESP+0x04] 0012FF18  00000000   iArray first element pushed here
[ESP+0x08] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x0C] 0012FF20  00000002   iArray third element pushed here
[ESP+0x010] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x014] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x18] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x1C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x20] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x24] 0012FF38  00000008   iArray ninth element pushed here
[ESP+0x28] 0012FF3C  00000009   iArray tenth element pushed here
[ESP+0x2C] 0012FF40  13789938   XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B   ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.22.jpg)

### 图 11.22：JL 之后的堆栈状态

现在，假设我们对指令迭代了 10 次，并且 `ESI` 处的 `iLoop` 值已变为 `10 (0x0A)`。此时，`CMP` 指令将导致 `ZF=1`，并且不会跳转到 `$LL3@main` 标签。指令指针将移动到下一条指令。此阶段的堆栈状态将为：

```
[ESP-0x0C] 0012FF08  00408140   Now JUNK
[ESP-0x08] 0012FF0C  00000009   Now JUNK
[ESP-0x04] 0012FF10  00000009   Now JUNK
[ESP]  0012FF14  00000000   old ESI value is preserved here
[ESP+0x04] 0012FF18  00000000   iArray first element pushed here
[ESP+0x08] 0012FF1C  00000001   iArray second element pushed here
[ESP+0x0C] 0012FF20  00000002   iArray third element pushed here
[ESP+0x010] 0012FF24  00000003   iArray forth element pushed here
[ESP+0x014] 0012FF28  00000004   iArray fifth element pushed here
[ESP+0x18] 0012FF2C  00000005   iArray sixth element pushed here
[ESP+0x1C] 0012FF30  00000006   iArray seventh element pushed here
[ESP+0x20] 0012FF34  00000007   iArray eighth element pushed here
[ESP+0x24] 0012FF38  00000008   iArray ninth element pushed here
[ESP+0x28] 0012FF3C  00000009   iArray tenth element pushed here
[ESP+0x2C] 0012FF40  13789938   XOR of stack cookie and ESP is stored here
[ESP+0x30] 0012FF44  0040128B   ESP before ‘sub esp, 44’ instruction
```
![](images/Figure-11.23.jpg)
