# Hidden Parameter

This pattern is a variant of **Execution Residue** (page 371) and **String Parameter** (page 962) where we have parameters left out from a stack trace due to register calling conventions and compiler optimizations. However, using raw stack analysis of a region around stack frames of interest we find what we are looking for. Here’s an example from an x64 system blocked thread waiting for data from a named pipe:

```
0: kd> kL
*** Stack trace for last set context - .thread/.cxr resets it
Child-SP          RetAddr           Call Site
fffffa60`2c3627d0 fffff800`018b90fa nt!KiSwapContext+0x7f
fffffa60`2c362910 fffff800`018add3b nt!KiSwapThread+0x13a
fffffa60`2c362980 fffff800`01b2121f nt!KeWaitForSingleObject+0x2cb
fffffa60`2c362a10 fffff800`01b319b6 nt!IopXxxControlFile+0xdeb
fffffa60`2c362b40 fffff800`018b68f3 nt!NtFsControlFile+0x56
fffffa60`2c362bb0 00000000`778d6eaa nt!KiSystemServiceCopyEnd+0x13
00000000`11f4da68 00000000`7776b76e ntdll!ZwFsControlFile+0xa
00000000`11f4da70 000007fe`ff94abc8 kernel32!WaitNamedPipeW+0x22f
00000000`11f4db60 000007fe`ff98a32d RPCRT4!NdrProxyForwardingFunction255+0x814d
00000000`11f4dc30 000007fe`ff9819b8 RPCRT4!OSF__CCONNECTION::TransOpen+0xccd
00000000`11f4dcc0 000007fe`ff988f5b RPCRT4!OSF_CCONNECTION::OpenConnectionAndBind+0x17b
00000000`11f4dd90 000007fe`ff988ec6 RPCRT4!OSF_CCALL::BindToServer+0xbb
00000000`11f4de40 000007fe`ff983368 RPCRT4!OSF_BINDING_HANDLE::InitCallWithAssociation+0xa5
00000000`11f4dea0 000007fe`ff983220 RPCRT4!OSF_BINDING_HANDLE::AllocateCCall+0x118
00000000`11f4dfd0 000007fe`ffaf1740 RPCRT4!OSF_BINDING_HANDLE::NegotiateTransferSyntax+0x30
00000000`11f4e020 000007fe`ffa1fecb RPCRT4!Ndr64pClientSetupTransferSyntax+0x200
00000000`11f4e080 000007fe`ffa20281 RPCRT4!NdrpClientCall3+0x6b
00000000`11f4e2d0 000007fe`fe087c8c RPCRT4!NdrClientCall3+0xddd
[...]
```

Even if we disassemble the return address of a caller of WaitNamedPipeW function we won’t easily find the passed first string parameter (named pipe name) unless we do a substantial reverse engineering and data flow analysis:

```
0: kd> ub 00007ffe`ff94abc8
RPCRT4!imp_load_getaddrinfo+0x7:
000007fe`ff94ab9f jmp     RPCRT4!tailMerge_WS2_32_dll (000007fe`ff94cef8)
000007fe`ff94aba4 call    qword ptr [RPCRT4!imp_GetLastError (000007fe`ffa2d528)]
000007fe`ff94abaa mov     r12d,eax
000007fe`ff94abad cmp     r12d,0E7h
000007fe`ff94abb4 jne     RPCRT4!NdrProxyForwardingFunction255+0x8193 (000007fe`ff99c8fb)
000007fe`ff94abba mov     edx,3E8h
000007fe`ff94abbf mov     rcx,rsi
000007fe`ff94abc2 call    qword ptr [RPCRT4!imp_WaitNamedPipeW (000007fe`ffa2d3f8)]
```