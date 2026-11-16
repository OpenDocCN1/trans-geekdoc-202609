# Mac OS X

This is a Mac OS X / GDB counterpart to Local Buffer Overflow pattern. Most of the time, simple mistakes in using memory and string manipulation functions are easily detected by runtime:

```
(gdb) bt
#0 0x00007fff885e982a in __kill ()
#1 0x00007fff83288b6c in __abort ()
#2 0x00007fff832a5b9f in __chk_fail ()
#3 0x00007fff832a583e in __memcpy_chk ()
#4 0x0000000100914edf3 in bar ()
#5 0x0000000100914e5e in foo ()
#6 0x0000000100914ee9b in main (argc=1, argv=0x7fff6d84daf0)
```

This detection happens in a default optimized release version as well:

```
(gdb) bt
#0 0x00007fff885e982a in __kill ()
#1 0x00007fff83288b6c in __abort ()
#2 0x00007fff832a5b9f in __chk_fail ()
#3 0x00007fff832a583e in __memcpy_chk ()
#4 0x000000010f59cea8 in bar [inlined] ()
#5 0x000000010f59cea8 in foo [inlined] ()
#6 0x000000010f59cea8 in main (argc=,
argv=)
```

The more sophisticated example which overwrites stack trace without being detected involves overwriting indirectly via a pointer to a local buffer passed to a called function. In such cases, we may see incorrect and truncated stack traces:

```
(gdb) bt
#0 0x00007fff885e982a in __kill ()
#1 0x00007fff83288b6c in __abort ()
#2 0x00007fff83285070 in __stack_chk_fail ()
#3 0x000000010524de77 in foo ()
#4 0xca400007ff64e5 in ?? ()
```

```
(gdb) bt
#0 0x00007fff885e982a in __kill ()
#1 0x00007fff83288b6c in __abort ()
#2 0x00007fff83285070 in __stack_chk_fail ()
#3 0x0000000105ad8df7 in foo ()
```