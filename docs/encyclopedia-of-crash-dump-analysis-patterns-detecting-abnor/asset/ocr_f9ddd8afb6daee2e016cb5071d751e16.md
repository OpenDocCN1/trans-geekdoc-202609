# Comments

Another example: a client LPC thread was waiting, but the corresponding server thread value was missing in the output of Ilpc extension. Because the server process name was known from the output, the server thread was found by the same waiting value:

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