
0013e248 7739bfce 0015fce4 7745b6e6 00010090 user32!UserCallWinProcCheckWow+0x151
0013e278 7739bf74 7745b6e6 00010090 0000000f user32!CallWindowProcAorW+0x98
0013e298 77431848 7745b6e6 00010090 0000000f user32!CallWindowProcW+0x1b
0013e2b4 77431b9b 00010090 0000000f 00000000 comctl32!CallOriginalWndProc+0x1a
0013e310 77431d5d 001c0f88 00010090 0000000f comctl32!CallNextSubclassProc+0x3c
0013e334 779cd761 00010090 0000000f 00000000 comctl32!DefSubclassProc+0x46
0013e350 77431b9b 00010090 0000000f 00000000 shdocvw!CNotifySubclassWndProc::_SubclassWndProc+0xa7
0013e3ac 77431d5d 001c0f88 00010090 0000000f comctl32!CallNextSubclassProc+0x3c
0013e3d0 779cd86f 00010090 0000000f 00000000 comctl32!DefSubclassProc+0x46
0013e41c 779cd7e4 00010090 0000000f 00000000 shdocvw!CNscTree::_SubClassTreeWndProc+0x3ae
0013e43c 77431d9b 00010090 0000000f 00000000 shdocvw!CNscTree::_SubClassTreeWndProc+0x34
0013e498 77431dc0 001c0f88 00010090 0000000f comctl32!CallNextSubclassProc+0x3c
0013e4ec 7739b6e3 00010090 0000000f 00000000 comctl32!MasterSubclassProc+0x54
0013e518 7739bb74 77431d6c 00010090 0000000f user32!InternalCallWinProc+0x28
0013e590 7739c8b8 0015fce4 77431d6c 00010090 user32!UserCallWinProcCheckWow+0x151
0013e5ec 7739c9c6 00617618 0000000f 00000000 user32!DispatchClientMessage+0xd9
0013e614 7ac28536 0013e62c 00000018 0013e750 user32!_fnDWORD+0x24
0013e640 7739cbb2 7739cb75 00010090 0000005e ntdll!KiUserCallbackDispatcher+0x2e
0013e654 77459d14 00010090 00000200 001c8900 user32!NtUserCallHwndLock+0xc
0013e66c 7745bd2d 00000004 016b0055 00000000 comctl32!TV_OnMouseMove+0x62
0013e6bc 7739b6e3 00010090 00000200 00000000 comctl32!TV_WndProc+0x647
0013e6e8 7739b874 7745b6e6 00010090 00000200 user32!InternalCallWinProc+0x28
0013e760 7739bfce 0015fce4 7745b6e6 00010090 user32!UserCallWinProcCheckWow+0x151
0013e790 7739bf74 7745b6e6 00010090 00000200 user32!CallWindowProcAorW+0x98
0013e7b0 77431848 7745b6e6 00010090 00000200 user32!CallWindowProcW+0x1b
0013e7cc 77431b9b 00010090 00000200 00000000 comctl32!CallOriginalWndProc+0x1a
0013e828 77431d5d 001c0f88 00010090 00000200 comctl32!CallNextSubclassProc+0x3c
0013e84c 779cd761 00010090 00000200 00000000 comctl32!DefSubclassProc+0x46
0013e868 77431b9b 00010090 00000200 00000000 shdocvw!CNotifySubclassWndProc::_SubclassWndProc+0xa7
0013e8c4 77431d5d 001c0f88 00010090 00000200 comctl32!CallNextSubclassProc+0x3c
0013e8e8 779cd6f 00010090 00000200 00000000 comctl32!DefSubclassProc+0x46
0013e934 779cd7e4 00010090 00000200 00000000 shdocvw!CNscTree::_SubClassTreeWndProc+0x3ae
0013e954 77431b9b 00010090 00000200 00000000 shdocvw!CNscTree::_SubClassTreeWndProc+0x34
0013e9b0 77431dc0 001c0f88 00010090 00000200 comctl32!CallNextSubclassProc+0x3c
0013ea04 7739b6e3 00010090 00000200 00000000 comctl32!MasterSubclassProc+0x54
0013ea30 7739b874 77431d6c 00010090 00000200 user32!InternalCallWinProc+0x28
0013eaa8 7739ba92 0015fce4 77431d6c 00010090 user32!UserCallWinProcCheckWow+0x151
0013eb10 7739bad0 0013eb50 00000000 0013eb38 user32!DispatchMessageWorker+0x327
0013eb20 75ed1410 0013eb50 00000000 00176388 user32!DispatchMessageW+0xf
0013eb38 75ed14fc 0013eb50 0013ee50 00000000 browseui!TimedDispatchMessage+0x33
0013ed98 75ec1c83 0015f7e8 0013ee50 0015f7e8 browseui!BrowserThreadProc+0x336
0013ee24 75ec61ef 0015f7e8 0015f7e8 00000000 browseui!BrowserProtectedThreadProc+0x44
0013fea8 779ba3a6 0015f7e8 00000001 00000000 browseui!SHOpenFolderWindow+0x22c
0013fec8 0040243d 00152552 0002d0f2 ffffffff shdocvw!IEWinMain+0x129
0013ff1c 00402744 00400000 00000000 00152552 iexplore!WinMain+0x316
0013fff0 77e6f23b 00000000 00000000 7ffde000 iexplore!WinMainCRTStartup+0x182
0013fff0 00000000 004025c2 00000000 78746341 kernel32!BaseProcessStart+0x23

1 Id: c068.d71c Suspend: 1 Teb: 7ffdc000 Unfrozen
ChildEBP RetAddr Args to Child
00d4fea0 7c827cfb 7c80e5bb 00000000 00d4fef0 ntdll!KiFastSystemCallRet
00d4fea4 7c80e5bb 00000002 00d4fe0 00000001 ntdll!NtWaitForMultipleObjects+0xc
00d4ff48 7c80e4a2 00000002 00d4ff70 00000000 ntdll!EtwpWaitForMultipleObjectsEx+0xf7
00d4ffb8 77e64829 00000000 00000000 00000000 ntdll!EtwpEventPump+0x27f
00d4ffec 00000000 7c80e1fa 00000000 00000000 kernel32!BaseThreadStart+0x34

2 Id: c068.cba4 Suspend: 1 Teb: 7ffdb000 Unfrozen
ChildEBP RetAddr Args to Child
012bfe18 7c82783b 77c885ac 000001c4 012bff74 ntdll!KiFastSystemCallRet
012bfe1c 77c885ac 000001c4 012bff74 00000000 ntdll!NtReplyWaitReceivePortEx+0xc
012bff84 77c88792 012bfac 77c8872d 00153cf0 rpcrt4!LRPC_ADDRESS::ReceiveLotsasCalls+0x198
012bff8c 77c8872d 00153cf0 00000000 00000000 rpcrt4!RecvLotsaCallsWrapper+0xd
012bffac 77c7b110 00167030 012bffec 77e64829 rpcrt4!BaseCachedThreadRoutine+0x9d
012bfff8 77e64829 00172088 00000000 00000000 rpcrt4!ThreadStartRoutine+0x1b
012bffe0 00000000 77c7b0f5 00172088 00000000 kernel32!BaseThreadStart+0x34

3 Id: c068.8604 Suspend: 1 Teb: 7ffda000 Unfrozen
ChildEBP RetAddr Args to Child
013bfe28 7c827d0b 7c83d236 000001d0 00000000 ntdll!KiFastSystemCallRet
013bfe2c 7c83d236 000001d0 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
013bfe68 7c83d281 000001d0 00000000 00000000 ntdll!RtlpWaitOnCriticalSection+0x1a3
013bfe88 7c839844 7c8877a0 00000000 77670000 ntdll!RtlEnterCriticalSection+0xa8
013bfff0 77e52860 77670000 77670000 00171698 ntdll!LdrUnloadDll+0x35
013bff4a 776b171d 77670000 00000000 00000000 kernel32!FreeLibraryAndExitThread+0x38
013bffb8 77e64829 00171698 00000000 00000000 ole32!CRpcThreadCache::RpcWorkerThreadEntry+0x39
013bffec 00000000 776b16e4 00171698 00000000 kernel32!BaseThreadStart+0x34

4 Id: c068.d6dc Suspend: 1 Teb: 7ffd9000 Unfrozen
ChildEBP RetAddr Args to Child
016dfd24 7c827cfb 77e6202c 00000005 016dfd74 ntdll!KiFastSystemCallRet
016dfd28 77e6202c 00000005 016dfd74 00000001 ntdll!NtWaitForMultipleObjects+0xc
016dfdd0 7739bbd1 00000005 016dfd8 00000000 kernel32!WaitForMultipleObjectsEx+0x11a
016dfe2c 7c919b2e 00000004 016dfa54 ffffffff user32!RealMsgWaitForMultipleObjectsEx+0x141
016dff50 7c8c7ada 77da3f12 00000000 00000000 shell32!CChangeNotify::_MessagePump+0x3b
016dfff54 77da3f12 00000000 00000000 00000000 shell32!CChangeNotify::ThreadProc+0x1e
016dff8 77e64829 00000000 00000000 00000000 shlwapi!WrapperThreadProc+0x94
016dffec 00000000 77da3ea5 0013dea8 00000000 kernel32!BaseThreadStart+0x34

5 Id: c068.caf4 Suspend: 1 Teb: 7ffd8000 Unfrozen
ChildEBP RetAddr Args to Child
01b1fd04 7c827cfb 77e6202c 00000002 01b1fe04 ntdll!KiFastSystemCallRet
01b1fd08 77e6202c 00000002 01b1fe04 00000001 ntdll!NtWaitForMultipleObjects+0xc
01b1fe60 7739bbd1 00000002 01b1fe88 00000000 kernel32!WaitForMultipleObjectsEx+0x11a
01b1febc 6c296601 00000001 01b1fe0 ffffffff user32!RealMsgWaitForMultipleObjectsEx+0x141
01b1fedc 6c29684b 000004ff ffffffff 00000001 duser!CoreSC::Wait+0x3a
01b1fedc 6c28f9e6 01b1ff50 00000000 00000000 duser!CoreSC::xwProcessNL+0xab
01b1fff30 6c28bc2e 01b1ff50 00000000 00000000 duser!GetMessageExA+0x44a
01b1ff84 77cbc530 00000000 00000000 00000000 duser!ResourceManager::SharedThreadProc+0xb6
01b1fff8 77e64829 000385f0 00000000 00000000 msvcrt!_endthreadex+0xa3
01b1fffec 00000000 77bcb4bc 000385f0 00000000 kernel32!BaseThreadStart+0x34

6 Id: c068.d624 Suspend: 1 Teb: 7ffd7000 Unfrozen
ChildEBP RetAddr  Args to Child
01c9ff9c 7c82d64b 7c83d424 00000001 01c9ffb0 ntdll!KiFastSystemCallRet
01c9ffa0 7c83d424 00000001 01c9ffb0 00000000 ntdll!NtDelayExecution+0xc
01c9ffb8 77e64829 00000000 00000000 00000000 ntdll!RtlpTimerThread+0x47
01c9ffec 00000000 7c83d3dd 00000000 00000000 kernel32!BaseThreadStart+0x34

7 Id: c068.b4e0 Suspend: 1 Teb: 7ffd6000 Unfrozen
ChildEBP RetAddr  Args to Child
01d9fd58 7c82d70b 7c83d236 000001d0 00000000 ntdll!KiFastSystemCallRet
01d9fd5c 7c83d236 000001d0 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
01d9fd98 7c83d281 000001d0 00000004 00000000 ntdll!RtlpWaitOnCriticalSection+0x1a3
01d9fd8b 7c839844 7c8877a0 75eb8b7c 75eb0000 ntdll!RtlEnterCriticalSection+0xa8
01d9fec0 77e6b1bb 75ebc000 75ebc000 001e2f98 ntdll!LdrUnloadDll+0x35
01d9fed4 77da4c1c 75eb0000 0020eec8 77da591b kernel32!FreeLibrary+0x41
01d9feec 7c83a827 0020eec8 7c8980c0 001e4ec0 shlwapi!ExecuteWorkItem+0x28
01d9ff44 7c83aa0b 77da591b 0020eec8 00000000 ntdll!RtlpWorkerCallout+0x71
01d9ff64 7c83aa82 00000000 0020eec8 001e4ec0 ntdll!RtlpExecuteWorkerRequest+0x4f
01d9ff78 7c839f60 7c83a9ca 00000000 0020eec8 ntdll!RtlpApcCallout+0x11
01d9ffb8 77e64829 00000000 00000000 00000000 ntdll!RtlpWorkerThread+0x61
01d9ffec 00000000 7c839feb 00000000 00000000 kernel32!BaseThreadStart+0x34

8 Id: c068.d5a8 Suspend: 1 Teb: 7ffd5000 Unfrozen
ChildEBP RetAddr  Args to Child
01fbb41c 7c827d0b 7c83d236 00000468 00000000 ntdll!KiFastSystemCallRet
01fbb420 7c83d236 00000468 00000000 00000000 ntdll!NtWaitForSingleObject+0xc
01fbb45c 7c83d281 00000468 00000004 00000000 ntdll!RtlpWaitOnCriticalSection+0x1a3
01fbb47c 7c9136c9 7cae42d0 001c97b0 80070003 ntdll!RtlEnterCriticalSection+0xa8
01fbb494 7c913b75 0000000c 00000000 00000001 shell32!CMountPoint::GetMountPoint+0x33
01fbb4c8 7c91358d 01fbb4fc 0000000c 00000000 shell32!CDrivesFolder:::_FillDDDrive+0x5c
01fbb52c 7c9109e7 0018e988 00000000 001c97b0 shell32!CDrivesFolder::ParseDisplayName+0x9f
01fbb594 7c9119ff 0018e9b0 00000000 001c97b0 shell32!CRegFolder::ParseDisplayName+0x93
01fbb5bc 7c910bb8 00000000 001a8e30 00000000 shell32!CDesktopFolder::_ChildParseDisplayName+0x22
01fbb60c 7c9109e7 0017cde0 00000000 001c97b0 shell32!CDesktopFolder::ParseDisplayName+0x7e
01fbb674 7c910a9b 0015f058 00000000 001c97b0 shell32!CRegFolder::ParseDisplayName+0x93
01fbb6ac 7c911ab4 00000000 00000000 00000000 shell32!SHParseDisplayName+0xa3
01fbb6d0 7c911a6e 01fbbe60 00000000 00000002 shell32!ILCreateFromPathEx+0x3d
01fbb6ec 7c911a4b 01fbbe60 01fbb700 00000000 shell32!SHILCreateFromPath+0x17
01fbb704 7c95e055 01fbbe60 00000104 01fbc0a0 shell32!ILCreateFromPathW+0x18
01fbbb84 7c9ef49d 01fbbe60 00000000 01fbbac shell32!SHGetFileInfo+0x117
01fbc06c 01b4d195 01fbc200 00000000 01fbc0a0 shell32!SHGetFileInfoA+0x6a
WARNING: Stack unwind information not available. Following frames may be wrong.
01fbc0a4 01b54a20 0000073c 02541f28 00000000 issftran!SSCopyFile+0x27ad
00000000 00000000 00000000 00000000 00000000 issftran!DllUnregisterServer+0x70ad

9 Id: c068.d750 Suspend: 1 Teb: 7ffd4000 Unfrozen
ChildEBP RetAddr  Args to Child
0228ff7c 7c8277db 71b25914 00000b44 0228ffc0 ntdll!KiFastSystemCallRet
0228ff80 71b25914 000004b4 0228ffc0 0228ffb4 ntdll!ZwRemoveIoCompletion+0xc
0228fff8 77e64829 71b259de 00000000 00000000 mswsock!SockAsyncThread+0x69
0228ffec 00000000 71b258ab 001fcd20 00000000 kernel32!BaseThreadStart+0x34

0:000> du 7c8d8828
7c8d8828 "EXPLORER.EXE"
