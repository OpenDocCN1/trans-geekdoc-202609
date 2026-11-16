# Mac OS X

This is a Mac OS X / GDB counterpart to Stack Overflow (user mode) pattern:

```
(gdb) bt 10
#0 0x0000000105dafea8 in bar (i=0)
#1 0x0000000105dafe9 in bar (i=262102)
#2 0x0000000105dafe9 in bar (i=262101)
#3 0x0000000105dafe9 in bar (i=262100)
#4 0x0000000105dafe9 in bar (i=262099)
#5 0x0000000105dafe9 in bar (i=262098)
#6 0x0000000105dafe9 in bar (i=262097)
#7 0x0000000105dafe9 in bar (i=262096)
#8 0x0000000105dafe9 in bar (i=262095)
#9 0x0000000105dafe9 in bar (i=262094)
(More stack frames follow...)

```

There are at least 262,102 frames, so we don’t attempt to list them all. What we’d like to do is to get stack trace boundaries from the list of sections based on the current stack pointer address and dump the upper part of it (the stack grows from higher addresses to the lower ones) to get bottom initial stack traces:

```
(gdb) x $rsp
0x7fff651aeff0: 0x00000000

```

Because this is a stack overflow, we expect that RSP went out of page bounds, and we expect the lowest address to be 0x7fff651af000.

```
(gdb) maint info sections
[...]
Core file:
`/cores/core.2763', file type mach-o-le.
[...]
0x0000000105e00000->0x0000000105f00000 at 0x00035000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff651af000->0x00007fff651af000 at 0x00135000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff651af000->0x00007fff651af000 at 0x03935000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff659af000->0x00007fff6599e400 at 0x04135000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
0x00007fff6599e400->0x00007fff6599e6000 at 0x0416a000: LC_SEGMENT. ALLOC LOAD CODE HAS_CONTENTS
[...]

```

```
(gdb) x/250a 0x00007fff659a0000-2000
0x7fff659a830: 0x0 0x150000000
0x7fff659a840: 0x7fff659ae860 0x105dafe9 <bar+25>
0x7fff659a850: 0x0 0x140000000
0x7fff659a860: 0x7fff659ae880 0x105dafe9 <bar+25>
0x7fff659a870: 0x0 0x130000000
0x7fff659a880: 0x7fff659ae8a0 0x105dafe9 <bar+25>
0x7fff659a890: 0x0 0x120000000
0x7fff659a8a0: 0x7fff659ae8c0 0x105dafe9 <bar+25>
0x7fff659a8b0: 0x0 0x110000000
0x7fff659a8c0: 0x7fff659ae8e0 0x105dafe9 <bar+25>
0x7fff659a8d0: 0x0 0x100000000
0x7fff659a8e0: 0x7fff659ae900 0x105dafe9 <bar+25>

```