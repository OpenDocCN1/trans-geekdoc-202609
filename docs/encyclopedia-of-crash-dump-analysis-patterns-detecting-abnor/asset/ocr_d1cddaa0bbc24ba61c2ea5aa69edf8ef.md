# Comments

We can get distribution stats for different block sizes and then filter all stack traces based on the specific size we are interested in:

```
0:001> !heap -stat -h 06a00000
heap @ 06a00000
group-by: TOTSIZE max-display: 20
size #blocks total ( %) (percent of total busy bytes)
240 13eb9 - 31cce80 (40.67)
48 2a813 - bf4558 (9.76)
88 14213 - ab1a18 (8.73)
28 2a6a1 - 6a0928 (5.41)
4 187062 - 61c188 (4.99)
30 1e140 - 5a3c00 (4.61)
53218d 1 - 53218d (4.24)
50 fa85 - 4e4990 (4.00)
39d2d4 1 - 39d2d4 (2.95)
c 3592b - 282e04 (2.05)
3c 9591 - 230dfc (1.79)
b8 2b2b - 1f06e8 (1.58)
9c 31a9 - 1e42fc (1.54)
70 3592 - 176fe0 (1.20)
3ec 5dc - 16fad0 (1.17)
33c 5dc - 12f390 (0.97)
14 b4d5 - e20a4 (0.72)
20 6101 - c2020 (0.62)
6c 135e - 82a8a (0.42)
60 1082 - 630c0 (0.32)
```

```
0:001> !heap -flt s 240
[...]
1c6c0db8 0055 0055 [00] 1c6c0dd0 00240 - (busy)
? ModuleA!DllUnregisterServer+272c7c
1c6c1060 0055 0055 [00] 1c6c1070 00240 - (busy)
? ModuleA!DllUnregisterServer+272c7c
1c6c1308 0055 0055 [00] 1c6c1320 00240 - (busy)
? ModuleA!DllUnregisterServer+272c7c
1c6c15b0 0055 0055 [00] 1c6c15c8 00240 - (busy)
? ModuleA!DllUnregisterServer+272c7c
1c6c1858 0055 0055 [00] 1c6c1870 00240 - (busy)
[...]
```