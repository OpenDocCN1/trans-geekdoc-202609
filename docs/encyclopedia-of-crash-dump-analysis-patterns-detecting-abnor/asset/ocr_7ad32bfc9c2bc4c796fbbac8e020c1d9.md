```
0x00007fff8a31e772 <__dyld_stub_binder+105>: mov 0x30(%rsp),%rax
0x00007fff8a31e777 <__dyld_stub_binder+110>: add $0xc8,%rsp
0x00007fff8a31e77e <__dyld_stub_binder+117>: pop %rbp
0x00007fff8a31e77f <__dyld_stub_binder+118>: add $0x10,%rsp
0x00007fff8a31e783 <__dyld_stub_binder+122>: jmpq *%r11
```

```
(gdb) x/2i 0x7fff8fab9a9c
0x7fff8fab9a9c <abort+177>: mov $0x2710,%edi
0x7fff8fab9aa1 <abort+182>: callq 0x7fff8fab9c43 <usleep$nocancel>
```

```
(gdb) disass 0x7fff8fab9a9c-5 0x7fff8fab9a9c
Dump of assembler code from 0x7fff8fab9a97 to 0x7fff8fab9a9c:
0x00007fff8fab9a97 <abort+172>: callq 0x7fff8fb1f54a <dyld_stub_kill>
End of assembler dump.
```

```
(gdb) disass 0x7fff5fc01000
Dump of assembler code for function __dyld_stub_binding_helper:
0x00007fff5fc01000 <__dyld_stub_binding_helper+0>: add %al,(%rax)
0x00007fff5fc01002 <__dyld_stub_binding_helper+2>: add %al,(%rax)
0x00007fff5fc01004 <__dyld_stub_binding_helper+4>: add %al,(%rax)
0x00007fff5fc01006 <__dyld_stub_binding_helper+6>: add %al,(%rax)
End of assembler dump.
```

```
(gdb) x/10 0x7fff5fc01000-0x10
0x7fff5fc00ff0: 0x00000000 0x00000000 0x00000000 0x00000000
0x7fff5fc01000 <__dyld_stub_binding_helper>: 0x00000000 0x00000000 0x00000000 0x00000000
0x7fff5fc01010 <__dyld_offset_to_dyld_all_image_infos>: 0x00000000 0x00000000
```