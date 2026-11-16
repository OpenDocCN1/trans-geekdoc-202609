# Kernel Mode

This is a kernel mode counterpart of Divide by Zero pattern in user mode (page 259). It manifests under different bugchecks, for example:

```
1: kd> !analyze -v

[...]

UNEXPECTED_KERNEL_MODE_TRAP (7f)
This means a trap occurred in kernel mode, and it's a trap of a kind that the kernel isn't allowed to
have/catch (bound trap) or that is always instant death (double fault).  The first number in the bugcheck
params is the number of the trap (8 = double fault, etc)  Consult an Intel x86 family manual to learn more
about what these traps are. Here is a *portion* of those codes:
If kv shows a taskGate
        use .tss on the part before the colon, then kv.
Else if kv shows a trapframe
        use .trap on that value
Else
        .trap on the appropriate frame will show where the trap was taken
        (on x86, this will be the ebp that goes with the procedure KiTrap)
Endif
kb will then show the corrected stack.
Arguments:
Arg1: 00000000, EXCEPTION_DIVIDED_BY_ZERO
Arg2: 00000000
Arg3: 00000000
Arg4: 00000000

[...]

TRAP_FRAME: a8954c8c -- (.trap 0xffffffffa8954c8c)
ErrCode = 00000000
eax=fffffffe ebx=00000000 ecx=00000005 edx=00000000 esi=00000000 edi=00000000
eip=975c42cd esp=a8954d00 ebp=a8954d04 iopl=0 nv up ei pl zr na pe nc
cs=0008 ss=0010 ds=0023 es=0023 fs=0030 gs=0000 efl=00010246
win32k!NtGdiEnumObjects+0xc6:
975c42cd f7f6  div eax,esi
Resetting default scope

PROCESS_NAME:  Application.EXE

[...]
```