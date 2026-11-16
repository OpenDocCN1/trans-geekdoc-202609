Non-Exp system threads (no nt!ExpWorkerThread in their stack traces) having “Worker”, “Logging” or “Logger” substrings in their function names are passive threads, and they wait for data too, for example:

```
nt!KiSwapContext+0x84
nt!KiSwapThread+0x125
nt!KeWaitForMultipleObjects+0x703
nt!PfTLoggingWorker+0x81
nt!PspSystemThreadStartup+0x5b
nt!KiStartSystemThread+0x16

nt!KiSwapContext+0x84
nt!KiSwapThread+0x125
nt!KeWaitForSingleObject+0x5f5
nt!EtwLogger+0xdd
nt!PspSystemThreadStartup+0x5b
nt!KiStartSystemThread+0x16

nt!KiSwapContext+0x84
nt!KiSwapThread+0x125
nt!KeRemoveQueueEx+0x848
nt!KeRemoveQueue+0x21
rdrdr!RxpWorkerThreadDispatcher+0x6f
nt!PspSystemThreadStartup+0x5b
nt!KiStartSystemThread+0x16

nt!KiSwapContext+0x84
nt!KiSwapThread+0x125
nt!KeWaitForSingleObject+0x5f5
HTTP!UlpThreadPoolWorker+0x26c
nt!PspSystemThreadStartup+0x5b
nt!KiStartSystemThread+0x16

nt!KiSwapContext+0x84
nt!KiSwapThread+0x125
nt!KeRemoveQueueEx+0x848
nt!KeRemoveQueue+0x21
srv2!SrvProcWorkerThread+0x74
nt!PspSystemThreadStartup+0x5b
nt!KiStartSystemThread+0x16

nt!KiSwapContext+0x84
nt!KiSwapThread+0x125
nt!KeRemoveQueueEx+0x848
nt!KeRemoveQueue+0x21
srv!WorkerThread+0x90
nt!PspSystemThreadStartup+0x5b
nt!KiStartSystemThread+0x16
```