These are exactly the same objects that are listed in !thread command output. We see that the second one is normal and resides in a nonpaged area:

```
0: kd> dt _DISPATCHER_HEADER b97004ac
ntdll!_DISPATCHER_HEADER
   +0x000 Type             : 0 ''
   +0x001 Absolute         : 0 ''
   +0x001 NpxIrql          : 0 ''
   +0x002 Size             : 0x4 ''
   +0x002 Hand             : 0x4 ''
   +0x003 Inserted         : 0 ''
   +0x003 DebugActive      : 0 ''
   +0x000 Lock             : 262144
   +0x004 SignalState      : 0
   +0x008 WaitListHead     : _LIST_ENTRY [ 0x89a11e70 - 0x89a11e70 ]

0: kd> !address b97004ac
a71e3000 - 13e1d000
           Usage      KernelSpaceUsageNonPagedSystem
```

The other looks like an invalid Random Object from the free nonpaged pool entry (it even says about itself that it is bad) that used to belong to Configuration Manager in the past:

```
0: kd> !pool 89b87770
Pool page 89b87770 region is Nonpaged pool
[...]

89b87540 size:  98 previous size:  40  (Allocated)  File (Protected)
*89b875d8 size: 260 previous size:  98    (Free)     *CMpa
    Pooltag CMpa : registry post apcs, Binary : nt!cm
89b87838 size:  28 previous size:  260  (Allocated)  FSFm
[...]
```

```
0: kd> dd 89b87770
89b87770  bad0b0b0 00000000 00000000 00000000
89b87780  8a04be01 00000000 89b87788 89b87788
89b87790  00150006 e56c6946 8993e208 89ab96b8
89b877a0  00000000 00000000 bad0b0b0 c0000800
89b877b0  02110004 63426343 83ebfb80 00001000
89b877c0  00199000 00000000 8993e238 88d0d248
89b877d0  0019a000 00000000 00000000 00000000
89b877e0  00000000 00000000 00000000 00000000
```