
This book focuses on `32-bit` architecture. In a traditional `32-bit` architecture, that would dictate that a word is `32 bits`. But this is a quirk of the `x86` architecture. Because `x86` has maintained its backward compatibility with the original `16-bit` architecture, a word on `x86` is `16 bits`, and a double word is `32 bits`.

### Working with Binary Values

Reverse engineering commonly involves working with large binary numbers that span multiple different bytes. When working with these numbers, understanding concepts such as zero-extension, bit and byte significance, and endianness is necessary to correctly interpret the number that a binary string represents.

#### *Zero-Extension and Readability*

Binary values are commonly `zero-padded` or `zero-extended` to the word size of the architecture. On a `32-bit` architecture, this means adding 0s to the left of the value until it is 32 bits long. For example, the value `11001[2]` would be zero-padded to `00000000 00000000 00000000 00011001[2]`.

Note that the bits are also broken into groups of four or eight to improve readability. This is just like commas are sometimes added every three digits in base 10 (i.e., 1,000 instead of 1000). When values are written in hexadecimal, they are also grouped by bytes with two characters per byte. For example, the value `4D2[16]` (equivalent to `1234[10]`) can be written as `04[16] D2[16]`.

#### *Bit and Byte Significance*

The bits and bytes within a binary number may be labeled based on their relative weight in a number. [Figure 2.3](#c02.xhtml#c02-fig-0003) illustrates some of these common labels.

![Figure 2.3: Bit and byte significance labels](images/c02f003.png)

[**Figure 2.3**](#c02.xhtml#R_c02-fig-0003): Bit and byte significance labels

In the value `00000000 00000000 00000000 00011001[2]`, the least significant bit (LSB) is the one at the far right, which has a value of 1. The most significant bit (MSB) is at the far left and has a value of 0. When converting from binary to base 10, the MSB will be multiplied by `2^(31)`, while the LSB will be multiplied by `2⁰`.

In addition to MSBs and LSB, there are also the concepts of the least and most significant bytes. In the value `00000000 00000000 00000000 00011001[2]`, the least significant byte has a value of `00011001[2]`, while the most significant byte has a value of `00000000[2]`.

Bits and bytes may also be labeled based on their proximity to the ends of the value. For example, bits and bytes near the LSB are said to be low-order, while bits and bytes near the MSB are high-order.

#### *Endianness*

In memory, data is stored in bytes. However, many data types use multiple bytes. For example, an `int` is 32 bits or 4 bytes.

Endianness describes the order that these bytes are stored in memory. In a *little-endian* system, the least significant byte is stored first (at the lowest address). In a *big-endian* system, the most significant byte is stored first (at the lowest address).

For example, consider the value `1337[10]`, which is `0000 0000 0000 0000 0000 0101 0011 1001[2]` in binary or `0x00000539` in hex. [Figure 2.4](#c02.xhtml#c02-fig-0004) shows how these values would be stored in memory.

![Figure 2.4: Endianness](images/c02f004.png)

[**Figure 2.4**](#c02.xhtml#R_c02-fig-0004): Endianness

Regardless of the endianness of the system, the address associated with a variable is the lowest address used or *base address*. In both a little and big-endian system, this would be address 1828 in this example.

This book focuses on the `x86` architecture, which is little endian. As a result, the least significant byte of a chunk of data will be located at offset 0 from the base address. You'll notice that this looks “backwards” to humans, as we read and write in big endian.

## Registers

Registers provide the processor with high-speed access to data. Since registers are physically located within the CPU, they have much lower latency than memory, where requests must traverse buses and bridges to access data.

In a 32-bit architecture, a register contains 32-bits of data and can be treated like a variable in a program. Each register has a unique name, and the data within a register can be modified based on computations or loading new values from memory.

The main limitation of registers is that they are limited in number and must be shared by the whole program. If a program runs out of registers, it needs to start storing information in memory, which negatively impacts performance. With a limited number of registers, the normal execution cycle is as follows:

*   Fetch data from memory and store it in registers

*   Work with data

*   Save data back to memory

*   Repeat

### Registers in x86

As we've mentioned before in the architecture overview, registers are special names and places in the CPU that allow for very fast operations. All registers can be thought of in two distinct categories.

*   **General-purpose registers (GPRs):** Used for general storing data, addresses, etc., and are directly manipulable

*   **Special-purpose registers (SPRs):** Used to store the program state

The x86 architecture defines numerous registers, which are shown in [Figure 2.5](#c02.xhtml#c02-fig-0005). However, many of those are reserved for use by the CPU itself, making it necessary to know only a subset of them.

![Figure 2.5: x86 registers ¶ Source: Liam McSherry/ wikimedia Commons /CC BY-SA 3.0.](images/c02f005.png)

[**Figure 2.5**](#c02.xhtml#R_c02-fig-0005): x86 registers ¶ Source: Liam McSherry/ wikimedia Commons /CC BY-SA 3.0.

#### *x86 General-Purpose Registers*

GPRs perform most of the heavy lifting within an application, storing values fetched from memory, doing data manipulations, and storing the results of calculations. The following GPRs are the most significant ones in x86, and each can store 32 bits of data. Each accumulator has a role that it is traditionally used for and that it is named after; however, GPRs can be used for any purpose, and you can put a counter in any register, not just the *`ecx`* register.

##### `eax`

*`eax`* is the “accumulator” register. Its name comes from the fact that it is commonly used to hold the result of an arithmetic operation. For example, a program may perform the calculation `eax += ebx`.

##### `ebx`

*`ebx`* is the “base” register. It is commonly used to hold the base address of the chunk of memory used to store a variable. For example, the expression `[ebx + 5]` can be used to access the fifth element of an array.

##### `ecx`

*`ecx`* is the “counter” register and is traditionally used to count. For example, *`ecx`* might be used to track the current iteration of a loop. In the command for `(i=0; i<10; i++)`, the variable *`i`* is likely to be stored in the *`ecx`* register.

##### `edx`

*`edx`* is the “data” register. Its name comes from the fact that it is commonly used to hold data. For example, an application may include the instruction `sub edx, 7`.

##### `esi`

*`esi`* is the “source index” register. It is traditionally used to store an index into a source array. For example, in the command `array[i] = array[k]`, the value of *`k`* would likely be stored in esi.

##### `edi`

*`edi`* is the “destination index” register. It is used to store an index into a destination array. For example, in the command `array[i] = array[k]`, the value of *`i`* would likely be stored in edi.

##### `ebp`

*`ebp`* is the “base pointer” register. Its purpose is to store the address of the base of the current stack frame. The concepts of the program stack and stack frames will be explored in later chapters.

##### `esp`

*`esp`* is the “stack pointer” register. It stores the address at the top of the current stack frame.

#### *Special-Purpose Registers*

SPRs are designed for specific tasks and are not allowed to be directly modified. For example, the instruction `mov eip, 1`, which uses an SPR, will not assemble, while `mov eax, 1`, which uses a GPR, will.

##### `eip`
