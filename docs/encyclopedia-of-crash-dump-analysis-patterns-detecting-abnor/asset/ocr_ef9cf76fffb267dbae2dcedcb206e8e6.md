```
11 000000a9`be01b5a0 00007ffe`1d490845 combase!CoGetContextToken+0x262
12 000000a9`be01b610 00007ffe`1d47f95e combase!CoCreateFreeThreadedMarshaler+0x5735
13 000000a9`be01b830 00007ffe`1d48219e combase!CoGetObjectContext+0x9bce
14 000000a9`be01bb00 00007ffe`1d4842bf combase!CoGetObjectContext+0xc40e
15 000000a9`be01bcb0 00007ffe`1d47da9c combase!CoGetObjectContext+0xe52f
16 000000a9`be01bf40 00007ffe`1ba300dc combase!CoGetObjectContext+0x70dc
17 000000a9`be01c090 00007ffe`1ba2fc07 user32!UserCallWinProcCheckWow+0x1fc
18 000000a9`be01c180 00007ffe`1d4865e9 user32!DispatchMessageWorker+0x1a7
19 000000a9`be01c200 00007ffe`1d486b8f combase!CoGetObjectContext+0x10859
1a 000000a9`be01c270 00007ffe`1d491c2d combase!CoGetObjectContext+0x10dff
1b 000000a9`be01c2d0 00007ffe`1d48d7a9 combase!CoCreateFreeThreadedMarshaler+0x6b1d
1c 000000a9`be01c420 00007ffe`1d48e215 combase!CoCreateFreeThreadedMarshaler+0x2699
1d 000000a9`be01c600 00007ffe`1d41475b combase!CoCreateFreeThreadedMarshaler+0x3105
1e 000000a9`be01c7c0 00007ffe`1baa3340 combase!NdrOleDllGetClassObject+0x0f2b
1f 000000a9`be01c830 00007ffe`1d414544 rpcrt4!NdrpClientCall3+0x460
20 000000a9`be01cc20 00007ffe`1d51f192 combase!NdrOleDllGetClassObject+0x0d14
21 000000a9`be01cfb0 00007ffe`1d4a8bd8 combase!ObjectStublessClient32+0xfc32
22 000000a9`be01d0b0 00007ffe`1d4a8a65 combase!CoWaitForMultipleHandles+0x3cd
23 000000a9`be01d070 00007ffe`1d49849d combase!CoWaitForMultipleHandles+0x2a5
24 000000a9`be01d110 00007ffe`1d49cc3a combase!CoCreateFreeThreadedMarshaler+0xd38d
25 000000a9`be01d2e0 00007ffe`1d48b6d0 combase!CoCreateFreeThreadedMarshaler+0x11b2a
26 000000a9`be01d3e0 00007ffe`1d4113f7 combase!CoCreateFreeThreadedMarshaler+0x5c0
27 000000a9`be01d430 00007ffe`1d94bd66 combase!CStdStubBuffer2_QueryInterface+0x117
28 000000a9`be01d460 00007ffd`f05ebef0 oleaut32!VariantClear+0x176
29 000000a9`be01d490 00007ffd`f05ed839 eModel!CIIFrameAuto::SetOwner+0x2b0
2a 000000a9`be01d4f0 00007ffd`f05f7892 eModel!CBrowserTabBase::v_OnDestroy+0x69
2b 000000a9`be01d520 00007ffd`f05f5247 eModel!CBrowserTab::v_OnDestroy+0x12
2c 000000a9`be01d550 00007ffd`f05f1b1b eModel!CBrowserTab:::_v_WndProc+0x447
2d 000000a9`be01d710 00007ffe`1ba300dc eModel!CBrowserTab:::_s_WndProc+0x5b
2e 000000a9`be01d760 00007ffe`1ba2fe52 user32!UserCallWinProcCheckWow+0x1fc
2f 000000a9`be01d850 00007ffe`1ba3d3fe user32!DispatchClientMessage+0xa2
30 000000a9`be01d8d0 00007ffe`1dd65714 user32!_fnDWORD+0x3e
31 000000a9`be01d910 00007ffe`1ba5061a ntdll!KiUserCallbackDispatcherContinue
32 000000a9`be01d998 00007ffd`f05f6c8c user32!NtUserDestroyWindow+0xa
33 000000a9`be01d9a0 00007ffd`f05f6ebb eModel!CBrowserTab::_DoFinalCleanup+0x35c
34 000000a9`be01da50 00007ffd`f05f6620 eModel!CBrowserTab::_OnConfirmedClose+0x2f
35 000000a9`be01da80 00007ffd`f05c0f26 eModel!CBrowserTab::_OnClose+0x170
36 000000a9`be01dae0 00007ffd`f063065b eModel!CTabWindow:::_TabWindowThreadProc+0x7a6
37 000000a9`be01fd40 00007ffe`1326856f eModel!CIETab_ThreadProc+0x2bb
38 000000a9`be01fe70 00007ffe`1b912d92 iertutil!IEGetTabWindowExports+0x2f
39 000000a9`be01fea0 00007ffe`1dcd9f64 kernel32!BaseThreadInitThunk+0x22
39a 000000a9`be01fed0 00000000`00000000 ntdll!RtlUserThreadStart+0x34

0:006> .cxr 000000a9`be01a600
rax=0000000000100002 rbx=0000000000000009 rcx=0000000000000000
rdx=000000a9be2d1300 rsi=000000a9be01ade0 rdi=0000000000000000
rip=00007ffdf98e8f69 rsp=000000a9be01ad00 rbp=000000a9be2d1190
r8=000000a9be2d1190 r9=000000a9be01ade0 r10=00007fffdf98e5c30
r11=0000000000000100 r12=00007ffdfb1b47382 r13=000000a9c01fc358
r14=000000a9be2d1300 r15=000000a9be01b5a0
iopl=0 nv up ei pl zr na po nc
cs=0033 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010246
edgehtml!CWebPlatformTridentHost::LoadNewWindowContent+0x35:
00007ffd`f98e8f69 488b07 mov rax,qword ptr [rdi] ds:00000000`00000000=????????????????
```