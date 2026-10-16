
# CHAPTER 2  

x86 Assembly: Data, Modes, Registers, and Memory Access  

## Introduction to x86  

Thousands of computer architectures exist. While they all work similarly, a computer is a computer—but there are minor or major differences between each.  

To study reverse engineering, we need to select an architecture to focus on. In this book, we'll be using x86, which was selected for a few different reasons:  

*   **Ubiquity:** x86 is the most widely used assembly language, making it widely applicable for reverse engineering.  
*   **Computer support:** x86 applications can be built, run, and reverse engineered on any desktop, laptop, or server.  
*   **Market share:** x86 is the core of the major operating systems (Windows, Linux, and macOS), so it is used in billions of systems.  

The x86 architecture has been around for decades and has evolved significantly over the years. It was first introduced in 1974 by Intel, and some of the main milestones in the history of x86 include the following:  

*   **Intel 8080:** 8-bit microprocessor, introduced in 1974  
*   **Intel 8086:** 16-bit microprocessor, introduced in 1978  
*   **Intel 80386:** 32-bit microprocessor, introduced in 1985  
*   **Intel Prescott, AMD Opteron, and Athlon 64:** 64-bit microprocessor, introduced in 2003/2004  

Over its nearly 50-year history, the x86 architecture has regularly added new features while maintaining backward compatibility. Even if a feature was determined to be unused, it was never removed from the system. As a result, programs written for the Intel 8086 processor released in 1978 can still run on the latest x86 chips with no modifications.  

This focus on backward compatibility has created an immense, complex, and interesting architecture. The latest Intel Software Developer's manual (`www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html`) is more than 5,000 pages long and only begins to scratch the surface of what this architecture can do. This book focuses on understanding the basics of x86, which is all that is needed to read, write, and manipulate most x86 code.  

As the x86 architecture has changed, the term *x86* has become an umbrella term for all of the architectures that have evolved from the Intel 8086 16-bit architecture. This includes the Intel 80286 architecture, which contains both 16-bit and 32-bit architectures, and the Intel 80886 architecture, which adds a 64-bit architecture. The term *x64* specifically refers to the 64-bit version of x86.  

## x86 Assembly: Data, Modes, Registers, and Memory Access  

Most software reverse engineering requires disassembling a compiled executable and analyzing the result. This disassembly results in assembly code, not a higher-level language.  

While a few assembly languages exist, x86 is one of the most widely used. This chapter introduces some of the key concepts of x86 assembly, providing a foundation for later chapters.  
