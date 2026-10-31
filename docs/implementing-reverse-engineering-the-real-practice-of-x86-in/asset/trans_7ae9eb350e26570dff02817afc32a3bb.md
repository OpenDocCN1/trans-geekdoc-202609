
```
[ESP+0x2C] 0012FF34 0012FF48 JUNK
[ESP+0x30] 0012FF38 004028DE JUNK
[ESP+0x34] 0012FF3C 0040345B JUNK
[ESP+0x38] 0012FF40 85D99E8B XOR of Stack Cookie and ESP is stored here
[ESP+0x3C] 0012FF44 004012B4 return to structures-optimized.004012B4
```

![](images/Figure-12.15.jpg)

### 图 12.15：栈 Cookie

### 第 34-37 行

```
; Line 18
mov eax, DWORD PTR $SG5660
mov ecx, DWORD PTR $SG5660+4
mov dl, BYTE PTR $SG5660+8
```

这些指令将 `rgName` 数组的前 4 个字节以小端格式移入 `EAX` 寄存器，将接下来的 4 个字节移入 `ECX` 寄存器。空终止字符被移入 `DL` 寄存器。

### 第 38-61 行

```
; Line 22
push 1
mov DWORD PTR _user$[esp+64], eax
xor eax, eax
push -691168947    ; d6cd994dH
mov DWORD PTR _user$[esp+77], eax
mov DWORD PTR _user$[esp+81], eax
mov DWORD PTR _user$[esp+85], eax
mov DWORD PTR _user$[esp+89], eax
mov DWORD PTR _user$[esp+93], eax
mov DWORD PTR _user$[esp+97], eax
mov DWORD PTR _user$[esp+101], eax
mov WORD PTR _user$[esp+105], ax
mov BYTE PTR _user$[esp+107], al
push 30     ; 0000001eH
lea eax, DWORD PTR _user$[esp+72]
push eax
push OFFSET $SG5662
mov DWORD PTR _user$[esp+84], ecx
mov BYTE PTR _user$[esp+88], dl
mov DWORD PTR _user$[esp+120], 30  ; 0000001eH
mov DWORD PTR _user$[esp+128], -691168947 ; d6cd994dH
mov DWORD PTR _user$[esp+132], 1
call _printf
```

在非优化部分，我们看到如何通过引用 `EBP` 来访问栈上的结构元素。在前面的 ASM 代码中，栈也是通过使用 `ESP+offset` 引用栈内存来填充结构元素。同样，对于第一次 `printf` 函数调用，参数会被压入栈中。调用 `printf` 前的栈状态如下：

```
[ESP]  0012FEF4  0040814C  "\n%s %d %llu", argument to printf() is pushed here
[ESP+0x4] 0012FEF8  0012FF08  pointer to rgName array is pushed here
[ESP+0x8] 0012FEFC  0000001E  iAge value is pushed here
[ESP+0xC] 0012FF00  D6CD994D  uMobile value is pushed here
[ESP+0x10] 0012FF04  00000001  uMobile value is pushed here
[ESP+0x14] 0012FF08  6574694A  4 bytes of array, rgName in little-endian etiJ
[ESP+0x18] 0012FF0C  7265646E  4 bytes of array, rgName in little-endian redn
[ESP+0x1C] 0012FF10  00000000  String terminator with NULL values in array
[ESP+0x20] 0012FF14  00000000  NULL values in char array of size 40 bytes
[ESP+0x24] 0012FF18  00000000  NULL values in char array of size 40 bytes
[ESP+0x28] 0012FF1C  00000000  NULL values in char array of size 40 bytes
[ESP+0x2C] 0012FF20  00000000  NULL values in char array of size 40 bytes
[ESP+0x30] 0012FF24  00000000  NULL values in char array of size 40 bytes
[ESP+0x34] 0012FF28  00000000  NULL values in char array of size 40 bytes
[ESP+0x38] 0012FF2C  00000000  rgName from 0x0012FF08 to 0x0012FF30, total 40 bytes
[ESP+0x3C] 0012FF30  0000001E  Second element of Structure, iAge is stored here
[ESP+0x40] 0012FF34  0012FF48  Pointer to structure is stored here, puser
[ESP+0x44] 0012FF38  D6CD994D  4 bytes of uMobile stored here
[ESP+0x48] 0012FF3C  00000001  remaining 4 bytes of uMobile stored here
[ESP+0x4C] 0012FF40  85D99E8B  XOR of Stack Cookie and EAX is stored here
[ESP+0x50] 0012FF44  004012B4  return to structures-optimized.004012B4
```

![](images/Figure-12.16.jpg)

### 图 12.16：调用 printf 前的栈状态

### 第 62-72 行

```
; Line 23
mov ecx, DWORD PTR _user$[esp+132]
mov edx, DWORD PTR _user$[esp+128]
mov eax, DWORD PTR _user$[esp+120]
push ecx
push edx
push eax
lea ecx, DWORD PTR _user$[esp+92]
push ecx
push OFFSET $SG5663
call _printf
```

前三个 `MOV` 和 `PUSH` 指令将 `uMobile` 和 `iAge` 值压入栈中。加载有效地址 (`LEA`) 将结构指针移入 `ECX` 寄存器，然后再移入栈中。现在，我们已将所有三个 `printf` 参数放在栈上。可以调用 `printf` 函数。调用第二个 `printf` 前的栈状态如下：

```
[ESP]  0012FEE0  00408158  "\n%s %d %llu", arg to 2nd printf() pushed here
[ESP+0x4] 0012FEE4  0012FF08  pointer to rgName array is pushed here
[ESP+0x8] 0012FEE8  0000001E  iAge value is pushed here
[ESP+0x0C] 0012FEEC  D6CD994D  uMobile value is pushed here
[ESP+0x10] 0012FEF0  00000001  uMobile value is pushed here
[ESP+0x14] 0012FEF4  0040814C  "\n%s %d %llu", arg to 1st printf() pushed here
[ESP+0x18] 0012FEF8  0012FF08  pointer to rgName array is pushed here
[ESP+0x1C] 0012FEFC  0000001E  iAge value is pushed here
[ESP+0x20] 0012FF00  D6CD994D  uMobile value is pushed here
[ESP+0x24] 0012FF04  00000001  uMobile value is pushed here
[ESP+0x28] 0012FF08  6574694A  4 bytes of array, rgName in little-endian etiJ
[ESP+0x2C] 0012FF0C  7265646E  4 bytes of array, rgName in little-endian redn
[ESP+0x30] 0012FF10  00000000  String terminator with NULL in remaining array
[ESP+0x34] 0012FF14  00000000  NULL values in char array of size 40 bytes
[ESP+0x38] 0012FF18  00000000  NULL values in char array of size 40 bytes
[ESP+0x3C] 0012FF1C  00000000  NULL values in char array of size 40 bytes
[ESP+0x40] 0012FF20  00000000  NULL values in char array of size 40 bytes
[ESP+0x44] 0012FF24  00000000  NULL values in char array of size 40 bytes
[ESP+0x48] 0012FF28  00000000  NULL values in char array of size 40 bytes
[ESP+0x4C] 0012FF2C  00000000  rgName from 0x0012FF08 to 0x0012FF30, total 40 bytes
[ESP+0x50] 0012FF30  0000001E  Second element of Structure, iAge is stored here
[ESP+0x54] 0012FF34  0012FF48  Pointer to structure is stored here, puser
[ESP+0x58] 0012FF38  D6CD994D  4 bytes of uMobile stored here
[ESP+0x6C] 0012FF3C  00000001  remaining 4 bytes of uMobile stored here
[ESP+0x64] 0012FF40  85D99E8B  XOR of Stack Cookie and EAX is stored here
[ESP+0x68] 0012FF44  004012B4  return to structures-optimized.004012B4
```

![](images/Figure-12.17.jpg)

### 图 12.17：调用第二个 printf 前的栈状态

### 第 73-83 行

```
; Line 26
mov ecx, DWORD PTR __$ArrayPad$[esp+100]
add esp, 40     ; 00000028H
xor ecx, esp
xor eax, eax
call @__security_check_cookie@4
add esp, 60     ; 0000003cH
ret 0
_main ENDP
_TEXT ENDS
END
```

其余的 ASM 代码相同，其中使用 `ADD` 指令清理栈以匹配缓冲区溢出的栈 cookie。最后，在调用 `security_check_cookie` 过程后，栈再次被清理以返回 0，从而结束 `main` 函数、`TEXT` 段和代码。`x32dbg` 中的栈状态如下：

```
[ESP-0x40] 0012FF08  6574694A   Now JUNK
[ESP-0x38] 0012FF0C  7265646E   Now JUNK
[ESP-0x34] 0012FF10  00000000   Now JUNK
[ESP-0x30] 0012FF14  00000000   Now JUNK
[ESP-0x2C] 0012FF18  00000000   Now JUNK
[ESP-0x28] 0012FF1C  00000000   Now JUNK
[ESP-0x24] 0012FF20  00000000   Now JUNK
[ESP-0x20] 0012FF24  00000000   Now JUNK
[ESP-0x1C] 0012FF28  00000000   Now JUNK
[ESP-0x18] 0012FF2C  00000000   Now JUNK
[ESP-0x14] 0012FF30  0000001E   Now JUNK
[ESP-0x10] 0012FF34  0012FF48   Now JUNK
[ESP-0x0C] 0012FF38  D6CD994D   Now JUNK
[ESP-0x08] 0012FF3C  00000001   Now JUNK
[ESP-0x04] 0012FF40  85D99E8B   Now JUNK
[ESP]  0012FF44  004012B4   return to structures-optimized.004012B4
```

![](images/Figure-12.18.jpg)

### 图 12.18：栈已被清理

## 结论
