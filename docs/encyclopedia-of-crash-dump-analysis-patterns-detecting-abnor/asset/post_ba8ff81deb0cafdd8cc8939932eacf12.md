
```
b80a62f8 b99de70b nt!IofCallDriver+0x45
b80a6308 b99da6ee filter!Dispatch+0xfb
b80a6318 b801df65 filter!dispatch+0x6e
b80a632c b9bddebfe nt!IofCallDriver+0x45
b80a6334 8081df65 2ndfilter!Redirect+0x7ea
b80a6348 b9bd1756 nt!IofCallDriver+0x45
b80a6374 b9bd1860 3rdfilter!PassThrough+0x136
b80a6384 8081df65 3rdfilter!Dispatch+0x80
b80a6398 808f5437 nt!IofCallDriver+0x45
b80a63ac 808e9693 nt!IopSynchronousServiceTail+0x10b
b80a63d0 8088978c nt!NtQueryDirectoryFile+0x5d
b80a63d0 7c8285ec nt!KiFastCallEntry+0xfc
00139524 7c8274eb ntdll!KiFastSystemCallRet
00139528 77e6ba40 ntdll!NtQueryDirectoryFile+0xc
00139830 77e6bbf5 kernel32!FindFirstFileExW+0x3d5
00139850 6002665e kernel32!FindFirstFileW+0x16
00139e74 60026363 process+0x2665e
0013a328 60027852 process+0x26363
0013a33c 60035b58 process+0x27852
0013b104 600385ff process+0x355b8
0013b224 612cb643 process+0x385ff
0013b988 612cc109 dll!FileDialog+0xc53
0013bba0 612cb47b dll!FileDialog+0x1719
0013c2c0 7739b6e3 dll!FileDialog+0xa8b
0013c2ec 77395f82 USER32!InternalCallWinProc+0x28
0013c368 77395e22 USER32!UserCallDlgProcCheckWow+0x147
0013c3b0 7739c9c6 USER32!DefDlgProcWorker+0xa8
0013c3d8 7c828536 USER32!__fnDWORD+0x24
0013c3d8 808308f4 ntdll!KiUserCallbackDispatcher+0x2e
b80a66b8 8091d6d1 nt!KiCallUserMode+0x4
b80a6710 bf8a2622 nt!KeUserModeCallback+0x8f
b80a6794 bf8a2517 win32k!SfnDWORD+0xb4
b80a67dc bf8a13d9 win32k!xxxSendMessageToClient+0x133
b80a6828 bf85ae67 win32k!xxxSendMessageTimeout+0x1a6
b80a684c bf8847a1 win32k!xxxWrapSendMessage+0x1b
b80a6868 bf8c1459 win32k!NtUserfnNCDESTROY+0x27
b80a68a0 8088978c win32k!NtUserMessageCall+0xc0
b80a68a0 7c8285ec nt!KiFastCallEntry+0xfc
0013c3d8 7c828536 ntdll!KiFastSystemCallRet
0013c3d8 808308f4 ntdll!KiUserCallbackDispatcher+0x2e
b80a6b7c 8091d6d1 nt!KiCallUserMode+0x4
b80a6bd4 bf8a2622 nt!KeUserModeCallback+0x8f
b80a6c58 bf8a23a0 win32k!SfnDWORD+0xb4
b80a6ca0 bf8a13d9 win32k!xxxSendMessageToClient+0x118
b80a6cec bf85ae67 win32k!xxxSendMessageTimeout+0x1a6
b80a6d10 bf8c148c win32k!xxxWrapSendMessage+0x1b
b80a6d40 8088978c win32k!NtUserMessageCall+0x9d
b80a6d40 7c8285ec nt!KiFastCallEntry+0xfc
0013f474 7c828536 ntdll!KiFastSystemCallRet
0013f4a0 7739d1ec ntdll!KiUserCallbackDispatcher+0x2e
0013f4dc 7738cf29 USER32!NtUserMessageCall+0xc
0013f4fc 612d3276 USER32!SendMessageA+0x7f
0013f63c 611ad41 dll!SubWindow+0x3dc6
0013f658 7739b6e3 dll!SetWindowText+0x37a1
0013f684 7739b874 USER32!InternalCallWinProc+0x28
0013f6fc 7739ba92 USER32!UserCallWinProcCheckWow+0x151
0013f764 7739bad0 USER32!DispatchMessageWorker+0x327
0013f774 61221ca8 USER32!DispatchMessageW+0xf
0013f7e0 0040156d dll!MainLoop+0xc28
0013ff24 004001da process+0x156d
0013ffc0 77e6f23b process+0x1dfa
0013fff0 00000000 kernel32!BaseProcessStart+0x23

MODULE_NAME: driver

IMAGE_NAME: driver.sys
```

We see that WinDbg pointed to driver.sys by using a procedure described in Component Identification article 50.

Any OS component could corrupt the pool prior to the detection as the bugcheck description says: “The pool is already corrupt at the time of the current request.”. What other evidence can reinforce our belief in driver.sys? Let’s look at our pool entry tag first:

```
1: kd> !pool a34583b8
Pool page a34583b8 region is Nonpaged pool

a3458000 size: 270 previous size: 0 (Allocated) Thre (Protected)
a3458270 size: 10 previous size: 270 (Free) RxIr
a3458280 size: 40 previous size: 10 (Allocated) VadI
a34582c0 size: 98 previous size: 40 (Allocated) File (Protected)
a3458358 size: 8 previous size: 98 (Free) Vad1
a3458360 size: 50 previous size: 8 (Allocated) Gsem
a34583b0 size: 8 previous size: 50 (Free) CcSc
*a34583b8 size: 138 previous size: 8 (Allocated) *DRIV

Owning component : Unknown (update pooltag.txt)
a34584f0 is not valid large pool allocation, checking large session pool...
a34584f0 is free (or corrupt) pool
Bad allocation size @a34584f0, zero is invalid

***
*** An error (or corruption) in the pool was detected;
*** Attempting to diagnose the problem.
***
*** Use !poolval a3458000 for more details.
***

Pool page [ a3458000 ] is _inVALID.

Analyzing linked list...
[ a34583b8 --> a34583d8 (size = 0x20 bytes)]: Corrupt region
[ a34583f8 --> a34585e8 (size = 0x1f0 bytes)]: Corrupt region

Scanning for single bit errors...

None found
```

We see that the tag is DRIV, and we know either from the association or from similar problems in the past that it belongs to driver.sys. Let's dump our pool entry contents to see if there are any symbolic hints in it:

```
1: kd> dps a34583b8
a34583b8 0a270001
a34583bc 5346574e
a34583c0 00000000
a34583c4 00000000
a34583c8 b958f532 driver+0x36532
a34583cc a3471010
a34583d0 0000012e
a34583d4 00000001
a34583d8 00041457
a34583dc 05af0026
a34583e0 00068002
a34583e4 7b9ce6f5
a34583e8 fffffff0
a34583ec 73650cff
a34583f0 7461445c
a34583f4 97a10061
a34583f8 ff340004
a34583fc c437862a
a3458400 6a000394
a3458404 00000038
a3458408 00000000
a345840c bf000000
a3458410 bf0741b5
a3458414 f70741b5
a3458418 00000000
a345841c 00000000
a3458420 00000000
a3458424 00000000
a3458428 05000000
a345842c 34303220
a3458430 31323332
a3458434 ff322d36
```

Indeed we see that the possible code pointer driver+0x36532 and the code around this address look normal:

```
3: kd> .asm no_code_bytes
Assembly options: no_code_bytes

3: kd> u b958f532
driver+0x36532:
b958f532 push        2Ch
b958f534 push        offset driver+0x68d08 (b95c1d08)
b958f539 call        driver+0x65c50 (b95bec50)
b958f53e mov         byte ptr [ebp-19h],0
b958f542 and         dword ptr [ebp-24h],0
b958f546 call        dword ptr [driver+0x6f5fc (b95bef5c)]
b958f54c mov         ecx,dword ptr [ebp+0Ch]
b958f54f cmp         eax,ecx
```

```
3: kd> ub b958f532
driver+0x36528:
b958f528 leave
b958f529 ret         18h
b958f52c int         3
b958f52d int         3
b958f52e int         3
b958f52f int         3
b958f530 int         3
b958f531 int         3
```

## Comments

> Q. I have the same problem with BAD_POOL_HEADER; I see the pool header e173c1d8 is corrupt and marked as *Ppen. Could you help me to know what is that?

```
BAD_POOL_HEADER (19)
The pool is already corrupt at the time of the current request.
This may or may not be due to the caller.
The internal pool links must be walked to figure out a possible cause of
the problem, and then special pool applied to the suspect tags or the driver
verifier to a suspect driver.
Arguments:
Arg1: 00000020, a pool block header size is corrupt.
Arg2: e173c1d8, The pool entry we were looking for within the page.
Arg3: e173c1f8, The next pool entry.
Arg4: 0c040404, (reserved)

Debugging Details:
--------

BUGCHECK_STR: 0x19_20

POOL_ADDRESS: e173c1d8

CUSTOMER_CRASH_COUNT: 6

DEFAULT_BUCKET_ID: COMMON_SYSTEM_FAULT

PROCESS_NAME: System

LOCK_ADDRESS: 8055b4e0 -- (!locks 8055b4e0)

Resource @ nt!PiEngineLock (0x8055b4e0) Available

WARNING: SystemResourcesList->Flink chain invalid. Resource may be corrupted, or already deleted.

WARNING: SystemResourcesList->Blink chain invalid. Resource may be corrupted, or already deleted.
```

```
1 total locks

PNP_TRIAGE:
Lock address : 0x8055b4e0
Thread Count : 0
Thread address: 0x00000000
Thread wait : 0x0

LAST_CONTROL_TRANSFER: from 8054b583 to 804f9f33

STACK_TEXT:
f79f392c 8054b583 00000019 00000020 e173c1d8 nt!KeBugCheckEx+0x1b
f79f397c 8054fc05 e173c1e0 00000000 00000000 nt!ExFreePoolWithTag+0x2a3
f79f39dc 8059161d 85804dd0 e10f29a8 f79f3a48 nt!PipMakeGloballyUniqueId+0x3a9
f79f3ad0 8059222b 8593a7c8 861d33e8 8593a7c8 nt!PipProcessNewDeviceNode+0x185
f79f3d24 805927fa 8593a7c8 00000001 00000000 nt!PipProcessDevNodeTree+0x16b
f79f3d54 804f698e 00000003 8055b5c0 8056485c nt!PiRestartDevice+0x80
f79f3d7c 8053876d 00000000 00000000 863c1da8 nt!PipDeviceActionWorker+0x168
f79f3dac 805cff64 00000000 00000000 00000000 nt!ExpWorkerThread+0xef
f79f3ddc 805460de 8053867e 00000001 00000000 nt!PspSystemThreadStartup+0x34
00000000 00000000 00000000 00000000 00000000 nt!KiThreadStartup+0x16

STACK_COMMAND: kb

FOLLOWUP_IP:
nt!ExFreePoolWithTag+2a3
8054b583 8b45f8 mov eax,dword ptr [ebp-8]

SYMBOL_STACK_INDEX: 1

SYMBOL_NAME: nt!ExFreePoolWithTag+2a3

FOLLOWUP_NAME: MachineOwner

MODULE_NAME: nt

IMAGE_NAME: ntkramp.exe

DEBUG_FLR_IMAGE_TIMESTAMP: 4802516a

FAILURE_BUCKET_ID: 0x19_20_nt!ExFreePoolWithTag+2a3

BUCKET_ID: 0x19_20_nt!ExFreePoolWithTag+2a3

Followup: MachineOwner
---
```
