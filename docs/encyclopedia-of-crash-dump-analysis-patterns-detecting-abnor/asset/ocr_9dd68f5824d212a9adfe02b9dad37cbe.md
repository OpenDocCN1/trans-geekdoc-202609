# Lateral Damage

# Linux

This is a Linux variant of **Lateral Damage** pattern previously described for Windows (page 603) platform. It also covers memory dumps where some usual commands may not work, and we have to find a workaround to simulate their output, for example, by using other commands:

```
(gdb) info threads
Cannot find new threads: generic error

(gdb) thread apply all bt
Cannot find new threads: generic error

(gdb) thread 2
[Switching to thread 2 (LWP 12567)]
#0 0x000000000042ff51 in nanosleep ()

(gdb) thread 3
[Switching to thread 3 (LWP 12566)]
#0 0x000000000041482e in __int_malloc ()
```