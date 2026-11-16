```
0:014> !CLRStack
OS Thread Id: 0x11ec (14)
ESP         EIP
075af4fc 016bfd9a Ironring.Management.MMC.SnapinBase+MmcWindow.Invoke(System.Delegate, System.Object[])
...
...
...
075af740 793d87af System.Threading._ThreadPoolWaitCallback.WaitCallback_Context(System.Object)
075af748 793608fd System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object)
075af760 79388898 System.Threading._ThreadPoolWaitCallback.PerformWaitCallback(System.Object)
075af8f0 79e7be1b [GCFrame: 075af8f0]
```

!help command gives the list of other available SOS extension commands:

```
0:014> !help

Object Inspection

DumpObj (do)
DumpArray (da)
DumpStackObjects (dso)
DumpHeap
DumpVC
GCRoot
ObjSize
FinalizeQueue
PrintException (pe)
TraverseHeap

Examining code and stacks

Threads
CLRStack
IP2MD
U
DumpStack
EEStack
GCInfo
EHInfo
COMState
BPMD

Examining CLR data structures

DumpDomain
EEHeap
Name2EE
SyncBlk
DumpMT
DumpClass
DumpMD
Token2EE
EEVersion
```