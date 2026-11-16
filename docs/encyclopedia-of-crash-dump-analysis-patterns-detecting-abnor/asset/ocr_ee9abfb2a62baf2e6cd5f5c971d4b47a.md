# Incomplete Stack Trace

# GDB

Users of WinDbg debugger accustomed to full thread stack traces will wonder whether a thread starts from *main*:

```
(gdb) where
#0 0x0000000010d3b0e90 in bar () at main.c:15
#1 0x0000000010d3b0ea9 in foo () at main.c:20
#2 0x0000000010d3b0ec4 in main (argc=1,
argv=0x7fff5fc fafbf8) at main.c:25
```

Of course, it doesn’t, and a stack trace is shown starting from *main* function by default. We can change this behavior by using the following command:

```
(gdb) set backtrace past-main
```

Now we see the additional frame:

```
(gdb) where
#0 0x0000000010d3b0e90 in bar () at main.c:15
#1 0x0000000010d3b0ea9 in foo () at main.c:20
#2 0x0000000010d3b0ec4 in main (argc=1,
argv=0x7fff5fc fafbf8) at main.c:25
#3 0x0000000010d3b0e74 in start ()
```

For Linux we have:

```
(gdb) set backtrace past-main
(gdb) bt
#0 0x000000000042fed1 in nanosleep ()
#1 0x000000000042fda0 in sleep ()
#2 0x000000000040078a in main ()
#3 0x0000000000405283 in __libc_start_main ()
#4 0x00000000004003e9 in _start ()
```