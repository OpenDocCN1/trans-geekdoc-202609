
## General

In addition to **Stack Trace Collection** (page 943) we are often interested in **Module Collection** (we initially called this pattern **Vendor Collection**), especially if we would like to check whether a particular vendor DLL is present in some process address space in a complete memory dump (kernel module list or module list from a process memory dump is trivial). Or we need to check for some vendor information from a problem description (**lmv** command). If we have a complete memory dump from x64 system then listing modules for each process is not enough. For example, we might have this:

```
0: kd> lmu
start             end                 module name
00000000`00ab0000 00000000`00ae8000 AppA        (deferred)
00000000`74fe0000 00000000`7502e000 wow64win    (deferred)
00000000`75030000 00000000`75075000 wow64       (deferred)
00000000`750c0000 00000000`750c9000 wow64cpu    (deferred)
00000000`77b70000 00000000`77cf7000 ntdll       (pdb symbols)
```

AppA is a 32-bit process and has an additional 32-bit module list that is more useful. We can set x86 context for a thread from that process and get the list of 32-bit modules:

```
0: kd> .load wow64exts

0: kd> .thread /w fffffa800e372060
Implicit thread is now fffffa80`0e372060
x86 context set

0: kd:x86> .reload
Loading Kernel Symbols
Loading User Symbols
Loading unloaded module list
Loading Wow64 Symbols

0: kd:x86> lmu
start             end                 module name
00000000`00ab0000 00000000`00ae8000 AppA        (deferred)
00000000`73490000 00000000`73515000 COMCTL32    (deferred)
00000000`73520000 00000000`735c3000 MSVCR90     (deferred)
00000000`735d0000 00000000`735e5000 MSVCP90     (deferred)
00000000`74920000 00000000`7493e000 USERENV      (deferred)
00000000`74940000 00000000`74ade000 comctl32_74940000 (deferred)
00000000`74af0000 00000000`74b02000 MSASN1       (deferred)
00000000`74b10000 00000000`74c03000 CRYPT32      (deferred)
00000000`74dc0000 00000000`74e5b000 MSVCR80      (deferred)
00000000`74f60000 00000000`74f60000 NETAPI32     (deferred)
00000000`74fe0000 00000000`7502e000 wow64win    (deferred)
00000000`75030000 00000000`75075000 wow64       (deferred)
00000000`750b0000 00000000`750ba000 WTSAPI32     (deferred)
00000000`750c0000 00000000`750c9000 wow64cpu     (deferred)
00000000`75cf0000 00000000`75d50000 Secur32 (deferred)
00000000`75d50000 00000000`76861000 SHELL32 (deferred)
00000000`76a10000 00000000`76aa0000 GDI32 (deferred)
00000000`76b30000 00000000`76b90000 IMM32 (deferred)
00000000`76be0000 00000000`76cf0000 kernel32 (deferred)
00000000`76e30000 00000000`76f75000 ole32 (deferred)
00000000`76f80000 00000000`7702a000 msvcrt (deferred)
00000000`77030000 00000000`77037000 PSAPI (deferred)
00000000`77040000 00000000`77110000 USER32 (deferred)
00000000`77110000 00000000`77169000 SHLWAPI (deferred)
00000000`77170000 00000000`771ed000 USP10 (deferred)
00000000`77380000 00000000`774d0000 OLEAUT32 (deferred)
00000000`77640000 00000000`77649000 LPK (deferred)
00000000`776e0000 00000000`777d0000 RPCRT4 (deferred)
00000000`777d0000 00000000`77898000 MSCTF (deferred)
00000000`778a0000 00000000`77966000 ADVAPI32 (deferred)
00000000`77b70000 00000000`77cf7000 ntdll (pdb symbols)
00000000`77d30000 00000000`77e90000 ntdll_77d30000 (pdb symbols)
```

So it looks like we need to dump modules for each thread. However, the output would be enormous unless we skip threads having the same PID. After some tinkering we wrote this WinDbg script with moderate output volume:

```
.load wow64exts
!for_each_thread ".thread @#Thread ;if (@$t0 != @@c++(@$thread->Cid.UniqueProcess)) {.reload /user;lmvu;thread /w @#Thread ;.reload /user;lmvu;r $t0 = @@c++(@$thread->Cid.UniqueProcess);.effmach AMD64; }"
```

## Predicate

While working on **Thread Cluster** pattern (page 1003) we realized that we need a predicate version of **Module Collection** pattern, similar to the predicate version of **Stack Trace Collection** (page 943) pattern. A predicate can be anything: company vendors, semantic proximity, functionality such as printing, remote file management, and so on. Such module sub-collections can be used instead of modules in more complex patterns: an example of software diagnostics pattern substitution and composition. For example, we might be able to identify a possible coupling between 2 semantically different module groups explained by **IPC Wait Chains** (page 1082) such as on this diagram:

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_694_0.png)

## Module Hint

This pattern is frequently observed in dynamic memory corruption incidents. It is similar to Execution Residue (page 371), or String Parameter (page 962) patterns where we have ASCII or UNICODE fragments providing troubleshooting and debugging hints. Module Hint is, therefore, a more specialized pattern where we can link module names to raw data. For example, a kernel memory dump saved after the detected pool corruption (Dynamic Memory Corruption pattern, page 292) shows P12345.DLL module name in a pool entry that can provide a link to the corresponding functionally to be reconfigured or removed:

```
BAD_POOL_HEADER (19)
    The pool is already corrupt at the time of the current request.
    This may or may not be due to the caller.
    The internal pool links must be walked to figure out a possible cause of the problem, and then special
    pool applied to the suspect tags or the driver verifier to a suspect driver.
    Arguments:
    Arg1: 00000020, a pool block header size is corrupt.
    Arg2: 8b79d078, The pool entry we were looking for within the page.
    Arg3: 8b79d158, The next pool entry.
    Arg4: 8a1c0004, (reserved)

STACK_TEXT:
b3e0aa4c 808947bb 00000019 00000020 8b79d078 nt!KeBugCheckEx+0x1b
b3e0aab4 b368c00f 8b79d080 00000000 00000000 nt!ExFreePoolWithTag+0x477
b3e0aac4 b366c668 8b79d080 00000000 00000000 DriverA!MemFree+0xf
[...]
b3e0ac44 8081e0c3 808f77c9 b3e0ac64 808f77c9 nt!IovCallDriver+0x112
b3e0ac50 808f77c9 8a8eef60 8b6862a8 8a8eef00 nt!IofCallDriver+0x13
b3e0ac64 808f856b 8ce456b0 8a8eef00 8b6862a8 nt!IopSynchronousServiceTail+0x10b
b3e0ad00 808f109a 000009dc 00000000 00000000 nt!IopXxxControlFile+0x5e5
b3e0ad34 8088b45c 000009dc 00000000 00000000 nt!NtDeviceIoControlFile+0x2a
b3e0ad34 7c82847c 000009dc 00000000 00000000 nt!KiFastCallEntry+0xfc
WARNING: Frame IP not in any known module. Following frames may be wrong.
00f5fb18 00000000 00000000 00000000 00000000 0x7c82847c

2: kd> !pool 8b79d080
Pool page 8b79d080 region is Unknown
8b79d000 size: 30 previous size: 0  (Allocated) FSFm
8b79d030 size: 28 previous size: 30 (Allocated) VadS
8b79d058 size: 20 previous size: 28 (Allocated) ReEv
*8b79d078 size: e0 previous size: 20 (Allocated) *DRV
    Owning component : Unknown (update pool.txt)
8b79d158 is not a valid large pool allocation, checking large session pool...
8b79d158 is freed (or corrupt) pool
Bad previous allocation size @8b79d158, last size was 1c

***
*** An error (or corruption) in the pool was detected;
*** Pool Region unknown (0xFFFFFFFF8B79D158)
***
***
*** Use !poolval 8b79d000 for more details.
***

2: kd> dc 8b79d078
8b79d078 [...] ...DRIV .......AP
8b79d088 [...] P12345.DLL......
8b79d098 [...] ....<%n..........
8b79d0a8 [...] ...$....:F..X.
[...]
```

## Comments

Another example is the presence of debugging or error handling modules in the module list.

It can also be a valid (non-coincidental, see **Coincidental Symbolic Information** analysis pattern, page 137) symbolic name via **dps** or **dps** command.

We can also use search commands **s-sa** and **s-su**.

## Module Product Process

If we found module related patterns (page 1167) in a complete memory dump and suspect a particular module, it may be worth looking at module product related process if it exists especially if this module (component, DLL) has product information or some related hint (!mv or !lmi commands). In complex environments, such modules may be loaded not only by hooking mechanisms but also as plugins. If we are not sure whether there is such a process, the best way is to get Module Collection (page 693) and find a process module that has the same vendor as the module in question. Then such process should also be analyzed for anomalies.
