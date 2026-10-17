
## `OslArchTransferToKernel` 过程分析

```asm
.text:0000000180123C90 OslArchTransferToKernel proc near
.text:0000000180123C90         xor     esi, esi
.text:0000000180123C92         mov     r12, rcx
.text:0000000180123C95         mov     r13, rdx
.text:0000000180123C98         wbinvd
.text:0000000180123C9A         sub     rax, rax
.text:0000000180123C9D         mov     ss, ax
.text:0000000180123CA0         mov     rsp, cs:OslArchKernelStack
.text:0000000180123CA7         lea     rax, OslArchKernelGdt
.text:0000000180123CAE         lea     rcx, OslArchKernelIdt
.text:0000000180123CB5         lgdt    fword ptr [rax]
.text:0000000180123CB8         lidt    fword ptr [rcx]
.text:0000000180123CBB         mov     rax, cr4
.text:0000000180123CBE         or      rax, 680h
.text:0000000180123CC4         mov     cr4, rax
.text:0000000180123CC7         mov     rax, cr0
.text:0000000180123CCA         or      rax, 50020h
.text:0000000180123CD0         mov     cr0, rax
.text:0000000180123CD3         xor     ecx, ecx
.text:0000000180123CD5         mov     cr8, rcx
.text:0000000180123CD9         mov     ecx, 0C0000080h
.text:0000000180123CDE         rdmsr
.text:0000000180123CE0         or      rax, cs:OslArchEferFlags
.text:0000000180123CE7         wrmsr
.text:0000000180123CE9         mov     eax, 40h
.text:0000000180123CEE         ltr     ax
.text:0000000180123CF1         mov     ecx, 2Bh
.text:0000000180123CF6         mov     gs, ecx
.text:0000000180123CF8         assume gs:nothing
.text:0000000180123CF8         mov     rcx, r12
.text:0000000180123CFB         push    rsi
.text:0000000180123CFC         push    10h
.text:0000000180123CFE         push    r13
.text:0000000180123D00         retfq
.text:0000000180123D00 OslArchTransferToKernel endp
```
