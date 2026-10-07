The ELF File Header contains information on the target operating system. This information is stored in 1-byte. The target operating system can be any flavor of Unix, Solaris, HP-UX, NetBSD, Linux, et. There is also a byte in the ELF File Header that stores the version of the target operating system.

There is a 2-byte information on the type of ELF File in the ELF File Header. The ELF file types can be Executable, Dynamic Linked Library, Core Dump, and so on.

There is 2-byte information on the type of machine for which the ELF File has been built. The information is for SPARC, Intel 80860, NEX, Power PC, Digital Alpha, Hitachi, and so on.

After all this information, there is a 4-byte pointer where the process should start execution. This is a very vulnerable point in the ELF File. The malware designers try to alter this pointer to the program to the memory location where the malware developers induce their code.

Then, there is a 4-byte pointer to the Program Header. This is also a vulnerable point in the ELF Files for the same reason discussed earlier.

There is a 4-byte pointer to the Section Header table. This is also a vulnerable point in the ELF Files for the same reason discussed earlier.

Then there is a 4-byte pointer to the Section Header table. Following that, there is a 2-byte pointer to the size of the ELF File Header. This value must be 64 bytes for the 64-bit format and 52 bytes for the 32-bit format.

There is more information like the number of entries in the Program Header, the of the Section Header, etc.

# Program Header

The program header table tells the system how to create a process image. It is found in the file offset e_phoff, and consists of e_phnum entries, each with e_phentsize. The layout is slightly different in 32-bit ELF vs. 64-bit ELF because the p_flags are in a different structure for alignment reasons.

The first information in the Program Header is the type of the segment, whether the segment is loadable, linkable, dynamically interpretable, auxiliary information, etc.

The rest of the information in the Program Header are flags of 1 byte or 2 bytes. One can assume that tampering with this information will not interest the malware developers.