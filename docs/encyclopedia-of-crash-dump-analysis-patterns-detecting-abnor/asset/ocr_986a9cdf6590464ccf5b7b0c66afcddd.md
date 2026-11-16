We see **Constant Subtrace** (page 137) until `wbemcore!EnsureInitialized` function which serves as a bifurcation stack frame. The first stack trace has `CriticalSection::Enter` after the bifurcation stack frame compared to the second stack trace which looks like **Spiking Thread** (page 885) in user space.

There is no hidden critical section associated with that process except the one which is probably related to the spiking **Variable Subtrace** (page 1058) since it doesn't have any `LockCount`:

```
0: kd> !cs -l -o -s
DebugInfo       = 0x0000000004a774d0
Critical section = 0x0000000000308d690 (+0x308D690)
LOCKED
LockCount       = 0x0
WaiterWoken     = No
OwningThread    = 0x0000000000000928
RecursionCount  = 0x1
LockSemaphore   = 0x0
SpinCount       = 0x0000000000000000
OwningThread    = .thread ffffa806ebd8060
ntdll!RtlpStackTraceDataBase is NULL. Probably the stack traces are not enabled
```

We can also disassemble `wbemcomm!CWbemCriticalSection::Enter` and find out that it calls `WaitForSingleObject` once and no other synchronization API indeed:

```
0: kd> uf wbemcomm!CWbemCriticalSection::Enter
[...]
wbemcomm!CWbemCriticalSection::Enter+0x41:
000007fe`f78ad1c0 mov     rcx,qword ptr [rbx+10h]
000007fe`f78ad1c4 mov     edx,r12d
000007fe`f78ad1c7 call    qword ptr [wbemcomm!_imp_WaitForSingleObject (000007fe`f78ee4f0)]
000007fe`f78ad1cd cmp     eax,esi
000007fe`f78ad1cf je      wbemcomm!CWbemCriticalSection::Enter+0x52 (000007fe`f78a62a3) Branch
```

We add this **Nonstandard Synchronization** memory analysis pattern to **Wait Chain** analysis pattern category.