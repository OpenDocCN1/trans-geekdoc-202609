We see that the tag is DRIV, and we know either from the association or from similar problems in the past that it belongs to driver.sys. Let's dump our pool entry contents to see if there are any symbolic hints in it:

```
1: kd> dps a34583b8
a34583b8 0a270001
a34583bc 5346574e
a34583c0 00000000
a34583c4 00000000
a34583c8 b958f532 driver+0x36532
a34583cc a3471010
a34583d0 0000012e
a34583d4 00000001
a34583d8 00041457
a34583dc 05af0026
a34583e0 00068002
a34583e4 7b9ce6f5
a34583e8 fffffff0
a34583ec 73650cff
a34583f0 7461445c
a34583f4 97a10061
a34583f8 ff340004
a34583fc c437862a
a3458400 6a000394
a3458404 00000038
a3458408 00000000
a345840c bf000000
a3458410 bf0741b5
a3458414 f70741b5
a3458418 00000000
a345841c 00000000
a3458420 00000000
a3458424 00000000
a3458428 05000000
a345842c 34303220
a3458430 31323332
a3458434 ff322d36
```

Indeed we see that the possible code pointer driver+0x36532 and the code around this address look normal:

```
3: kd> .asm no_code_bytes
Assembly options: no_code_bytes

3: kd> u b958f532
driver+0x36532:
b958f532 push        2Ch
b958f534 push        offset driver+0x68d08 (b95c1d08)
b958f539 call        driver+0x65c50 (b95bec50)
b958f53e mov         byte ptr [ebp-19h],0
b958f542 and         dword ptr [ebp-24h],0
b958f546 call        dword ptr [driver+0x6f5fc (b95bef5c)]
b958f54c mov         ecx,dword ptr [ebp+0Ch]
b958f54f cmp         eax,ecx
```