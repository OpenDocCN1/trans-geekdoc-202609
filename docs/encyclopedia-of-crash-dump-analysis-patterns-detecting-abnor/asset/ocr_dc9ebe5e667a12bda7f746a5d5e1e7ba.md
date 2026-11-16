```
nt!KiIdleLoop+0x24:
8088d27c mov     cl,2
8088d27e call    dword ptr [nt!_imp_HalClearSoftwareInterrupt (808010a8)]
8088d284 lea     ecx,[ebx+120h]
8088d28a call    nt!KiRetireDpcList (80831be8)

nt!KiIdleLoop+0x37:
8088d28f cmp     dword ptr [ebx+128h],0
8088d296 je      nt!KiIdleLoop+0xca (8088d322)

nt!KiIdleLoop+0x44:
8088d29c mov     ecx,1Bh
8088d2a1 call    dword ptr [nt!_imp_KfRaiseIrql (80801100)]
8088d2a7 sti
8088d2a8 mov     edi,dword ptr [ebx+124h]
8088d2ae mov     byte ptr [edi+5Dh],1
8088d2b2 lock bts dword ptr [ebx+0A7Ch],0
8088d2bb jae     nt!KiIdleLoop+0x70 (8088d2c8)

nt!KiIdleLoop+0x65:
8088d2bd lea     ecx,[ebx+0A7Ch]
8088d2c3 call    nt!KefAcquireSpinLockAtDpcLevel (80887fd0)

nt!KiIdleLoop+0x70:
8088d2c8 mov     esi,dword ptr [ebx+128h]
8088d2ce cmp     esi,edi
8088d2d0 je      nt!KiIdleLoop+0xb3 (8088d30b)

nt!KiIdleLoop+0x7a:
8088d2d2 and     dword ptr [ebx+128h],0
8088d2d9 mov     dword ptr [ebx+124h],esi
8088d2df mov     byte ptr [esi+4Ch],2
8088d2e3 and     byte ptr [ebx+0AA3h],0
8088d2ea and     dword ptr [ebx+0A7Ch],0

nt!KiIdleLoop+0x99:
8088d2f1 mov     ecx,1
8088d2f6 call    nt!SwapContext (8088d040)
8088d2fb mov     ecx,2
8088d300 call    dword ptr [nt!_imp_KfLowerIrql (80801104)]
8088d306 jmp     nt!KiIdleLoop+0xa (8088d262)

nt!KiIdleLoop+0xb3:
8088d30b and     dword ptr [ebx+128h],0
8088d312 and     dword ptr [ebx+0A7Ch],0
8088d319 and     byte ptr [edi+5Dh],0
8088d31d jmp     nt!KiIdleLoop+0xa (8088d262)

nt!KiIdleLoop+0xca:
8088d322 cmp     byte ptr [ebx+0AA3h],0
8088d329 je      nt!KiIdleLoop+0x2 (8088d25a)
```