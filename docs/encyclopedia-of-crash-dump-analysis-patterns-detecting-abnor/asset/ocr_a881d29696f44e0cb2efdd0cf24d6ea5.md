```
6: 00170000
Segment at 00170000 to 00180000 (00008000 bytes committed)
7: 013b0000
Segment at 013b0000 to 013c0000 (00003000 bytes committed)
```

but GC heap and the number of Leak and System.Byte[][] objects in it were growing significantly:

```
Process Uptime: 0 days 0:00:04.000

0:000> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013c1018
generation 1 starts at 0x013c100c
generation 2 starts at 0x013c1000
ephemeral segment allocation context: (0x013cd804, 0x013cdff4)
segment begin allocated size
0055ee08 790d7ae4 790f7064 0x0001f580(128384)
013c0000 013c1000 013cdff4 0x0000cff4(53236)
Large object heap starts at 0x023c1000
segment begin allocated size
023c0000 023c1000 023c3250 0x00002250(8784)
Total Size 0x2e7c4(190404)
------------------------
GC Heap Size 0x2e7c4(190404)
```

```
0:000> !dumpheap -stat
total 2176 objects
Statistics:
              Count    TotalSize Class Name
...
...
...
             46      736 CLRHeapLeak.Leak
              5      8816 System.Object[]
             46    47656  System.Byte[]
           2035   129604  System.String
Total 2176 objects
```

```
Process Uptime: 0 days 0:09:56.000

0:000> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x018cddbc
generation 1 starts at 0x01541ec4
generation 2 starts at 0x013c1000
ephemeral segment allocation context: (0x0192d668, 0x0192ddc8)
segment begin allocated size
0055ee08 790d7ae4 790f7064 0x0001f580(128384)
013c0000 013c1000 0192ddc8 0x0056cdc8(5688776)
Large object heap starts at 0x023c1000
segment begin allocated size
023c0000 023c1000 023c3240 0x00002240(8768)
Total Size 0x58e588(5825928)
```