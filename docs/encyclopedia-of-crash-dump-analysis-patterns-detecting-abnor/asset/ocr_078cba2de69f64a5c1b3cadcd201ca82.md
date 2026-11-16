```
0: kd> .sympath+ c:\sym\ModuleA.pdb\C14E734A367F4DD0974DFA47C1194F281
Symbol search path is: SRV*c:\mss*http://msdl.microsoft.com/download/symbols;
c:\sym\ModuleA.pdb\C14E734A367F4DD0974DFA47C1194F281
[...]

0: kd> .reload
Loading Kernel Symbols
Loading User Symbols
Loading unloaded module list

0: kd> kL
*** Stack trace for last set context - .thread/.cxr resets it
ChildEBP RetAddr
ba38fcb8 80503836 nt!KiSwapContext+0x2f
ba38fcc4 804fb068 nt!KiSwapThread+0x8a
ba38fcec 805c0750 nt!KeWaitForSingleObject+0x1c2
ba38fd50 8054161c nt!NtWaitForSingleObject+0x9a
ba38fd50 7c90e4f4 nt!KiFastCallEntry+0xfc
0006f648 7c90df3c ntdll!KiFastSystemCallRet
0006f64c 7c91b22b ntdll!NtWaitForSingleObject+0xc
0006fd4 7c901046 ntdll!RtlpWaitForCriticalSection+0x132
0006f6dc 01373d7f ntdll!RtlEnterCriticalSection+0x46
0006f64e 0132b22e ModuleA!CSLock+0x7
0006f7a4 0132b785 ModuleA!SignalEvent+0x5e
[...]

0006f848 7e418734 ModuleA!WindowProc+0x136
0006f874 7e418816 USER32!InternalCallWinProc+0x28
0006f8dc 7e4189cd USER32!UserCallWinProcCheckWow+0x150
0006f93c 7e418a10 USER32!DispatchMessageWorker+0x306
0006f94c 0084367e USER32!DispatchMessageW+0xf
[...]
```