However, two critical section addresses belong to the same heap:

```
0:000> !address 00310608
    00310000 : 00310000 - 00010000
                Type     00020000 MEM_PRIVATE
                Protect  00000004 PAGE_READWRITE
                State    00001000 MEM_COMMIT
                Usage    RegionUsageHeap
                Handle   00310000
0:000> !address 08f60f78
    08f30000 : 08f30000 - 00200000
                Type     00020000 MEM_PRIVATE
                Protect  00000004 PAGE_READWRITE
                State    00001000 MEM_COMMIT
                Usage    RegionUsageHeap
                Handle   00310000
```

Lock contention is confirmed by heap statistics as well:

```
0:000> !heap -s
LFH Key                   : 0x07262959
  Heap     Flags   Reserv  Commit  Virt   Free  List   UCR  Virt  Lock  Fast
                    (k)     (k)    (k)     (k)  length      blocks cont. heap
00140000 00000002   8192   2876   3664    631     140      46    0     1   L
  External fragmentation  21 % (140 free blocks)
00240000 00008000     64      12     12     10       1      1    0     0
Virtual block: 0ea20000 - 0ea20000 (size 00000000)
Virtual block: 0fa30000 - 0fa30000 (size 00000000)
00310000 00001002 1255320 961480 1249548 105378      0 16830     2 453093   L
  Virtual address fragmentation 23 % (16830 uncommitted ranges)
                Lock contention      4534419
003f0000 00001002      64     36     36      0       0      1    0     0   L
00610000 00001002      64     16     16      4       2      1    0     0   L
...
```