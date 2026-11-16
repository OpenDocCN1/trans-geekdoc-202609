# 1010 | Thread Starvation

```
0012ffa0 8082ea41 MSVBVM50!CMSOComponent::PushMsgLoop+0x24
0012fef8 762d5f8e ntl!KiDeliverApc+0x11f
0012fff0 762df55 MSVBVM50!SCM_MsoCompMgr::FPushMessageLoop+0x2f
0012ffa0 8082ea41 MSVBVM50!CMSOComponent::PushMsgLoop+0x24
0012fff8 762d5f55 nt!KiDeliverApc+0x11f
0012ffa0 8082ea41 MSVBVM50!CMSOComponent::PushMsgLoop+0x24
0012fff4 0012ffc8 nt!KiDeliverApc+0x11f
00000000 00000000 0x12ffc8
```

What we see here is unusually high Priority and BasePriority values (24 and 24). This means that the base priority of these processes was most likely artificially increased to Realtime. Most processes have base priority 8 (Normal):

```
0: kd> !thread 88780db0 1f
THREAD 88780db0 Cid 44a8.1b8c Teb: 7ffaf000 Win32Thread: bc315d20 WAIT: (Unknown) UserMode Non-
Alertable
	8878b650 Semaphore Limit 0x7fffffff
	88780e28 NotificationTimer
Not impersonating
DeviceMap e1085298
Owning Process 889263a0 Image: explorer.exe
Wait Start TickCount 1565543 Ticks: 4194 (0:00:01:05.531)
Context Switch Count 7 LargeStack
UserTime 00:00:00.000
KernelTime 00:00:00.000
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init b6754000 Current b6753c0c Base b6754000 Limit b6750000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0

ChildEBP RetAddr
b6753c24 80833e8d nt!KiSwapContext+0x26
b6753c50 80829b74 nt!KiSwapThread+0x2e5
b6753c98 809249cd nt!KeWaitForSingleObject+0x346
b6753d48 8088ac4c nt!NtReplyWaitReceivePortEx+0x521
b6753d48 7c8285ec nt!KiFastCallEntry+0x8fc
01a2fe18 7c82783b ntdll!KiFastSystemCallRet
01a2fe1c 77c885ac ntdll!NtReplyWaitReceivePortEx+0xc
01a2ff84 77c88792 RPCRT4!LRPC_ADDRESS::ReceiveLotsaCalls+0x198
01a2ff8c 77c8872d RPCRT4!RecvLotsaCallsWrapper+0xd
01a2ffac 77c7b110 RPCRT4!BaseCachedThreadRoutine+0x9d
01a2ffb8 77e64829 RPCRT4!ThreadStartRoutine+0x1b
01a2ffc 00000000 kernel32!BaseThreadStart+0x34
```