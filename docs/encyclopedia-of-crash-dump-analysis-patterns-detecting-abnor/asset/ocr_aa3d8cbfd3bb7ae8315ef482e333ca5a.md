```
```
+0x050 Reserved2  : 0x00000001`00000001 Void
+0x058 Address  : 0x00000000`00000005 Void
+0x058 CreatorBackTraceIndex : 5
+0x060 SpinLock  : 0
```
```

However, we need to be sure that we supplied the correct pointer to dt WinDbg command. One of the signs that the pointer was incorrect is memory read errors or all zeroes:

```
```
0: kd> dt _ERESOURCE ffffd000229af830
ntdll!_ERESOURCE
+0x000 SystemResourcesList : _LIST_ENTRY [ 0x00000000`00000000 - 0x00000000`00000000 ]
+0x010 OwnerTable : (null)
+0x018 ActiveCount : 0n0
+0x01a Flag : 0
+0x01a ReservedLowFlags : 0 ''
+0x01b WaiterPriority : 0 ''
+0x020 SharedWaiters : (null)
+0x028 ExclusiveWaiters : (null)
+0x030 OwnerEntry : _OWNER_ENTRY
+0x040 ActiveEntries : 0
+0x044 ContentionCount : 0
+0x048 NumberOfSharedWaiters : 0
+0x04c NumberOfExclusiveWaiters : 0
+0x050 Reserved2 : (null)
+0x058 Address : (null)
+0x058 CreatorBackTraceIndex : 0
+0x060 SpinLock : 0

0: kd> dt _ERESOURCE ffffd000022faf830
ntdll!_ERESOURCE
+0x000 SystemResourcesList : _LIST_ENTRY
+0x010 OwnerTable  : ???
+0x018 ActiveCount  : ??
+0x01a Flag  : ??
+0x01a ReservedLowFlags  : ??
+0x01b WaiterPriority  : ??
+0x020 SharedWaiters  : ???
+0x028 ExclusiveWaiters  : ???
+0x030 OwnerEntry  : _OWNER_ENTRY
+0x040 ActiveEntries  : ??
+0x044 ContentionCount  : ??
+0x048 NumberOfSharedWaiters  : ??
+0x04c NumberOfExclusiveWaiters  : ??
+0x050 Reserved2  : ???
+0x058 Address  : ???
+0x058 CreatorBackTraceIndex  : ??
+0x060 SpinLock  : ??
Memory read error ffffd000022faf890
```
```