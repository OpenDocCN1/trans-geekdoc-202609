
Adds two operands, source operand and destination operand. The result is stored in the destination operand. If CF flag is set to 1, then 1 is added to the destination.

**Flags Affected:** AF CF OF PF SF ZF

## ADD
Instruction Format:
`ADD DESTINATION_OPERAND SOURCE_OPERAND`
**Meaning:**
The instruction adds two operands, source operand and destination operand. The result is stored in the destination operand.
**Flags Affected:** AF CF OF PF SF ZF

## CMP
**Instruction Format:**
`CMP DESTINATION_OPERAND SOURCE_OPERAND`
**Meaning:**
It subtracts two operands, source operand and destination operand. The result is not stored, but the flags are updated. The flags are subsequently checked in the instructions.
**Flags Affected:** AF CF OF PF SF ZF

## DAA
**Instruction Format:**
`DAA`
**Meaning:**
The decimal is adjusted after addition. This instruction comes after the `ADD` or `ADC` instruction to adjust the final result in BCD. This only works with the `AL` registers.
**Flags Affected:** AF CF (OF, PF, SF, ZF undefined)
**Example**
```
MOV DX, 1122H     ;load 1122H BCD
MOV BX, 3088H     ;load 3088H BCD
MOV AL, BL        ;only AL register works for DAA
ADD AL, DL        ;
DAA               ; BCD adjusted result, answer saved in AL
```

## DAS
**Instruction Format:**
`DAS`
**Meaning:**
The decimal is adjusted after subtraction. This instruction comes after the `SUB` or `SBB` instruction to adjust the final result in BCD. This only works with the `AL` registers.
**Flags Affected:** AF CF (OF, PF, SF, ZF undefined)
**Example:**
```
MOV DX, 1122H     ;load 1122H BCD
MOV BX, 3088H     ;load 3088H BCD
MOV AL, BL        ;only AL register works for DAA
SUB AL, DL        ;
DAS               ; BCD adjusted result, answer saved in AL
```

## DEC
Instruction Format:
`DEC DESTINATION_OPERAND`
**Meaning:**
The instruction decrements one from the destination operand which can be register or a memory location. The result is saved back in the register or memory location.
**Flags Affected:** AF OF PF SF ZF
**Example:**
```
MOV EAX, 02H      ;load EAX with 02H
DEC EAX           ;EAX will be 01H
```

## DIV
**Instruction Format:**
`DIV SOURCE_OPERAND`
**Meaning:**
The `DIV` instruction is used to divide the unsigned QWORD/DWORD/WORD by DWORD/WORD/BYTE.
When a WORD is divided by byte, the number to be divided, that is WORD, must be in the `AX` register and the divisor, which is source operand, can be in register or memory location. After division, the quotient will be saved in `AL` and the remainder will be in `AH`.
When a DWORD is divided by WORD, the number to be divided, that is DWORD, must be in `DX:AX` (most significant WORD in `DX` and least significant WORD in `AX`). The divisor, which is the source operand, can be in register or memory location. After division, the quotient will be saved in `AX` and the remainder will be saved in `DX`.
When a Double DWORD (QWORD) is divided by DWORD, the number to be divided, that is Double DWORD (QWORD), must be in `EDX:EAX` (higher order DWORD in `EDX` and lower order DWORD in `EAX`). The divisor, which is the source operand, can be in register or memory location. After division, the quotient will be saved in `EAX` and remainder in `EDX`.
**Flags Affected:** None
**Example**
```
MOX DX, 0          ;load DX with 00H
MOV AX, 0x8003     ;load AX with 8003H
MOV CX, 0x100      ;load CX with 100H
DIV CX             ;AX=80H, DX=03H
```

## IDIV
Instruction Format:
`IDIV SOURCE_OPERAND`
**Meaning:**
The `DIV` instruction (Integer Divide) is used in division of signed data. The rest is the same with respect to the dividend, divisor, quotient, and remainder as in `DIV` instruction.
**Flags Affected:** None

## MUL
Instruction Format:
`MUL SOURCE_OPERAND`
**Meaning:**
The `MUL` instruction is used to multiple the unsigned DWORD/WORD/BYTE by DWORD/WORD/BYTE.
When a BYTE is multiplied by BYTE, the multiplicand, that is BYTE, must be in the `AL` register and the multiplier, which is the source operand, can be in the register or memory location. After multiplication, the result will be saved in `AX`. Higher order 8 bits are stored in `AH` and lower order 8 bits are stored in `AL`.
When a WORD is multiplied by WORD, the multiplicand, that is WORD, must be in the `AX` register and the multiplier, which is the source operand, can be in the register or memory location. After multiplication, the result will be DWORD, which is saved in `DX:AX`. The higher order WORD is stored in `DX` and the lower order WORD in `AX`.
When a DWORD is multiplied by DWORD, the multiplicand, that is DWORD, must be in the `EAX` register and the multiplier, which is the source operand, can be in the register or memory location. After multiplication, the result will be QWORD, which is saved in `EDX:EAX`. The higher order DWORD is stored in `EDX` and the lower order DWORD in `EAX`.
**Flags Affected:** OF, CF
**Example**
```
MOV AX, 0x8003     ;load AX with 8003H
MOV CX, 0x100      ;load AX with 100H
MUL CX             ;DX=80H, AX=0300H
```

## IMUL
Instruction Format:
`IMUL SOURCE_OPERAND`
**Meaning:**
The Integer Multiple (`IMUL`) instruction is used to multiply the signed data. The rest is the same with respect to the multiplicand and multiplier as in `MUL` instruction.
**Flags Affected:** OF, CF

## INC
Instruction Format:
`INC DESTINATION_OPERAND`
**Meaning:**
It increments or adds one to the destination operand, which can be the register or a memory location. Result is saved back in register or a memory location.
**Flags Affected:** AF OF PF SF ZF
**Example**
```
MOV EAX, 02H     ;load EAX with 02H
INC EAX          ;EAX will be 03H
```

## NEG
**Instruction Format:**
`NEG DESTINATION_OPERAND`
**Meaning:**
This instruction changes the sign of the destination operand from a positive number to a negative number or from a negative number to a positive number. Basically, it subtracts 0 from the destination operand and performs the 2’s complement to save the result back in the destination operand. 2’s complement of an 8-bit number 00100101 -> 11011010 (Invert bits) -> then add 00000001 = 11011011
**Flags Affected:** AF OF PF SF ZF
**Example**
```
MOV EAX, 02H     ;load EAX with 02H, (2 in decimal)
NEG EAX          ;EAX will be FFFFFFFEH, (-2 in decimal)
```

## SBB
Instruction Format:
`SBB DESTINATION_OPERAND SOURCE_OPERAND`
**Meaning:**
It subtracts source operand from the destination operand. The result is stored in the destination operand. If the CF flag is set to 1, then 1 is subtracted from the destination.
**Flags Affected:** AF CF OF PF SF ZF

## SUB
**Instruction Format:**
`SUB DESTINATION_OPERAND SOURCE_OPERAND`
**Meaning:**
Subtract the source operand from destination operand. The result is stored in the destination operand.
**Flags Affected:** AF CF OF PF SF ZF

## XADD
**Instruction Format:**
`XADD DESTINATION_OPERAND SOURCE_OPERAND`
**Meaning:**
The Exchange and Add (`XADD`) instruction is the same as the `ADD` instruction where it adds the source operand and the destination operand, to store the result in the destination operand. The difference from `ADD` instruction is that after the `XADD` instruction, the original value of the destination operand is copied to the source operand.
**Flags Affected:** AF CF OF PF SF ZF
**Example**
```
MOV EAX, 0x00000001    ; load EAX with 01H, (1 in decimal)
MOV EBX, 0x00000002    ; load EBX with 02H, (2 in decimal)
XADD EAX,EBX          ; EAX= 03H (3 in decimal), EBX=01H
```

# Program Execution Instructions
These instructions are used in controlling the program execution flow and flags.

## CALL
**Instruction Format:**
`CALL DESTINATION_OPERAND`
**Meaning:**
