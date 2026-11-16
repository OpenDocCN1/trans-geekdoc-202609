# Custom Exception Handler

# Kernel Space

This is a kernel space counterpart to **Custom Exception Handler** pattern in user space (page 171). In the following stack trace below we see that **DriverA** code intercepted an access violation exception resulted from dereferencing **NULL Pointer** (page 752) and generated a custom bugcheck:

```
kd> !analyze -v

[...]

EXCEPTION_RECORD: fffff8801c757158 -- (.exr 0xfffff8801c757158)
ExceptionAddress: fffff88003977de1 (DriverA!foo+0x0000000000000381)
ExceptionCode: c0000005 (Access violation)
ExceptionFlags: 00000000
NumberParameters: 2
Parameter[0]: 0000000000000000
Parameter[1]: 0000000000000070
Attempt to read from address 0000000000000070

TRAP_FRAME: fffff8801c757200 -- (.trap 0xfffff8801c757200)
NOTE: The trap frame does not contain all registers.
Some register values may be zeroed or incorrect.
rax=0000000000000000 rbx=0000000000000000 rcx=fffff8a00da3f3c0
rdx=0000000000000000 rsi=0000000000000000 rdi=0000000000000000
rip=fffff88003977de1 rsp=fffff8801c757390 rbp=fffff800a9a853f0
r8=0000000000000000 r9=0000000000000000 r10=006800744002006e
r11=fffff8a00da3f3c6 r12=0000000000000000 r13=0000000000000000
r14=0000000000000000 r15=0000000000000000
iopl=0 nv up ei pl zr na po nc
DriverA!foo+0x381:
fffff880`03977de1 0fb74070 movzx eax,word ptr [rax+70h] ds:0703:0070=????
Resetting default scope

[...]

kd> Kl 100
Child-SP RetAddr Call Site
fffff880`1c7560f8 fffff880`039498f7 nt!KeBugCheckEx
fffff880`1c756100 fffff880`039352a0 DriverA!MyBugCheckEx+0x93
fffff880`1c756140 fffff880`016f1didc DriverA!MyExceptionFilter+0x1d0
fffff880`1c756210 fffff880`016e94da nt!_C_specific_handler+0x8c
fffff880`1c756280 fffff880`016f0a90 nt!RtlpExecuteHandlerForException+0xd
fffff880`1c7562b0 fffff880`016fd9ef nt!RtlDispatchException+0x410
fffff880`1c756990 fffff880`016c2df2 nt!KiDispatchException+0x16f
fffff880`1c757020 fffff880`016c18fa nt!KiExceptionDispatch+0xc2
fffff880`1c757200 fffff880`03977de1 nt!KiPageFault+0x23a
fffff880`1c757390 fffff880`03977754 DriverA!foo+0x381
fffff880`1c757430 fffff880`0396f006 DriverA!bar+0x74
[...]
fffff880`1c7579b0 fffff880`019a6e0a DriverA!QueryInformation+0x30b
```