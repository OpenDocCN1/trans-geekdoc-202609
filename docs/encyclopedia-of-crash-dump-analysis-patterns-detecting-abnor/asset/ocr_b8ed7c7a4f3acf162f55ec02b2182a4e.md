# Broken Link

Sometimes we have a broken linked list for some reason, either from memory corruption, **Lateral Damage** (page 602) or **Truncated Dump** (page 1015). For example, an active process list enumeration stopped after showing some processes (**!for_each_thread** and **!vm** also don't work):

```
0: kd> !process 0 3f

[...]

TYPE mismatch for process object at fffffffa80041da5c0

0: kd> !validatelist nt!PsActiveProcessHead
Blink at address fffffffa80041da748 does not point back to previous at fffffffa8005bc8c8b
```

Here we can either try to repair or navigate links manually or use other means such as dumping pool allocations for process structures with _Proc_ pool tag:

```
0: kd> !poolfind Proc

Searching NonPaged pool (fffffa80032fc000 : ffffffe000000000) for Tag: Proc

*fffffa80033879a0 size: 510 previous size: a0 (Allocated) Proc (Protected)
*fffffa80033ffad0 size: 530 previous size: 280 (Allocated) Proc (Protected)
*fffffa80041a2af0 size: 510 previous size: 90 (Allocated) Proc (Protected)
*fffffa8004395c50 size: 530 previous size: 80 (Allocated) Proc (Protected)
[...]
*fffffa8007475ad0 size: 530 previous size: 30 (Allocated) Proc (Protected)
*fffffa80074e8490 size: 530 previous size: 100 (Allocated) Proc (Protected)
*fffffa80075eeb00 size: 530 previous size: b0 (Free) Pro.
*fffffa800761d000 size: 530 previous size: 0 (Free) Pro.
*fffffa8007645ad0 size: 530 previous size: b0 (Allocated) Proc (Protected)

0: kd> dc fffffffa8007645ad0
fffffa80`07645ad0 0253000b e36f7250 07644030 fffffa80 ...S.Pro.0.d......
fffffa80`07645ae0 00001000 00000528 00000068 ffffff80 .....(.h.......
fffffa80`07645af0 011a940 fffff800 00080090 00490024 @..........$I.
fffffa80`07645b00 000000c4 00000000 00000008 00000000 ................
fffffa80`07645b10 00000000 00000000 00080007 00300033 .........3.0..
fffffa80`07645b20 011a940 fffff800 013cfeae fffff8a0 @.......<.....
fffffa80`07645b30 00580003 00000000 05ba19a0 fffffa80 ..X...........
fffffa80`07645b40 05ba19a0 fffffa80 07645b48 fffffa80 .....H[d......
```