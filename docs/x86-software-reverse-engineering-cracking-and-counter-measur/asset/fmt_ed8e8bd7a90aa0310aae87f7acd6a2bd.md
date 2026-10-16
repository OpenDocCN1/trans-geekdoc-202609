
When executing this code, the processor will evaluate the condition, *`x`* , and determine whether it is true. If so, it moves on to the instructions within the `if` block.

However, if the condition, *`x`* , is not true, then the instructions within the `if` block are skipped. This requires the ability to tell the processor to execute some instructions and not others, changing the flow of execution.

### The Instruction Pointer

The *`eip`* register is known as the *instruction pointer* and holds the address of the next instruction to execute. The processor will automatically increment the value stored in *`eip`* after an instruction is executed.

Allowing *`eip`* to be incremented after each instruction makes it possible to run a sequential series of instructions. However, in some cases, we want to conditionally execute code. This requires a different updating of *`eip`* . However, *`eip`* can't be manipulated directly (recall it's a special-purpose register \[SPR\]). Instead, control flow instructions are used to adjust *`eip`* .

### Control Flow Instructions

The most common deviations from the normal execution flow that force changes to *`eip`* are known as *jumps* or *branches*. For example, the following code block has a branch at the `if` statement:

```
int x = 1;
int y = 2*x;
if (!y) { // branch!
    x = 2;
}
```

When high-level code like this is assembled, jump instructions are used to indicate what the *`eip`* register should be set to. A jump instruction has the syntax `jmp op`, where *`op`* can be a memory address or a label.

The `jmp` instruction is a nonconditional jump that is always followed (conditional jumps are covered later in this chapter).

#### *jmp*

The `jmp` instruction has the syntax `jmp op`. Its purpose is to transfer the program's control flow to the memory location *`op`* by setting *`eip`* to the value stored in *`op`* .

Some examples of `jmp` instructions include the following:

```
jmp eax       ; Copies eax into eip (branches to eax)
jmp label     ; Branches to the instruction at label
jmp $         ; An infinite loop in nasm(valuable 
              ;debugging tool in assembly)
 
```

`jmp` instructions can be used to implement various functions. For example, the following instructions count up from zero in an infinite loop:

```
      mov eax, 0
loop: add eax, 1
      jmp loop
```

#### *Conditional Jumps*

Conditional jumps are a way to tie whether or not a jump is taken to a condition being either true or false. This determines whether a jump should be performed based on the values stored in the status flags. For example, consider the following instructions:

```
cmp eax, ebx
jle done
```

The `jle` (jump less than or equal to) instruction will jump to the specified address or label if the flags register indicates that a previous comparison resulted in a less than or equal to. In this case, the instruction right before it (`cmp`) is being used to compare *`eax`* and *`ebx`* and set the flags. Recall that `cmp` takes operand 1 minus operand 2 and throws away the result. So, to get a less than or equal to condition, *`eax`* would need to be less than or equal to *`ebx`* . In this case, the processor will jump to the label *`done`* . Otherwise, the jump will be skipped, and execution will continue to the next instruction after `jle`.

Numerous conditional jump instructions exist in the x86 language. [Table 7.1](#c07.xhtml#c07-tbl-0001) lists these instructions and the conditions that determine whether the jump is performed.

[**Table 7.1**](#c07.xhtml#R_c07-tbl-0001): x86 conditional jump instructions

| INSTRUCTION || MEANING || CONDITIONS |

| --- | --- | --- |

| `je` || Jump if equal. || ZF = 1 |

| --- | --- | --- |

| `jz` || Jump if last result is zero. || ZF = 1 |

| `jne` || Jump if not equal. || ZF = 0 |

| `jge` || Jump if greater than or equal to. || SF = OF |

| `jl` || Jump if less than. || SF != OF |

| `jle` || Jump if less than or equal to. || ZF = 1 OR  

SF != OF |

| `jg` || Jump if greater than. || ZF = 0 AND  

SF == OF |

Looking at the table, you might note that some instructions have identical conditions. For example, `jz` and `je` will both jump if the zero flag (ZF) is set to one. This means that the jump is performed if the two indicated values are equal. But logically, they're treated as different things. “Jump if the previous result is zero” might be used after subtracting two numbers, whereas “jump equal” is more likely used after a comparison.

For example, consider the case where *`eax`* = *`ebx`* = `0x10`. The instruction `cmp eax, ebx` performs subtraction and will set the zero flag if executed. Both the `jz` and `je` instructions will perform a jump if they follow this instruction.

These instructions can be used interchangeably, but they are typically chosen based on the instruction used to set the flags that determine the jump. For example, if the instruction `sub eax, ebx` is used to perform the conditional, then `jz` will likely be used since you're looking at a zero result to a mathematical operation. If the instruction `cmp eax, ebx` is used, then `je` will be used because a comparison tests equivalence.

Remember that `cmp` performs subtraction behind the scenes, so it has the same effect on flags as the `sub` operation. `jz` and `je` are synonymous instructions designed solely to make assembly code more readable.

#### *Pitfalls of Conditional Jumps*

Conditional jumps use the status flags to determine whether a jump should be taken. But every instruction operates in isolation, and the conditional jumps are unaware of which compare or mathematical expression you want to do a conditional jump on. This can cause issues if the status flags are changed between the conditional instruction and the jump. While a compiler would not make this mix up, if you're writing assembly, you will be forced to reason about this.

For example, consider the following set of instructions:

```
cmp eax, ebx
cmp edx, ecx
jle done
```

In this case, your intent may be for the instruction `cmp eax, ebx` to determine whether the jump is followed. However, `cmp edx, ecx` sets the flags last before the jump, overwriting the previous settings. Therefore, the jump is performed based on the outcome of the second compare, not the first.

With multiple `cmp` instructions in a row, it may be obvious that the last `cmp` instruction sets the flags for the jump. However, with other instructions, this may be less obvious, as in the following instructions:

```
cmp eax, ebx
add ecx, 1
je done
 
```

In this series of instructions, the intent may have been to use the `cmp` instruction to set the flags for the jump. However, the `add` instruction also updates the status flags and overwrites the previous settings. Instead of jumping if *`eax`* = *`ebx`* , the jump is performed if the `add` instruction sets the zero flag (i.e., *`ecx`* + 1 = 0).

#### *Example*

Jump instructions are commonly used to implement `if` statements and loops. The following assembly code sums the numbers 0–4 using a loop:

```
       mov   eax, 0    ; initialize eax (accumulator) to 0
       mov   ecx, 0    ; initialize ecx (counter) to 0
 
loop:
       add   eax, ecx  ; add current iteration
       add   ecx, 1    ; increment counter
       cmp   ecx, 5    ; at 5 iterations yet?
       jne   loop      ; loop if not yet 5
 
done:
```

The iterator in this loop is stored in the *`ecx`* register and is initialized before the loop. The *`eax`* register is the accumulator register and holds the running sum.

The loop begins by adding the current loop counter to the accumulator and then incrementing the loop counter. This implements the desired logic of summing the values 0–4 as the loop iterates.
