
The `stepi` command steps one instruction at a time, as shown in [Figure 6.7](#c06.xhtml#c06-fig-0007), allowing more in-depth analysis. Note that comments are shown because the application was built in debug mode.

![Figure 6.7: gdb stepi command](images/c06f007.png)

[**Figure 6.7**](#c06.xhtml#R_c06-fig-0007): `gdb stepi` command

If the next instruction to execute is a function call, `stepi` will follow the call into the called function. In many cases, this is undesirable, especially if the function is well-understood. For example, knowing that an instruction will print a string is enough information, and there is no need to inspect each instruction within the `printf` function.

The `nexti` command makes it possible to step over a function call. This will execute the function call and advance to the next visible instruction.

#### *Examining Memory*

In `gdb`, the `x` command (for “eXamine memory”) can be used to examine memory. The syntax of the command is `x/nfu addr`.

In this command, *`n`*, *`f`*, and *`u`* are optional parameters with the following meanings:

*   *`n`*: Specifies the number of units (*`u`*) of memory that should be displayed

*   *`f`*: Specifies the display format 

    *   *`s`*: Null-terminated string

    *   *`i`*: Machine instruction

    *   *`x`*: Hexadecimal (default)

*   *`u`*: Specifies the unit size 

    *   *`b`*: Bytes

    *   *`h`*: Halfwords (two bytes)

    *   *`w`*: Words (default)

    *   *`g`*: Giant words (eight bytes)

[Figure 6.6](#c06.xhtml#c06-fig-0006) showed a variable named *`byteToPrint`*, which was located at the address `0x080490e4`. To display 16 bytes of memory at this location, the command would be `x/16x 0x80490e4`, as shown in [Figure 6.8](#c06.xhtml#c06-fig-0008). The output of the command shows that the byte of interest has a value of `0x41`, which is *A* in ASCII.

![Figure 6.8: gdb x command](images/c06f008.png)

[**Figure 6.8**](#c06.xhtml#R_c06-fig-0008): `gdb x` command

In addition to using memory addresses, the `x` command can also use registers to specify the dump location. For example, [Figure 6.9](#c06.xhtml#c06-fig-0009) shows an example of dumping 10 bytes in hex format at the location specified by *`esp`*.

![Figure 6.9: Printing 10 bytes with the gdb x command](images/c06f009.png)

[**Figure 6.9**](#c06.xhtml#R_c06-fig-0009): Printing 10 bytes with the `gdb x` command

## Segmentation Faults

Segmentation faults, or *segfaults*, occur when the CPU attempts to read or write an inaccessible memory location. This could happen because the indicated location doesn't exist or the CPU lacks the permissions necessary to access or modify that memory location.

For example, the command `mov eax, [0x00000000]` will always result in a segfault. The reason for this is that address 0x0 is typically not mapped or accessible by an application, so a read from memory address `0x0`. `gdb` will cause a segfault to occur.

Segfaults can occur for a variety of different reasons. When exploiting software, a buffer overflow can cause a segfault. When cracking software, segfaults can happen if a program is incorrectly patched or errors are made when modifying execution during debugging. As you start to get into writing and manipulating assembly code, you will become good friends with segfault. Keeping a stress ball nearby that you use every time you see a segfault can be therapeutic when cracking. As a silver lining, when hooked to GDB, as a segfault occurs, `gdb` will show the line that caused it, which is helpful for tracking down where the code went haywire.

## Lab: Shark Sim 3000

This lab provides a warm-up reverse engineering challenge. The application is intentionally designed so that its behavior is nonobvious. Experience deciphering and analyzing programs like this are the foundation of software cracking.

Head to the book's GitHub page (`https://github.com/DazzleCatDuo/X86-SOFTWARE-REVERSE-ENGINEERING-CRACKING-AND-COUNTER-MEASURES`) and locate the Shark Sim 3000 lab.

### Skills

This lab is designed to test foundational skills in reverse engineering, including the ability to take apart and understand an unknown program. Some of the skills being tested include the following:

*   ASCII

*   Condition codes

*   Debugging compiled programs

*   Deciphering unknown assembly instructions and programs

### Takeaways

Debugging is an invaluable tool in reverse engineering an application. A fundamental part of reverse engineering is deciphering new instructions—there's not always enough time to understand everything!

One of the secrets to success in reverse engineering is to not get caught up on unknown assembly instructions. Try to quickly understand the basics of what they are doing, so you can proceed. In future chapters, you'll keep working with `gdb` and other more powerful debuggers. Now that you've started to modify assembly, you can progress to doing it without any source at all.

## Tuning Out the Noise

Effective reverse engineering and software cracking requires proficiency in a few different skill sets. However, one of the most important is the ability to tune out the noise and focus on what matters.

Even small programs contain too much code to analyze everything. The vast majority of the instructions have no relevance to the core application features and are a waste of time to reverse engineer. Often, knowing what to focus on is less important than knowing what *not* to focus on.

When determining what to focus on and not focus on, understanding the basics is essential. Some extremely common code that should be immediately recognizable includes the following:

*   Control flow constructs

*   Stack layout (local variables, incoming parameters, and outgoing parameters)

*   Compiler boilerplate (prologues/epilogues, canaries, stack allocation, and register management)

These will all be explored in detail in the upcoming chapters to make you a pro at recognizing them quickly.

There is an order of operations to follow when prioritizing reverse engineering efforts: function calls ➪ control flow ➪ instructions ➪ boilerplate.

*   **Function calls:** Focus on determining what functions are called. Often, knowing that a function calls `CreateDialog` is enough to understand its purpose.

*   **Control flow:** If necessary, explore the control flow, such as determining that `CreateDialog` is called in a loop within that function.

*   **Individual instructions:** If that is not enough, examine individual instructions.

*   **Compiler boilerplate:** Examining boilerplate is almost never useful to software RE or cracking. However, it's important to understand typical boilerplate so that it can be quickly identified and ignored.

## Summary

This chapter introduced `gdb`, a powerful and widely used debugger for Linux systems. Gaining familiarity and hands-on experience with `gdb` is important for an aspiring reverse engineer or cracker since this tool can be used to analyze software for a wide variety of different systems.

# CHAPTER 7  

Functions and Control Flow

A program is a series of instructions, and an application may not move linearly from one instruction to the next. When reversing and cracking an application, it's vital to understand control flows and the various factors that can affect them, such as `if` statements and loops in higher-level languages.

When reversing a function in x86 or a higher-level language, you'll likely run into functions as well. This chapter also explores how functions work in x86 and their effects on the program stack.

## Control Flow

So far, the assembly code that has been explored in this book has followed a sequential stream of instructions. Execution simply continues from top to bottom. However, most applications are not completely sequential. Consider the following code block:

```
if (x) {
       // Do something
}
```
