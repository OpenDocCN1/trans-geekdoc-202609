
## Control Blocks

Certain system and subsystem architectures and designs may put a hard limit on the amount of data structures created to manage resources. If there is a dependency on such resources from other subsystems, there could be starvation and blockage conditions resulting in sluggish system behavior, the absence of functional response and even in some cases perceived system, service or application freeze. For example, **!filecache** WinDbg command diagnoses low VACB (Virtual [or View] Address Control Block) conditions.

```
7: kd> !filecache
***** Dump file cache******
    Reading and sorting VACBs ...
Removed **0** nonactive VACBs, processing 1907 active VACBs ...
File Cache Information
Current size 408276 kb
Peak size 468992 kb
1907 Control Areas
[...]
```

## Handle Leak

Sometimes **Handle Leaks** (page 416) also result in insufficient memory especially if handles point to structures allocated by OS. Here is the typical example of the handle leak resulted in freezing several servers. The complete memory dump shows exhausted non-paged pool:

```
0: kd> !vm

*** Virtual Memory Usage ***
Physical Memory:      1048352 (   4193408 Kb)
Page File: \\?\C:\pagefile.sys
  Current:  4190208 Kb  Free Space:   3749732 Kb
  Minimum:  4190208 Kb  Maximum:      4190208 Kb
Available Pages:      697734 (   2790936 Kb)
ResAvail Pages:       958085 (   3832340 Kb)
Locked IO Pages:           95 (        380 Kb)
Free System PTEs:     199971 (    799884 Kb)
Free NP PTEs:            105 (        420 Kb)
Free Special NP:           0 (         0 Kb)
Modified Pages:          195 (        780 Kb)
Modified PF Pages:       195 (        780 Kb)
NonPagedPool Usage:    65244 (    260976 Kb)
NonPagedPool Max:      65503 (    262012 Kb)
**************** Excessive NonPaged Pool Usage *****************
PagedPool 0 Usage:     6576 (     26304 Kb)
PagedPool 1 Usage:      629 (      2516 Kb)
PagedPool 2 Usage:      624 (      2496 Kb)
PagedPool 3 Usage:      608 (      2432 Kb)
PagedPool 4 Usage:      625 (      2500 Kb)
PagedPool Usage:       9062 (     36248 Kb)
PagedPool Maximum:     66560 (    266240 Kb)

***************** 184 pool allocations have failed ***************

Shared Commit:          7711 (     30844 Kb)
Special Pool:              0 (         0 Kb)
Shared Process:        10625 (     42500 Kb)
PagedPool Commit:       9102 (     36408 Kb)
Driver Commit:          1759 (      7036 Kb)
Committed pages:      425816 (   1703264 Kb)
Commit limit:        2052560 (   8210240 Kb)
```

Looking at non-paged pool consumption reveals an excessive number of thread objects:

```
0: kd> !poolused 3
Sorting by NonPaged Pool Consumed

Pool Used:
  NonPaged

Tag   Allocs   Frees    Diff   Used
Thre 772672   463590   309082 192867168 Thread objects , Binary: nt!ps
MmCm       42       9       33 12153104 Calls made to MmAllocateContiguousMemory , Binary: nt!mm
...
...
...
```

The next logical step would be to list processes and find their handle usage. Indeed, there is such a process:

```
0: kd> !process 0 0
...
...
...
PROCESS 88b75020 SessionId: 7 Cid: 172e4 Peb: 7ffdf000 ParentCid: 17238
DirBase: c7f6b6c0 ObjectTable: e17f50a0 HandleCount: 143428.
Image: iexplore.exe
...
...
...
```

Making the process current and listing its handles shows contiguously allocated handles to thread objects:

```
0: kd> .process 88b75020
Implicit process is now 88b75020

0: kd> .reload /user

0: kd> !handle
...
...
...
0d94: Object: 88a6b020 GrantedAccess: 001f03ff Entry: e35e1b28
Object: 88a6b020 Type: (8780c68) Thread
ObjectHeader: 88a6b008
HandleCount: 1 PointerCount: 1

0d98: Object: 88a97320 GrantedAccess: 001f03ff Entry: e35e1b30
Object: 88a97320 Type: (8780c68) Thread
ObjectHeader: 88a97308
HandleCount: 1 PointerCount: 1

0d9c: Object: 88b2b020 GrantedAccess: 001f03ff Entry: e35e1b38
Object: 88b2b020 Type: (8780c68) Thread
ObjectHeader: 88b2b008
HandleCount: 1 PointerCount: 1
```

```
0da0: Object: 88b2a730  GrantedAccess: 001f03ff Entry: e35e1b40
Object: 88b2a730  Type: (8780c68) Thread
    ObjectHeader: 88b2a718
    HandleCount: 1  PointerCount: 1
0da4: Object: 88b929a0  GrantedAccess: 001f03ff Entry: e35e1b48
Object: 88b929a0  Type: (8780c68) Thread
    ObjectHeader: 88b92988
    HandleCount: 1  PointerCount: 1
0da8: Object: 88a57db0  GrantedAccess: 001f03ff Entry: e35e1b50
Object: 88a57db0  Type: (8780c68) Thread
    ObjectHeader: 88a57d98
    HandleCount: 1  PointerCount: 1
0dac: Object: 88b92db0  GrantedAccess: 001f03ff Entry: e35e1b58
Object: 88b92db0  Type: (8780c68) Thread
    ObjectHeader: 88b92d98
    HandleCount: 1  PointerCount: 1
0db0: Object: 88b4a730  GrantedAccess: 001f03ff Entry: e35e1b60
Object: 88b4a730  Type: (8780c68) Thread
    ObjectHeader: 88b4a718
    HandleCount: 1  PointerCount: 1
0db4: Object: 88a7e730  GrantedAccess: 001f03ff Entry: e35e1b68
Object: 88a7e730  Type: (8780c68) Thread
    ObjectHeader: 88a7e718
    HandleCount: 1  PointerCount: 1
0db8: Object: 88a349a0  GrantedAccess: 001f03ff Entry: e35e1b70
Object: 88a349a0  Type: (8780c68) Thread
    ObjectHeader: 88a34988
    HandleCount: 1  PointerCount: 1
0dbc: Object: 88a554c0  GrantedAccess: 001f03ff Entry: e35e1b78
Object: 88a554c0  Type: (8780c68) Thread
    ObjectHeader: 88a554a8
    HandleCount: 1  PointerCount: 1
...
```

Examination of these threads shows their stack traces and start addresses:

```
0: kd> !thread 88b4a730
THREAD 88b4a730  Cid 0004.185c  Teb: 00000000 Win32Thread: 00000000 TERMINATED
Not impersonating
DeviceMap    e1000930
Owning Process    8b7807a8    Image:         System
Wait Start TickCount    975361    Ticks: 980987 (0:04:15:27.921)
Context Switch Count    1    
UserTime    00:00:00.0000
KernelTime    00:00:00.0000
Start Address mydriver!StatusWaitThread (0xf5c5d128)
Stack Init f3c4cc98 Base f3c4d000 Limit f3c4a000 Call 0
Priority 8 BasePriority 8 PriorityDecrement 0
ChildEBP RetAddr  Args to Child
f3c4ccac 8083129e ffdff5f0 8697ba00 a674c913 hal!KfLowerIrql+0x62
f3c4ccc8 00000000 808ae498 8697ba00 00000000 nt!KiExitDispatcher+0x130
```

```
0: kd> !thread 88a554c0
THREAD 88a554c0  Cid 0004.1888c  Teb: 00000000 Win32Thread: 00000000 TERMINATED
Not impersonating
DeviceMap    e1000930
Owning Process    8b7807a8    Image:         System
Wait Start TickCount    975380    Ticks: 980968 (0:04:15:27.625)
Context Switch Count    1    
UserTime    00:00:00.0000
KernelTime    00:00:00.0000
Start Address mydriver!StatusWaitThread (0xf5c5d128)
Stack Init 0 Current f34cc98 Base f3c4d000 Limit f3c4a000 Call 0
Priority 8 BasePriority 8 PriorityDecrement 0
ChildEBP RetAddr  Args to Child
f3c4ccac 8083129e ffdff5f0 8697ba00 a674c913 hal!KfLowerIrql+0x62
f3c4ccc8 00000000 808ae498 8697ba00 00000000 nt!KiExitDispatcher+0x130
```

We can see that these threads have been terminated, and their start address belongs to mydriver.sys.

Therefore, we can say that mydriver code has to be examined to find the source of our handle leak.

## Comments

Enabling Application Verifier using gflags.exe before running the leaking application and then using !htrace WinDbg command can show stack traces for handle usage. For example, quick test for notepad.exe:

```
0:001> !htrace 0x00000100
--------------------------------------
Handle = 0x00000100 - CLOSE
Thread ID = 0x00002d7c, Process ID = 0x0000237c

0x7c836b0c: ntdll!LdrGetDllHandleEx+0x000002b8
0x7c836cf9: ntdll!LdrGetDllHandle+0x00000018
0x77e645c2: kernel32!GetModuleHandleForUnicodeString+0x00000049
0x77e66516: kernel32!BasepGetModuleHandleExW+0x0000017f
0x77e663f4: kernel32!GetModuleHandleW+0x00000029
0x773a2eb3: USER32!_InitializeImmEntryTable+0x00000047
0x773c5369: USER32!UserClientDllInitialize+0x00000163
0x5a61897f: verifier!AvrfpStandardDllEntryPointRoutine+0x0000014f
0x7c82257a: ntdll!LdrpCallInitRoutine+0x00000014
0x7c8358fb: ntdll!LdrpRunInitializeRoutines+0x00000367
--------------------------------------
Handle = 0x00000100 - OPEN
Thread ID = 0x00002d7c, Process ID = 0x0000237c

0x7c836b0c: ntdll!LdrGetDllHandleEx+0x000002b8
0x7c836cf9: ntdll!LdrGetDllHandle+0x00000018
0x77e645c2: kernel32!GetModuleHandleForUnicodeString+0x00000049
0x77e66516: kernel32!BasepGetModuleHandleExW+0x0000017f
0x77e663f4: kernel32!GetModuleHandleW+0x00000029
0x773a2eb3: USER32!_InitializeImmEntryTable+0x00000047
0x773c5369: USER32!UserClientDllInitialize+0x00000163
0x5a61897f: verifier!AvrfpStandardDllEntryPointRoutine+0x0000014f
--------------------------------------
Parsed 0x2EC stack traces.
Dumped 0x2 stack traces.
```

Another example from the complete memory dump where Application Verifier was enabled for MyApp.exe:

```
03: kd> .process /p /r 0x8896e670
Implicit process is now 8896e670
Loading User Symbols

03: kd> dt _PEB 7ffdd000
ntdll!_PEB
+0x000 InheritedAddressSpace : 0 ""
+0x001 ReadImageFileExecOptions : 0x1 ""
+0x002 BeingDebugged : 0 ""
+0x003 BitField : 0 ""
+0x003 ImageUsesLargePages : 0y0
+0x003 SpareBits : 0y0000000 (0)
+0x004 Mutant : 0xffffffff
+0x008 ImageBaseAddress : 0x04000000
```
