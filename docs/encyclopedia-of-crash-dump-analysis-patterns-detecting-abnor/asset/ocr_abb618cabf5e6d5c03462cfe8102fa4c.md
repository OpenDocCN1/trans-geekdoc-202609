```
+0x004 Blink             : 0x00136a48 _LIST_ENTRY [ 0x136a70 - 0x161148 ]
+0x004 Blink             : 0x00161148 _LIST_ENTRY [ 0x136a48 - 0x119f58 ]
+0x004 Flink             : 0x00136a48 _LIST_ENTRY [ 0x136a70 - 0x161148 ]
+0x004 Blink             : 0x00119f58 _LIST_ENTRY [ 0x161148 - 0x16cc3c0 ]
+0x010 EntryCount        : 0
+0x014 ContentionCount   : 0
+0x018 Spare             : [2] 0x2e760000

0:000> !address 0x1018de08
10120000 : 10120000 - 00100000
           Type     00020000 MEM_PRIVATE
           Protect  00000004 PAGE_READWRITE
           State    00001000 MEM_COMMIT
           Usage    RegionUsageIsVAD
```

The address points miraculously to some DLL:

```
0:000> du 1018de08
1018de08 "...componentA.dll"
```

We might suggest that componentA.dll played some role there.

There are other messages from verbose version of !locks WinDbg command pointing to critical section problems:

```
CritSec componentB!Section+0 at 74004008
LockCount            NOT LOCKED
RecursionCount       0
OwningThread         0
EntryCount           0
ContentionCount      0

The CritSec componentC!Info+c at 72455074 has been RE-INITIALIZED.
The critical section points to DebugInfo at 00107cc8 instead of 000f4788

CritSec componentC!Info+c at 72455074
LockCount            NOT LOCKED
RecursionCount       0
OwningThread         0
EntryCount           0
ContentionCount      0

CritSec componentD!foo+8ec0 at 0101add0
LockCount            NOT LOCKED
RecursionCount       0
OwningThread         0
EntryCount           0
ContentionCount      0
```