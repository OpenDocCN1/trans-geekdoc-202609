```
EntryCount 0
ContentionCount 0

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