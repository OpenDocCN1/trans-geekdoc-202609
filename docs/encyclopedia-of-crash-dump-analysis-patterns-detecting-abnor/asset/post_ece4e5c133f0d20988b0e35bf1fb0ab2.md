
## Network Packet BuildUp

When looking at the network packet pools using NDIS WinDbg extension, we might see increased number of allocated blocks possibly correlated with network problems, for example:

| Pool | Allocator | BlocksAllocated | BlockSize | PktrsPerBlock | PacketLength |
| --- | --- | --- | --- | --- | --- |
| 8a467e20 | b9909f96 | 0x1 | 0x1000 | 0x14 | 0xc8   tcpip!ARPRegister+119 |
| 8a491460 | ba4eea56 | 0x1 | 0x1000 | 0x14 | 0xc8   wanarp!WanpInitializeNdis+a8 |
| 8a466508 | b905d368 | 0x1 | 0x1000 | 0xd | 0x138  tcpip!InitForwardingPools+53 |
| 8a373578 | b905becb | 0x3 | 0x1000 | 0x11 | 0xe8   tcpip!AllocIPPacketList+59 |
| 8a466580 | b9095ac5 | 0x1 | 0x1000 | 0xe | 0x118  tcpip!IPInit+e0 |
| 8a460958 | bac40a97 | 0xb | 0x1000 | 0x14 | 0xc8   vmxnet+a97 |

| Pool | Allocator | BlocksAllocated | BlockSize | PktrsPerBlock | PacketLength |
| --- | --- | --- | --- | --- | --- |
| 8a467e20 | b9909f96 | 0x1 | 0x1000 | 0x14 | 0xc8   tcpip!ARPRegister+119 |
| 8a491460 | ba4eea56 | 0x1 | 0x1000 | 0x14 | 0xc8   wanarp!WanpInitializeNdis+a8 |
| 8a466508 | b905d368 | 0x1 | 0x1000 | 0xd | 0x138  tcpip!InitForwardingPools+53 |
| 8a373578 | b905becb | 0xa3 | 0x1000 | 0x11 | 0xe8   tcpip!AllocIPPacketList+59 |
| 8a466580 | b9095ac5 | 0x1 | 0x1000 | 0xe | 0x118  tcpip!IPInit+e0 |
| 8a460958 | bac40a97 | 0x9b | 0x1000 | 0x14 | 0xc8   vmxnet+a97 |

## No Component Symbols

No Component Symbols often happens in crash dumps. In this case, we can guess what a component does by looking at its name, overall thread stack where it is called and also its import table. Here is an example. We have *component.sys* driver visible on some thread stack in a kernel dump but we don't know what that component can potentially do. Because we don't have symbols we cannot see its imported functions:

```
kd> x component!*
k>
```

We use !dh command to dump its image headers:

```
kd> lmv m component
start             end                 module name
fffffadf`e0eb5000 fffffadf`e0ebc000   component   (no symbols)
    Loaded symbol image file: component.sys
    Image path: \?\C:\Component\x64\component.sys
    Image name: component.sys
    Timestamp:        Sat Jul 01 19:06:16 2006 (44A6B998)
    CheckSum:         00007E4F
    ImageSize:        00007000
    Translations:     0000.04b0 0000.04e0 0409.04b0 0409.04e0

kd> !dh fffffadf`e0eb5000
File Type: EXECUTABLE IMAGE
FILE HEADER VALUES
    8664 machine (X64)
      6 number of sections
44A6B998 time date stamp Sat Jul 01 19:06:16 2006
      0 file pointer to symbol table
      0 number of symbols
    F0 size of optional header
      22 characteristics
        Executable
        App can handle >2gb addresses
OPTIONAL HEADER VALUES
      20B magic #
      8.00 linker version
      C00 size of code
      A00 size of initialized data
      0 size of uninitialized data
    5100 address of entry point
    1000 base of code
------- new -------
00000000`00010000 image base
      1000 section alignment
      200 file alignment
      1 subsystem (Native)
    5.02 operating system version
    5.02 image version
    5.02 subsystem version
     7000 size of image
400 size of headers
74EF checksum
0000000000040000 size of stack reserve
0000000000001000 size of stack commit
0000000000100000 size of heap reserve
0000000000001000 size of heap commit
0 [ 0] address [size] of Export Directory
51B0 [ 28] address [size] of Import Directory
6000 [ 388] address [size] of Resource Directory
4000 [ 6C] address [size] of Exception Directory
0 [ 0] address [size] of Security Directory
0 [ 0] address [size] of Base Relocation Directory
2090 [ 1C] address [size] of Debug Directory
0 [ 0] address [size] of Description Directory
0 [ 0] address [size] of Special Directory
0 [ 0] address [size] of Thread Storage Directory
0 [ 0] address [size] of Load Configuration Directory
0 [ 0] address [size] of Bound Import Directory
2000 [ 88] address [size] of Import Address Table Directory
0 [ 0] address [size] of Delay Import Directory
0 [ 0] address [size] of COR20 Header Directory
0 [ 0] address [size] of Reserved Directory
...
```

Then we display the contents of Import Address Table Directory using dps command:

```
kd> dps fffffadf`e0eb5000+2000 fffffadf`e0eb5000+2000+88
fffffadf`e0eb7000 fffffff800`01044370 nt!IoCompleteRequest
fffffadf`e0eb7008 fffffff800`01019700 nt!IoDeleteDevice
fffffadf`e0eb7010 fffffff800`012551a0 nt!IoDeleteSymbolicLink
fffffadf`e0eb7018 fffffff800`01056a90 nt!MiResolveTransitionFault+0x7c2
fffffadf`e0eb7020 fffffff800`0103a380 nt!ObDereferenceObject
fffffadf`e0eb7028 fffffff800`0103ace0 nt!KeWaitForSingleObject
fffffadf`e0eb7030 fffffff800`0103c570 nt!KeSetTimer
fffffadf`e0eb7038 fffffff800`0102d070 nt!IoBuildPartialMdl+0x3
fffffadf`e0eb7040 fffffff800`012d4480 nt!PsTerminateSystemThread
fffffadf`e0eb7048 fffffff800`01041690 nt!KeBugCheckEx
fffffadf`e0eb7050 fffffff800`010381b0 nt!KeInitializeTimer
fffffadf`e0eb7058 fffffff800`0103ceb0 nt!ZwClose
fffffadf`e0eb7060 fffffff800`012b39f0 nt!ObReferenceObjectByHandle
fffffadf`e0eb7068 fffffff800`012b7380 nt!PsCreateSystemThread
fffffadf`e0eb7070 fffffff800`01251f90 nt!FsRtlpIsDfsEnabled+0x114
fffffadf`e0eb7078 fffffff800`01275160 nt!IoCreateDevice
fffffadf`e0eb7080 00000000`00000000
fffffadf`e0eb7088 00000000`00000000
```

We see that this driver under certain circumstances can bugcheck the system using KeBugCheckEx, it creates system thread(s) (PsCreateSystemThread) and uses timer(s) (KeInitializeTimer, KeSetTimer).

If we see name+offset in the import table (I think this is an effect of OMAP Code Optimization, page 756) we can get the function by using ln command (list nearest symbols):

```
kd> ln fffff800`01056a90
(fffff800`01056760)   nt!MiResolveTransitionFault+0x7c2   |   (fffff800`01056a92)   nt!RtlInitUnicodeString

kd> ln fffff800`01251f90
(fffff800`01251e90)   nt!FsRtlpIsDfsEnabled+0x114   |   (fffff800`01251f92)   nt!IoCreateSymbolicLink
```

This technique is useful if we have a bugcheck that happens when a driver calls certain functions or must call certain functions in pairs, like bugcheck 0x20:

```
kd> !analyze -show 0x20
KERNEL_APC_PENDING_DURING_EXIT (20)
The key data item is the thread's APC disable count. If this is non-zero, then this is the source of the problem. The APC disable count is decremented each time a driver calls KeEnterCriticalRegion, KeInitializeMutex, or FsRtlEnterFileSystem. The APC disable count is incremented each time a driver calls KeLeaveCriticalRegion, KeReleaseMutex, or FsRtlExitFileSystem. Since these calls should always be in pairs, this value should be zero when a thread exits. A negative value indicates that a driver has disabled APC calls without re-enabling them. A positive value indicates that the reverse is true. If you ever see this error, be very suspicious of all drivers installed on the machine – especially unusual or non-standard drivers. Third party file system redirectors are especially suspicious since they do not generally receive the heavy duty testing that NTFS, FAT, RDR, etc receive. This current IRQL should also be 0. If it is not, that a driver's cancelation routine can cause this bugcheck by returning at an elevated IRQL. Always attempt to note what you were doing/closing at the time of the crash, and note all of the installed drivers at the time of the crash. This symptom is usually a severe bug in a third party driver.
```

Then we can see at least whether the suspicious driver could have potentially used those functions and if it imports one of them we can see whether it imports the corresponding counterpart function.

**No Component Symbols** pattern can be easily identified in stack traces by huge function offsets or no exported functions at all:

```
STACK_TEXT:
WARNING: Stack unwind information not available. Following frames may be wrong.
00b2f42c 091607aa mydll!foo+0x8338
00b2f4cc 7c83ab9e mydll+0x8fe3
```
