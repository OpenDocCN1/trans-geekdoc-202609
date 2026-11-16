
f2861d50 7c94ed54 nt!KiFastCallEntry+0xfc
0a6cf590 7c942124 ntdll!KiFastSystemCallRet
0a6cf594 7c82baa8 ntdll!NtWaitForSingleObject+0xc
0a6cf604 7c82ba12 kernel32!WaitForSingleObjectEx+0xac
0a6cf618 3f691c11 kernel32!WaitForSingleObject+0x12
0a6cf658 09734436 component2!WaitForResponse+0x75
...
0a6cfb4 77cb23f7 RPCRT4!Invoke+0x30
0a6cfcb4 77cb26ed RPCRT4!NdrStubCall2+0x299
0a6cfcd0 77c409be RPCRT4!NdrServerCall2+0x19
0a6cfd04 77c4093f RPCRT4!DispatchToStubInCNoAvrf+0x38
0a6cfd58 77c40865 RPCRT4!RPC_INTERFACE::DispatchToStubWorker+0x117
0a6cfd7c 77c357eb RPCRT4!RPC_INTERFACE::DispatchToStub+0xa3
0a6cfdbc 77c41e26 RPCRT4!RPC_INTERFACE::DispatchToStubWithObject+0xc0
0a6cfdfc 77c41bb3 RPCRT4!LRPC_SCALLO::DealWithRequestMessage+0x42c
0a6cfe20 77c45458 RPCRT4!LRPC_ADDRESS::DealWithLRPCRequest+0x127
0a6cfff4 77c277f8 RPCRT4!LRPC_ADDRESS::ReceiveLotsaCalls+0x430
0a6cff8c 77c2f7dd RPCRT4!RecvLotsaCallsWrapper+0x9d
0a6cffac 77c2de88 RPCRT4!BaseCachedThreadRoutine+0x9d
0a6cfff8 7c826063 RPCRT4!ThreadStartRoutine+0x1b
0a6cfff 00000000 kernel32!BaseThreadStart+0x34

To convert ticks to the time interval we can use !whatttime command:

```
3: kd> !whatttime 0n7256
7256 Ticks in Standard Time: 01:53.375s
```

Also !stacks command shows Ticks data for threads.

## Comments

Another example: a client LPC thread was waiting, but the corresponding server thread value was missing in the output of !lpc extension. Because the server process name was known from the output, the server thread was found by the same waiting value:

```
THREAD 894e13a8 Cid 02d4.0e28 Teb: 7ffdf000 Win32Thread: e6e7cea8 WAIT: (Unknown) KernelMode Non-Alertable
894e1594 Semaphore Limit 0x1
Waiting for reply to LPC MessageId 3786440d:
Current LPC port e6edd680
IRP List:
894cb818: (0006,01d8) Flags: 00000884 Mdl: 00000000
Impersonation token: e76aa028 (Level Impersonation)
DeviceMap e558a008
Owning Process 895497d0 Image: ApplicationA.exe
Attached Process N/A Image: N/A
Wait Start TickCount 9426151 Ticks: 162368 (0:00:42:17.000)
Context Switch Count 1297 LargeStack
UserTime 00:00:00.031
KernelTime 00:00:00.359
Start Address 0x0103e100
Stack Init b7ad8000 Current b7ad7174 Base b7ad8000 Limit b7ad3000 Call 0
Priority 15 BasePriority 15 PriorityDecrement 0

0: kd> !lpc message 3786440d
Searching message 3786440d in threads ...
Client thread 894e13a8 waiting a reply from 3786440d
Searching thread 894e13a8 in port rundown queues ...

Server communication port 0xe7e7f08
Handles: 1 References: 1
The LpcDataInfoChainHead queue is empty
Connected port: 0xe6edd680 Server connection port: 0xe4f348e0

Client communication port 0xe6edd680
Handles: 0 References: 1
The LpcDataInfoChainHead queue is empty

Server connection port e4f348e0 Name: ServiceBPort
Handles: 1 References: 156
Server process : 8a75f438 (ServiceB.exe)
Queue semaphore : 8a6c4908
Semaphore state 0 (0x0)
The message queue is empty
The LpcDataInfoChainHead queue is empty
Done.
```

```
THREAD 8a6439d8 Cid 0234.02b0 Teb: 7ffa5000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Alertable
8a63b7f0 NotificationEvent
IRP List:
8a229a59: (0006,0094) Flags: 00000900 Mdl: 00000000
Not impersonating
DeviceMap e1001840
Owning Process 8a754f38 Image: ServiceB.exe
Attached Process N/A Image: N/A
Wait Start TickCount 9426151 Ticks: 162368 (0:00:42:17.000)
Context Switch Count 31433
UserTime 00:00:00.375
KernelTime 00:00:02.625
Win32 Start Address 0x4ab8f3f1
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init ba466000 Current ba465c60 Base ba466000 Limit ba463000 Call 0
Priority 13 BasePriority 9 PriorityDecrement 0
ChildEBP RetAddr
ba465c78 80833491 nt!KiSwapContext+0x26
ba465c44 80829a82 nt!KiSwapThread+0x2e5
ba465cec 80938e0a nt!KeWaitForSingleObject+0x346
ba465d50 808897ec nt!NtWaitForSingleObject+0x9a
ba465d50 7c82845c nt!KiFastCallEntry+0xfc (TrapFrame @ ba465d64)
00eef250 7c827b79 ntdll!KiFastSystemCallRet
00eef254 77e61d1e ntdll!ZwWaitForSingleObject+0xc
00eef2c4 77c6a927 kernel32!WaitForSingleObjectEx+0xac
00eef2e0 77c69cbf RPCRT4!UTIL_WaitForSyncIO+0x20
00eef304 77c6cef0 RPCRT4!UTIL_GetOverlappedResultEx+0x1d
00eef32c 77c6bb02a RPCRT4!CO_SyncRecv+0x71
00eef354 77c697f2 RPCRT4!OSF_CONNECTION::TransSendReceive+0xb8
00eef3dc 77c6969c RPCRT4!OSF_CONNECTION::SendFragment+0x2ae
00eef434 77c69842 RPCRT4!OSF_SCALL::SendNextFragment+0x1e2
00eef47c 77c69aba RPCRT4!OSF_SCALL::FastSendReceive+0x148
00eef498 77c69a3d RPCRT4!OSF_SCALL::SendReceiveHelper+0x5b
00eef4c8 77c7fef0 RPCRT4!OSF_SCALL::SendReceive+0x41
00eef4d4 77c80845 RPCRT4!I_RpcSendReceive+0x24
00eef4e8 77ce415a RPCRT4!NdrSendReceive+0x2b
00eef8d8 7d1fac12 RPCRT4!NdrClientCall2+0x22e
[...]
```

## User Dumps

Waiting Thread Time kernel pattern (page 1137) shows how to calculate thread waiting time in kernel and complete memory dumps. Unfortunately, kernel information is not available in user space and, therefore, this can be done only approximately by calculating an average or maximum waiting time.

The key is to take advantage of **!runaway** WinDbg command. Modern versions of postmortem debuggers and process dumpers usually save thread time information additionally. For example, **/ma** switch for **.dump** command does it. The _procdump.exe_ and the later versions of _userdump.exe_ also do it. When **!runaway** is invoked with 0y111 (7) flag it shows each thread user and kernel times and also the time elapsed since each thread was created. Therefore for threads that didn’t do a much CPU-intensive computation their average waiting time will almost correspond to their elapsed time. Unfortunately, we cannot say when that computation took place. It could be the case that the thread in question was waiting 98.9% of the time, and then did some computation for 0.01% and was waiting again 1% of the time, or it could be the case that it was doing computation 0.01% of the time initially and then waiting the rest of the time (99.9%) until the dump was saved.

Consider this example of a sleeping thread:

```
0:000> ~32kL 100
ChildEBP RetAddr
0a18f03c 7c82f64b ntdll!KiFastSystemCallRet
0a18f040 77e41ed1 ntdll!NtDelayExecution+0xc
0a18f0a8 77e42aed kernel32!SleepEx+0x68
0a18f0b8 0ba0c343 kernel32!Sleep+0xf
0a18f100 1b00ba49 msjet40!System::AllocatePages+0x15e
0a18f11c 1b00ba08 msjet40!PageDesc::WireCurrentPage+0x2f
0a18f13c 1b00b8dd msjet40!PageDesc::ReadPage+0x119
0a18f164 1b01b567 msjet40!Database::ReadPage+0x7a
0a18f190 1b00e309 msjet40!TableMover::GetNextRow+0xc9
0a18f1a8 1b015de9 msjet40!TableMover::Move+0xc4
0a18f1d8 1b015d9c msjet40!ErrIsamMove+0x6c
0a18f1f0 1b038aa4 msjet40!ErrRispMove+0x43
0a18f43c 1b015d9c msjet40!ErrRJPMoveRange+0x350
0a18f454 1b0200b3 msjet40!ErrDispMove+0x43
0a18f6a0 1b021e4d msjet40!ErrMaterializeRows+0x1fd
0a18f6f0 1b021c0d msjet40!ErrJPSetColumnSort+0x191
0a18f718 1b0210a4 msjet40!ErrJPOpenSort+0x105
0a18f750 1b020de5 msjet40!ErrJPOpenRvt+0x171
0a18f9f0 1b039b82 msjet40!ErrExecuteQuery+0x548
0a18fa3c 1b05548b msjet40!ErrExecuteTempQuery+0x13d
0a18fa6c 4c23b01e msjet40!JetExecuteTempQuery+0xc9
0a18fa94 4c23a8d1 odbcjt32!DoJetCloseTable+0x64
0a18fd10 4c23a6b6 odbcjt32!SQLInternalExecute+0x217
0a18fd20 4c23a694 odbcjt32!SQLExecuteCover+0x1f
0a18fd28 48b3fc1 odbcjt32!SQLExecute+0x9
0a18fd44 0c4898b5 odbc32!SQLExecute+0xd3
...
```

The process uptime can be seen from vertarget WinDbg command:

```
0:000> vertarget
...
Process Uptime: 0 days 1:17:22.000
...
```

Then we dump thread times (the output is long, and the only information for the 32nd thread is shown here):

```
0:000> !runaway 0y111
User Mode Time
  Thread    Time
  32:cfc    0 days 0:00:00.109
...
Kernel Mode Time
  Thread    Time
  32:cfc    0 days 0:00:00.062
...
Elapsed Time
  Thread    Time
...
  32:cfc    0 days 1:17:20.703
...
```

We see that 1 hour, 17 minutes and almost 21 seconds passed since the thread was created. By subtracting this time from process uptime we see that it was created in the first 2 seconds, and it was consuming less than one second of CPU time. Therefore, most of the time this thread was waiting. Unfortunately, we cannot say when it was waiting most of the time, in the beginning before it started sleeping or after. Fortunately, we might continue guessing by looking at Sleep function argument:

```
0:032> kv
ChildEBP RetAddr  Args to Child
0a18f03c 7c8264fb 77e41ed1 00000000 0a18f080 ntdll!KiFastSystemCallRet
0a18f040 77e41ed1 00000000 0a18f080 00000000 ntdll!NtDelayExecution+0xc
0a18f0a8 77e424ed 00000032 00000000 43990000 kernel32!SleepEx+0x68
0a18f0b8 1b0ac343 00000032 042a34b4 0a18f1c8 kernel32!Sleep+0xf
...
```

We see that it had been sleeping for at most 32 milliseconds and, perhaps, this is a retry / sleep loop. We might guess that the thread was recently spinning in that loop and therefore waiting all the time before that. Alternatively, we might guess that the retry portion is very small and fast and 32 milliseconds are spread over all elapsed time, and the thread was in this loop the significant proportion of time. What we can surely say that the last waiting time was no more than 32 milliseconds. in the case of waiting for an event, for example, at present, it seems there is no any reliable way of calculating this time.

## Comments

Note that “sleeping for at most 32 milliseconds” means 32 HEX milliseconds.
