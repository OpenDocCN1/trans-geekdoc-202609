```
Allocate: p1
Allocate: p2
Allocate: p3
Free: p1
Free: p2
Double-Free: p2
Crash!
```

The crash dump shows the following Stack Trace (page 926):

```
0:000> r
eax=feefeee ebx=001b2040 ecx=001b0000 edx=001b2040 esi=d4476047 edi=001b2038
eip=76ee2086 esp=0012fe68 ebp=0012fe9c iopl=0 nv up ei ng nz na pe nc
cs=001b ss=0023 ds=0023 es=0023 fs=003b gs=0000 efl=00010286
ntdll!RtlpLowFragHeapFree+0x31:
76ee2086 8b4604 mov eax,dword ptr [esi+4] ds:0023:d447604b=????????
```