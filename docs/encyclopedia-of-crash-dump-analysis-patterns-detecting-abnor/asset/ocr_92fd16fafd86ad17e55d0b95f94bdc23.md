```
nt!KiTrap08:
8088ab72 fa           cli
```

```
5: kd> .asm no_code_bytes
Assembly options: no_code_bytes
```

```
5: kd> uf nt!KiTrap08
nt!KiTrap08:
8088ab72 cli
8088ab73 mov eax,dword ptr fs:[00000040h]
8088ab79 mov ecx,dword ptr fs:[124h]
8088ab80 mov edi,dword ptr [ecx+38h]
8088ab83 mov ecx,dword ptr [edi+18h]
8088ab86 mov dword ptr [eax+1Ch],ecx
8088ab89 mov cx,word ptr [edi+30h]
8088ab8d mov word ptr [eax+66h],cx
8088ab91 mov ecx,dword ptr [edi+20h]
8088ab94 test ecx,ecx
8088ab96 je nt!KiTrap08+0x2a (8088ab9c)
```

```
nt!KiTrap08+0x26:
8088ab98 mov cx,48h
```

```
nt!KiTrap08+0x2a:
8088ab9c mov word ptr [eax+60h],cx
8088aba0 mov ecx,dword ptr fs:[3Ch]
8088aba7 lea eax,[ecx+50h]
8088abaa mov byte ptr [eax+5],89h
8088abae pushfd
8088abaf dword ptr [esp],0FFFFFFFh
8088abb6 popfd
8088abb7 mov eax,dword ptr fs:[0000003Ch]
8088abbd mov ch,byte ptr [eax+57h]
8088abc0 mov cl,byte ptr [eax+54h]
8088abc3 shl ecx,10h
8088abc6 mov cx,word ptr [eax+52h]
8088abca mov eax,dword ptr fs:[00000040h]
8088abd0 mov dword ptr fs:[40h],ecx
```

```
nt!KiTrap08+0x65:
8088abd7 push 0
8088abd9 push 0
8088abdb push 0
8088abdd push eax
8088abde push 8
8088abe0 push 7Fh
8088abe2 call nt!KeBugCheck2 (80826a92)
8088abe7 jmp nt!KiTrap08+0x65 (8088abd7)
```