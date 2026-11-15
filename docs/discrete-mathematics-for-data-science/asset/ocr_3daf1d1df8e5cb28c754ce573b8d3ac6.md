At the machine level, numbers are computed and stored as *binary*, which is a base 2 representation of the number. A computer's *Central Processing Unit* (CPU) operates on binary numbers in CPU registers, a series of binary 1s and 0s termed *bits*, for (bi)nary digi(ts).

Registers nowadays are typically 64 bits wide. Memory allocations for 64-bit variables may be referred to as *double precision*, versus 32-bit *single precision* allocations, depending on the underlying architecture of the computing system (the CPU type and a program's instructions). There is more about the topic of precision in the *IEEE 754 Floating Point Standard* sections of this book.

The CPU stores and retrieves data from *computer memory*, where one byte (8 bits) of data is stored per memory address.

Different computers and programming languages require different amounts of memory space for storing numbers and characters. For example, a CPU with 32-bit registers will most likely have 32-bit memory addressing, with four contiguous bytes of memory required to store an integer.

For an alphabetical character, the first eight bits of a 32-bit register will typically map an integer representation of that character to one or two bytes of memory. That integer will accord with the character's Unicode value. For example, the character ‘A’ is represented by the integer 65 in Unicode. In 8-bit binary, the integer 65 is 01000001.