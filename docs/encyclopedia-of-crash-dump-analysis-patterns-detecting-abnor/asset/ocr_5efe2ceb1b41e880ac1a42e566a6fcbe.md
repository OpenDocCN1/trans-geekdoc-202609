```
0:019> .ecxr
eax=15f237e5 ebx=15f235e9 ecx=15f237e1 edx=7e95b000 esi=15f237e1 edi=09724b10
eip=76f00fb2 esp=0c2df3ac ebp=0c2df3ac iopl=0 nv up ei pl nz na po nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010202
ntdll!RtlEnterCriticalSection+0x12:
76f00fb2 f00fba3000 lock btr dword ptr [eax],0 ds:002b:15f237e5=????????
```

So this **Hidden Stack Trace** is detected straightforwardly. But in other cases, such as when we have **Multiple Exceptions** (page 714) in a process dump or **Stack Trace Collection** (page 943) from a complete memory dump, we need to pay attention to such a possibility.