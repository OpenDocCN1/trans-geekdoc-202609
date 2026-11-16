# # Truncated Stack Trace

Sometimes we see this pattern with missing stack frames. For example, in one incident, after enabling user mode stack trace database for **Memory Leaking** (page 650) application we got these entries from the growing heap segment (other segments had non-truncated saved stack traces):

```
```
0bdc1350: 40010 . 40010 [101] - busy (3fff8) Internal

7702fbd2: ntdll!RtlAllocateHeap+0x0000021d
77005eef: ntdll!RtlpAllocateUserBlock+0x000000a2
77026a65: ntdll!RtlpLowFragHeapAllocFromContext+0x00000785
7702661f: ntdll!RtlAllocateHeap+0x00000017c
```
```

```
```
0be01360: 40010 . 40010 [101] - busy (3fff8) Internal

7702fbd2: ntdll!RtlAllocateHeap+0x0000021d
77005eef: ntdll!RtlpAllocateUserBlock+0x000000a2
77026a65: ntdll!RtlpLowFragHeapAllocFromContext+0x00000785
7702661f: ntdll!RtlAllocateHeap+0x00000017c
```
```

```
```
0be41370: 40010 . 40010 [101] - busy (3fff8) Internal

7702fbd2: ntdll!RtlAllocateHeap+0x0000021d
77005eef: ntdll!RtlpAllocateUserBlock+0x000000a2
77026a65: ntdll!RtlpLowFragHeapAllocFromContext+0x00000785
7702661f: ntdll!RtlAllocateHeap+0x00000017c
```
```

**Truncated Stack Traces** are different from **Incorrect Stack Traces** (page 499) because their surviving part is correct. How can we find the rest of such stack traces? Here we can suggest looking at other heap segments and see allocations of the same size. If **Truncated Stack Trace** comes from **Stack Trace Collection** (page 943), we can compare it with a non-truncated thread stack from another process instance having the same thread position.

# ## Comments

Another example is when a debugger truncates the output. In WinDbg case, there is a command .kframes that sets the default number of stack trace frames.

Here’s another example of **Truncated Stack Trace** from x64 Windows 10 after **NULL Code Pointer** (page 750) was called.