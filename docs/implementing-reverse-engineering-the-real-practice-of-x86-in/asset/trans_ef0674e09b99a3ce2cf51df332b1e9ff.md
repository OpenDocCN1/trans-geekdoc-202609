
## 图 4.15：CMPSB 示例

```
MOV ESI, 0x41000001     ; ESI pointing to STRING1
MOV EDI, 0x82000001     ; ESI pointing to STRING2
MOV ECX, 0x08                ; ECX is initialized to 0x08
CLD                                     ; Clear direction flag, DF=0
REPE CMPSB                   ; Compare two strings until ECX=0 or ZF=0
```

# IN/INSB/INSW/INSD

该指令可视化为 `IN` 表示 Input 输入 + `S` 表示 String 字符串 + `B` 表示 Byte 字节 或 `W` 表示 WORD 字 或 `D` 表示 DWORD 双字 的组合。

### Meaning：

用于在处理器输入/输出端口与外围设备之间传输数据的指令有两种。这两种指令如下：

* `Register input/output instructions`：这些指令在处理器 I/O 端口与寄存器之间移动数据。
* `Block (or string) input/output instructions`：这些指令在处理器 I/O 端口与内存之间移动数据块。

### Register input instruction format：

`IN DESTINATION SOURCE`

其中，`SOURCE` 是端口地址

并且 `DESTNATION` 是寄存器，`EAX`（32-bit）寄存器或 `AX`（16-bit）寄存器或 `AL`（8-bit）寄存器。目标寄存器的长度决定了从输入端口读取的数据量，可以是字节、字或双字。目标也可以是其他通用寄存器。

```
IN EAX, 80    ; It will read dword (32-bits) from port 80 and store it in EAX.
IN AX, 80       ; It will read word (16-bits) from port 80 and store it in AX.
```

### Block (or string) input instruction format：

`INSB/INSW/INSD`

其中处理器输入端口地址指定在 `DX` 寄存器中，目标是 `EDI` 寄存器指向的内存位置。

`INSB` 指令将从 `DX` 寄存器指定的输入端口地址移动一个字节（8 位）数据到 `EDI` 寄存器指向的内存位置。为了在处理器输入端口与内存之间传输数据块，`INSB` 指令与重复前缀 `REP` 一起使用。每次在输入端口与 `EDI` 指向的内存之间传输一个字节后，`EDI` 会在 `DF=0` 时递增，或在 `DF=1` 时递减 1。

`INSW` 指令将从 `DX` 寄存器指定的输入端口地址移动一个字（16 位）数据到 `EDI` 寄存器指向的内存位置。为了在处理器输入端口与内存之间传输数据块，`INSW` 指令与重复前缀 `REP` 一起使用。每次在输入端口与 `EDI` 指向的内存之间传输一个字后，`EDI` 会在 `DF=0` 时递增，或在 `DF=1` 时递减 2。

`INSD` 指令将从 `DX` 寄存器指定的输入端口地址移动一个双字（32 位）数据到 `EDI` 寄存器指向的内存位置。为了在处理器输入端口与内存之间传输数据块，`INSD` 指令与重复前缀 `REP` 一起使用。每次在输入端口与 `EDI` 指向的内存之间传输一个双字后，`EDI` 会在 `DF=0` 时递增，或在 `DF=1` 时递减 4。

### Flags Affected：

无

### Example

```
MOV DX, PORT_ADDRESS    ; Move the input port address to the DX register
MOV EDI, offset STR                ; Move the memory offset for string to the EDI register
INSW                                       ; Move a word (16 bits) from the input port address
                                                    ; specified in the DX register to the memory location pointed
                                                    ; by EDI register
```

# OUT/OUTSB/OUTSW/OUTSD

该指令可视化为 `OUT` 表示 Output 输出 + `S` 表示 String 字符串 + `B` 表示 Byte 字节 或 `W` 表示 WORD 字 或 `D` 表示 DWORD 双字 的组合。

### Meaning：

这里重申了输入指令的相同概念。用于在处理器输入/输出端口与外围设备之间传输数据的指令有两种。这两种指令如下：

* `Register input/output instructions`：这些指令在处理器 I/O 端口与寄存器之间移动数据。
* `Block (or string) input/output instructions`：这些指令在处理器 I/O 端口与内存之间移动数据块。

### Register output instruction format：

`OUT DESTINATION SOURCE`

`SOURCE` 是寄存器，`EAX`（32 bit）寄存器或 `AX`（16 bit）寄存器或 `AL`（8 bit）寄存器。源寄存器的长度决定了从源寄存器输出到端口的数据量，可以是字节、字或双字。源也可以是其他通用寄存器。

并且 `DESTNATION` 是端口地址

```
OUT 80, EAX     ; It will output dword (32-bits) from EAX to port 80.
OUT 80, AX        ; It will output word (16-bits) from AX to port 80.
```

### Block (or string) output instruction format：

`OUTSB/OUTSW/OUTSD`

其中处理器输出端口地址指定在 `DX` 寄存器中，源是 `ESI` 寄存器指向的内存位置。

`OUTSB` 指令将从 `ESI` 寄存器指向的内存位置输出一个字节（8 位）数据到 `DX` 寄存器指定的输出端口地址。为了在内存与处理器输出端口之间传输数据块，`OUTSB` 指令与重复前缀 `REP` 一起使用。每次从 `ESI` 指向的内存向 `DX` 寄存器指定的输出端口地址输出一个字节（8 位）后，`ESI` 会在 `DF=0` 时递增，或在 `DF=1` 时递减 1。

`OUTSW` 指令将从 `ESI` 寄存器指向的内存位置输出一个字（16 位）数据到 `DX` 寄存器指定的输出端口地址。为了在内存与处理器输出端口之间传输数据块，`OUTSW` 指令与重复前缀 `REP` 一起使用。每次从 `ESI` 指向的内存向 `DX` 寄存器指定的输出端口地址输出一个字（16 位）后，`ESI` 会在 `DF=0` 时递增，或在 `DF=1` 时递减 2。

`OUTSD` 指令将从 `ESI` 寄存器指向的内存位置输出一个双字（32 位）数据到 `DX` 寄存器指定的输出端口地址。为了在内存与处理器输出端口之间传输数据块，`OUTSD` 指令与重复前缀 `REP` 一起使用。每次从 `ESI` 指向的内存向 `DX` 寄存器指定的输出端口地址输出一个双字（32 位）后，`ESI` 会在 `DF=0` 时递增，或在 `DF=1` 时递减 4。

### Flags Affected：

无

### Example

```
MOV ESI, offset STR                   ; Move memory offset for string to the ESI register
MOV DX, PORT_ADDRESS       ; Move Output Port address to the DX register
OUTSW                                         ; Output a word (16 bits) from memory location pointed
                                                       ; by ESI register to output Port address in DX register
```

# LODS/LODSB/LODSW/LODSD

### Instruction Format：

`LODSB`

`LODSW`

`LODSD`

### Meaning：

`Load String`（`LODS`）将 `ESI` 寄存器指向的字符串加载到 `EAX` 寄存器。

`Load String Byte`（`LODSB`）将 `ESI` 寄存器指向的字符串的一个字节加载到 `AL` 寄存器。

`Load String Word`（`LODSW`）将 `ESI` 寄存器指向的字符串的一个字加载到 `AX` 寄存器。

`Load String DWORD`（`LODSD`）将 `ESI` 寄存器指向的字符串的一个双字加载到 `EAX` 寄存器。

`ESI` 在 `DF=0` 时递增，或在 `DF=1` 时递减，对于 `Load String Byte`（`LODSB`）为 1，对于 `Load String Word`（`LODSW`）为 2，对于 `Load String DWORD`（`LODSD`）为 4。

### Flags Affected：

无

### Example

```
CLD                                 ; Clear Direction flag, DF=0
MOV ESI, Offset STR     ; Move memory offset of string to ESI register
LODSB                           ; Loads a byte of the string pointed by ESI register to AL
                                         ; register
```

# STOS/STOSB/STOSW

### Instruction Format：

`STOSB`

`STOSW`

`STOSD`

### Meaning：

