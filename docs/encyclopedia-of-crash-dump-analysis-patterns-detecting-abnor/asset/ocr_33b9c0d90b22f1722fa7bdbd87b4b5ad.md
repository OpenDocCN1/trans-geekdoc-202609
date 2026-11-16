```
0:000> !locks
CritSec ntdll!LdrpLoaderLock+0 at 7c8877a0
WaiterWoken No
LockCount 0
RecursionCount 1
OwningThread 1184
EntryCount 0
ContentionCount b04707
*** Locked
```

```
0:000> dt -r1 _RTL_CRITICAL_SECTION 7c8877a0
+0x000 DebugInfo : 0x7c8877c0 _RTL_CRITICAL_SECTION_DEBUG
+0x000 Type : 0
+0x002 CreatorBackTraceIndex : 0
+0x004 CriticalSection : 0x7c8877a0 _RTL_CRITICAL_SECTION
+0x008 ProcessLocksList : _LIST_ENTRY [ 0x7c887be8 - 0x7c887bc8 ]
+0x010 EntryCount : 0
+0x014 ContentionCount : 0xb04707
+0x018 Spare : [2] 0
+0x004 LockCount : -2
+0x008 RecursionCount : 1
+0x00c OwningThread : 0x00001184
+0x010 LockSemaphore : 0x0000013c
+0x014 SpinCount : 0
```

```
0:000> !address 7c8877a0
7c800000 : 7c887000 - 00003000
Type 01000000 MEM_IMAGE
Protect 00000004 PAGE_READWRITE
State 00001000 MEM_COMMIT
Usage RegionUsageImage
FullPath C:\WINDOWS\system32\ntdll.dll
```

```
0:000> !address 0x7c8877c0
7c800000 : 7c887000 - 00003000
Type 01000000 MEM_IMAGE
Protect 00000004 PAGE_READWRITE
State 00001000 MEM_COMMIT
Usage RegionUsageImage
FullPath C:\WINDOWS\system32\ntdll.dll
```

Consider the case when CRITICAL_SECTION structure is defined on a stack, and there was **Local Buffer Overflow** (page 608) overwriting DebugInfo pointer. Then we have an example of **Wild Pointer** pattern (page 1151) and traversing the list of critical sections from this point will diverge into completely unrelated memory area or stop there. Consider another example of heap corruption or race condition overwriting ProcessLocksList or CriticalSection pointer. Then we have another instance of Wild Pointer pattern illustrated below: