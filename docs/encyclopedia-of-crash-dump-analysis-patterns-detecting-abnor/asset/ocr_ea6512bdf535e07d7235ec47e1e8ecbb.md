# Handle Limit

# GDI

# Kernel Space

Among various memory leaks leading to **Insufficient Memory** pattern (page 523), there is so-called session pool leak briefly touched in the pattern about kernel pool leaks (page 535). It also involves GDI handles and structures allocated per user session that has the limit on how many of them can be created and this pattern should rather be called **Handle Limit**. Such leaks can result in poor visual application behavior after some time when drawing requests are not satisfied anymore. In severe cases, when the same bugs are present in a display driver, it can result in bugchecks like

> BugCheck AB: SESSION_HAS_VALID_POOL_ON_EXIT

or, if a handle allocation request was not satisfied, it may result in a NULL pointer stored somewhere with the subsequent **Invalid Pointer** access (page 589):

```
SYSTEM_THREAD_EXCEPTION_NOT_HANDLED (7e)

CONTEXT: b791e010 -- (.cxr 0xffffffffb791e010)
eax=00000000 ebx=bc43d004 ecx=a233add8 edx=00000000 esi=bc430fff edi=00000000
eip=bfed7380 esp=b791e3dc ebp=b791e480 iopl=0 nv up ei pl zr na pe nc
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00010246
DisplayDriver+0x3e380:
bfed7380 8a4702        mov     al,byte ptr [edi+2]     ds:0023:00000002=?
```

We can write three Win32 applications in Visual C++ that simulate GDI leaks. All of them create GDI objects in a loop and select them into their current graphics device context (DC) on Windows Server 2003 x64 SP2. Before running them, we get the following session paged pool statistics:

```
lkd> !poolused c

Sorting by Session Paged Pool Consumed

Pool Used:

              NonPaged           Paged
Tag       Allocs  Used       Allocs  Used
NV_x      0       0          5       14024704 UNKNONWN pooltag 'NV_x', please update pooltag.txt
BIG       0       0          257     3629056 Large session pool allocations (ntos\ex\pool.c) , Binary:
nt!mm
NV        0       0          203     1347648 nVidia video driver
Ttfd      0       0          233     1053152 TrueType Font driver
Gh05      0       0          391     1058400 Gdi Handle manager specific object types: defined in
w32\ntgdi\inc\ntgdistr.h , Binary: win32k.sys
Gla1      0       0          348     785088 Gdi handle manager specific object types allocated from
lookaside memory: defined in w32\ntgdi\inc\ntgdistr.h , Binary: win32k.sys
Gcac      0       0          25      640880 Gdi glyph cache
Gla5      0       0          631     323072 Gdi handle manager specific object types allocated from
```