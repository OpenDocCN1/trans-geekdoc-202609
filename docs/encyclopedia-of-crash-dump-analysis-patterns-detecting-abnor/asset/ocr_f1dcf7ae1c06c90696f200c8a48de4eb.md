# Executive Resources

Some Windows synchronization objects like executive resources and critical sections have a struct member called *ContentionCount*. This is the number of times a resource was accessed or, in other words, it is the accumulated number of threads waiting for an object: when a thread tries to acquire an object and is put into a waiting state the count is incremented. Hence the name of this pattern: **High Contention**.

Here is an example. In a kernel memory dump, we have just one exclusively owned lock, and it seems that no other threads were blocked by it at the time the dump was saved. However, the high contention count reveals CPU spike (**Spiking Thread**, page 888):

```
3: kd> !locks
**** DUMP OF ALL RESOURCE OBJECTS ****
KD: Scanning for held locks...

Resource @ 0x8abc11f0 Exclusively owned
 Contention Count = 19648535
 Threads: 896395f8-01<*>
KD: Scanning for held locks...

Resource @ 0x896fab88 Shared 1 owning threads
 Threads: 88c78608-01<*>
KD: Scanning for held locks...
15464 total locks, 2 locks currently held

3: kd> !thread 896395f8
THREAD 896395f8 Cid 04c.0.0138 Teb: 7ffde000 Win32Thread: bc922d20 RUNNING on processor 1
Not impersonating
DeviceMap e3d4c008
Owning Process 8a035020 Image: MyApp.exe
Wait Start TickCount 36969283 Ticks: 0
Context Switch Count 1926423 LargeStack
UserTime 00:00:53.843
KernelTime 00:13:10.703
Win32 Start Address 0x00401478
Start Address 0x776e17f8
Stack Init ba14b000 Current ba14abf8 Base ba14b000 Limit ba146000 Call 0
Priority 11 BasePriority 6 PriorityDecrement 5
ChildEBP RetAddr
ba14ac94 bf8c6505 001544c8 bf995948 000c000a nt!_wcsicmp+0x3a
ba14ace0 bf8c6682 00000000 00000000 00000000 win32k!_FindWindowEx+0xfb
ba14ad48 8088978c 00000000 00000000 0012f8d4 win32k!NtUserFindWindowEx+0xfef
ba14ad48 7c828sec 00000000 00000000 0012f8d4 nt!KiFastCallEntry+0xfc
```