# NULL Pointer

# Linux

# Code

This is a Linux variant of **NULL Pointer** (code) pattern previously described for Mac OS X (page 747) and Windows (page 750) platforms:

```
(gdb) bt
#0 0x0000000000000000 in ?? ()
#1 0x000000000040531 in procB ()
#2 0x00000000004005f8 in bar_four ()
#3 0x0000000000400608 in foo_four ()
#4 0x0000000000400620 in thread_four ()
#5 0x0000000000401630 in start_thread (arg=<optimized out>)
 at pthread_create.c:304
#6 0x00000000004324e9 in clone ()
#7 0x0000000000000000 in ?? ()

(gdb) disassemble procB
Dump of assembler code for function procB:
0x0000000000400516 <+0>: push %rbp
0x0000000000400517 <+1>: mov %rsp,%rbp
0x000000000040051a <+4>: sub $0x10,%rsp
0x000000000040051e <+8>: movq $0x0,-0x8(%rbp)
0x0000000000400526 <+16>: mov -0x8(%rbp),%rdx
0x000000000040052a <+20>: mov $0x0,%eax
0x000000000040052f <+25>: callq *%rdx
0x0000000000400531 <+27>: leaveq 
0x0000000000400532 <+28>: retq 
End of assembler dump.

(gdb) info r rdx
rdx 0x0 0
```