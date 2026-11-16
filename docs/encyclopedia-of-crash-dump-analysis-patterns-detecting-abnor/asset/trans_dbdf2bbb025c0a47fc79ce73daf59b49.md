

当我们使用 uf 命令反汇编函数体时，也能看到 OMAP 的作用：

```
kd> uf nt!IoCreateDevice
nt!IoCreateDevice+0x34d:
fffff800`0123907d or
fffff800`01239081 jmp nt!IoCreateDevice+0x351
...
...
...
nt!IoCreateDevice+0x14c:
fffff800`0126f320 mov r14w,200h
fffff800`0126f325 jmp nt!IoCreateDevice+0x158
nt!IoCreateDevice+0x3cc:
fffff800`01270bd0 lea rax,[rdi+50h]
fffff800`01270bd4 mov qword ptr [rax+8],rax
fffff800`01270bd8 mov word ptr [rax],rax
fffff800`01270bd1 jmp nt!IoCreateDevice+0x3d7
nt!IoCreateDevice+0xa4:
fffff800`01273eb9 mov r8d,1
fffff800`01273ebf lea rdx,[nt!`string']
fffff800`01273ec6 lea rcx,[rsp+0D8h]
fffff800`01273ece xadd dword ptr [nt!IopUniqueDeviceObjectNumber],r8d
fffff800`01273ed3 inc r8d
fffff800`01273ed9 call nt!swprintf
fffff800`01273ede test r13b,r13b
fffff800`01273ee1 jne nt!IoCreateDevice+0xcce
...
...
...
```

当我们尝试向后反汇编时，OMAP 优化的另一个示例：

```
ChildEBP RetAddr Args to Child
0006f87c 01034efb application!MultiUserLogonAttempt+0x5ba
0006fee4 01037120 application!LogonAttempt+0x406

1: kd> ub application!LogonAttempt+0x406
^ Unable to find valid previous instruction for 'ub application!LogonAttempt+0x406'

1: kd> u application!LogonAttempt+0x406
application!LogonAttempt+0x20b:
010348d5 add dword ptr [edx+10h],ebp
```

然后我们需要为 *多用户登录尝试* 指定返回地址：

```
1: kd> ub 01034efb
application!LogonAttempt+0x3e4:
01034ed9 mov     dword ptr [ebp-628h],ecx
01034edf mov     ecx,dword ptr [ebp-61Ch]
01034ee5 mov     dword ptr [eax+24h],ecx
01034ee8 push    dword ptr [ebp-61Ch]
01034eee lea     eax,[ebp-638h]
01034ef4 push    eax
01034ef5 push    ebx
01034ef6 call    application!MultiUserLogonAttempt (0102c822)
```

```
1: kd> u 01034efb
application!LogonAttempt+0x406:
01034efb mov     ecx,dword ptr [ebp-628h]
01034f01 mov     dword ptr [ebp-608h],eax
01034f07 mov     eax,dword ptr [ebx+8]
01034f0a mov     dword ptr [eax+24h],ecx
01034f0d cmp     dword ptr [application!g_SessionId (010742dc)],0
01034f14 je      application!LogonAttempt+0x47e (01034f73)
01034f16 lea     eax,[ebx+1078h]
01034f1c push    eax
```

## 注释

另请参阅 Microsoft 关于调试性能优化代码的文章 160。

## 单线程进程

像记事本这样的单线程进程很少见。这类进程总是可疑的，尤其是当它是服务或属于复杂产品时。通常，这种情况发生在所有其他线程都已终止，而剩余线程处于某个等待链中阻塞时。例如，该进程有一个线程在向自身（同一进程）发出 ALPC 请求时被阻塞（阻塞队列模式，第 77 页）：

```
0: kd> !process ffffffa8013ed9b30 3f
PROCESS ffffffa8013ed9b30
    SessionId: 0  Cid: 44b4    Peb: 7fffffdd8000  ParentCid: 0114
    DirBase: 2da448000  ObjectTable: ffffffa801948c670  HandleCount: 660.
    Image: ServiceA.exe
    VadRoot ffffffa801356dd10 Vads 398 Clone 0 Private 5795. Modified 204253. Locked 0.
    DeviceMap ffffff8a000008340
    Token                             fffff8a01b546060
    ElapsedTime                       01:32:37.622
    UserTime                          00:00:01.421
    KernelTime                        00:00:01.578
    QuotaPoolUsage[PagedPool]         0
    QuotaPoolUsage[NonPagedPool]      0
    Working Set Sizes (now,min,max)   (1525, 50, 345) (6100KB, 200KB, 1380KB)
    PeakWorkingSetSize                7607
    VirtualSize                       178 Mb
    PeakVirtualSize                   182 Mb
    PageFaultCount                    752709
    MemoryPriority                    BACKGROUND
    BasePriority                      8
    CommitCharge                      8043

    THREAD ffffffa8012caab50  Cid 44b4.4f70  Teb: 000007fffffa5a000 Win32Thread: 0000000000000000 WAIT: (WrLpcReply) KernelMode Non-Alertable
        ffffffa8012caaf18  Semaphore Limit 0x1
    Waiting for reply to ALPC Message fffff8a0194d4780 : queued at port ffffffa8012911c80 : owned by process ffffffa8013ed9b30
    IRP List:
        fffffa8013923300: (0006,0118) Flags: 00060000 Mdl: 00000000
    Not impersonating
    DeviceMap                 fffff8a000008340
    Owning Process            ffffffa8013ed9b30       Image:         ServiceA.exe
    Attached Process          N/A                     Image:         N/A
    Wait Start TickCount      139828         Ticks: 347372 (0:01:30:27.687)
    Context Switch Count      7380
    UserTime                  00:00:00.031
    KernelTime                00:00:04.890
    Win32 Start Address ServiceA (0x00000001401156e0)
    Stack Init fffff880014c9dd0 Current fffff880014c96b0
    Base fffff880014c9e000 Limit fffff880014c98000 Call 0
    Priority 8 BasePriority 8 UnusualBoost 0 ForegroundBoost 0 IoPriority 2 PagePriority 5
    Child-SP          RetAddr           Call Site
```

| Child-SP | RetAddr | Call Site |
|----------|---------|-----------|
| fffff880`14c9c6f0 | fffff800`01873652 | nt!KiSwapContext+0x7a |
| fffff880`14c9c830 | fffff800`01884a9f | nt!KiCommitThreadWait+0x1d2 |
| fffff880`14c9c8c0 | fffff800`0189f04f | nt!KeWaitForSingleObject+0x19f |
| fffff880`14c9c960 | fffff800`01b919f6 | nt!AlpcpSignalAndWait+0x8f |
| fffff880`14c9ca10 | fffff800`01b910f0 | nt!AlpcpReceiveSynchronousReply+0x46 |
| fffff880`14c9ca70 | fffff800`01b9519d | nt!AlpcpProcessSynchronousRequest+0x33d |
| fffff880`14c9cbb0 | fffff800`01b95276 | nt!LpcpRequestWaitReplyPort+0x9c |
| fffff880`14c9cc10 | fffff800`0187ced3 | nt!NtRequestWaitReplyPort+0x76 |
| fffff880`14c9cc60 | fffff800`01879490 | nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`14c9cc60) |
| fffff880`14c9cdf8 | fffff880`05c31050 | nt!KiServiceLinkage |
| fffff880`14c9ce70 | fffff880`045ce005 | ModuleA+0x12468 |
| ... | ... | ... |
| fffff880`14c9da10 | fffff800`01b9d3b6 | nt!IopXxxControlFile+0x607 |
| fffff880`14c9db40 | fffff800`0187ced3 | nt!NtDeviceIoControlFile+0x56 |
| fffff880`14c9dbd0 | 00000000`76d8138a | nt!KiSystemServiceCopyEnd+0x13 (TrapFrame @ fffff880`00000000`082af028) |
| 00000000`082af028 | 0000007fe`fd366cf6 | ntdll!NtDeviceIoControlFile+0xa |
| 00000000`082af030 | 00000000`76c2683f | KERNELBASE!TlsGetValue+0x1a36 |
| 00000000`082af0a0 | 00000001`4019d38c | kernel32!DeviceIoControlImplementation+0x7f |
| ... | ... | ... |

## 优化代码

在 **优化代码** 的情况下，我们不应信任像 WinDbg 这样的崩溃转储分析工具。我们建议，如果发现工具出现任何可疑或奇怪的行为，始终怀疑编译器生成的代码已被优化。让我们考虑这个堆栈跟踪片段：

| 参数1 | 参数2 | 参数3 | 调用站点 |
|-------|-------|-------|----------|
| 77e44c24 | 000001ac | 00000000 | ntdll!KiFastSystemCallRet |
| 000001ac | 00000000 | 00000000 | ntdll!NtFsControlFile+0xc |
| 00000034 | 00000bb8 | 0013e3f4 | kernel32!WaitNamedPipeW+0x2c3 |
| 0016fc60 | 00000000 | 67c14804 | MyModule!PipeCreate+0x48 |

来自 MyModule 的第三方函数 PipeCreate 打开一个命名管道，其第一个参数 (0016fc60) 指向管道名 L"\\pipe\\MyPipe"。在源代码中，它调用 Win32 API 函数 WaitNamedPipeW 等待管道可用于连接，并传递相同的管道名。但是我们看到传递给 WaitNamedPipeW 的第一个参数是 00000034，这不可能是指向有效 Unicode 字符串的指针。如果 00000034 是一个指针值，程序本应崩溃。

如果我们查看 WaitNamedPipeW 的反汇编，一切都变得清晰：

```
0:000> uf kernel32!WaitNamedPipeW
mov	edi,edi
push	ebp
mov	ebp,esp
sub	esp,50h
push	dword ptr [ebp+8] ; Use pipe name
lea	eax,[ebp-18h]
push eax
call	dword ptr [kernel32!_imp__RtlCreateUnicodeString (77e411c8)]
...
...
...
call	dword ptr [kernel32!_imp__NtOpenFile (77e41014)]
cmp	dword ptr [ebp-4],edi
mov	esi,eax
jne	kernel32!WaitNamedPipeW+0x1d5 (77e93316)
cmp	esi,edi
jl	kernel32!WaitNamedPipeW+0x1ef (77e93331)
movzx	eax,word ptr [ebp-10h]
mov	ecx,dword ptr fs:[18h]
add	eax,0Eh
push eax
push	dword ptr [kernel32!BaseDllTag (77ecd14c)]
mov	dword ptr [ebp+8],eax ; reuse parameter slot
```

众所周知，[ebp+8] 是非 FPO 调用的第一个函数参数，我们看到它被重复使用，因为在将 LPWSTR 转换为 UNICODE_STRING 并调用 NtOpenFile 获取句柄后，我们不再需要参数槽，编译器可以重用它来存储其他信息。

