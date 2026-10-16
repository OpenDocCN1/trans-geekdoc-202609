
-   [堆栈对齐](#stack-alignment)  
    当某些编译器在进入函数时会强制执行 32 字节的堆栈对齐。这意味着栈指针的内存地址必须能被 32 整除。历史上，这对于系统在 32 字节对齐边界上获取内存更高效。虽然这种效率优势可能已经不存在，但你仍会偶尔看到编译器为保持堆栈对齐而做的操作。常见的表现是，在为局部变量分配空间时，编译器会额外分配空间以维持对齐。

    这意味着在函数的堆栈帧中，未使用的空间很常见。在逆向工程时，不要过度关注这些多余空间，因为它完全是正常的。编写代码时，你无需手动处理它，但本书的目标是让你能够在代码中识别出这种情况，并知道它大体上可以忽略。

### The Big Picture

当函数被调用时，它会对程序堆栈产生多项更改。为了在一个地方看到所有这些变化，可以参考下面的程序：

```
void hack(...)
{
    ...
}

void drink(...)
{
    ...
    hack(...);
    ...
}
```

这两个函数（`hack` 和 `drink`）可能有零个或多个参数和局部变量。[Figure 7.3](#c07.xhtml#c07-fig-0003) 展示了这两个函数的堆栈帧结构。

![Figure 7.3: Stack frames for hack and drink functions](images/c07f003.png)

[**Figure 7.3**](#c07.xhtml#R_c07-fig-0003): Stack frames for hack and drink functions

### 记忆要点

x86 汇编程序可能很复杂。要在 x86 逆向工程中高效工作，必须记住以下几点之一是函数的堆栈帧结构。[Table 7.16](#c07.xhtml#c07-tbl-0016) 列出了完整的堆栈帧，包括参数、返回地址、局部变量和临时空间。

[**Table 7.16**](#c07.xhtml#R_c07-tbl-0016): Complete function stack frame

| STACK  |

| --- |

|  || `...` |

| `[ebp—12] or [ebp-0xC]` || `Third local variable` |

| --- | --- |

| `[ebp-8]` || `Second local variable` |

| `[ebp-4]` || `First local variable` |

| `[ebp]` || `Previous frame pointer` |

| `[ebp+4]` || `Function return address` |

| `[ebp+8]` || `First parameter` |

| `[ebp+12] or [ebp+0xC]` || `Second parameter` |

| `[ebp+16] or [ebp+0xF]` || `Third parameter` |

|   || `...` |

另一个需要记住的点是 **boilerplate**（模板代码）与 **完整函数前置**（complete function prologue）之间的区别。[Table 7.17](#c07.xhtml#c07-tbl-0017) 展示了两者在前置代码中的不同。

[**Table 7.17**](#c07.xhtml#R_c07-tbl-0017): Two types of prologues

| BOILERPLATE PROLOGUE || COMPLETE PROLOGUE |

| --- | --- |

| `push ebp ; save stack frame`  

`mov ebp, esp ; start new frame` || `push ebp ; save stack frame`  

`mov ebp, esp ; start new frame`  

`sub esp, 20 ; allocate 5 4 byte locals`  

`push ebx ; save modified regs`  

`push esi`  

`(etc)` |

| --- | --- |

| --- | --- |

| --- | --- |

[**Table 7.18**](#c07.xhtml#R_c07-tbl-0018): Two types of epilogues

| BOILERPLATE EPILOGUE || COMPLETE EPILOGUE |

| --- | --- |

| `mov esp, ebp ; discard locals`  

`pop ebp ; restore frame`  

`ret ; return` || `(etc)`  

`pop esi ; restore modified regs`  

`pop ebx`  

`mov esp, ebp ; discard locals`  

`pop ebp ; restore frame`  

`ret ; return` |

| --- | --- |

| --- | --- |

| --- | --- |

函数的**函数尾声**（function epilogue）会逆转函数前置的效果。[Table 7.18](#c07.xhtml#c07-tbl-0018) 展示了这两种前置方式对应的尾声。

## Summary

本章探讨了反向工程和破解应用的关键概念。在继续前进之前，请确保你已牢固掌握控制流在应用中的工作方式以及函数和其堆栈帧的细节。

# CHAPTER 8  

Compilers and Optimizers

For many higher-level programming languages, compilation is a vital part of the process of converting an application from source code to machine-readable binary code. During this process, a compiler may make minor changes to the code to make it as fast and efficient as possible.

The process of compiling and optimizing an application can make it more difficult to reverse engineer. This chapter describes how to find a starting point for reversing an application and some of the common actions that compilers take that can complicate reverse engineering.

## Finding Starting Code

When code is compiled, the compiler introduces a large amount of boilerplate that is executed before the actual application code is ever called. When reverse engineering, one of the art forms you'll need to master is how to skip over this and focus on the target code, not the boilerplate setup. However, identifying the entry point into the target code can be complex.

When reversing someone else's code, it's unlikely that the code will be compiled with debugging symbols. This means function and variable names and other information that could provide a hint regarding the actual code's entry point have been stripped from the application. [Figure 8.1](#c08.xhtml#c08-fig-0001) shows what opening a file without debugging symbols looks like in `gdb`.

![Figure 8.1: Application without debugging symbols in gdb](images/c08f001.png)

[**Figure 8.1**](#c08.xhtml#R_c08-fig-0001): Application without debugging symbols in `gdb`

This lack of debugging symbols creates a major challenge because applications written in higher languages rather than pure assembly include much more overhead and compiler-generated symbols. The following is sample output from an `info files` command in `gdb` showing the number of different sections that exist in a simple executable:

```
Entry point: 0x80483a0
0x08048154 - 0x08048167 is .interp
0x08048168 - 0x08048188 is .note.ABI-tag
0x08048188 - 0x080481ac is .note.gnu.build-id
0x080481ac - 0x080481cc is .gnu.hash
0x080481cc - 0x0804823c is .dynsym
0x0804823c - 0x080482a6 is .dynstr
0x080482a6 - 0x080482b4 is .gnu.version
0x080482b4 - 0x080482e4 is .gnu.version_r
0x080482e4 - 0x080482ec is .rel.dyn
0x080482ec - 0x08048314 is .rel.plt
0x08048314 - 0x08048338 is .init
0x08048340 - 0x080483a0 is .plt
0x080483a0 - 0x08048648 is .text
0x08048648 - 0x0804865d is .fini
0x08048660 - 0x080486a9 is .rodata
0x080486ac - 0x080486f0 is .eh_frame_hdr
0x080486f0 - 0x080487f4 is .eh_frame
0x08049f08 - 0x08049f0c is .init_array
0x08049f0c - 0x08049f10 is .fini_array
0x08049f10 - 0x08049f14 is .jcr
0x08049f14 - 0x08049ffc is .dynamic
0x08049ffc - 0x0804a000 is .got
0x0804a000 - 0x0804a020 is .got.plt
0x0804a020 - 0x0804a028 is .data
0x0804a028 - 0x0804a02c is .bss
0xf7fdc114 - 0xf7fdc138 is .note.gnu.build-id in /lib/ld-linux.so.2
0xf7fdc138 - 0xf7fdc1f4 is .hash in /lib/ld-linux.so.2
0xf7fdc1f4 - 0xf7fdc2d4 is .gnu.hash in /lib/ld-linux.so.2
0xf7fdc494 - 0xf7fdc612 is .dynsym in /lib/ld-linux.so.2
0xf7fdc494 - 0xf7fdc64a is .dynstr in /lib/ld-linux.so.2
0xf7fdc64c - 0xf7fdc714 is .gnu.version in /lib/ld-linux.so.2
0xf7fdc64c - 0xf7fdc714 is .gnu.version_d in /lib/ld-linux.so.2
0xf7fdc714 - 0xf7fdc77c is .rel.dyn in /lib/ld-linux.so.2
0xf7fdc77c - 0xf7fdc7ac is .rel.plt in /lib/ld-linux.so.2
0xf7fdc7b0 - 0xf7fdc820 is .plt in /lib/ld-linux.so.2
0xf7fdc820 - 0xf7ff4baf is .text in /lib/ld-linux.so.2
0xf7ff4bc0 - 0xf7ff8a60 is .rodata in /lib/ld-linux.so.2
0xf7ff8a60 - 0xf7ff90ec is .eh_frame_hdr in /lib/ld-linux.so.2
0xf7ff90ec - 0xf7ffb654 is .eh_frame in /lib/ld-linux.so.2
0xf7ffccc0 - 0xf7ffcf3c is .data.rel.ro in /lib/ld-linux.so.2
0xf7ffcf3c - 0xf7ffcff4 is .dynamic in /lib/ld-linux.so.2
```
