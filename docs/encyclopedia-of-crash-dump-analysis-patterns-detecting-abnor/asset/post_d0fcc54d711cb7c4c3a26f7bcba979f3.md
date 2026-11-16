
```
0:000> lmv m MyDLL_1e60000
start    end        module name
00000000`01e60000 00000000`01e71000   MyDLL_1e60000
    Loaded symbol image file: MyDLL.dll
    Image path: C:\OLD\MyDLL.dll
    Image name: MyDLL.dll
    Timestamp:        Wed Jun 18 14:49:13 2008 (48591259)
...
0:000> lmv m MyDLL
start    end        module name
00000000`80000000 00000001`80011000   MyDLL
    Image path: C:\2DLLs\DLLs\MyDLL.dll
    Image name: MyDLL.dll
    Timestamp:        Wed Jun 18 14:50:56 2008 (485912C0)
...
```

We can also see that the old version of MyDLL was the last loaded DLL:

```
0:000> !dlls -l
0x002c2680: C:\2DLLs\2DLLs.exe
    Base    0x140000000   EntryPoint  0x1400013b0   Size      0x00010000
    Flags   0x00004000    LoadCount   0x0000ffff    TlsIndex  0x00000000
        LDRP_ENTRY_PROCESSED
...
0x002ea9b0: C:\2DLLs\DLL\MyDLL.dll
    Base    0x180000000   EntryPoint  0x1800013d0   Size      0x00011000
    Flags   0x00084004    LoadCount   0x00000001    TlsIndex  0x00000000
        LDRP_IMAGE_DLL
        LDRP_ENTRY_PROCESSED
        LDRP_PROCESS_ATTACH_CALLED
...
0x002ec430: C:\OLD\MyDLL.dll
    Base    0x01e600000   EntryPoint  0x01e613e0    Size      0x00011000
    Flags   0x00284004    LoadCount   0x00000001    TlsIndex  0x00000000
        LDRP_IMAGE_DLL
        LDRP_ENTRY_PROCESSED
        LDRP_PROCESS_ATTACH_CALLED
        LDRP_IMAGE_NOT_AT_BASE
```

We can also see that the PATH variable points to its location, and this might explain why it was loaded:

```
0:000> !peb
PEB at 000007fffffd6000
...
Path=C:\OLD;C:\Windows\system32;C:\Windows;...
...
```

We might think that the module having an address in its name was loaded the last, but this is not true. If we save another copy of the dump from the existing one using .dump command and load the new dump file we would see that order of the module names is reversed:

```
0:000> kL
Child-SP          RetAddr           Call Site
00000000`0012fed8 00000001`40001093 MyDLL!fnMyDLL
00000000`0012fee0 00000001`40001344 2DLLs+0x1093
00000000`0012ff10 00000000`773acdcd 2DLLs+0x1344
00000000`0012ff60 00000000`774fc6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0012ff90 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
0:000> lm
start             end                 module name
00000000`01e60000 00000000`01e71000   MyDLL
00000000`772a0000 00000000`7736a000   user32
00000000`77370000 00000000`774a1000   kernel32
00000000`774b0000 00000000`7762a000   ntdll
00000001`40000000 00000001`40010000   2DLLs
00000001`80000000 00000001`80011000   MyDLL_180000000
000007fe`fc9e0000 000007fe`fca32000   uxtheme
000007fe`fe870000 000007fe`fe9a9000   rpcrt4
000007fe`fe9b0000 000007fe`fe9bc000   lpk
000007fe`fea10000 000007fe`feae8000   oleaut32
000007fe`fecc0000 000007fe`fed6a000   usp10
000007fe`fedc0000 000007fe`fefb0000   ole32
000007fe`fefb0000 000007fe`ff0af000   advapi32
000007fe`ff0d0000 000007fe`ff131000   gdi32
000007fe`ff2e0000 000007fe`ff381000   msvcrt
000007fe`ff390000 000007fe`ff3b8000   imm32
000007fe`ff4b0000 000007fe`ff5b4000   msctf
```

```
0:000> !dlls -l

...

0x002ec430: C:\OLD\MyDLL.dll
    Base    0x01e60000      EntryPoint  0x01e613e0      Size        0x00011000
    Flags   0x00284004      LoadCount   0x00000001      TlsIndex    0x00000000
        LDRP_IMAGE_DLL
        LDRP_ENTRY_PROCESSED
        LDRP_PROCESS_ATTACH_CALLED
        LDRP_IMAGE_NOT_AT_BASE
```

The post-processed dump file used for this example can be downloaded from FTP to play with⁴⁸.

## Comments

There were a few questions:

Q. We can also see that the old version of MyDLL was the last loaded DLL. That statement contradicts the following output where it's clear that the old DLL was loaded first:

```
0:000> lmv m MyDLL_1e60000
start end module name
00000000`01e60000 01e71000 MyDLL_1e60000
Loaded symbol image file: MyDLL.dll
Image path: C:\OLD\MyDLL.dll
Image name: MyDLL.dll
Timestamp: Wed Jun 18 14:49:13 2008 (48591259)
[...]

0:000> lmv m MyDLL
start end module name
00000001`80000000 00000001`80011000 MyDLL
Image path: C:\2DLLs\DLL\MyDLL.dll
Image name: MyDLL.dll
Timestamp: Wed Jun 18 14:50:56 2008 (485912C0)
[...]
```

A. We don't see the contradiction here: Timestamp is for the link time not the load time, and the loader is free to choose the base address.

Q. From the list of modules we are able to see two modules are duplicated. Is there any way to find out, who called the module to load into memory. We would like to see the calling function (the originator of duplication).

A. We suggest searching for module start address on thread raw stacks. Also, consider live debugging with enabled load modules event handling in WinDbg.

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_290_0.png)

## Dynamic Memory Corruption

### Kernel Pool

If kernel pools are corrupt then calls that allocate or free memory result in bugchecks C2 or 19 and in other fewer frequent bugchecks (from Google stats⁴⁹):

| BugCheck C2: BAD_POOL_CALLER | 1600 |
|---|---|
| BugCheck 19: BAD_POOL_HEADER | 434 |
| BugCheck C5: DRIVER_CORRUPTED_EXPOOL | 207 |
| BugCheck DE: POOL_CORRUPTION_IN_FILE_AREA | 106 |
| BugCheck D0: DRIVER_CORRUPTED_MMPOOL | 8 |
| BugCheck D6: DRIVER_PAGE_FAULT_BEYOND_END_OF_ALLOCATION | 3 |
| BugCheck CD: PAGE_FAULT_BEYOND_END_OF_ALLOCATION | 2 |
| BugCheck C6: DRIVER_CAUGHT_MODIFYING_FREED_POOL | 0 |

Bugchecks 0xC2 and 0x19 have parameters in their arguments that tell the type of detected pool corruption. We should refer to WinDbg help for details or use the variant of **!analyze** command where we can supply optional bugcheck arguments:

```
1: kd> !analyze -show c2
BAD_POOL_CALLER (c2)
The current thread is making a bad pool request. Typically this is at a bad IRQL level or double freeing
the same allocation, etc.
Arguments:
Arg1: 00000000, The caller is requesting a zero byte pool allocation.
Arg2: 00000000, zero.
Arg3: 00000000, the pool type being allocated.
Arg4: 00000000, the pool tag being used.
```

```
1: kd> !analyze -show 19 2 1 1 1
BAD_POOL_HEADER (19)
The pool is already corrupt at the time of the current request.
This may or may not be due to the caller.
The internal pool links must be walked to figure out a possible cause of
the problem, and then special pool applied to the suspect tags or the driver
verifier to a suspect driver.
Arguments:
Arg1: 00000002, the verifier pool pattern check failed. The owner has likely corrupted the pool block
Arg2: 00000001, the pool entry being checked.
Arg3: 00000001, size of the block.
Arg4: 00000001, 0.
```

If we enable special pool on suspected drivers, we may get these bugchecks too with the following Google frequency:

| BugCheck C1: SPECIAL_POOL_DETECTED_MEMORY_CORRUPTION | 59 |
|---|---|
| BugCheck D5: DRIVER_PAGE_FAULT_IN_FREED_SPECIAL_POOL | 5 |
| BugCheck CC: PAGE_FAULT_IN_FREED_SPECIAL_POOL | 1 |

Here is one example of nonpaged pool corruption detected during *free* operation with the following **!analyze -v** output:

```
BAD_POOL_HEADER (19)
The pool is already corrupt at the time of the current request.
This may or may not be due to the caller.
The internal pool links must be walked to figure out a possible cause of
the problem, and then special pool applied to the suspect tags or the driver
verifier to a suspect driver.
Arguments:
Arg1: 00000020, a pool block header size is corrupt.
Arg2: a34583b8, The pool entry we were looking for within the page.
Arg3: a34584f0, The next pool entry.
Arg4: 0a270001, (reserved)

POOL_ADDRESS: a34583b8 Nonpaged pool

PROCESS_NAME: process.exe

CURRENT_IRQL: 2

STACK_TEXT:
b80a60cc 808927bb nt!KeBugCheckEx+0x1b
b80a6134 80892b6f nt!ExFreePoolWithTag+0x477
b80a6144 b5991400 nt!ExFreePool+0xf
WARNING: Stack unwind information not available. Following frames may be wrong.
b80a615c b957b954 driver+0x38400
b80a617c b957d482 driver+0x22954
b80a61c0 b957abf4 driver+0x24482
b80a6260 b957ccf driver+0x21bf4
b80a62a8 8081df65 driver+0x23cef
b80a62bc f721ac45 nt!IofCallDriver+0x45
b80a62e4 8081df65 fltMgr!FltpDispatch+0x6f
```
