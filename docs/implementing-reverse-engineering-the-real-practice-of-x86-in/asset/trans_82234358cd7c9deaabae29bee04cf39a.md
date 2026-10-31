
```
[ESP+0x3C] 0012FF3C  0040345B  Right now JUNK, space for local variables
[ESP+0x40] 0012FF40  0012FF88  [EBP]
[ESP+0x44] 0012FF44  004012B3  return to structures.004012B3
```

![](images/Figure-12.6.jpg)

### 图 12.6：堆栈 cookie

### 第 37-56 行

```
; Line 18
mov eax, DWORD PTR $SG5660
mov DWORD PTR _user$[ebp], eax
mov ecx, DWORD PTR $SG5660+4
mov DWORD PTR _user$[ebp+4], ecx
mov dl, BYTE PTR $SG5660+8
mov BYTE PTR _user$[ebp+8], dl
xor eax, eax
mov DWORD PTR _user$[ebp+9], eax
mov DWORD PTR _user$[ebp+13], eax
mov DWORD PTR _user$[ebp+17], eax
mov DWORD PTR _user$[ebp+21], eax
mov DWORD PTR _user$[ebp+25], eax
mov DWORD PTR _user$[ebp+29], eax
mov DWORD PTR _user$[ebp+33], eax
mov WORD PTR _user$[ebp+37], ax
mov BYTE PTR _user$[ebp+39], al
mov DWORD PTR _user$[ebp+40], 30  ; 0000001eH
mov DWORD PTR _user$[ebp+48], -691168947 ; d6cd994dH
mov DWORD PTR _user$[ebp+52], 1
; Line 18
```

此注释说明其前面的 ASM 指令将代表 C/C++ 代码的第 18 行，即：

`struct SSubscriber user = {"Jitender", 30, 7898765645};    // Structure Variable`

在 ASM 代码中，我们看到多个 `MOV` 指令。要理解这些指令，我们必须理解结构的元素始终存储在连续的内存位置中。所有 `MOV` 指令都将结构的元素存储到堆栈上。为了理解堆栈状态，让我们首先以十六进制表示形式列出结构的每个元素，如下所示：

`char rgName[40]; = 40 bytes = Jitender (0x4A6974656E646572)`

| 4A || 69 || 74 || 65 || 6e || 64 || 65 || 72 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 || 00 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

`int iAge; = 4 bytes = 30 (0x0000001E)`

| 00 || 00 || 00 || 1E |
| --- | --- | --- | --- |

`unsigned long long uMobile; = 8 bytes = 7898765645 (0x00000001D6CD994D)`

| 00 || 00 || 00 || 01 || D6 || CD || 99 || 4D |
| --- | --- | --- | --- | --- | --- | --- | --- |

执行完所有 `MOV` 指令后，堆栈状态如下：

```
[ESP]  0012FF00  6574694A  4 bytes of array, rgName in little-endian etiJ
[ESP+0x04] 0012FF04  7265646E  4 bytes of array, rgName in little-endian redn
[ESP+0x08] 0012FF08  00000000  String terminator with NULL in remaining array
[ESP+0x0C] 0012FF0C  00000000  NULL values in char array of size 40 bytes
[ESP+0x10] 0012FF10  00000000  NULL values in char array of size 40 bytes
[ESP+0x14] 0012FF14  00000000  NULL values in char array of size 40 bytes
[ESP+0x18] 0012FF18  00000000  NULL values in char array of size 40 bytes
[ESP+0x1C] 0012FF1C  00000000  NULL values in char array of size 40 bytes
[ESP+0x20] 0012FF20  00000000  NULL values in char array of size 40 bytes
[ESP+0x24] 0012FF24  00000000  array from 0x0012FF00 to 0x0012FF28, total 40 bytes
[ESP+0x28] 0012FF28  0000001E  Second element of Structure, iAge is stored here
[ESP+0x2C] 0012FF2C  004054C0  return to 0x004054C0 from 0x00405477
[ESP+0x30] 0012FF30  D6CD994D  4 bytes of uMobile stored here
[ESP+0x34] 0012FF34  00000001  remaining 4 bytes of uMobile stored here
[ESP+0x38] 0012FF38  01D7D682  XOR of Stack Cookie and EAX is stored here
[ESP+0x3C] 0012FF3C  0040345B  structures.0040345B
[ESP+0x40] 0012FF40  0012FF88  [EBP]
[ESP+0x44] 0012FF44  004012B3  return to 0x004012B3 from 0x00401000
```

![](images/Figure-12.7.jpg)

### 图 12.7：执行完所有 MOV 指令后的堆栈

### 第 57-59 行

```
; Line 21
lea ecx, DWORD PTR _user$[ebp]
mov DWORD PTR _puser$[ebp], ecx
```

此注释说明其前面的 ASM 指令将代表 C/C++ 代码的第 21 行，即：

`puser = &user;`

在 ASM 代码中，结构指针使用加载有效地址指令推入 `ECX` 寄存器。结构指针指向结构的第一个元素，因为结构始终存储在连续的内存位置中。

`MOV` 指令将把结构指针推到堆栈的 `[EBP-0x04]` 处。此指令后的堆栈状态如下：

```
[ESP]  0012FF00  6574694A  4 bytes of array, rgName in little-endian etiJ
[ESP+0x04] 0012FF04  7265646E  4 bytes of array, rgName in little-endian redn
[ESP+0x08] 0012FF08  00000000  String terminator with NULL in remaining array
[ESP+0x0C] 0012FF0C  00000000  NULL values in char array of size 40 bytes
[ESP+0x10] 0012FF10  00000000  NULL values in char array of size 40 bytes
[ESP+0x14] 0012FF14  00000000  NULL values in char array of size 40 bytes
[ESP+0x18] 0012FF18  00000000  NULL values in char array of size 40 bytes
[ESP+0x1C] 0012FF1C  00000000  NULL values in char array of size 40 bytes
[ESP+0x20] 0012FF20  00000000  NULL values in char array of size 40 bytes
[ESP+0x24] 0012FF24  00000000  rgName from 0x0012FF00 to 0x0012FF28, total 40 bytes    
[ESP+0x28] 0012FF28  0000001E  Second element of Structure, iAge is stored here
[ESP+0x2C] 0012FF2C  004054C0  return to 0x004054C0 from 0x00405477
[ESP+0x30] 0012FF30  D6CD994D  4 bytes of uMobile stored here
[ESP+0x34] 0012FF34  00000001  remaining 4 bytes of uMobile stored here
[ESP+0x38] 0012FF38  01D7D682  XOR of Stack Cookie and EAX is stored here
[ESP+0x3C] 0012FF3C  0012FF00  Pointer to structure is stored here, puser
[ESP+0x40] 0012FF40  0012FF88  [EBP]
[ESP+0x44] 0012FF44  004012B3   return to 0x004012B3 from 0x00401000
```

![](images/Figure-12.8.jpg)

### 图 12.8：堆栈上的结构指针

### 第 60-71 行

```
; Line 22
mov edx, DWORD PTR _user$[ebp+52]
push edx
mov eax, DWORD PTR _user$[ebp+48]
push eax
mov ecx, DWORD PTR _user$[ebp+40]
push ecx
lea edx, DWORD PTR _user$[ebp]
push edx
push OFFSET $SG5662
call _printf
add esp, 20     ; 00000014H
```

此注释说明其前面的 ASM 指令将代表 C/C++ 代码的第 22 行，即：

`printf("\n%s %d %llu", user.rgName, user.iAge, user.uMobile);`

在 ASM 代码中，我们将所有参数逐一推入堆栈，然后进行对 `printf` 函数的调用。调用 `printf` 函数之前的堆栈状态如下：

```
[ESP]  0012FEEC  0040814C  "\n%s %d %llu", argument to printf() is pushed here
[ESP+0x04] 0012FEF0  0012FF00  pointer to rgName array is pushed here
[ESP+0x08] 0012FEF4  0000001E  iAge value is pushed here
[ESP+0x0C] 0012FEF8  D6CD994D  uMobile value is pushed here
[ESP+0x10] 0012FEFC  00000001  uMobile value is pushed here
[ESP+0x14] 0012FF00  6574694A  4 bytes of array, rgName in little-endian etiJ
[ESP+0x18] 0012FF04  7265646E  4 bytes of array, rgName in little-endian redn
[ESP+0x1C] 0012FF08  00000000  String terminator with NULL in remaining array
[ESP+0x20] 0012FF0C  00000000  NULL values in char array of size 40 bytes
[ESP+0x24] 0012FF10  00000000  NULL values in char array of size 40 bytes
[ESP+0x28] 0012FF14  00000000  NULL values in char array of size 40 bytes
[ESP+0x2C] 0012FF18  00000000  NULL values in char array of size 40 bytes
[ESP+0x30] 0012FF1C  00000000  NULL values in char array of size 40 bytes
[ESP+0x34] 0012FF20  00000000  NULL values in char array of size 40 bytes
[ESP+0x38] 0012FF24  00000000  rgName from 0x0012FF00 to 0x0012FF28, total 40 bytes    
[ESP+0x3C] 0012FF28  0000001E  Second element of Structure, iAge is stored here
[ESP+0x40] 0012FF2C  004054C0  return to 0x004054C0 from 0x00405477
[ESP+0x44] 0012FF30  D6CD994D  4 bytes of uMobile stored here
```
