# Comments

To check the correctness of some frames, we can use the same method as described in **Coincidental Symbolic Information** pattern (page 137). We use backward disassembly on a return address:

```
0286f430 690e6daa mshtml!CBase::PrivateInvokeEx+0x6d
WARNING: Stack unwind information not available. Following frames may be wrong.
0286f494 691f5fc5 jscript9!DllGetClassObject+0x18bb1

0:005> ub 690e6daa
jscript9!DllGetClassObject+0x18b9e:
690e6d97 ff7514 push dword ptr [ebp+14h]
690e6d9a ff7510 push dword ptr [ebp+10h]
690e6d9d 8b06 mov eax,dword ptr [esi]
690e6d9f 53 push ebx
690e6da0 ff75ec push dword ptr [ebp-14h]
690e6da3 ff7508 push dword ptr [ebp+8]
690e6da6 56 push esi
690e6da7 ff5020 call dword ptr [eax+20h]
```