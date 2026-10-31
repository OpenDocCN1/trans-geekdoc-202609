
## Figure 4.15: CMPSB example

```
MOV ESI, 0x41000001     ; ESI pointing to STRING1
MOV EDI, 0x82000001     ; ESI pointing to STRING2
MOV ECX, 0x08                ; ECX is initialized to 0x08
CLD                                     ; Clear direction flag, DF=0
REPE CMPSB                   ; Compare two strings until ECX=0 or ZF=0
```

# IN/INSB/INSW/INSD

This instruction can be visualized as a combination of `IN` for Input + `S` for String + `B` for Byte or `W` for WORD or `D` for DWORD.

### Meaning:

There are two types of instructions used to transfer data between the processor input/output ports and the peripheral devices. These two types of instruction are as follows:

* `Register input/output instructions`: These instructions move the data between the processor I/O port and the register.
* `Block (or string) input/output instructions`: These instructions move blocks of data between the processor I/O port and the memory.

### Register input instruction format:

`IN DESTINATION SOURCE`

Where, `SOURCE` is the port address

And `DESTNATION` is the register, `EAX` (32-bit) register or `AX` (16-bit) register or `AL` (8-bit) register. The destination register length determines the amount of data to be read from the input port, which can be byte, word, or dword. The destination can be some other general purpose register.

```
IN EAX, 80    ; It will read dword (32-bits) from port 80 and store it in EAX.
IN AX, 80       ; It will read word (16-bits) from port 80 and store it in AX.
```

### Block (or string) input instruction format:

`INSB/INSW/INSD`

Where the processor input port address is specified in the `DX` register and the destination is the memory location pointed by the `EDI` register.

The `INSB` instruction moves a byte (8-bits) data from the input port address specified in the `DX` register to the memory location pointed by the `EDI` register. To transfer blocks of data between the processor input port and the memory, the `INSB` instruction is used with the repeat prefix `REP`. After every byte transfer between the input port and the memory pointed by `EDI`, `EDI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 1.

The `INSW` instruction moves a word (16 bits) data from the input port address specified in the `DX` register to the memory location pointed by the `EDI` register. To transfer blocks of data between the processor input port and the memory, the `INSW` instruction is used with the repeat prefix `REP`. After every word transfer between the input port and the memory pointed by `EDI`, `EDI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 2.

The `INSD` instruction moves a dword (32 bits) data from the input port address specified in the `DX` register to the memory location pointed by the `EDI` register. To transfer blocks of data between the processor input port and the memory, the `INSD` instruction is used with the repeat prefix `REP`. After every dword transfer between the input port and the memory pointed by `EDI`, `EDI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 4.

### Flags Affected:

None

### Example

```
MOV DX, PORT_ADDRESS    ; Move the input port address to the DX register
MOV EDI, offset STR                ; Move the memory offset for string to the EDI register
INSW                                       ; Move a word (16 bits) from the input port address
                                                    ; specified in the DX register to the memory location pointed
                                                    ; by EDI register
```

# OUT/OUTSB/OUTSW/OUTSD

This instruction can be visualized as a combination of `OUT` for Output + `S` for String + `B` for Byte or `W` for WORD or `D` for DWORD.

### Meaning:

The same concept from input instruction is reiterated here. There are two types of instructions used to transfer data between the processor input/output ports and the peripheral devices. These two types of instruction are as follows:

* `Register input/output instructions`: These instructions move the data between the processor I/O port and the register.
* `Block (or string) input/output instructions`: These instruction move blocks of data between the processor I/O port and the memory.

### Register output instruction format:

`OUT DESTINATION SOURCE`

`SOURCE` is the register, `EAX` (32 bit) register or `AX` (16 bit) register or `AL` (8 bit) register. The source register length determines the amount of data to be output from the source register to the port, which can be byte, word, or dword. The source can also be some other general purpose register.

And `DESTNATION` is the port address

```
OUT 80, EAX     ; It will output dword (32-bits) from EAX to port 80.
OUT 80, AX        ; It will output word (16-bits) from AX to port 80.
```

### Block (or string) output instruction format:

`OUTSB/OUTSW/OUTSD`

Where the processor output port address is specified in the `DX` register and the source is the memory location pointed by the `ESI` register.

The `OUTSB` instruction outputs a byte (8-bits) data from the memory location pointed by the `ESI` register to the output port address specified in the `DX` register. To transfer blocks of data between the memory and the processor output port, the `OUTSB` instruction is used with the repeat prefix `REP`. After every byte (8-bits) output from the memory pointed by `ESI` to the output port address specified in the `DX` register, `ESI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 1.

The `OUTSW` instruction outputs a word (16-bits) data from the memory location pointed by the `ESI` register to the output port address specified in the `DX` register. To transfer blocks of data between the memory and the processor output port, the `OUTSW` instruction is used with the repeat prefix `REP`. After every word (16-bits) output from the memory pointed by `ESI` to the output port address specified in the `DX` register, `ESI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 2.

The `OUTSD` instruction outputs a dword (32-bits) data from the memory location pointed by the `ESI` register to the output port address specified in the `DX` register. To transfer blocks of data between the memory and the processor output port, the `OUTSD` instruction is used with the repeat prefix `REP`. After every dword (32-bits) output from the memory pointed by `ESI` to the output port address specified in the `DX` register, `ESI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 4.

### Flags Affected:

None

### Example

```
MOV ESI, offset STR                   ; Move memory offset for string to the ESI register
MOV DX, PORT_ADDRESS       ; Move Output Port address to the DX register
OUTSW                                         ; Output a word (16 bits) from memory location pointed
                                                       ; by ESI register to output Port address in DX register
```

# LODS/LODSB/LODSW/LODSD

### Instruction Format:

`LODSB`

`LODSW`

`LODSD`

### Meaning:

`Load String` (`LODS`) loads the string pointed by the `ESI` register to the `EAX` register.

`Load String Byte` (`LODSB`) loads a byte of string pointed by the `ESI` register to the `AL` register.

`Load String Word` (`LODSW`) loads a word of string pointed by the `ESI` register to the `AX` register.

`Load String DWORD` (`LODSD`) loads a dword of string pointed by the `ESI` register to the `EAX` register.

`ESI` is incremented (when `DF=0`) or decremented (when `DF=1`) by 1 for `Load String Byte` (`LODSB`), 2 for `Load String Word` (`LODSW`), and 4 for `Load String DWORD` (`LODSD`).

### Flags Affected:

None

### Example

```
CLD                                 ; Clear Direction flag, DF=0
MOV ESI, Offset STR     ; Move memory offset of string to ESI register
LODSB                           ; Loads a byte of the string pointed by ESI register to AL
                                         ; register
```

# STOS/STOSB/STOSW

### Instruction Format:

`STOSB`

`STOSW`

`STOSD`

### Meaning:
