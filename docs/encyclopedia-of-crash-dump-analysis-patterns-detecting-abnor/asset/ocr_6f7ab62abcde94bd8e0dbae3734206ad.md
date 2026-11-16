# Coincidental Frames

For certain stack traces, we should always be aware of coincidental frames similar to **Coincidental Symbolic Information** pattern (page 137) for raw stack data. Such frames can lead to a wrong analysis conclusion. Consider this stack trace fragment from a kernel memory dump:

```
0: kd> kL 100
ChildEBP RetAddr
9c5b6550 8082d9a4 nt!KeBugCheckEx+0x1b
9c5b6914 8088befa nt!KiDispatchException+0x3a2
9c5b697c 8088beae nt!CommonDispatchException+0x4a
9c5b699c 80a6056d nt!KiExceptionExit+0x186
9c5b69a0 80893ae2 hal!KeReleaseQueuedSpinLock+0x2d
9c5b6a08 b20c3de5 nt!MiFreePoolPages+0x7dc
WARNING: Stack unwind information not available. Following frames may be wrong.
9c5b6a48 b20c4107 DriverA+0x17de5
[...]
```

The frame with MiFreePoolPages symbol might suggest some sort of a pool corruption. We can even double check return addresses and see the valid common sense assembly language code:

```
0: kd> ub 8088beae
nt!KiExceptionExit+0x167:
8088be8f 33c9 xor ecx,ecx
8088be91 e1a0000000 call nt!CommonDispatchException (8088beb0)
8088be96 33d2 xor edx,edx
8088be98 b901000000 mov ecx,1
8088be9d 8e00000000 call nt!CommonDispatchException (8088beb0)
8088bea2 33d2 xor edx,edx
8088bea4 b902000000 mov ecx,2
8088bea9 e802000000 call nt!CommonDispatchException (8088beb0)
```

```
0: kd> ub 80a6056d
hal!KeReleaseQueuedSpinLock+0x1b:
80a6055b 7511 jne hal!KeReleaseQueuedSpinLock+0x2e (80a6056e)
80a6055d 50 push eax
80a6055e f00fbb119 lock cmpxchg dword ptr [ecx],ebx
80a60562 58 pop eax
80a60563 7512 jne hal!KeReleaseQueuedSpinLock+0x37 (80a60577)
80a60565 5b pop ebx
80a60566 8aca mov cl,dl
80a60568 e8871e0000 call hal!KfLowerIrql (80a623f4)
```

```
0: kd> ub 80893ae2
nt!MiFreePoolPages+0x7c3:
80893ac9 761c jbe nt!MiFreePoolPages+0x7e1 (80893ae7)
80893acb ff75f8 push dword ptr [ebp-8]
80893ace ff7508 push dword ptr [ebp+8]
80893ad1 e87e1fcfff call nt!MiFreeNonPagedPool (8085dc54)
80893ad6 8a55ff mov dl,byte ptr [ebp-1]
80893ad9 6a0f push 0Fh
```