
During program execution, a procedure is called from another function; the `CALL` instruction is used. Using `CALL` instruction pointer jump to the code of a procedure called within a function. When the `CALL` instruction is executed, the memory address of the next instruction after the `CALL` instruction is pushed onto the stack. This memory address is popped back from the stack once the called procedure execution is over with the `RET` instruction.

**Flags Affected:** None

**Example**

`CALL PROC_LABEL` ; Program flow is deviated to the procedure label memory location

## [`ENTER`](#toc.xhtml#s92a)

Instruction Format:

`ENTER Storage, Level`

**Meaning:**

In Intel Architecture, another method of performing the procedure call is supported with the `ENTER` and `LEAVE` instructions. These instructions create and release the stack frame for the procedure to store variables and pointers to return the execution from the procedure. In block-structured language like C and Pascal, these instructions provide machine language support for procedure calls.

The `ENTER` instruction has 2 operands:

*   `Storage`: This tells the number of bytes to be reserved on the stack for the procedure call.
*   `Level`: Also called lexical nesting level (from 0 to 31), it is the depth of procedure in a ladder of procedure calls.

**Flags Affected:** None

## [`LEAVE`](#toc.xhtml#s93a)

**Instruction Format:**

`LEAVE`

**Meaning:**

This instruction releases the stack frame created for the procedure to store variables and pointers to return the execution from the procedure by restoring `(E)SP`/`(E)BP`.

**Flags Affected:** None

## [`INT`](#toc.xhtml#s94a)

**Instruction Format:**

`INT <type>`

The `type` is between 0 and 255.

**Meaning:**

Interrupt is a condition which halts the processor to temporarily work on some other task and then return to the main task. Interrupt is an event or signal that asks for the CPU’s attention. This is used by peripheral hardware devices to access the CPU. Whenever the interrupt occurs, the processor completes the current set of instructions and then starts the interrupt service routine (`ISR`) or interrupt handler. `ISR` is a routine which contains a set of instructions to handle specific interrupts. This `ISR` tells the processor what to do when an interrupt occurs.

Now, the `INT` instruction allows a program to explicitly call the interrupt handler. The following tasks are done when an `INT` instruction is called:

*   The `FLAGS` register is pushed on the stack.
*   The Code segment (`CS`) is pushed on the stack.
*   The offset of the next instruction after the `INT` instruction is pushed onto the stack.
*   The `IP` (Instruction Pointer) is loaded from an absolute memory address, which is a multiple of the interrupt type by 4. If `INT` is 8, the `IP` (Instruction Pointer) will be read from 8 * 4 = 32 decimal = 0x00020 memory location.
*   The code segment will be the next WORD location. The `CS` will be 0x00022 (0x00020 + 2).
*   Reset `TF` Trap flag (`TF`) and `IF` Interrupt flag (`IF`).

**Flags Affected:** `IF`, `TF`

## [`INTO`](#toc.xhtml#s95a)

**Instruction Format:**

`INTO`

**Meaning:**

`Interrupt Overflow` (`INTO`): If the Overflow flag (`OF`) is set, this instruction raises the overflow exception. If `OF` is not set, then the instruction execution continues without raising an exception. This helps to check the overflow condition. The following tasks are done when an `INT` instruction is called:

*   The `FLAGS` register is pushed on the stack.
*   The `CS` (code segment) is pushed on the stack.
*   The offset of the next instruction after the `INT` instruction is pushed onto the stack.
*   The `IP` (Instruction Pointer) is loaded from an absolute memory address, which is multiple of interrupt type by 4.
*   If the overflow condition is `INT` 4, the `IP` (Instruction Pointer) will be read from 4 * 4 = 16 decimal = 0x00010 memory location.
*   The code segment will be the next WORD location. The `CS` will be 0x00012 (0x00010 + 2).
*   Reset Interrupt flag and Trap flag to 0.

**Flags Affected:** `IF`, `TF`

## [`IRET`](#toc.xhtml#s96a)

**Instruction Format:**

`IRET`

**Meaning:**

`Interrupt Return` (`IRET`): This instruction is used to end the Interrupt Service Routine (`ISR`) or interrupt handler and return the execution to the interrupted program. When an Interrupt Service Routine (`ISR`) is called, the instruction pointer, code segment, and flags registers are pushed onto the stack. On return from the `ISR` instruction pointer, the code segment and flags are restored back from the stack to continue the execution of the interrupted program.

**Flags Affected:** `AF`, `CF`, `DF`, `IF`, `ZF`, `SF`, `TF`, `PF`

## [`LOOP`](#toc.xhtml#s97a)

Instruction Format:

`LOOP DESTINATION`

**Meaning:**

In `LOOP` instruction, the `(E)CX` register is decremented by 1. If the new value in the `(E)CX` register is non-zero, then a jump is taken to the destination mentioned in the instruction. If the `(E)CX` register is decremented and the `ECX` is equal to 0, then no action will be taken and the instruction next to the `LOOPE` instruction is executed.

**Flags Affected:** None

**Example**

```
LOOPE MEM_LOC     ; Program will jump to the memory location if ECX is non-zero
                  ; after decrementing
```

## [`LOOPE`](#toc.xhtml#s98a)

Instruction Format:

`LOOPE DESTINATION`

**Meaning:**

In the `LOOPE` instruction, the `(E)CX` register is decremented by 1. If the new value in the `(E)CX` register is non-zero and the `ZF` flag is set to 1, then a jump is taken to the destination mentioned in the instruction. If the `(E)CX` register is decremented and `ECX` is equal to 0, then no action will be taken and the instruction next to the `LOOPE` instruction is executed.

**Flags Affected:** None

**Example**

```
LOOPE MEM_LOC     ; Program will jump to the memory location if ECX is non-zero
                  ; after decrementing and ZF=1 due to the previous instruction
```

## [`LOOPNE`](#toc.xhtml#s99a)

Instruction Format:

`LOOPNE DESTINATION`

**Meaning:**

In the `LOOPNE` instruction, the `(E)CX` register is decremented by 1. If the new value in the `(E)CX` register is non-zero and the `ZF` flag is set to 0, then a jump is taken to the destination mentioned in the instruction. If the `(E)CX` register is decremented and `ECX` is equal to 0, then no action will be taken and the instruction next to the `LOOPNE` instruction is executed.

**Flags Affected:** None

**Example**

```
LOOPNE MEM_LOC    ; Program will jump to the memory location if ECX is non-zero
                  ; after decrementing and ZF=0 due to the previous instruction
```

## [`TEST`](#toc.xhtml#s100a)

Instruction Format:

`TEST DESTINATION_OPERAND SOURCE_OPERAND`

**Meaning:**

This instruction performs the logical AND between the source operand and the destination operand. Unlike the `AND` instruction, the `TEST` instruction does not update any of the operands. It updates the flags without saving the results. This instruction is used to check the registers for zero, without altering its value.

**Flags Affected:** `SF`, `ZF`, and `PF`

**Example**

```
TEST EAX, 01H    ; IF EAX=01H
                 ; 01H AND 01H = 01H (non-zero value)
                 ; Result is non-zero value, ZF is not set, ZF=0
TEST EAX, 02H    ; IF EAX=01H
                 ; 01H AND 02H = 00H (zero value)
                 ; Result is zero value, ZF is set, ZF=1
TEST EAX, EAX    ; if EAX is equal to 0, set ZF to 1
```

## [`Branching Instructions`](#toc.xhtml#s101a)

This includes instructions which help in controlling the code flow. There are two types of jumps in x86:

*   `Unconditional jump`: The instruction pointer jumps to the code path mentioned.
