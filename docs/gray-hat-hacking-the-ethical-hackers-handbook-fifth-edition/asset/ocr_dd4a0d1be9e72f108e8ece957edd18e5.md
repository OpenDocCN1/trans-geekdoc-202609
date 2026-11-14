# MSHTML!CTextArea::CreateElement+0x13:

```
Breakpoint 0 hit
eax=03018300 ebx=00000000 ecx=03170000 edx=011868ca esi=03b3bdc4 edi=6dde62e0
eip=6dde62f3 esp=03b3bdb0 ebp=03b3bdb0 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
MSHTML!CTextArea::CreateElement+0x13:
6dde62f3 85c0            test    eax,eax
```

At this point, inside EAX is the memory address 0x03018300, which is the textarea
object just after creation. At this point we want to enable breakpoint 2 for
MSHTML!CTxtPtr::InsertRange so that we can track the copying of the a’s from an
allocation associated with the textarea element. After enabling this breakpoint with be 2,
we press F5 twice to hit breakpoint 2 a second time. Once we hit the breakpoint, we hold
down F8 to single-step until we reach the call to memcpy, as shown here:

```
0:007> be 2
0:007> g
Breakpoint 2 hit
eax=00000001 ebx=00000039 ecx=03b3bd84 edx=fdef0000 esi=030a80f0 edi=00000001
eip=6d93bef0 esp=03b3bd44 ebp=03b3be04 iopl=0         nv up ei ng nz na pe cy
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000287
MSHTML!CTxtPtr::InsertRange:
6d93bef0 8bff            mov     edi,edi
0:007> g
Breakpoint 2 hit
eax=00000269 ebx=00000039 ecx=03b3bd84 edx=00000265 esi=030a80f0 edi=00000265
eip=6d93bef0 esp=03b3bd44 ebp=03b3be04 iopl=0         nv up ei pl nz na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000206
MSHTML!CTxtPtr::InsertRange:
6d93bef0 8bff            mov     edi,edi
```

# Truncated for space. F8 was held until reaching the next instruction:

```
0:007> t
eax=0050dafa ebx=03b3bd84 ecx=000004ca edx=00002000 esi=02fec0d0 edi=00000072
eip=6d93bf91 esp=03b3bd00 ebp=03b3bd40 iopl=0         nv up ei pl nz na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000206
MSHTML!CTxtPtr::InsertRange+0x9d:
6d93bf91 ff15d001a56e    call    dword ptr [MSHTML!_imp__memcpy_s
```

You can see we have reached the call from MSTHTML!CTxtPtr::InsertRange to
memcpy_s. The EAX register holds the address 0x0050dafa, which is the destination
address for where the a’s will be written. The following shows the memory at the address
before the completion of the memcpy_s function, followed by the gu command to step out
of the function, and then another dump: