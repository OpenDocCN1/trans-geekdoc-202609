# Nonstandard Synchronization

Sometimes developers introduce their own variants of synchronization code instead of using synchronization API provided by language runtime and OS. If we are lucky we can spot it in function and class method names and then use **Constant Subtrace** (page 137) analysis pattern:

```
0: kd> kc
*** Stack trace for last set context - .thread/.cxr resets it
 # Call Site
00 nt!KiSwapContext
01 nt!KiCommitThreadWait
02 nt!KeWaitForSingleObject
03 nt!NtWaitForSingleObject
04 nt!KiSystemServiceCopyEnd
05 ntdll!ZwWaitForSingleObject
06 KERNELBASE!WaitForSingleObjectEx
**07 wbemcom!CWbemCriticalSection::Enter**
**08 wbemcore!EnsureInitialized**
09 wbemcore!InitAndWaitForClient
aa wbemcore!CWbemLevel1Login::ConnectorLogin
0b wbemcore!CWbemLevel1Login::NTLMLogin
0c RPCRT4!Invoke
dd RPCRT4!NdrStubCall22
0e ole32!CStdStubBuffer_Invoke
0f ole32!SyncStubInvoke
10 ole32!StubInvoke
11 ole32!CCtxComChnl::ContextInvoke
12 ole32!AppInvoke
13 ole32!ComInvokeWithLockAndIPID
14 ole32!ThreadInvoke
15 RPCRT4!DispatchToStubInCNoAvrf
16 RPCRT4!RPC_INTERFACE::DispatchToStubWorker
17 RPCRT4!RPC_INTERFACE::DispatchToStub
18 RPCRT4!RPC_INTERFACE::DispatchToStubWithObject
19 RPCRT4!LRPC_SCALL::DispatchRequest
1a RPCRT4!LRPC_SCALL::HandleRequest
1b RPCRT4!LRPC_SSASSOCIATION::HandleRequest
1c RPCRT4!LRPC_ADDRESS::HandleRequest
1d RPCRT4!LRPC_ADDRESS::ProcessIO
1e RPCRT4!LrpciOComplete
1f ntdll!TppAlpcpExecuteCallback
20 ntdll!TppWorkerThread
21 kernel32!BaseThreadInitThunk
22 ntdll!RtlUserThreadStart
```