

| 寄存器类别 | 寄存器名称 | 用途 |
|---|---|---|
| 通用寄存器 | 32 位：EAX, EBX, ECX, EDX<br>64 位：RAX, RBX, RCX, RDX, R8-R15 | 用于操作数据。 |
| | AX, BX, CX, DX | 前项的 16 位版本。 |
| | AH, BH, CH, DH, AL, BL, CL, DL | 前项的 8 位高字节和低字节。 |
| 段寄存器 | CS, SS, DS, ES, FS, GS | 16 位。用于保存内存地址的第一部分，以及指向代码、堆栈和额外数据段的指针。 |
| 偏移寄存器 | | 用于指示与段寄存器相关的偏移量。 |
| | EBP/RBP（基址指针） | EBP 指向函数堆栈上局部环境的起始位置。64 位下基址指针的使用取决于帧指针省略、语言支持以及寄存器 R8–R15 的使用情况。 |
| | ESI/RSI（源索引） | 用于保存在使用内存块的操作中数据源偏移量。 |
| | EDI/RDI（目的索引） | 用于保存在使用内存块的操作中目的数据偏移量。 |
| | ESP/RSP（堆栈指针） | 用于指向堆栈顶部。 |
| 特殊寄存器 | | 仅由 CPU 使用。 |
| | EFLAGS 或 RFLAGS 寄存器；需要了解的关键标志有<br>ZF=零标志<br>IF=中断允许标志<br>SF=符号标志 | CPU 用于跟踪逻辑结果和处理器状态。 |
| | EIP 或 RIP（指令指针） | 用于指向下一条要执行的指令的地址。 |

虽然已有整本书专门讲述汇编语言，但你只需轻松掌握一些基础知识，就能成为一名更高效的道德黑客。

## 机器语言 vs. 汇编 vs. C

计算机只能理解机器语言——即 1 和 0 的模式。而人类则难以解读长长的 1 和 0 字符串，因此汇编语言应运而生，通过助记符帮助程序员记住一系列数字。随后，出现了 C 语言等更高级的语言，它们进一步将人类与 1 和 0 隔离。如果你想成为一名优秀的道德黑客，就必须抵制社会潮流，回归汇编的基础。

## AT&T vs. NASM

汇编语法主要有两种形式：AT&T 和 Intel。AT&T 语法由 GNU 汇编器（gas）使用，gas 包含在 gcc 编译器套件中，常被 Linux 开发者使用。在 Intel 语法汇编器中，Netwide Assembler（NASM）是最常用的。NASM 格式被许多 Windows 汇编器和调试器使用。这两种格式生成的机器语言基本相同；然而，在样式和格式上存在少数差异：

- 源操作数和目标操作数的顺序颠倒，并且用于标记注释开头的符号不同：
  - NASM 格式  CMD <dest>, <source> <; comment>
  - AT&T 格式  CMD <source>, <dest> <# comment>
- AT&T 格式在寄存器前使用 %；NASM 不使用。% 表示“间接操作数”。
- AT&T 格式在字面量前使用 $；NASM 不使用。$ 表示“立即数操作数”。
- AT&T 处理内存引用的方式与 NASM 不同。

本节以 NASM 格式展示每条命令的语法和示例。此外，还展示了同一命令在 AT&T 格式下的示例以供比较。通常，所有命令均采用以下格式：

```
<optional label>: <mnemonic> <operands> <optional comments>
```

操作数（参数）的数量取决于命令（助记符）。虽然汇编指令众多，但你只需掌握少数几条。这些内容将在以下各节中介绍。

### mov

mov 命令将数据从源复制到目标。源位置的值不会被移除。

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| mov <dest>, <source> | mov eax, 51h;comment | movl $51h, %eax #comment |

数据不能直接从内存移动到段寄存器。相反，你必须使用通用寄存器作为中间步骤。以下是示例：

```
mov eax, 1234h ; store the value 1234 (hex) into EAX
mov cs, ax      ; then copy the value of AX into CS.
```

### add and sub

add 命令将源加到目标，并将结果存储在目标中。sub 命令从目标减去源，并将结果存储在目标中。

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| add <dest>, <source> | add eax, 51h | addl $51h, %eax |
| sub <dest>, <source> | sub eax, 51h | subl $51h, %eax |

### push and pop

push 和 pop 命令用于向堆栈压入和弹出项目。

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| push <value> | push eax | pushl %eax |
| pop <dest> | pop eax | popl %eax |

### xor

xor 命令执行按位逻辑“异或”（XOR）操作——例如，11111111 XOR 11111111 = 00000000。因此，一种选择是对寄存器或内存位置使用 XOR value, value 将其清零。另一种常用的按位运算符是 AND。我们可以执行按位 AND 运算，以判断寄存器或内存位置中特定位是置位还是清除，或者判断像 malloc 这样的函数调用是返回指向某块内存的指针还是返回空指针。这可以通过在调用 malloc 后使用 test eax, eax 等汇编代码来完成。如果 malloc 调用返回空指针，则 test 操作会将 FLAGS 寄存器中的“零标志”设置为 1。在此 test 操作之后，条件跳转指令（如 jnz）所遵循的路径可基于 AND 操作的结果。以下是在汇编中的示例：

```
call malloc(100)
test eax, eax
jnz loc_6362cc012
```

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| xor <dest>, <source> | xor eax, eax | xor %eax, %eax |

### jne, je, jz, jnz, and jmp

jne、je、jz、jnz 和 jmp 命令根据 eflags“零标志”的值将程序流程分支到另一位置。jne/jnz 在零标志等于 0 时跳转；je/jz 在零标志等于 1 时跳转；而 jmp 总是跳转。

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| jnz <dest> / jne <dest> | jne start | jne start |
| jz <dest> / je <dest> | jz loop | jz loop |
| jmp <dest> | jmp end | jmp end |

### call and ret

call 指令将执行重定向到另一个函数。call 指令之后的虚拟内存地址首先被压入堆栈，作为返回指针，然后将执行重定向到被调用的函数。ret 命令用于过程结束时，将流程返回到 call 指令之后的命令。

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| call <dest> | call subroutine1 | call subroutine1 |
| ret | ret | ret |

### inc and dec

inc 和 dec 命令分别递增和递减目标。

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| inc <dest> | inc eax | incl %eax |
| dec <dest> | dec eax | decl %eax |

### lea

lea 命令将源的有效地址加载到目标中。这通常在将目标参数传递给字符串复制函数时出现，例如在以下 AT&T 语法 gdb 反汇编示例中，我们将目标缓冲区地址写入堆栈顶部，作为 gets 函数的参数：

```
lea -0x20(%ebp), %eax
mov %eax, (%esp)
call 0x8048608 <gets@plt>
```

| NASM 语法 | NASM 示例 | AT&T 示例 |
|---|---|---|
| lea <dest>, <source> | lea eax, [esi +4] | leal 4(%esi), %eax |

### System Calls: int, sysenter, and syscall

系统调用是进程请求执行特权操作的一种机制，在此期间，代码的上下文和执行会从用户模式切换到内核模式。调用系统调用的传统 x86 指令是 int 0x80。这被视为已弃用，但仍在 32 位操作系统上受支持。sysenter 指令是其面向 32 位应用程序的后继指令。对于基于 64 位 Linux 的操作系统和应用程序，需要使用 syscall 指令。在编写 shellcode 及其他专用程序或有效载荷时，必须深入理解调用系统调用并设置适当参数的各种方法。

## Addressing Modes

在汇编语言中，可使用多种方法完成同一任务。尤其是，有许多方法可以指示要在内存中操作的有效地址。这些选项称为 _寻址模式_，如表 2-5 所示。

| 寻址模式 | 描述 | NASM 示例 |
|---|---|---|
| 寄存器 | 寄存器保存要操作的数据。无内存交互。两个寄存器大小必须相同。 | mov rbx, rdx<br>add al, ch |
| 立即数 | 源操作数是一个数值。<br>默认情况下为十进制；使用 h 表示十六进制。 | mov eax, 1234h<br>mov dx, 301 |
| 直接 | 第一个操作数是要操作的内存地址。它用方括号标记。 | mov bh, 100<br>mov [4321h], bh |
| 寄存器间接 | 第一个操作数是带方括号的寄存器，用于保存要操作的地址。 | mov [di], ecx |
| 基址相对 | 要操作的有效地址通过 ebx 或 ebp 加上一个偏移值来计算。 | mov edx, 20[ebx] |
| 索引相对 | 与基址相同，但使用 edi 和 esi 来保存偏移量。 | mov ecx, 20[esi] |
| 基址索引相对 | 有效地址通过组合基址相对和索引相对模式来查找。 | mov ax, [bx][si]+1 |

## Assembly File Structure

汇编源文件分为以下几个部分：

- .model .model 指令指示 .data 和 .text 节的大小。
- .stack .stack 指令标记堆栈节的开头，并以字节为单位指示堆栈的大小。
- .data .data 指令标记 .data 节的开头，并定义变量（包括已初始化和未初始化的变量）。
- .text .text 指令保存程序的命令。

