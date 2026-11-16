# FIGURE 8.4 Overview of PE in Cutter

| Name | Size | Address | EndAddress | Entropy |
| :--- | :--- | :--- | :--- | :--- |
| .CRT | 512 | 0x00409000 | 0x00409200 | 0.27091923 |
| .bss | 0 | 0x00407000 | 0x00407000 | 0.00000000 |
| .data | 512 | 0x00403000 | 0x00403200 | 0.67055940 |
| .debug_abbrev | 512 | 0x00404000 | 0x00404200 | 1.64302401 |
| .debug_aranges | 512 | 0x00400000 | 0x00400200 | 0.21630991 |
| .debug_frame | 512 | 0x00400000 | 0x00400200 | 0.60834407 |
| .debug_info | 4096 | 0x00400C00 | 0x00404C00 | 5.20530666 |
| .debug_line | 512 | 0x00406000 | 0x00406200 | 3.23045935 |
| .idata | 2560 | 0x00408000 | 0x0040A600 | 3.49846220 |
| .pdata | 1024 | 0x00405000 | 0x00405400 | 2.60281113 |
| .reloc | 3072 | 0x00404000 | 0x00404C00 | 4.93296316 |
| .text | 7880 | 0x00401000 | 0x00402F00 | 5.92407755 |
| .tls | 512 | 0x00404000 | 0x00404200 | 0.19743808 |
| .xdata | 1024 | 0x00406000 | 0x00406400 | 2.59930829 |

The goal of a PE file, as noted earlier, is to provide information for the loader to get all the elements of the program into memory. We can look at the different elements using Cutter. Figure 8.5 shows a list of the program sections from our sample program. When a program is compiled, it is broken into multiple sections, which are identified with labels so the operating system loader will know what to do with them. There are multiple sections that may be part of PE files, but we’re going to focus on a couple of them specifically. The first section is the .text section, which is all the executable code. Another section is the .data section, which contains all initialized data in the program. This means it’s data that is known about at compile time. Variables that are defined when the program is compiled, with values assigned, are stored in the .data section. There is a lot of data that is only known about and assigned at runtime. That is stored somewhere else.

# FIGURE 8.5 Portable executable sections

| Name | Size | Address | End Address |
| :--- | :--- | :--- | :--- |
| .bss | 0 | 0x00407000 | 0x00408000 |
| .CRT | 512 | 0x00409000 | 0x00409200 |
| .data | 512 | 0x00404000 | 0x00405000 |
| .debug_abbrev | 512 | 0x00404000 | 0x00404900 |
| .debug_aranges | 512 | 0x00400000 | 0x00400400 |
| .debug_frame | 512 | 0x00401000 | 0x00401100 |
| .debug_info | 7680 | 0x00404000 | 0x00406000 |
| .debug_line | 512 | 0x00400000 | 0x00401000 |
| .eh_frame | 2560 | 0x00406000 | 0x00407000 |