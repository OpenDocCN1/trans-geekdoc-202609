
## PUSHFD
指令格式：
`PUSHFD`
**含义：**
此指令将标志寄存器压入堆栈。
**影响的标志：** 无

## POP
指令格式：
`POP DESTINATION_OPERAND`
**含义：**
`POP` 从堆栈顶部检索值并将其复制到目的操作数。它递增 `ESP` 寄存器。
**影响的标志：** 无

## POPAD
指令格式：
`POPAD`
**含义：**
此指令弹出堆栈的值并将其复制到所有寄存器。寄存器按 `EDI`、`ESI`、`EBP`、`ESP`、`EDX`、`ECX` 和 `EAX` 的顺序弹出。`ESP` 值在 `POPAD` 中被忽略。
**影响的标志：** 无

## POPFD
指令格式：
`POPFD`
**含义：**
此指令从堆栈弹出 DWORD 到标志寄存器。
**影响的标志：** 无

## RET
指令格式：
`RET [nBytes]`
**含义：**
当一个函数调用另一个函数时，调用另一个函数的函数称为‘调用者’，而被调用的函数称为‘被调用者’。`RET` 将控制权从被调用者转移到调用者，到堆栈上保存的返回地址。`nBytes` 是可选的；当提到 `nBytes` 时，表示释放 n 个字节以清理堆栈。

# 数据传输指令
这些是用于数据传输操作的通用指令。

## MOV
**指令格式：**
`MOV DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**
将数据从源操作数移动到目的操作数，结果存储在目的操作数中。
**影响的标志：** 无

## LEA
指令格式：
`LEA REGISTER OPERAND`
**含义：**
`LEA` 代表加载有效地址，它将操作数的内存地址加载到寄存器中。
**影响的标志：** 无

## XCHG
指令格式：
`XCHG DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**
`XCHG` 指令在源操作数和目的操作数之间交换值。
**影响的标志：** 无

## CMPXCHG
**指令格式：**
`CMPXCHG DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**
此指令用于比较和交换。`EAX` 与 `DESTINATION_OPERAND` 进行比较，
如果 `EAX` 等于 `DESTINATION_OPERAND` 则 `DESTINATION_OPERAND` 用 `SOURCE_OPERAND` 加载。
如果 `EAX` 不等于 `DESTINATION_OPERAND` 则 `EAX` 用 `DESTINATION_OPERAND` 加载。
**影响的标志：** `CF` `ZF` `SF` `AF` `PF` `OF`

## LAHF
**指令格式：**
`LAHF`
**含义：**
此指令从标志中加载 `AH`。它将状态复制到 `AH` 寄存器，并且只有 5 个标志被复制到 `AH` 寄存器的位 7、6、4、2 和 0；`AH` 寄存器的位 5、3 和 1 将不受影响。
运行此指令后 `AH` 寄存器：
![](images/Figure-4.3.jpg)
**图 4.3：** 从标志加载 AH
**影响的标志：** 无

## SAHF
指令格式：
`SAHF`
**含义：**
它将 `AH` 存储到标志中。此指令将 `AH` 寄存器的位（位 7、6、4、2 和 0）复制到 `SF`、`ZF`、`AF`、`PF` 和 `CF` 标志。
**影响的标志：** `SF`、`ZF`、`AF`、`PF` 和 `CF`

## LAR
**指令格式：**
`LAR DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**
从 `SOURCE_OPERAND` 指定的段描述符加载有效权限到 `DESTINATION_OPERAND` 中。
**影响的标志：** `ZF`

## MOVSX
指令格式：
`MOVSX DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**
带符号扩展的移动。假设你有一个较小的值并想将其复制到一个大寄存器。在这种情况下，我们将使用 `MOVSX`；它将 `SOURCE_OPERAND` 复制到 `DESTINATION_OPERAND` 并用符号位填充 `SOURCE_OPERAND` 未提供的位。
**影响的标志：** 无

## MOVZX
**指令格式：**
`MOVZX DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**
带零扩展的移动。假设你有一个较小的值并想将其复制到一个大寄存器。在这种情况下，我们将使用 `MOVSX`；它将 `SOURCE_OPERAND` 复制到 `DESTINATION_OPERAND` 并用零填充 `SOURCE_OPERAND` 未提供的位。
**影响的标志：** 无

## XLAT
**指令格式：**
`XLAT`
**含义：**
`XLAT` 指令用表项替换 `AL` 寄存器的表索引。它将 `AL` 设置为 `DS:[EBX + unsigned AL]`。`AL` 的值被视为无符号索引，加上 `EBX` 寄存器以获取表项。`EBX` 包含表的基地址。

## MOVS
**指令格式：**
`MOVS DESTINATION_STRING SOURCE_STRING`
**含义：**
此指令将数据（字节、字、双字）从 `SOURCE_STRING` 复制到 `DESTINATION_STRING`，其中：
`SOURCE_STRING` 由 `DS:SI`（或 `ESI`）指向
`DESTINATION_STRING` 由 `ES:DI`（或 `EDI`）指向
`SI` 是 **数据段** `DS` 中的偏移地址
`DI` 是 **附加段** `ES` 中的偏移地址
**影响的标志：** 无

# 算术指令
这些指令用于汇编语言中的算术运算。

## AAA
指令格式：
`AAA`
**含义：**
此指令在加法后调整 ASCII。`AAA` 指令用于在两个未打包 BCD 数字相加（`ADD` 指令）之后。未打包 BCD 数字是 ASCII 单数字 0 到 9 或 0x30 到 0x39。当 `AAA` 指令在 `ADD` 指令之后使用时，它将结果转换为两位 BCD 数字。有关 ASCII 代码，请参阅 *附录*。
当两个 ASCII 编码的数字相加时，结果不是 ASCII。要将其转换为 ASCII，在 `ADD` 之后使用 `AAA`。
**影响的标志：** `AF` `CF` (`SF`,`ZF`,`OF`,`PF` 未定义)
**示例**
```
XOR AH, AH        ;clear AH register
MOV AL, 32H      ;move ASCII 2 in AL
ADD AL, 39H      ;add ASCII 9, the result should be ASCII 11, but we get 6B in AL
AAA                     ;AH=0x01, AL=0x01 and AX=0x0101
```

## AAS
指令格式：
`AAS`
**含义：**
指令在减法后调整 ASCII。`AAS` 指令用于在两个未打包 BCD 数字相减（`SUB` 指令）之后。未打包 BCD 数字是 ASCII 单数字 0 到 9 或 0x30 到 0x39。当 `AAS` 指令在 `SUB` 指令之后使用时，它将结果转换为两位 BCD 数字。
**影响的标志：** `AF` `CF` (`SF`,`ZF`,`OF`,`PF` 未定义)

## AAD
**指令格式：**
`AAD`
**含义：**
除法前调整 ASCII。此指令在除法指令之前使用，以将 `AH` 和 `AL` 中的未打包 BCD 数字转换为二进制等价物。商将保存在 `AL` 中，余数将保存在 `AH` 中；两者都是未打包 BCD。
**影响的标志：** `PF`、`SF`、`ZF`
**示例**
将 68 除以 8。
```
MOV AX, 0608H      ;AH=0x06, AL=0x08 and AX=0x0608
MOV CH, 08H          ;divide ASCII 8, the result should be 8 in quotient and 4 in remainder
AAD                          ;AX = 0044 = 44H = 68
DIV CH                     ;Divide AX by in CH, result: AL = 08, AH = 04 unpacked BCD
```

## AAM
指令格式：
`AAM`
**含义：**
乘法时调整 ASCII。此指令用于两个 ASCII 数字的乘法。当未打包 BCD 数字相乘时，存储在 `AX` 中的结果转换为 `AH` 和 `AL` 中的未打包 BCD 数字。
**影响的标志：** `PF`、`SF`、`ZF`
**示例**
```
MOV AL, 00000111      ;move 7 in AL, masking upper 4 bits
MOV BH, 00000101     ;move 5 in BH, masking upper 4 bits
MUL BH                        ;AX = 23H, 35 in decimal
AAM                              ;result: AX = 0203H, AH = 02H, AL = 03H unpacked BCD
```

## ADC
指令格式：
`ADC DESTINATION_OPERAND SOURCE_OPERAND`
**含义：**

