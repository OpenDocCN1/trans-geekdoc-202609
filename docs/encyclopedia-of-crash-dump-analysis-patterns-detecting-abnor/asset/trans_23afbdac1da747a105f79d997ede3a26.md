

```
Tail.Apc = 00000000
Tail.CompletionKey = 00000000
    cmd   flg cl  Device  File     Completion-Context
[ 0, 0]   0   0 00000000 00000000 00000000-00000000

    Args: 00000000 00000000 00000000 00000000
[ 0, 0]   0   0 00000000 00000000 00000000-00000000

    Args: 00000000 00000000 00000000 00000000
[ 0, 0]   0   0 00000000 00000000 00000000-00000000

    Args: 00000000 00000000 00000000 00000000
>[c, 2]   0   1 8ab20388 89ff8920 00000000-00000000    pending
    \Device\DeviceA
    Args: 00000020 00000017 00000000 00000000
[c, 2]   0   0 8affa4b8 89ff8920 00000000-00000000
    \Device\DeviceB
    Args: 00000020 00000017 00000000 00000000
```

## 注释

Windows Server 2008 中的等待链遍历 API^227。

涉及 LPC 调用的等待链（第 1092 页）可以通过在 `!process 0 3f` 命令的输出中搜索“等待回复”轻松识别，或者如果我们知道某个特定进程挂起并且在其线程信息输出中看到了该消息。例如，在 AppA 挂起时保存的一个内核内存转储文件中，我们看到了阻塞线程模式（第 82 页）的示例：

```
7: kd> !process 88556778 3f
PROCESS 88556778 SessionId: 0 Cid: 1f88 Peb: 7ffdc000 ParentCid: 0f74
DirBase: 96460000 ObjectTable: e65a5348 HandleCount: 80.
Image: AppA.exe
VadRoot 870d2208 Vads 54 Clone 0 Private 234. Modified 0. Locked 0.
DeviceMap e22ba7c0
Token e5e47cf0
ElapsedTime 00:04:44.017
UserTime 00:00:00.000
KernelTime 00:00:00.000
QuotaPoolUsage[PagedPool] 20092
QuotaPoolUsage[NonPagedPool] 2160
Working Set Sizes (now,min,max) (748, 50, 345) (2992KB, 200KB, 1380KB)
PeakWorkingSetSize 748
VirtualSize 16 Mb
PeakVirtualSize 16 Mb
PageFaultCount 810
MemoryPriority BACKGROUND
BasePriority 8
CommitCharge 252

PEB NULL...

THREAD 8861aa88 Cid 1f88.1bd4 Teb: 7ffdf000 Win32Thread: bc161ea8 WAIT: (Unknown) UserMode Non-
Alertable
8861aca4 Semaphore Limit 0x1
Waiting for reply to LPC MessageId 00037bb2:
Current LPC port e625bbd0
Not impersonating
DeviceMap e22ba7c0
Owning Process 88556778 Image: AppA.exe
Wait Start TickCount 426549 Ticks: 18176 (0:00:04:44.000)
Context Switch Count 76 LargeStack
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x010043ab
Start Address 0x776e17f8
Stack Init bab4b000 Current bab4ac08 Base bab4b000 Limit bab47000 Call 0
Priority 11 BasePriority 8 PriorityDecrement 2
Kernel stack not resident.
ChildEBP RetAddr
bab4ac20 8083d5b1 nt!KiSwapContext+0x26
bab4ac4c 8083df9e nt!KiSwapThread+0x2e5
bab4ac94 8093eda1 nt!KeWaitForSingleObject+0x346
bab4ad50 80833bef nt!NtRequestWaitReplyPort+0x776
bab4ad50 7c8288ec nt!KiFastCallEntry+0xfc
```

现在我们查找正在处理消息 00037bb2 的服务器线程：

```
7: kd> !lpc message 00037bb2
Searching message 37bb2 in threads ...
Server thread 89815db0 is working on message 37bb2
Client thread 8861aab8 waiting a reply from 37bb2
Searching thread 8861aab8 in port rundown queues ...

Server communication port 0xe1216be8
 Handles: 1  References: 1
 The LpcDataInfoChainHead queue is empty
 Connected port: 0xe625bbd0         Server connection port: 0xe1323f68

Client communication port 0xe625bbd0
 Handles: 1  References: 2
 The LpcDataInfoChainHead queue is empty

Server connection port e1323f68 Name: ApiABC
 Handles: 1  References: 43
 Server process : 887d32d0 (svchost.exe)
 Queue semaphore : 884df210
 Semaphore state 0 (0x0)
 The message queue is empty

 Messages in LpcDataInfoChainHead:
 0000 e6067418 - Busy Id=00020695 From: 0224.134c Context=80050003 [e1323fe8 . e65fa5a8]
         Length=0044002c Type=00380001 (LPC_REQUEST)
         Data: 00000001 00050242 00000000 00000000 00000000 00000000

 0000 e65fa5a8 - Busy Id=0002e1dd From: 0f0d8.0fe0 Context=80110002 [e6067418 . e5f6a360]
         Length=0044002c Type=00380001 (LPC_REQUEST)
         Data: 00000001 00050242 c3007fc0 c01fff7c 00000000 80a84456

 0000 e5f6a360 - Busy Id=00037bb2 From: 1f88.1b4d Context=8017000f [e65fa5a8 . e1323fe8]
         Length=0044002c Type=00380001 (LPC_REQUEST)
         Data: 00000001 00050242 88572278 88572290 8a386990 000015e7

 The LpcDataInfoChainHead queue contains 3 messages
 Threads in RunDown queue : 0xe6067258 0xe65fa3e8 0xe5f61a10

Done.
```

```
7: kd> !thread 89815db0
THREAD 89815db0 Cid 1218.0c00 Teb: 7ff8f000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-
Alertable

88603e40 Mutant - owning thread 884d7db0

Not impersonating
DeviceMap            e10018b8
Owning Process       887d32d0       Image:         svchost.exe
Wait Start TickCount 426549          Ticks: 18176 (0:00:04:44.000)
Context Switch Count 42
UserTime             00:00:00.000
KernelTime           00:00:00.000
Win32 Start Address 0x00037bb2
LPC Server thread working on message Id 37bb2
Start Address 0x77e617ec
Stack Init f60e0000 Current f60dfc60 Base f60e0000 Limit f60dd000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0
Kernel stack not resident.
ChildEBP RetAddr   Args to Child
f60dfc78 8083d5b1 89815db0 89815e58 00000006 nt!KiSwapContext+0x26
f60dfca4 8083df9e 00000000 00000000 00000000 nt!KiSwapThread+0x2e5
f60dfcec 8092ae57 88603e40 00000006 00000001 nt!KeWaitForSingleObject+0x346
f60dfd50 80833bef 000004fc 00000000 00000000 nt!NtWaitForSingleObject+0x9a
f60dfd50 7c8285ec 000004fc 00000000 00000000 nt!KiFastCallEntry+0xfc
```

我们看到它正在阻塞并等待一个同步对象（互斥体，如上文所示，以粗斜体显示），我们检查拥有它的线程 884d7db0：

```
7: kd> !thread 884d7db0
THREAD 884d7db0 Cid 1218.1ec2 Teb: 7ffdd000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-
Alertable
884d7f9c Semaphore Limit 0x1
Waiting for reply to LPC MessageId 0000fa9e:
Current LPC port e121fdb8
Not impersonating
DeviceMap e10018b8
Owning Process 887d32d0 Image: svchost.exe
Wait Start TickCount 11800 Ticks: 432925 (0:01:52:44.453)
Context Switch Count 111
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x0000fa9b
LPC Server thread working on message Id fa9b
Start Address 0x77e617ec
Stack Init f4598000 Current f4597c08 Base f4598000 Limit f4595000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0
Kernel stack not resident.
ChildEBP RetAddr Args to Child
f4597c20 8083d5b1 884d7db0 884d7e58 00000007 nt!KiSwapContext+0x26
f4597c4c 8083df9e 884d7f9c 884d7f70 884d7db0 nt!KiSwapThread+0x2e5
f4597c94 8093eda1 884d7f9c 00000011 80939091 nt!KeWaitForSingleObject+0x346
f4597d50 80833bef 00000560 0000ebfe 0000ebfe nt!NtRequestWaitReplyPort+0x776
f4597d50 7c8285ec 00000560 0000ebfe 0000ebfe nt!KiFastCallEntry+0xfc
```

该线程正在等待 LPC 消息 0000fa9e，我们查找正在处理该消息的服务器线程：

```
7: kd> !thread 898c6db0
THREAD 898c6db0 Cid 0b38.188c Teb: 7ff4d000 Win32Thread: 00000000 WAIT: (Unknown) UserMode Non-
Alertable
884362c8 SynchronizationEvent
Not impersonating
DeviceMap e11399e8
Owning Process 88340758 Image: AppB.exe
Wait Start TickCount 11801 Ticks: 432924 (0:01:52:44.437)
Context Switch Count 7
UserTime 00:00:00.000
KernelTime 00:00:00.000
Win32 Start Address 0x0000fa9e
LPC Server thread working on message Id fa9e
Start Address 0x77e617ec
Stack Init f5138000 Current f5137c60 Base f5138000 Limit f5135000 Call 0
Priority 9 BasePriority 8 PriorityDecrement 0
Kernel stack not resident.
ChildEBP RetAddr  Args to Child
f5137c78 8083d5b1 898c6db0 898c6e58 00000006 nt!KiSwapContext+0x26
f5137ca4 8083df9e 00000000 00000000 00000000 nt!KiSwapThread+0x2e5
f5137cec 8092ae57 884362c8 00000006 00000001 nt!KeWaitForSingleObject+0x346
f5137d50 80833bef 000005c0 00000000 00000000 nt!NtWaitForSingleObject+0x9a
f5137d50 7c8285ec 000005c0 00000000 00000000 nt!KiFastCallEntry+0xfc
```

我们还看到线程 884d7db0 正在处理消息 fa9b（如上文所示，以带下划线加粗显示），因此我们可以找到其客户端线程：

```
7: kd> !lpc message fa9b
Searching message fa9b in threads ...
Server thread 884d7db0 is working on message fa9b
Client thread 871ab9a0 waiting a reply from fa9b
Searching thread 871ab9a0 in port rundown queues ...

Server communication port 0xe23f68b8
Handles: 1 References: 1
The LpcDataInfoChainHead queue is empty
Connected port: 0xe1325c10         Server connection port: 0xe1323f68

Client communication port 0xe1325c10
Handles: 1 References: 2
The LpcDataInfoChainHead queue is empty

Server connection port e1323f68 Name: ApiABC
Handles: 1 References: 43
Server process : 887d32d0 (svchost.exe)
Queue semaphore : 884df210
Semaphore state 0 (0x0)
The message queue is empty

Messages in LpcDataInfoChainHead:
0000 e6067418 - Busy Id=00020695 From: 0224.134c Context=80050003 [e1323fe8 . e65fa5a8]
Length=0044002c Type=00380001 (LPC_REQUEST)
Data: 00000001 00050242 00000000 00000000 00000000 00000000
0000 e65fa5a8 - Busy Id=00021edd From: 0fd8.0fe0 Context=80110002 [e6067418 . e5f6a360]
Length=0044002c Type=00380001 (LPC_REQUEST)
Data: 00000001 00050242 c03007fc c01fff7c 00000000 80a84456
0000 e5f6a360 - Busy Id=00037bb2 From: 1f88.1bd4 Context=8017000f [e65fa5a8 . e1323fe8]
Length=0044002c Type=00380001 (LPC_REQUEST)
Data: 00000001 00050242 88572278 88572290 8a386990 000015e7
The LpcDataInfoChainHead queue contains 3 messages

Threads in RunDown queue :    0xe6067258    0xe65fa3e8    0xe5f6a1a0
Done.
```

