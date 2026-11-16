Here we might need to do manual stack trace reconstruction⁶⁴ like shown in the following example:

```
0:002> ~2s
eax=00000070 ebx=0110fb94 ecx=00000010 edx=005725d8 esi=0110fe58 edi=00000d80
eip=7c82847c esp=0110efe0 ebp=0110eff0 iopl=0 nv up ei pl zr na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00000246
ntdll!KiFastSystemCallRet:
7c82847c c3 ret

0:002> kl
ChildEBP RetAddr
0110efdc 00000000 ntdll!KiFastSystemCallRet

0:002> !teb
TEB at 7ffdc000
ExceptionList: 0110f980
StackBase: 01110000
StackLimit: 0110d000
SubSystemTib: 00000000
FiberData: 00001e00
ArbitraryUserPointer: 00000000
Self: 7ffdc000
EnvironmentPointer: 00000000
ClientId: 00000d04 . 00000bd0
RpcHandle: 00000000
Tls Storage: 00000000
PEB Address: 7ffda000
LastErrorValue: 87
LastStatusValue: c000000d
Count Owned Locks: 0
HardErrorMode: 0

0:002> dps 0110d000 01110000
0110d000 00000000
0110d004 00000000
[...]
0110f640 0110f64c
0110f644 02b91ea8
0110f648 00001000
0110f64c 00000004
0110f650 0110f6f0
0110f654 0374669d DbgHelp!WriteFullMemory+0x3cd
0110f658 fffffffd
0110f65c 0110fdd0
0110f660 00000000
[...]
```

⁶⁴ Manual Stack Trace Reconstruction, Memory Dump Analysis Anthology, Volume 1, page 157