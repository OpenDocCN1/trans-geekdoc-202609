
## 字符串提示

此模式涵盖看起来可疑的 ASCII 和 UNICODE 字符串痕迹，例如网站、密码和 HTTP 表单，或根据模块或其容器进程的目的，直觉上不应该出现的奇怪名称（示例取自 Victimware 演示案例研究 205）：

```
0:005> s-sa 00040000 L1d000
0004004d  "!This program cannot be run in D"
0004006d "OS mode."
00040081 "3y@"
000400b8 "Rich"
000401d0 ".text"
000401f7 ".rdata"
0004021f ".data"
00040248 ".reloc"
[...]
00540018 "GET /stat?uptime=%d&downlink=%d&"
00540038 "uplink=%d&id=%s&statpass=%s&comm"
00540058 "ent-%s HTTP/1.0"
005400d8 "ftp://%s:%s@%s:%d"
005400fc "Accept-Encoding:"
00054118 "Accept-Encoding:"
00054130 "0123456789ABCDEF"
00054144 ": /"
00054160 "POST %s HTTP/1.0"
00054172 "Host: %s"
0005417c "User-Agent: %s"
0005418c "Accept: text/html"
0005419f "Connection: Close"
000541b2 "Content-Type: application/x-www"
000541d2 "form-urlencoded"
000541e3 "Content-Length: %d"
000541fc "id="
00054208 "POST %s HTTP/1.1"
0005421a "Host: %s"
00054224 "User-Agent: %s"
00054234 "Accept: text/html"
00054247 "Connection: Close"
0005425a "Content-Type: application/x-www"
0005427a "form-urlencoded"
0005428b "Content-Length: %d"
000542a4 "id=%s&base="
000542b8 "id=%s&bw=%d&type=%d&data="
000542d8 "POST %s HTTP/1.1"
000542ea "Host: %s"
000542f4 "User-Agent: %s"
00054304 "Accept: text/html"
00054317 "Connection: Close"
0005432a "Content-Type: application/x-www"
0005434a "form-urlencoded"
0005435b "Content-Length: %d"
00054378 "id=%s&os=%s&plist="
00054390 "POST %s HTTP/1.1"
000543a2 "Host: %s"
000543ac "User-Agent: %s"
000543bc "Accept: text/html"
000543cf "Connection: Close"
000543e2 "Content-Type: application/x-www-"
00054402 "form-urlencoded"
00054413 "Content-Length: %d"
00054430 "id=%s&data=%s"
00054440 "POST %s HTTP/1.1"
00054452 "Host: %s"
0005445c "User-Agent: %s"
0005446c "Accept: text/html"
0005447f "Connection: Close"
00054492 "Content-Type: application/x-www-"
000544b2 "form-urlencoded"
000544c3 "Content-Length: %d"
000544e0 "GET %s HTTP/1.0"
000544f1 "Host: %s"
000544fb "User-Agent: %s"
0005450b "Connection: close"
00054528 "POST /get/src.html HTTP/1.0"
00054545 "Host: %s"
0005454f "User-Agent: %s"
0005455f "Connection: close"
00054572 "Content-Length: %d"
00054586 "Content-Type: multipart/form-dat"
000545a6 "a; boundary=------------"
000545c6 "--------------%d"
000545d4 "--%d"
000545f8 "%sContent-Disposition: form-data"
00054618 "; name="id""
00054630 "%sContent-Disposition: form-data"
00054650 "; name="screen"; filename="%d""
00054670 "Content-Type: application/octet-"
00054690 "stream"
000546ac "%s failed with error %d: %s"
000546d8 "BlackwoodPRO"
000546e8 "FinamDirect"
000546f4 "GrayBox"
0005470c "MbtPRO"
00054704 "Laser"
0005470c "LightSpeed"
00054718 "LTGroup"
00054720 "Mbt"
00054724 "ScotTrader"
00054730 "SaxoTrader"
00054740 "Program: %s"
0005474f "Username: %s"
0005475e "Password: %s"
0005476d "AccountNO: %s"
[...]
```

## 字符串参数

当在函数调用栈中发现时，此分析模式常常很有用。简单情况是当函数参数是指向 ASCII 或 Unicode 字符串的指针时（**da** 和 **du** WinDbg 命令）。更有趣的情况是当我们有一个函数，它接受指向带有字符串字段的结构体的指针时（**dpa** 和 **dpu** 命令），例如：

```
0:018> kv 100
ChildEBP RetAddr  Args to Child
00de8c7c 7739bf53 7739610a 07750056 00000000 ntdll!KiFastSystemCallRet
00de8cb4 7738965e 00080126 07750056 00000001 user32!NtUserWaitMessage+0xc
00de8cdc 7739f762 77380000 0012b238 07750056 user32!InternalDialogBox+0xd0
00de8f9c 7739f047 00de90f8 00000000 ffffffff user32!SoftModalMessageBox+0x94b
00de90ec 7739eec9 00de90f8 00000028 07750056 user32!MessageBoxWorker+0x2ba
00de9144 773d7d0d 07750056 0015cd68 00132a60 user32!MessageBoxTimeoutW+0x7a
00de9178 773c42c8 07750056 00de923f 00de91ec user32!MessageBoxTimeoutA+0x9c
00de9198 773cc424 07750056 00de923f 00de91ec user32!MessageBoxExA+0x1b
00de91b4 6dfcf8c2 07750056 00de923f 00de91ec user32!MessageBoxA+0x45
00de99f0 6dfcfad2 00de9285 00de9a1c 77bc6cd5 compstui!FilterException+0x174
00dead94 7739b6e3 0038010e 00000100 ntdll!RtlUnicodeStringToAnsiString+0xf3
00deada4 7739b6e3 0038010e 00000100 compstui!CPSUIPageDlgProc+0xf3
00deadc0 7739f582 6dfcf9df 0038010e 00000110 user32!InternalCallWinProc+0x28
00deea3c 77395e22 0015d384 6dfcf9df 0038010e user32!UserCallDlgProcCheckWow+0x147
00deae84 7738aa44 00000000 00000110 00000000 user32!DefDlgProcWorker+0xa8
00deeab4 77388c01 004673d0 00461130 00000000 user32!SendMessageWorker+0x43e
00deaf6c 77387910 6dfcf000 004673d0 00000404 user32!InternalCreateDialog+0x9cf
00deaf90 7739fb5b 6dfcf000 001621d0 07750056 user32!CreateDialogIndirectParamAorW+0x33
00deafb0 774279a5 6dfcf000 001621d0 07750056 user32!CreateDialogIndirectParamW+0x1b
00deb000 77427abc 02192c78 000ddd08 07750056 comctl32!_CreatePageDlg+0x79
00deb028 77429d12 02192c78 6dff5c30 07750056 comctl32!_CreatePage+0xb1
00deb244 77428bb6 02192c78 00000001 00290110 comctl32!PageChange+0xcc
00deb604 7742c446 07750056 02192c78 00deb6ec comctl32!InitPropSheetDlg+0xbb8
00deb674 7739b6e3 07750056 00000110 00290110 comctl32!PropSheetDlgProc+0x4cb
00deb6a0 77395f82 7742bf7b 07750056 00000110 user32!InternalCallWinProc+0x28
00deb71c 77395e22 0008c33c 7742bf7b 07750056 user32!UserCallDlgProcCheckWow+0x147
00deb764 7738aa44 00000000 00000110 00290110 user32!DefDlgProcWorker+0xa8
00deb794 77388c01 004652e0 00461130 00290110 user32!SendMessageWorker+0x43e
00deb84c 77387910 77420000 004652e0 00000100 user32!InternalCreateDialog+0x9cf
00deb870 7739fb5b 77420000 02184be8 00000000 user32!CreateDialogIndirectParamAorW+0x33
00deb890 774ab1c5 77420000 02184be8 00000000 user32!CreateDialogIndirectParamW+0x1b
00deb8d8 7742ca78 77420000 02184be8 00000000 comctl32!SHFusionCreateDialogIndirectParam+0x36
00deb93c 7742ccea 00000000 00000a00 00000000 comctl32!_RealPropertySheet+0x242
00deb954 7742cd05 00deb9b4 00000000 00deb99c comctl32!_PropertySheet+0x146
00deb964 6dfd1178 00deb9b4 000000a0 00deba30 comctl32!PropertySheetW+0xf
00deb99c 6ffcf49b 00deb9b4 0256b3f8 0013bf08 compstui!PropertySheetW+0x4b
00deba14 6dfd0718 00000000 0013da4 00debae8 compstui!DoComPropSheet+0x2ef
00deba44 6dfd0799 00000000 7307c8da 00debad0 compstui!DoCommonPropertySheetUI+0xe9
00deba5c 730801c5 00000000 7307c8da 00debad0 compstui!CommonPropertySheetUIW+0x17
00debaa4 73080f5d 00000000 7307c8da 00debad0 winspool!CallCommonPropertySheetUI+0x43
00debace 4f49cdfe 00000000 0218bd84 02277fe8 winspool!PrinterPropertiesNative+0x10c
WARNING: Stack unwind information not available. Following frames may be wrong.
00debfc2 4f495a55 00deea08 00000002 02277fe8 PrintDriver!DllGetClassObject+0x0db7e
00deee18 4f4904fb 00ca6ee0 00000003 00000001 PrintDriverA!DllGetClassObject+0x5e25
00deee30 18f60282 02277fe8 00ca6ee0 00000003 PrintDriverA!DllGetClassObject+0x127b
00deee58 18f5abce 001042e4 00ca6ee0 00000003 pssui!HComOEMPrinterEvent+0x33
00deee9c 7308218c 00ca6ee0 00000003 00000001 pssui!DrvPrinterEvent+0x22e
00deeea8 761543c8 00ca6ee0 00000003 00000001 winspool!SpoolerPrinterEventNative+0x57
00deeeef04 761560d2 00ca6ee0 00000003 00000001 localspl!SplDriverEvent+0x21
00deeef28 761447f9 00cb2160 00000003 00000000 localspl!PrinterDriverEvent+0x46
00deeef3f0 76144b12 00000000 00000000 00d12020 localspl!SplAddPrinter+0x5f3
00deef41c 74070193 00000000 00000002 00d12020 localspl!LocalAddPrinterEx+0x2e
00deef6c 7407025c 00000000 00000000 00d12020 spoolss!AddPrinterExW+0x151
00deef88 01007a93 00000000 00000000 00d12020 spoolss!AddPrinterW+0x17
00deefa4 01006772 00000000 00ce74b0 021b6278 spoolss!YAddPrinter+0x75
00deef8c 77c80355 00000000 00ce74b0 021b6278 spoolsv!RpcAddPrinter+0x37
00deef80 77ce43e1 0100673b 00defae0 00000005 rpcrt4!Invoke+0x30
00defcf8 77ce45c4 00000000 00000000 0000e584 rpcrt4!NdrStubCall2+0x299
00defd14 77c8013a 000e5884 000e63d8 0000e584 rpcrt4!NdrServerCall2+0x19
00defd48 77c805ef 01002c57 000e5884 000defdec rpcrt4!DispatchToStubInCNoAvrf+0x38
00defd9c 77c80515 00000005 00000000 0100d228 rpcrt4!RPC_INTERFACE::DispatchToStubWorker+0x11f
00defdc0 77c8139e 000e5884 00000000 0100d228 rpcrt4!RPC_INTERFACE::DispatchToStub+0xa3
00defdfc 77c814b2 000e1c48 000d5b58 02154180 rpcrt4!LRPC_SCALL::DealWithRequestMessage+0x42c
00defe20 77c88848 000d85f0 000def38 000ec148 rpcrt4!LRPC_ADDRESS::DealWithLRPCRequest+0x127
00deff84 77c88962 00deffac 77c888fd 0000d5b8 rpcrt4!LRPC_ADDRESS::ReceiveLotsaCalls+0x430
00deff8c 77c888fd 000d85f8 00000000 00000000 rpcrt4!RecvLotsaCallsWrapper+0xd
00deffac 77c7b293 000b8038 00deffec 77e6482f rpcrt4!BaseCachedThreadRoutine+0x9d
00defff8 77e6482f 000bdba8 00000000 00000000 rpcrt4!ThreadStartRoutine+0x1b
00deffec 00000000 77c7b278 000bdaa8 00000000 kernel32!BaseThreadStart+0x34
```

```
0:018> da 00de923f
00de923f "Function address 0x77481456 caus"
00de925f "ed a protection fault. (exceptio"
00de927f "n code 0xc0000005).The applicati"
00de929f "on property sheet page(s) may no"
00de92bf "t function properly."
```

```
0:018> dp 00d12020
00d12020 00000000
00d12024 021b6088 "Printer A User B Server C"
00d12028 00000000
00d1202c 021b6124 "Remote Printer Address for User C"
00d12030 021b6190 "Printer Name and Family"
00d12034 021b61c4 "Printer Client Name"
00d12038 021b6228 "Printer Location"
00d1203c 00000000
00d12040 00000000
00d12044 021b6264 "Printer Module Name"
00d12048 00000000
00d1204c 00000000
00d12050 021b628c
00d12054 00008841
00d12058 00000000
00d1205c 00000000
00d12060 00000000
00d12064 00000000
[...]
```
