# Windows

# Kernel Mode

Here is an example of **Stack Overflow** pattern in x86 Windows kernel. When it happens in kernel mode we usually have bugcheck 7F with the first argument being EXCEPTION_DOUBLE_FAULT (8):

```
UNEXPECTED_KERNEL_MODE_TRAP (7f)
This means a trap occurred in kernel mode, and it's a trap of a kind that the kernel isn't allowed to have/catch (bound trap) or that is always instant death (double fault). The first number in the bugcheck params is the number of the trap (8 = double fault, etc). Consult an Intel x86 family manual to learn more about what these traps are. Here is a *portion* of those codes:
If kv shows a taskGate
 use .tss on the part before the colon, then kv.
Else if kv shows a trapframe
 use .trap on that value
Else
 .trap on the appropriate frame will show where the trap was taken (on x86, this will be the ebp that goes with the procedure KiTrap)
Endif
kb will then show the corrected stack.
Arguments:
Arg1: 00000008, EXCEPTION_DOUBLE_FAULT
Arg2: f7747fe0
Arg3: 00000000
Arg4: 00000000
```

The kernel stack size for a thread is limited to 12Kb on x86 platforms (24kb on x64 platforms) and is guarded by an invalid page. Therefore when we hit an invalid address on that page, the processor generates a page fault, tries to push registers and gets a second page fault. This is what “double fault” means. In this scenario, the processor switches to another stack via TSS (task state segment) task switching mechanism because IDT entry for trap 8 contains not an interrupt handler address but the so-called TSS segment selector. This selector points to a memory segment that contains a new kernel stack pointer. The difference between normal IDT entry and double fault entry can be seen by inspecting IDT:

```
5: kd> !pcr 5
KPCR for Processor 5 at f7747000:
Major 1 Minor 1
NTib.ExceptionList: b044e0b8
NTib.StackBase: 00000000
NTib.StackLimit: 00000000
NTib.SubSystemTib: f7747fe0
NTib.Version: 00ae1064
NTib.UserPointer: 00000020
NTib.SelfTib: 7ffdf000
SelfPcr: f7747000
Prcb: f7747120
Irql: 00000000
IRR: 00000000
IDR: ffffffff
InterruptMode: 00000000
```