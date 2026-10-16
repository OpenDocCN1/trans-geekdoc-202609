
Remember, nobody (not even me, though that's hard for me to admit) knows all of the x86 instructions by heart. Whether you're writing x86 or reading it, if you encounter something you don't understand, knowing how to look it up quickly is key. We always have this tab open for quick lookups: `http://ref.x86asm.net/coder32.html`.

## Summary

x86 is a complex, powerful assembly language. However, it isn't necessary to understand every bit of it to be an effective software cracker and reverse engineer.

This chapter covered the x86 instructions that make up the vast majority of assembly code. Learning these instructions is essential and provides a strong foundation for reverse engineering.

# CHAPTER 4  

Building and Running Assembly Programs

Software reverse engineering is about taking a compiled executable and turning it into human-readable code. However, understanding how to do the opposite, building and running an assembly program, can be invaluable to understanding this process.

This chapter explores some of the key concepts needed to understand how assembly programs are built and run. This includes how these programs interact with the outside world, how to actually build and run them, and how they manage strings.

## Output

Assembly and machine code are great, but at some point your code will want to communicate with the outside world. For that we need a way to output information.

If you've ever looked at a processor, they are covered in little pins. A processor's pins enable the processor to communicate with the outside world. Using assembly, it is possible to control these pins by toggling them on and off, causing effects such as turning LEDs on and off. A modern x86 processor has between 400 and 1,000 pins, making it possible to control a lot of things.

Pins are organized into groups called *ports*. With ports, instead of controlling individual pins, which would be tedious and time-consuming, it is possible to control several at the same time. Setting a value on the pins is equivalent to writing to the port, and getting a value from the pins is reading from the port.

A number of different ports are defined for x86. [Table 4.1](#c04.xhtml#c04-tbl-0001) shows some examples of a small subset.

[**Table 4.1**](#c04.xhtml#R_c04-tbl-0001): x86 Ports

| PORT RANGE || SUMMARY |
| --- | --- |
| `0x0000-0x001F` || The first legacy DMA controller, often used for transfers to floppies |
| `0x0020-0x0021` || The first programmable interrupt controller |
| `0x0022-0x0023` || Access to the model-specific registers of Cyrix processors. |
| `0x0040-0x0047` || The programmable interval timer (PIT) |
| `0x0060-0x0064` || The “8042” PS/2 controller or its predecessors |
| `0x0070-0x0071` || The CMOS and RTC registers |
| `0x0080-0x008F` || The DMA (page registers) |
| `0x0092` || The location of the fast A20 gate register |
| `0x00A0-0x00A1` || The second PIC |
| `0x00C0-0x00DF` || The second DMA controller, often used for sound blasters |
| `0x00E9` || Home of the Port E9 hack |
| `0x0170-0x0177` || The secondary ATA hard disk controller |
| `0x01F0-0x01F7` || The primary ATA hard disk controller |
| `0x0278-0x027A` || Parallel port |
| `0x02F8-0x02FF` || Second serial port |
| `0x03B0-0x03DF` || The range used for the IBM VGA, its direct predecessors |
| `0x03F0-0x03F7` || Floppy disk controller |
| `0x03F8-0x03FF` || First serial port |

### Controlling Pins

In x86, pins can be controlled via the `in` and `out` instructions, which take a register and a port as parameters.

The syntax of the `in` instruction is `in register, port`. For example, `in al, 0x64` gets the status of the keyboard.

The `out` instruction reverses the order of the parameters, with the syntax `out port, register`. For example, `out 0x3c0, eax` sets the value of a pixel.

In actuality, you are often not directly hardwired to the destination or source ports, and things are a little more complicated. Pins are attached to a shared bus, and the work of sending reads/writes to the correct destination is offloaded to a separate card or bridge. The `in` and `out` instructions access predefined addresses on the bus that the bridge translates. However, the idea is the same.

### Tedium

Let's get back to this notion of output: through `in` and `out` instructions it is possible to set and unset individual pixels. However, a single display screen can contain thousands or millions of pixels. Setting them individually would be tedious and inefficient.

Instead, these details are abstracted away. When displaying images, the graphics card handles the details of setting each of the individual pixels. However, learning exactly how to communicate with the graphics card can be tedious.

This is where the operating system steps in. It can handle the complexity of interfacing with the graphics card, which sets the pixel values and displays the image. Interacting with the operating system requires a system call. So if you want to play x86 on epic hard mode, you can go down the route of directly interfacing with the graphics card, but for the purposes of this book, we like to play on hard-with-help mode, and we'll leverage the OS to do this heavy lifting for us.

## System Calls

System calls are available in x86 to provide limited I/O functionality invoking behavior through the operating system (OS). The sets of available system calls vary depending on the operating system.

Since system calls are a notion of the OS, they are OS-dependent; we will go through some of the more useful system calls in Linux. System calls are invoked by loading a function number into the *`eax`* register. In Linux, a system call is then made by invoking an interrupt through the instruction `int 0x80`.

### sys_write

In a higher-level programming language, the `sys_write` function would have the syntax `ssize_t sys_write(unsigned int fd, const char * buf, size_t count)`. This function will return a size indicating the amount of data written.

The `sys_write` function takes three arguments. The first, *`fd`*, is a file descriptor that indicates where the data should be written. A value of 1 would indicate writing data to the Linux console. The *`buf`* argument contains the data to be written as output, and *`count`* tells the function the number of characters to print.

In x86 assembly, functions can't be called using this function description. Instead, the arguments would be loaded into registers, as shown in [Table 4.2](#c04.xhtml#c04-tbl-0002). After loading these registers, the system call can be performed with the `int 0x80` instruction.

[**Table 4.2**](#c04.xhtml#R_c04-tbl-0002): `sys_write`

| REGISTER || VALUE || DESCRIPTION |
| --- | --- | --- |
| `eax` || 4 || `sys_write` identifier |
| `ebx` || 1 (console out) || File descriptor |
| `ecx` || `const char*` *`buf`* || String to write |
| `edx` || `size_t` *`count`* || Length of string |

The registers used in the `sys_write` function must be loaded over a series of assembly instructions. The following example shows how `sys_write` could be used:

```
mov   edx,len       ; message length
mov   ecx,buff      ; message to write
mov   ebx,1         ; file descriptor (stdout)
mov   eax,4         ; system function(sys_write)
int   0x80          ; call kernel
```

### sys_exit

The `sys_exit` system call is equivalent to your `main` doing a `return status;` in higher-level programming languages. This will cause the program to exit. It takes a single argument, the status code, that is stored in *`ebx`*, as shown in [Table 4.3](#c04.xhtml#c04-tbl-0003).

[**Table 4.3**](#c04.xhtml#R_c04-tbl-0003): `sys_exit`

| REGISTER || VALUE || DESCRIPTION |
| --- | --- | --- |
| `eax` || 1 || `sys_exit` identifier |
| `ebx` || int || Status code |

A call to `sys_exit` begins by loading values into the registers *`eax`* and *`ebx`*, as shown in the following example:
