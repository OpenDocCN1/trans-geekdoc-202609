PROCESS_NAME: App.exe

ERROR_CODE: (NTSTATUS) 0x6d9 - There are no more endpoints available from the endpoint mapper.

NTGLOBALFLAG: 0

APPLICATION_VERIFIER_FLAGS: 0

LAST_CONTROL_TRANSFER: from 000000007da4a631 to 000000007d4e2366

```
STACK_TEXT:
0012d98c 7da4a631 kernel32!RaiseException+0x53
0012d9a4 7da4a5f7 rpcrt4!RpcpRaiseException+0x24
0012d9b4 7dac0140 rpcrt4!NdrGetBuffer+0x46
0012dda0 5f2a2fba rpcrt4!NdrClientCall2+0x197
0012ddbc 5f29c6a6 hnetcfg!FwOpenDynamicFwPort+0x1d
0012de68 7db4291f hnetcfg!FwCOfOpenDynamicFwPort+0x6a
0012dff0 71c043db mswsock!WSPBind+0x2e3
WARNING: Frame IP not in any known module. Following frames may be wrong.
0012df24 76ed91c8 ws2_32+0x43db
0012df6c 76ed9128 rasapi32+0x491c8
0012df98 76ed997c rasapi32+0x49128
0012dfc0 76ed8ac2 rasapi32+0x4997c
0012fdf4 76ed89cd rasapi32+0x48ac2
0012fdff 76ed82e5 rasapi32+0x489cd
0012e010 76ed827f rasapi32+0x482e5
0012e044 76ed8bf0 rasapi32+0x4827f
0012e0c8 76ed844d rasapi32+0x48bf0
0012e170 76ed74b5 rasapi32+0x4844d
0012e200 76ed544f rasapi32+0x474b5
0012e22c 76ed944d rasapi32+0x4544f
0012e24c 76ed93a4 rasapi32+0x4944d
0012e298 76ed509f rasapi32+0x493a4
0012e2bc 7db442bf rasapi32+0x4509f
0012e2ec 7db4418b mswsock!SaBlob_Query+0x2d
0012e330 7db4407c mswsock!Rnr_DoNsLookup+0xf0
0012e5c8 71c06dc0 mswsock!Dns_NSLookupServiceNext+0x24b
0012e5e0 71c06da0 ws2_32+0x6dc0
0012e5fc 71c06d6a ws2_32+0x6da0
0012e628 71c06d08 ws2_32+0x6d6a
0012e648 71c08282 ws2_32+0x6d08
0012fef0 71c07f68 ws2_32+0x7f68
0012ef34 71c08433 ws2_32+0x8433
0012fea0 71c03236 ws2_32+0x3236
0012f094 71c03340 ws2_32+0x3340
0012f0bc 7dab22fb ws2_32+0x3340
0012f11c 7dab3a0e rpcrt4!IP_ADDRESS_RESOLVER::NextAddress+0x13e
0012f238 7dab3c11 rpcrt4!TCPRorHTTP_Open+0xdb
0012f270 7da44c85 rpcrt4!TCP_Open+0x55
0012f2b8 7da44b53 rpcrt4!OSF_SC_ONNECTION::TransOpen+0x5e
0012f31c 7da447d7 rpcrt4!OSF_CCONNECTION::OpenConnectionAndBind+0xbe
0012f360 7da44720 rpcrt4!OSF_SCALL::BindToServer+0x4fa
0012f378 7da3a9df rpcrt4!OSF_BINDING_HANDLE::InitCCallWithAssociation+0x63
0012f3f4 7da3a8dd rpcrt4!OSF_BINDING_HANDLE::AllocateCCall+0x49d
0012f428 7da37a1c rpcrt4!OSF_BINDING_HANDLE::NegotiateTransferSyntax+0x2e
```