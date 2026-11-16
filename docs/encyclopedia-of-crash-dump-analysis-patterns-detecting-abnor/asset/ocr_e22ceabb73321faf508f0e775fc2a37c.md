```
00000000`1a98f0a0 000007fe`f74e2bbb 0x7ff`00167271
00000000`1a98f130 000007fe`f753ed76 mscorlib_ni+0xf2bbb
00000000`1a98f180 000007fe`f8390282 mscorlib_ni+0x34ed76
00000000`1a98f1d0 000007fe`f8274363 mscorwks!CallDescWorker+0x82
00000000`1a98f220 000007fe`f8274216 mscorwks!CallDescrWorkerWithHandler+0xd3
00000000`1a98f2c0 000007fe`f81c96a7 mscorwks!DispatchCallDebuggerWrapper+0x3e
00000000`1a98f320 000007fe`f830ae42 mscorwks!DispatchCallNoEH+0x5f
00000000`1a98f3a0 000007fe`f81bdc00 mscorwks!AddTimerCallBack_Worker+0x92
00000000`1a98f430 000007fe`f824a1a5 mscorwks!ManagedThreadCallState::IsAppDomainEqual+0x4c
00000000`1a98f480 000007fe`f82d1f99 mscorwks!SVR::gc_heap::make_heap_segment+0x155
00000000`1a98f550 000007fe`f82ceca2 mscorwks!DoOpenInstanceStress::DoOpenAssemblyStress+0x99
00000000`1a98f590 000007fe`f830c0db mscorwks!AddTimerCallBackEx+0xba
00000000`1a98f650 000007fe`f81eeb37 mscorwks!ThreadpoolMgr::AsyncTimerCallbackCompletion+0x53
00000000`1a98f6b0 000007fe`f81fe92a mscorwks!UnManagedPerAppDomainTPCount::DispatchWorkItem+0x157
00000000`1a98f750 000007fe`f81bb1fc mscorwks!ThreadpoolMgr::WorkerThreadStart+0x1ba
00000000`1a98f7f0 00000000`76e7652d mscorwks!Thread::intermediateThreadProc+0x78
00000000`1a98fcc0 00000000`76fac521 kernel32!BaseThreadInitThunk+0xd
00000000`1a98fcf0 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
[...]
```

15 Id: d50.7248 Suspend: 0 Teb: 000007ff`ffee6000 Unfrozen
Child-SP RetAddr Call Site

```
00000000`1c16e6f0 000007fe`f87946af mscorwks!AwareLock::Contention+0x13b
00000000`1c16e7c0 000007ff`0016135e mscorwks!JITutil_MonContention+0xdf
00000000`1c16e970 000007ff`0016726b 0x7ff`0016135e
00000000`1c16e9c0 000007fe`f74e2bbb 0x7ff`0016726b
00000000`1c16ea50 000007fe`f753ed76 mscorlib_ni+0xf2bbb
00000000`1c16eaa0 000007fe`f8390282 mscorlib_ni+0x34ed76
00000000`1c16eaf0 000007fe`f8274363 mscorwks!CallDescWorker+0x82
00000000`1c16eb40 000007fe`f8274216 mscorwks!CallDescrWorkerWithHandler+0xd3
00000000`1c16ebe0 000007fe`f81c96a7 mscorwks!DispatchCallDebuggerWrapper+0x3e
00000000`1c16ecc0 000007fe`f81bdc00 mscorwks!AddTimerCallBack_Worker+0x92
00000000`1c16ed50 000007fe`f824a1a5 mscorwks!ManagedThreadCallState::IsAppDomainEqual+0x4c
00000000`1c16eda0 000007fe`f82df199 mscorwks!SVR::gc_heap::make_heap_segment+0x155
00000000`1c16ee70 000007fe`f82ceca2 mscorwks!DoOpenInstanceStress::DoOpenAssemblyStress+0x99
00000000`1c16eeb0 000007fe`f830c0db mscorwks!AddTimerCallBackEx+0xba
00000000`1c16ef70 000007fe`f81eeb37 mscorwks!ThreadpoolMgr::AsyncTimerCallbackCompletion+0x53
00000000`1c16efd0 000007fe`f81fe92a mscorwks!UnManagedPerAppDomainTPCount::DispatchWorkItem+0x157
00000000`1c16f070 000007fe`f81bb1fc mscorwks!ThreadpoolMgr::WorkerThreadStart+0x1ba
00000000`1c16f110 00000000`76e7652d mscorwks!Thread::intermediateThreadProc+0x78
00000000`1c16f9e0 00000000`76fac521 kernel32!BaseThreadInitThunk+0xd
00000000`1c16fa10 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
[...]
```