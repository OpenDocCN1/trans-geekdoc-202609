
`Base + displacement addressing` or `based addressing` uses the combination of a register value and a displacement to indicate an address. This type of mode is often used for access into arrays. So in a language where you might have had `*myList[8]``, you're accessing eight elements from the base of `*myList`. In assembly, for example, `[eax + 8]` indicates the eight bytes from the base address of the array, which is stored in `*eax`.

### Indexed Addressing

`Base + displacement addressing` works well if the elements in an array are always a single byte long. For arrays with larger elements, the offset must be computed by hand, which is tedious and prone to error.

In these cases, `indexed addressing` can be a better choice. Indexed addressing uses an index register, a scale factor, and a displacement to specify the address. The scale factor must always be 1, 2, 4, or 8.

#### *Example: Arrays*

Let's define an array of integers, `int x[100];`, which declares an array containing 100 `int`s. In memory, each value in the array is stored at a particular offset from the base address. This offset is determined by the size of the values in the array, such as a 32-bit or 4-byte `int`.

Assume that the `int` array was created at offset `0x1000`. The following instruction would move the *`n`*th element of the array into `*eax`* if *`n`* is stored in `*ebx`:

```
mov eax, [ ebx * 4 + 0x1000]
```

### Based-Index Addressing

`Based-index addressing` combines elements of indexed addressing and `base + displacement addressing`. It uses a base register, an index register, a scale factor (1, 2, 4, or 8), and a displacement for the address.

For example, consider `[ ebx + edi * 4 + 0x1000 ]`. This address has a base stored in `*ebx*`, an index stored in `*edi*`, and a displacement of `0x1000`.

#### *Example: Structs*

`Based-index addressing` is ideal for accessing elements of nested data types. For example, consider the C command `struct { int i; short a[4]; } s;`. This creates a `struct` containing multiple fields, including an array.

Each element within this `struct` is located at a particular offset, which means that the array *`a`* has a certain displacement or base address. However, the elements contained within *`a`* are also located at different offsets from this base address.

Assume that base address of the struct `s` is stored in `*ebx*`, and the array `a` is stored 4 bytes from this base address. The following instruction will access the *`n`*th element within `a` if `n` is stored in `*ecx`:

```
mov eax, [ebx + 2 * ecx + 4]
```

Don't get too tripped up if the more advanced addressing is hard to grasp. Your operating system has been hiding memory from you, so it's natural that thinking about how arrays are stored in memory is new territory. These addressing modes need to be introduced as theory first, but they can be hard to grasp before you start to see them in use later in real assembly code. And don't worry, you will.

## Summary

`x86` is a commonly used assembly language. Understanding how it works is essential to becoming a successful software reverse engineer and cracker.

This chapter explored some of the key concepts of x86 assembly. These include data representation, assembly syntax, and the use of registers and memory addresses for data access and storage.

# CHAPTER 3  

x86 Assembly: Instructions

Cracking and reverse engineering involve reading, writing, and modifying assembly code. In this book, the focus is on the x86 assembly language.

It isn't necessary to understand every detail of x86 assembly to be a reverse engineer or even to write programs in assembly. This chapter explores the fundamentals of x86 and the main instructions that make up more than 90 percent of assembly code for software.

## x86 Instruction Format

Mnemonics are used in x86 assembly to make human-readable assembly code. Each of these mnemonic instructions is assembled into the machine code that controls the processor. So, the processor has no notion of mnemonics, only the machine code. For example, the mnemonic `add` assembles to the machine code value 0x04.

In x86, instructions are written in a particular format. An example of a simple x86 instruction is:

```
add eax, 1
```

In this instruction, `add` is the mnemonic used to instruct the processor on what to do. This instruction also includes a couple of operands that indicate the data to be used in this operation. In this case, the operands are the register `eax` and the value 1. An x86 instruction under normal conditions can have up to three operands if it has any at all. There are special extensions to the language that allow extensions up to four operations (`VEX` prefix), but we won't be delving into this corner of assembly.

The operands to x86 instructions can be registers, immediates, or memory addresses. Registers are usually the general-purpose registers (GPRs), and memory locations are specified by address. Immediates are numbers or constants like 12345.

While an x86 instruction can include any of these, it can contain a maximum of one memory location. For example, the instructions `add eax, ebx` and `add eax, [0x12345678]` are valid because they access two registers and a register and a memory location, respectively. However, the instruction `add [0x12345678], [0x87654321]` is invalid because it uses two memory addresses at once. This is because the processor pipeline is a delicate design that can perform only one memory fetch per instruction.

## x86 Instructions

The x86 assembly language includes hundreds of different instructions. Some of the most commonly used include the following:

*   Arithmetic 

    *   `add`

    *   `sub`

    *   `mul`

    *   `inc`

    *   `dec`

*   Bit Manipulation 

    *   `and`

    *   `or`

    *   `xor`

    *   `not`

*   Stack 

    *   `call`

    *   `return`

    *   `push`

    *   `pop`

*   Data movement: 

    *   `mov`

*   Execution flow 

    *   `jmp`

    *   Conditional jumps

*   Comparison 

    *   `test`

    *   `cmp`

*   Other 

    *   `lea`

    *   `nop`

While this may seem like a lot, consider the common operators used in programming languages (`+`, `−`, `*`, `/`, `%`, `&&`, `||`, `&`, `|`, `^`, `!`, `~`, `<`, `>`, `>=`, `<=`, `==`, `.`, `->`, etc.) and the main keywords (`if`, `else`, `switch`, `while`, `do`, `case`, `break`, `continue`, `for`, etc.). It takes a lot of capability to achieve these behaviors in assembly.

Truthfully, no one knows all of the x86 instructions or has a need to (unless they really want to impress their friends). A complete list of x86 instructions can be found at `http://ref.x86asm.net/coder32.html`, and the details of any instruction can be looked up when needed.

However, a clear understanding of how the most common x86 assembly works is essential to success as a reverse engineer. If you understand this important subset of x86 instructions, you will be able to read and understand most x86 programs.

### mov

As its name suggests, the `mov` instruction is designed to move data from one location to another. This includes copying data between registers and memory locations or placing an immediate at a particular location. Note that despite its name being move, it copies data; it does not move it (meaning it is not removed from source; it is rather copied from source to destination).

The syntax of the `mov` instruction is `mov destination, source`. For example, the command `mov eax, 5` places the value 5 in the register `eax`. Similarly, the instruction `mov eax, [1]` moves the value at address `0x1` into `eax`.

When working with `mov` and similar instructions, it is important to recall that the names of the variables used impact the length of the value being moved. For example, the instruction `mov eax, [0x100]` moves a 32-bit value into `eax`, while the instruction `mov dx, [0x100]` moves a 16-bit value into `dx`.
