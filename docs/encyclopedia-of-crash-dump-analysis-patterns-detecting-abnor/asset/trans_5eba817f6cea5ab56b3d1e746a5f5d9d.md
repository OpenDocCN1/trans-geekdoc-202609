
用户空间（第307页）和内核空间（第292页）中的动态内存损坏模式是名为**损坏结构**（第144页）的一个大型父模式的专门化，因为崩溃发生在那里是由于损坏或被覆盖的堆或池控制结构（后者请参见**双重释放**模式，第259页）。临界段通过静态预分配或堆分配的辅助结构链接在一起（以粗体斜体显示），尽管它们本身可以存储在从静态和栈区域到进程堆的任何位置：

```
0:001> dt -r1 ntdll!_RTL_CRITICAL_SECTION 77795240
+0x000 DebugInfo : 0x00175d28 _RTL_CRITICAL_SECTION_DEBUG
    +0x000 Type : 0
    +0x002 CreatorBackTraceIndex : 0
    +0x004 CriticalSection : 0x77795240 _RTL_CRITICAL_SECTION
    +0x008 ProcessLocksList : _LIST_ENTRY [ 0x173a08 - 0x173298 ]
    +0x010 EntryCount : 0
    +0x014 ContentionCount : 0
    +0x018 Spare : [2] 0
+0x004 LockCount : -1
+0x008 RecursionCount : 0
+0x00c OwningThread : (null)
+0x010 LockSemaphore : (null)
+0x014 SpinCount : 0
0:001> !address 77795240
    77670000 : 77792000 - 00005000
        Type 01000000 MEM_IMAGE
        Protect 00000004 PAGE_READWRITE
        State 00001000 MEM_COMMIT
        Usage RegionUsageImage
        FullPath C:\WINDOWS\system32\ole32.dll
0:001> !address 0x00175d28
    00140000 : 00173000 - 0000d000
        Type 00020000 MEM_PRIVATE
        Protect 00000004 PAGE_READWRITE
        State 00001000 MEM_COMMIT
        Usage RegionUsageHeap
        Handle 00140000
```

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

考虑这样一种情况：CRITICAL_SECTION 结构定义在栈上，并且**局部缓冲区溢出**（第608页）覆盖了 DebugInfo 指针。那么我们就得到了**野指针**模式（第1151页）的示例，从此点遍历临界段列表将偏移到完全不相关的内存区域或停在那里。考虑另一个示例：堆损坏或竞态条件覆盖了 ProcessLocksList 或 CriticalSection 指针。那么我们就得到了野指针模式的另一个实例，如下所示：

```
0:000> !locks

CritSec ntdll!LdrpLoaderLock+0 at 7c8877a0
WaiterWoken     No
LockCount       0
RecursionCount  1
OwningThread    1184
EntryCount      0
ContentionCount b04707
*** Locked

CritSec +1018de08 at 1018de08
WaiterWoken     Yes
LockCount       -49153
RecursionCount  5046347
OwningThread    460050
EntryCount      0
ContentionCount 0
*** Locked

CritSec +1018ddd8 at 1018ddd8
WaiterWoken     Yes
LockCount       -1
RecursionCount  0
OwningThread    0
*** Locked

CritSec +1018de28 at 1018de28
WaiterWoken     Yes
LockCount       -1
RecursionCount  0
OwningThread    0
*** Locked

CritSec +1018de08 at 1018de08
WaiterWoken     Yes
LockCount       -49153
RecursionCount  5046347
OwningThread    460050
EntryCount      0
ContentionCount 0
*** Locked

CritSec +1018de28 at 1018de28
WaiterWoken     Yes
LockCount       -1
RecursionCount  0
OwningThread    0
*** Locked
```

```
CritSec +1018ddd8 at 1018ddd8
WaiterWoken        Yes
LockCount          -1
RecursionCount     0
OwningThread       0
*** Locked

Scanned 841 critical sections
```

我们在 1018de08 地址处看到损坏的迹象，该地址被解释为指向已锁定的临界段。要查看损坏从哪里开始，我们需要查看所有临界段的列表，无论是否锁定：

```
0:000> !locks -v

CritSec ntdll!RtlCriticalSectionLock+0 at 7c887780
LockCount          NOT LOCKED
RecursionCount     0
OwningThread       0
EntryCount         0
ContentionCount    28

CritSec ntdll!LdrpLoaderLock+0 at 7c8877a0
WaiterWoken        No
LockCount          0
RecursionCount     1
OwningThread       1184
EntryCount         0
ContentionCount    b04707
*** Locked

CritSec ntdll!FastPebLock+0 at 7c887740
LockCount          NOT LOCKED
RecursionCount     0
OwningThread       0
EntryCount         0
ContentionCount    42c9

CritSec ntdll!RtlpCalloutEntryLock+0 at 7c888ea0
LockCount          NOT LOCKED
RecursionCount     0
OwningThread       0
EntryCount         0
ContentionCount    0

CritSec ntdll!PMCritSect+0 at 7c8883c0
LockCount          NOT LOCKED
RecursionCount     0
OwningThread       0
EntryCount         0
ContentionCount    0

CritSec ntdll!UMLogCritSect+0 at 7c888400
LockCount          NOT LOCKED
RecursionCount     0
OwningThread       0
EntryCount         0
ContentionCount    0

CritSec ntdll!RtlpProcessHeapsListLock+0 at 7c887960
LockCount NOT LOCKED
RecursionCount 0
OwningThread 0
EntryCount 0
ContentionCount 0

CritSec +80608 at 00080608
LockCount NOT LOCKED
RecursionCount 0
OwningThread 0
EntryCount 0
ContentionCount 22

...

CritSec cabinet!_adbgmsg+13c at 74fb4658
LockCount NOT LOCKED
RecursionCount 0
OwningThread 0
EntryCount 0
ContentionCount 0

CritSec +c6c17c at 00c6c17c
LockCount NOT LOCKED
RecursionCount 0
OwningThread 0
EntryCount 0
ContentionCount 0

CritSec +c6c0e4 at 00c6c0e4
LockCount NOT LOCKED
RecursionCount 0
OwningThread 0
EntryCount 0
ContentionCount 0

CritSec at 1018de08 does not point back to the debug info at 00136a40
Perhaps the memory that held the critical section has been reused without calling DeleteCriticalSection() ?

CritSec +1018de08 at 1018de08
WaiterWoken Yes
LockCount -49153
RecursionCount 5046347
OwningThread 460050
EntryCount 0
ContentionCount 0
*** Locked

CritSec at 1018ddd8 does not point back to the debug info at 00136a68
Perhaps the memory that held the critical section has been reused without calling DeleteCriticalSection() ?
```

```
CritSec +0108ddd8 at 1018ddd8
WaiterWoken Yes
LockCount -1
RecursionCount 0
OwningThread 0
*** Locked
...
```

我们发现，当地址为 00c6c0e4 的堆分配临界段链接到地址为 0x1018de08 的不一致临界段时问题会出现，该处的内存数据包含 UNICODE 字符串片段：

```
0:000> !address 00c6c0e4
00c60000 : 00c60000 - 00010000
Type 00020000 MEM_PRIVATE
Protect 00000004 PAGE_READWRITE
State 00001000 MEM_COMMIT
Usage RegionUsageHeap
Handle 00c60000
```

```
0:000> dt -r1 _RTL_CRITICAL_SECTION 00c6c0e4
+0x000 DebugInfo : 0x00161140 _RTL_CRITICAL_SECTION_DEBUG
+0x000 Type : 0
+0x002 CreatorBackTraceIndex : 0
+0x004 CriticalSection : 0x00c6c0e4 _RTL_CRITICAL_SECTION
+0x008 ProcessLocksList : _LIST_ENTRY [ 0x136a48 - 0x119f58 ]
+0x010 EntryCount : 0
+0x014 ContentionCount : 0
+0x018 Spare : [2] 0
+0x004 LockCount : -1
+0x008 RecursionCount : 0
+0x00c OwningThread : (null)
+0x010 LockSemaphore : (null)
+0x014 SpinCount : 0
```

```
0:000> dt -r _RTL_CRITICAL_SECTION_DEBUG 0x00136a48-0x0008
+0x000 Type : 0
+0x002 CreatorBackTraceIndex : 0
+0x004 CriticalSection : 0x1018de08 _RTL_CRITICAL_SECTION
+0x000 DebugInfo : 0x000d001b _RTL_CRITICAL_SECTION_DEBUG
+0x000 Type : 0
+0x002 CreatorBackTraceIndex : 0
+0x004 CriticalSection : (null)
+0x008 ProcessLocksList : _LIST_ENTRY [ 0x0 - 0x0 ]
+0x010 EntryCount : 0
+0x014 ContentionCount : 0x37e3c700
+0x018 Spare : [2] 0x8000025
+0x004 LockCount : 196609
+0x008 RecursionCount : 5046347
+0x00c OwningThread : 0x00460050
+0x010 LockSemaphore : 0x00310033
+0x014 SpinCount : 0x520044
+0x008 ProcessLocksList : _LIST_ENTRY [ 0x136a70 - 0x161148 ]
+0x000 Flink : 0x00136a70 _LIST_ENTRY [ 0x136a98 - 0x136a48 ]
+0x000 Flink : 0x00136a98 _LIST_ENTRY [ 0x136ae8 - 0x136a70 ]
```
