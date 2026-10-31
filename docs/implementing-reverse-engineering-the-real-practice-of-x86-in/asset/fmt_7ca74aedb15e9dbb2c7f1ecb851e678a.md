
# `SAL` Shift Arithmetic Left

`SAL` shifts the bits `n` (`count`) times in the destination operand from the right to left and the `CF` flag will have the value of the last bit shifted out. As it is arithmetic shifting, the bit placeholder at LSB will always be 0.

### Flags Affected
`CF` `OF` `PF` `SF` `ZF` (`AF` undefined)

### Example
```
MOV EAX, 40000001H      ; EAX is 40000001H and CF=0
SAL EAX, 2              ; SAL EAX bits 2 times, EAX will become 0x00000004 and CF will set to 1
```

## `SHLD`

### Instruction Format
`SHLD DESTINATION_OPERAND, SOURCE_OPERAND, COUNT`

### Meaning
![](images/Figure-4.13.jpg)

Figure 4.13: `SHLD`

Shift Left Double (`SHLD`) shifts the bits `n` (`count`) times in the destination operand from the right to left and the empty bit placeholders in the destination operand are filled by the bits shifted out of the source operand. The `CF` flag will have the value of the last bit shifted out of the destination operand. The source operand will not be modified.

### Flags Affected
`CF` `OF` `PF` `SF` `ZF` (`AF` undefined)

### Example
```
MOV EAX, 40000001H    ; EAX is 40000001H and CF=0
MOV EBX, 50000001H    ; EBX is 50000001H and CF=0
SHLD EAX, EBX, 2      ; EAX = 0x00000005 and EAX = 0x50000001
                      ; CF will set to 1
```

## `SHRD`

### Instruction Format
`SHRD DESTINATION_OPERAND, SOURCE_OPERAND, COUNT`

### Meaning
![](images/Figure-4.14.jpg)

Figure 4.14: `SHRD`

Shift Right Double (`SHRD`) shifts the bits `n` (`count`) times in the destination operand from the left to right and the empty bit placeholders in the destination operand are filled by the bits shifted out of the source operand. The `CF` flag will have the value of the last bit shifted out of the destination operand. The source operand will not be modified.

### Flags Affected
`CF` `OF` `PF` `SF` `ZF` (`AF` undefined)

### Example
```
MOV EAX, 40000001H    ; EAX is 40000001H and CF=1
MOV EBX, 50000001H    ; EBX is 50000001H and CF=1
SHRD EAX, EBX, 2      ; EAX = 0x50000000 and EAX = 0x50000001
                      ; CF will set to 0
```

# Processor Control Instructions

This includes instructions used in controlling the processor operations.

## `CLC`

### Instruction Format
`CLC`

### Meaning
Clear the Carry Flag (`CLC`): This instruction clears the Carry Flag.

### Flags Affected
`CF`

### Example
```
MOV EAX, 40000001H       ; EAX is 40000001H and CF=0
SAL EAX, 2               ; SAL EAX bits 2 times, EAX will become 0x00000004 and CF will set to 1
CLC                      ; Clear the CF flag, CF=0
```

## `CLD`

### Instruction Format
`CLD`

### Meaning
Clear the Direction Flag (`CLD`): This instruction clears the Direction Flag to 0.

### Flags Affected
`CF`

## `CLI`

### Instruction Format
`CLI`

### Meaning
Clear the Interrupt Flag (`CLI`): This instruction clears the Interrupt Flag to 0. Once the `IF` flag is reset, the processor will not respond to the interrupt signal.

### Flags Affected
`CF`

## `CMC`

### Instruction Format
`CMC`

### Meaning
Complement Carry (`CMC`): This instruction inverts the Carry Flag.

### Flags Affected
`CF`

### Example
```
MOV EAX, 40000001H       ; EAX is 40000001H and CF=0
SAL EAX, 2               ; SAL EAX bits 2 times, EAX will become 0x00000004 and CF will set to 1
CMC                      ; Toggle CF flag from 1 to 0, CF=0
```

## `ESC`

### Instruction Format
`ESC OPCODE SOURCE_OPERAND`
`OPCODE = D8 to DF`
`SOURCE_OPERAND = REGISTER OR MEMORY`

### Meaning
Escape to Floating Point Coprocessor (`ESC`): This instruction passes the instructions to the coprocessor, also called floating point or math coprocessor. The microprocessor fetches the instruction bytes and the coprocessor also fetches these instruction bytes from the data bus and queues them. All the normal microprocessor instructions are treated as NOP by the coprocessor but when the `ESC` instruction is fetched by the microprocessor, the coprocessor decodes the instruction to carry out the action. When the `ESC` instruction is executed, the microprocessor provides the memory address otherwise perform NOP.

### Flags Affected
None

## `LOCK`

### Instruction Format
`LOCK: [INSTRUCTION]`

### Meaning
`LOCK` is the not an instruction but an instruction prefix. When `LOCK` is used as a prefix in front of any instruction, the processor LOCK pin is activated or also called asserted. When the LOCK pin is activated by the `LOCK` instruction, the external bus master and other peripherals are disabled until the instruction after `LOCK` is executed. So, `LOCK` is used in front of critical instructions that are to be executed without any disturbance to bus master (Bus Master is a program that controls the bus on which the address and control signals flow) and system bus (System Bus is a common term for address bus and data bus).

### Flags Affected
None

### Example
```
LOCK: MOV EAX, EBX   ; Activate the LOCK pin of the processor for the MOV instruction execution
```

## `NOP`

### Instruction Format
`NOP`

### Meaning
No Operation (`NOP`): This instruction does nothing. It is used to eat up the processor time and memory.

### Flags Affected
None

### Example
```
NOP    ; Do nothing
```

## `STC`

### Instruction Format
`STC`

### Meaning
Set the Carry Flag (`STC`): This instruction sets the Carry Flag to 1.

### Flags Affected
`CF`

### Example
```
CLC   ; Clear the CF flag, CF=0
STC   ; Set the CF flag, CF=1
```

## `STD`

### Instruction Format
`STD`

### Meaning
Set the Direction Flag (`STD`): This instruction sets the Direction Flag to 1.

### Flags Affected
`DF`

## `STI`

### Instruction Format
`STI`

### Meaning
Set the Interrupt Flag (`STI`): This instruction sets the Interrupt Flag to 1. As already explained in above instructions, when the `IF` flag is enabled, the interrupt event or signal will cause the processor to interrupt the program execution. Whenever the interrupt occurs, the processor completes the current set of instructions and then starts the interrupt service routine (`ISR`) or interrupt handler. `ISR` is a routine which contains a set of instructions to handle specific interrupts. This `ISR` tells the processor what to do when an interrupt occurs.

The `IRET` instruction after `ISR` returns the execution back to the interrupted program.

### Flags Affected
`IF`

# String Instructions

This includes instructions used in handling string operations.

## `CMPS`/`CMPSB`/`CMPSW`

### Instruction Format
This instruction can be visualized as a combination of `CMP` for compare + S for String + B for Byte or W for WORD or D for DWORD

`CMPSB SOURCE, DESTINATION`
`CMPSW SOURCE, DESTINATION`
`CMPSD SOURCE, DESTINATION`

### Meaning
This instruction is used to compare two strings where the source string is pointed by `ESI` and the destination string is pointed by `EDI`. When `CMPSB` is used, the comparison is done between every byte. When `CMPSW` is used, the comparison is done between every word. When `CMPSD` is used, the comparison is done between every DWORD. By comparison, it means subtracting a byte/word/dword pointed by the `ESI` and `EDI` registers, just as we studied in the `CMP` instruction.

The `CMPS` instruction is used with the prefixes `REPE`/`REPZ`, which means repeat the comparison until `ECX`=0 or `ZF`=0. We will cover `REPE`/`REPZ` later.

If Direction flag, `DF`=0, then `ESI` and `EDI` are incremented by 1 for byte, 2 for word, and 4 for dword after each move.

If Direction flag, `DF`=1 then `ESI` and `EDI` are decremented by 1 for byte, 2 for word, and 4 for dword after each move.

### Flags Affected
`AF`, `CF`, `OF`, `PF`, `SF`, `ZF`

### Example
![](images/Figure-4.15.jpg)
