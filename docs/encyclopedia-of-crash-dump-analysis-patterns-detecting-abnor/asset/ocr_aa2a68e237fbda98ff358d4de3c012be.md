```
0:009> .exprt 1022f928

---- Exception record at 1022fa1c:
ExceptionAddress: 7c812afb (kernel32!RaiseException+0x00000053)
  ExceptionCode: e06d7363 (C++ EH exception)
ExceptionFlags: 00000001
NumberParameters: 3
  Parameter[0]: 19930520
  Parameter[1]: 1022fda4
  Parameter[2]: 0b985074
pExceptionObject: 1022fda4
_s_ThrowInfo : 0b985074

---- Context record at 1022fa3c:
eax=1022fd0c ebx=00000001 ecx=00000000 edx=1022fda4 esi=1022fd94 edi=77606068
eip=7c812afb esp=1022fdf0 ebp=1022fd5c iopl=0 nv up ei pl nz na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00000206
kernel32!RaiseException+0x53:
7c812afb 5e pop esi
```

# Comments

We can use Raymond Chen’s technique to find out more about the type of C++ exception 70.

This pattern example is taken from Software Diagnostics Services case study 71.

70 http://blogs.msdn.com/b/oldnewthing/archive/2010/07/30/10044061.aspx

71 http://www.patterndiagnostics.com/case-study