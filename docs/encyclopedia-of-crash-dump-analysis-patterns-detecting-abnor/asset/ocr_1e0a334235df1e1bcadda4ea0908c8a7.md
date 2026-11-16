# CLR Thread

In cases where we don't see **Managed Code Exceptions** (page 617) or **Managed Stack Traces** (page 624) by default, we need to identify **CLR Threads** in order to try various SOS commands and start digging into a managed realm. These threads are easily distinguished by *mscorwks* module on their stack traces (don't forget to list full stack traces¹⁴):

```
0:000> ~*kl 100

 .  0  Id: 658.4ec Suspend: 1 Teb: 7ffdf000 Unfrozen
ChildEBP RetAddr
0007fc98 78c27d19 ntdll!KiFastSystemCallRet
0007fc9c 776e202c ntdll!NtWaitForMultipleObjects+0xc
0007fd44 7739bbd1 kernel32!WaitForMultipleObjectsEx+0x11a
0007fda0 6c296601 user32!RealMsgWaitForMultipleObjectsEx+0x141
0007fd0c 6c29684d buser!CoreSC::Wait+0x3a
0007fdf4 6c29693d duser!CoreSC::xwProcessNL+0xab
0007fe14 773b0c02 duser!MphProcessMessage+0x2e
0007fe5c 7c828556 user32!_ClientGetMessageMP+0x30
0007fe84 7739c811 ntdll!KiUserCallbackDispatcher+0x2e
0007fea4 7f072fd6 user32!NtUserGetMessage+0xc
0007fec0 010080ef mfc42u!CWinThread::PumpMessage+0x16
0007fef0 7f072dda mmclCAMApp::PumpMessage+0x37
0007fff08 7f044d5b mfc42u!CWinThread::Run+0x4a
0007fffc1 01034e19 mfc42u!AfxWinMain+0x7b
0007fffc0 776e2f3b mmcl!WinMainCRTStartup+0x19d
0007ffff 00000000 kernel32!BaseProcessStart+0x23

  1  Id: 658.82c Suspend: 1 Teb: 7ffde000 Unfrozen
ChildEBP RetAddr
003afea0 7c827d19 ntdll!KiFastSystemCallRet
003afea4 7c80e5bb ntdll!NtWaitForMultipleObjects+0xc
003aff48 7c80e4a2 ntdll!EtwWaitForMultipleObjectsEx+0xf7
003affb8 776e482f ntdll!EtwEventPump+0x27f
003affec 00000000 kernel32!BaseThreadStart+0x34

  2  Id: 658.648 Suspend: 1 Teb: 7ffdd000 Unfrozen
ChildEBP RetAddr
00f3fe18 7c827859 ntdll!KiFastSystemCallRet
00f3fe1c 77c885ac ntdll!NtReplyWaitReceivePortEx+0xc
00f3ff84 77c88792 rpcrt4!LRPC_ADDRESS::ReceiveLotsaCalls+0x198
00f3ff8c 77c8872d rpcrt4!RecvLotsaCallsWrapper+0xd
00f3ffac 77c7b110 rpcrt4!BaseCachedThreadRoutine+0x9d
00f3fffb8 776e482f rpcrt4!ThreadStartRoutine+0x1b
00f3ffec 00000000 kernel32!BaseThreadStart+0x34
```