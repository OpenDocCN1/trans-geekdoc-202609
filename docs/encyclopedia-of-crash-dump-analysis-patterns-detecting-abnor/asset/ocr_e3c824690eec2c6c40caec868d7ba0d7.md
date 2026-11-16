We can also see code f001 on the following thread stack as well:

```
DRIVER_VERIFIER_DETECTED_VIOLATION (c4)
A device driver attempting to corrupt the system has been caught. This is
because the driver was specified in the registry as being suspect (by the
administrator) and the kernel has enabled substantial checking of this driver.
If the driver attempts to corrupt the system, bugchecks 0xC4, 0xC1 and 0xA will
be among the most commonly seen crashes.
Arguments:
Arg1: 0000000000000091, A driver switched stacks using a method that is not supported by
the operating system. The only supported way to extend a kernel
mode stack is by using KeExpandKernelStackAndCallout.
Arg2: 0000000000000000
Arg3: fffff8800185bc40
Arg4: 0000000000000000

0: kd> k1 100
Child-SP RetAddr Call Site
fffff880`0891f8c8 fffff800`01729c8a nt!KeBugCheckEx
fffff880`0891f8d0 fffff800`01700573 nt! ?? ::FNODOBFM::`string'+0x4904
fffff880`0891f910 fffff800`0170d8df nt!RtlDispatchException+0x33
fffff880`0891f1f0 fffff800`016d2c42 nt!KiDispatchException+0x16f
fffff880`08920680 fffff800`016d17ba nt!KiExceptionDispatch+0xcx2
fffff880`08920860 fffff800`016ca533 nt!KiPageFault+0x23a
fffff880`089209f8 fffff800`016a88c0 nt!memcpy+0x223
fffff880`08920a00 fffff800`016a8638 nt!KiOpFetchBytes+0x30
fffff880`08920a30 fffff800`017d0d6f nt!KiOpDecode+0x68
fffff880`08920a80 fffff800`017d0896 nt!KiPreprocessFault+0x53
fffff880`08920b10 fffff800`016d2c42 nt!KiDispatchException+0x126
fffff880`089211a0 fffff800`016d17ba nt!KiExceptionDispatch+0xcx2
fffff880`08921380 00000000`0000f001 nt!KiPageFault+0x23a
fffff880`08921518 fffff800`016d9b4b 0xf001
fffff880`08921520 fffff800`016d94da nt!EnlightenedSwapContext_PatchXSave+0xa8
fffff880`08921560 fffff800`016da752 nt!KiSwapContext+0x7a
fffff880`089216a0 fffff800`016dc8af nt!KiCommitThreadWait+0x1d2
fffff880`08921730 fffff800`0169c1de nt!KeWaitForSingleObject+0x19f
fffff880`089217d0 fffff800`016db8bc nt!ExpWaitForResource+0xae
fffff880`08921840 fffff880`042fcd91 nt!ExAcquireResourceExclusiveLite+0x14f
[...]
fffff880`08921a10 fffff800`019eff16 nt!IopXxxControlFile+0x607
fffff880`08921b40 fffff800`016d2853 nt!NtDeviceIoControlFile+0x56
fffff880`08921bb0 00000000`7755ff2a nt!KiSystemServiceCopyEnd+0x13
00000000`0343f708 00000000`00000000 0x7755ff2a
```