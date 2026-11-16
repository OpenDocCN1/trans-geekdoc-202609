

为了确认这一猜测，我们可以编写调用 CreateThread 函数的代码，示例如下：

```
typedef DWORD (WINAPI *THREADPROC)(PVOID);

DWORD WINAPI ThreadProc(PVOID pvParam)
{
    // Does some work
    return 0;
}

void foo()
{
    //...
    THREADPROC thProc = ThreadProc;
    //...
    // thProc becomes NULL because of a bug
    //...
    HANDLE Thread = CreateThread(NULL, 0, thProc, 0, 0, NULL);
    CloseHandle(hThread);
}
```

## 数据

这是更通用的“无效指针”模式（第 589 页）的一个特殊版本，类似于“空代码指针”（第 750 页）。有效地址低于 0xFFFF，通常是一个值为 0 且带有小偏移量的寄存器，例如：

```
0: kd> r
Last set context:
eax=8923b008 ebx=00000000 ecx=00000000 edx=8923b008 esi=891312d0 edi=89f0b300
eip=8081c7c4 esp=f1b5d744 ebp=f1b5d744 iopl=0 nv up ei ng nz ac pe nc
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00010296
nt!IopIoOperationSynchronous+0x2e:
8081c7c4 f6412c02 test byte ptr [ecx+2Ch],2 ds:0023:0000002c=?
```

这里，在向后反汇编该函数后，我们可以看到从 [EBP+8] 开始的一系列取消引用操作，这意味着一个指向结构体（此处为 IRP）的指针被传递给了该函数，并且该结构体中包含一个指向另一个结构体的数据指针，而后者又包含一个 NULL 指针：

```
0: kd> ub 8081c7c4
nt!IopIoOperationSynchronous:
8081c7b6 8bff mov edi,edi
8081c7b8 55 push ebp
8081c7b9 8bec mov ebp,esp
8081c7bb 8b4508 mov eax,dword ptr [ebp+8]
8081c7be 8b4860 mov ecx,dword ptr [eax+60h]
8081c7c1 8b4918 mov ecx,dword ptr [ecx+18h]
```

## 注释

x64 示例，同时展示 x64 上下文中的 .cxr 命令：

```
0:006> k
# Child-SP RetAddr Call Site
00 000000a9`be019378 00007ffe`1b1198f8 ntdll!NtWaitForMultipleObjects+0xa
01 000000a9`be019380 00007ffe`1b11908e KERNELBASE!WaitForMultipleObjectsEx+0xef
02 000000a9`be019680 00007ffe`1b92155c KERNELBASE!WaitForMultipleObjects+0xe
03 000000a9`be0196c0 00007ffe`1b921088 kernel32!BasepReportFault+0x54c
04 000000a9`be019c30 00007ffe`1b1403cd kernel32!BasepReportFault+0x78
05 000000a9`be019c60 00007ffe`1dd8df6f KERNELBASE!UnhandledExceptionFilter+0x1fd
06 000000a9`be019d60 00007ffe`1dd65680 ntdll!LdrpLogFatalUserCallbackException+0x56
07 000000a9`be019e90 00007ffe`1dd6666d ntdll!KiUserCallbackDispatcherHandler+0x20
08 000000a9`be019ed0 00007ffe`1dde3c00 ntdll!RtlpExecuteHandlerForException+0xd
09 000000a9`be019f00 00007ffe`1dd6577a ntdll!RtlDispatchException+0x370
0a 000000a9`be01a600 00007ffd`f98e8f69 ntdll!KiUserExceptionDispatch+0x3a
0b 000000a9`be01ad00 00007ffd`f985c944 edgehtml!CWebPlatformTridentHost::LoadNewWindowContent+0x35
0c 000000a9`be01ad90 00007ffe`1b84b0b3 edgehtml!CWebPlatform::LoadNewWindowContent+0x64
0d 000000a9`be01ae10 00007ffe`1b80521e rpcrt4!Invoke+0x73
0e 000000a9`be01aea0 00007ffe`1b83aaba rpcrt4!NdrStubCall2+0x34e
0f 000000a9`be01b4f0 00007ffe`1d414b1b rpcrt4!NdrStubCall3+0xea
10 000000a9`be01b560 00007ffe`1d4c25b2 combase!CStdStubBuffer_Invoke+0x6b
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

```
0:006> kc
*** Stack trace for last set context - .thread/.cxr resets it
# Call Site
00 edgehtml!CWebPlatformTridentHost::LoadNewWindowContent
01 edgehtml!CWebPlatform::LoadNewWindowContent
02 rpcrt4!Invoke
03 rpcrt4!NdrStubCall2
04 rpcrt4!NdrStubCall3
05 combase!CStdStubBuffer_Invoke
06 combase!CoGetContextToken
07 combase!COCreateFreeThreadedMarshaler
08 combase!CoGetObjectContext
09 combase!CoGetObjectContext
0a combase!CoGetObjectContext
0b combase!CoGetObjectContext
0c user32!UserCallWinProcCheckWow
0d user32!DispatchMessageWorker
0e combase!CoGetObjectContext
0f combase!CoGetObjectContext
10 combase!CoCreateFreeThreadedMarshaler
11 combase!CoCreateFreeThreadedMarshaler
12 combase!CoCreateFreeThreadedMarshaler
13 combase!NdrOleDllGetClassObject
14 rpcrt4!NdrpClientCall3
15 combase!NdrOleDllGetClassObject
16 combase!ObjectStublessClient32
17 combase!CoWaitForMultipleHandles
18 combase!CoWaitForMultipleHandles
19 combase!CoCreateFreeThreadedMarshaler
1a combase!CoCreateFreeThreadedMarshaler
1b combase!CoCreateFreeThreadedMarshaler
1c combase!CStdStubBuffer2_QueryInterface
1d oleaut32!VariantClear
1e eModel!CIEFrameAuto::SetOwner
1f eModel!CBrowserTabBase::v_OnDestroy
20 eModel!CBrowserTab::v_OnDestroy
21 eModel!CBrowserTab:::_v_WndProc
22 eModel!CBrowserTab:::_s_WndProc
23 user32!UserCallWinProcCheckWow
24 user32!DispatchClientMessage
25 user32!fnDWORD
26 ntdll!KiUserCallbackDispatcherContinue
27 user32!NtUserDestroyWindow
28 eModel!CBrowserTab:::_DoFinalCleanup
29 eModel!CBrowserTab:::_OnConfirmedClose
2a eModel!CBrowserTab:::_OnClose
2b eModel!CTabWindow:::_TabWindowThreadProc
2c eModel!CIETab_ThreadProc
2d iertutil!IEGetTabWindowExports
2e kernel32!BaseThreadInitThunk
2f ntdll!RtlUserThreadStart
```

