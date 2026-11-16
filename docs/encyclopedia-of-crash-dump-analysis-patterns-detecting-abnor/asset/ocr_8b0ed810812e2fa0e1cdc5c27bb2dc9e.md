```
0184ffc0 00097df0
0184ffc4 00000000
0184ffc8 00000000
0184ffcc 00097df0
0184ffd0 8ad84818
0184ffd4 0184ffc4
0184ffd8 8980a700
0184ffdc ffffffff
0184ffe0 77e6b70d kernel32!_except_handler3
0184ffe4 77e66098 kernel32! string'+0x98
0184ffe8 00000000
0184ffec 00000000
0184fff0 00000000
77c5de6d RPCRT4!ThreadStartRoutine
0184fff8 00097df0
0184fffc 00000000
01850000 00000008
```

Next, we need to use custom `k` command and specify the base pointer. In our case, the last found stack address that links EBP pointers is 0184eef0:

```
0:011> k L=0184eef0
ChildEBP RetAddr
WARNING: Frame IP not in any known module. Following frames may be wrong.
0184eef0 7615dff2 0x184e5bf
0184efc0 7615f9d0 localspl!SplDriverEvent+0x21
0184fe30 76143a94 localspl!PrinterDriverEvent+0x46
0184f3f8 761482de localspl!SplAddPrinter+0x5f3
0184f424 74067c8f localspl!LocalAddPrinterEx+0x2e
0184f874 74067b76 SPOOLSS!AddPrinterExW+0x151
0184f890 01007e29 SPOOLSS!AddPrinterW+0x17
0184f8ac 01006ec3 spoolsv!YAddPrinter+0x75
0184f8d0 77c70f3b spoolsv!RpcAddPrinter+0x37
0184f8f8 77ce23f7 RPCRT4!Invoke+0x30
0184fc48 77ce26ed RPCRT4!NdrStubCall2+0x299
0184fd14 77c709be RPCRT4!NdrServerCall2+0x19
0184fd48 77c709f3 RPCRT4!DispatchToStubInCNoAvrf+0x38
0184fd9c 77c70865 RPCRT4!RPC_INTERFACE::DispatchToStubWorker+0x117
0184fdfc 77c734b1 RPCRT4!RPC_INTERFACE::DispatchToStub+0xa3
0184fdfc 77c71bb3 RPCRT4!LRPC_SCALL::DealWithRequestMessage+0x42c
0184fe20 77c75458 RPCRT4!LRPC_ADDRESS::DealWithLRPCRequest+0x127
0184ff84 77c577f8 RPCRT4!LRPC_ADDRESS::ReceiveLotsaCalls+0x430
0184fff8 77c5f7dd RPCRT4!RecvLotsaCallsWrapper+0xd
```

Stack traces make more sense now, but we don’t see BaseThreadStart+0x34. By default, WinDbg displays only certain amount of function calls (stack frames), so we need to specify stack frame count, for example, 100: