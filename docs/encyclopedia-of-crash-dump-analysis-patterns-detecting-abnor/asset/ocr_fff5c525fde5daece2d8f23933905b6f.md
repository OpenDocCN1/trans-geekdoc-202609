```
Pool page [ a4ef7000 ] is __inVALID.

Analyzing linked list...
[ a4ef7890 -> a4ef7a10 (size = 0x180 bytes)]: Corrupt region

Scanning for single bit errors...

None found
```

The problem block start address can be calculated:

```
a4ef7890+88 = a4ef7918
```

We would try to see its contents, perhaps dds and dps would point to some symbolic data. Also, search for this address in kernel space might point to some other blocks as well. If we suspect some driver, we may want to enable Driver Verifier special pool.

Another asked question: the special pool is enabled, and it shows both free operation happening through the same thread and the stacks are exactly same:

```
2: kd> .bugcheck
Bugcheck code 000000C2
Arguments 00000000`00000007 00000000`00001097 00000000`00210007 fffffff8a0`04b98e00

2: kd> !pool fffff8a0`04b98e00 2
Pool page fffff8a0a04b98e00 region is Paged pool
*fffff8a004b98df0 size: 210 previous size: 70 (Free) *MmSt
Pooltag MmSt : Mm section object prototype ptes, Binary : nt!mm

2: kd> !verifier 0x80 fffff8a0`04b98e00

Log of recent kernel pool Allocate and Free operations:

There are up to 0x10000 entries in the log.

Parsing 0x0000000000010000 log entries, searching for address 0xfffff8a004b98e00.

=================================================
Pool block fffff8a0a04b98df0, Size 0000000000000210, Thread fffffa80122674f0
fffff80001bcb9ca nt!VfFreePoolNotification+0x4a
fffff800017a367c nt!ExDeferredFreePool+0x126d
fffff8000165b880 nt!MiDeleteSegmentPages+0x35c
fffff8000195cf2f nt!MiSegmentDelete+0x7b
fffff80001637e07 nt!MiCleanSection+0x2f7
fffff80001676754 nt!ObDereferenceObject+0xd4
fffff80001661170 nt!CcDeleteSharedCacheMap+0x1bc
fffff80001699880 nt!CCUninitializeCacheMap+0x2f0
fffff880030ecfa6 ModuleA!ProcC+0x4b6
fffff880030ec840 ModuleA!ProcB+0x2a8
fffff880030ec994 ModuleA!ProcA+0x38
```