calling mscorwks!WaitHandleNative::CorWaitOneNative
05faf4fc 00f2f00a (MethodDesc 0x4f97500 +0x9a
IronRing.Management.MMC.SnapinBase+MmcWindow.Invoke(System.Delegate, System.Object[])), calling
mscorwks!JIT_Throw
05faf510 05e00dfa (MethodDesc 0x4f98fd8 +0xca MyNamespace.MyClass.MyMethod(Boolean)), calling 05fc7124
05faf55c 00f62fbc (MethodDesc 0x4f95f90 +0x16f4 MyNamespace.MyClass.MyMethod.Initialise(System.Object))
05faf740 793d912f (MethodDesc 0x7925fc70 +0x2f
System.Threading._ThreadPoolWaitCallback.WaitCallback_Context(System.Object))
05faf748 793683dd (MethodDesc 0x7913f3d0 +0x81
System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object))
05faf75c 793d9218 (MethodDesc 0x7925fc80 +0x6c
System.Threading._ThreadPoolWaitCallback.PerformWaitCallback(System.Object)), calling (MethodDesc
0x7913fd30 +0 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object))
05faf774 79e88f63 mscorwks!CallDescWorker+0x33
05faf784 79e88ee4 mscorwks!CallDescWorkerWithHandler+0xa3, calling mscorwks!CallDescWorker
05faf804 79f20212 mscorwks!DispatchCallBody+0x1e, calling mscorwks!CallDescWorkerWithHandler
05faf824 79f201bc mscorwks!DispatchCallDebuggerWrapper+0x3d, calling mscorwks!DispatchCallBody
05faf888 79f2024b mscorwks!DispatchCallNoEH+0x51, calling mscorwks!DispatchCallDebuggerWrapper
05faf8bc 7a07bdf0 mscorwks!Holder,2::-::Holder,2+0x8bb, calling mscorwks!DispatchCallNoEH
05faf90c 77e61d1e kernel32!WaitForSingleObjectEx+0xac, calling ntdll!ZwWaitForSingleObject
05faf91c 79ecb4a4 mscorwks!Thread::UserResumeThread+0xfb
05faf92c 79ecb442 mscorwks!Thread::DoADCallBack+0x355, calling mscorwks!Thread::UserResumeThread+0xae
05faf950 79e74fae mscorwks!Thread::EnterRuntimeNoThrow+0x9b, calling mscorwks!_EH_epilog3
05faf988 79e77fe8 mscorwks!PEImage::LoadImage+0x1e1, calling mscorwks!_SEH_epilog4
05faf9c0 79ecb364 mscorwks!Thread::DoADCallBack+0x541, calling mscorwks!Thread::DoADCallBack+0x2a5
05faf9fc 7a0e1b7e mscorwks!Thread::DoADCallBack+0x575, calling mscorwks!Thread::DoADCallBack+0x4d4
05fafa24 7a0e1bab mscorwks!ManagedThreadBase::ThreadPool+0x13, calling
mscorwks!Thread::DoADCallBack+0x550
05fafa38 07a0cae8 mscorwks!QueueUserWorkItemCallback+0x9d, calling mscorwks!ManagedThreadBase::ThreadPool
05fafa54 7a07ca48 mscorwks!QueueUserWorkItemCallback, calling
mscorwks!UnwindAndContinueRethrowHelperAfterCatch
05fafa90 7a110f08 mscorwks!ThreadpoolMgr::ExecuteWorkRequest+0x40
05fafaa8 7a112328 mscorwks!ThreadpoolMgr::WorkerThreadStart+0x1f2, calling
mscorwks!ThreadpoolMgr::ExecuteWorkRequest
05fafad0 79e7839d mscorwks!EEHeapFreeInProcessHeap+0x21, calling mscorwks!EEHeapFree
05fafae0 79e782dc mscorwks!operator delete[]+0x30, calling mscorwks!EEHeapFreeInProcessHeap
05fafb14 79ecb00b mscorwks!Thread::intermediateThreadProc+0x49
05fafb48 77e65512 kernel32!FlsSetValue+0xc7, calling kernel32!_SEH_epilog
05fafb6c 75da1400 sxs!_calll_retval+0x19, calling sxs!calloc
05fafb80 77e65512 kernel32!FlsSetValue+0xc7, calling kernel32!_SEH_epilog
05fafb88 75da1401 sxs!_CRT_INIT+0x17e, calling sxs!_initptd
05fafb8c 75da1408 sxs!_CRT_INIT+0x185, calling kernel32!GetCurrentThreadId
05fafb9c 304f3805 MMCFormsShim!DllMain+0x15, calling MMCFormsShim!PrxDllMain
05fafbb0 304f8b69 MMCFormsShim!_DllMainCRTStartup+0x7a, calling MMCFormsShim!DllMain
05fafbdc 75de0e4c sxs!SxsDllMain+0x87, calling sxs!DllStartup_CrtInit
05fafbf0 304f8bf9 MMCFormsShim!_DllMainCRTStartup+0x10a, calling MMCFormsShim!__SEH_epilog4
05fafbf4 304f8c2e MMCFormsShim!_DllMainCRTStartup+0x1d, calling MMCFormsShim!_DllMainCRTStartup
05fafbfc 7c81a352 ntdll!LdrpCallInitRoutine+0x14
05fafc24 7c82ee8b ntdll!LdrpInitializeThread+0x1a5, calling ntdll!RtlLeaveCriticalSection
05fafc2c 7c82edec ntdll!LdrpInitializeThread+0x18f, calling ntdll!_SEH_epilog
05fafc7c 7c82ed71 ntdll!LdrpInitializeThread+0xd8, calling ntdll!RtlActivateActivationContextUnsafeFast
05fafc80 7c82ed35 ntdll!LdrpInitializeThread+0x12c, calling
ntdll!RtlDeactivateActivationContextUnsafeFast
05facb4c 7c82edec ntdll!LdrpInitializeThread+0x18f, calling ntdll!_SEH_epilog