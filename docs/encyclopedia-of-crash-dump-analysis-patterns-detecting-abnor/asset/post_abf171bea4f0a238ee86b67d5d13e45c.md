

We also see that 2 `conhost.exe` processes have identical physical to virtual mapping because their user space mappings are no longer valid (zeroed) and the `svchost.exe` process has user space mapping:

```
1: kd> !ptov 27a2f000
Amd64PtoV: pagedir 27a2f000
27a2f000 fffffffb`7dbed000
71530000 fffffffb`7dbee000
19d000 fffffffb`7dbef000
199000 fffffffb`7dbf0000
b6a40000 fffffffb`7dbf1000
b1f57000 fffffffb`7dbf2000
29c4000 fffffffb`7dbf3000
1c53000 fffffffb`7dbf5000
[...]
2e4d8000 ffffffa80`28f2d000
2c3d7000 ffffffa80`28f2e000
30ed6000 ffffffa80`28f2f000
2efd5000 ffffffa80`28f30000
2ded4000 ffffffa80`28f31000
2a5d3000 ffffffa80`28f32000
bb400000 ffffffa80`29600000 (large page)
bb200000 ffffffa80`29800000 (large page)
100000 ffffffff`ffd00000
105000 ffffffff`ffd01000
101000 ffffffff`ffd02000
102000 ffffffff`ffd03000
103000 ffffffff`ffd04000
104000 ffffffff`ffd05000
fec00000 ffffffff`ffd06000
1000 ffffffff`ffd07000
106000 ffffffff`ffd08000
123000 ffffffff`ffd09000
0 ffffffff`ffd0a000
124000 ffffffff`ffd0b000
2000 ffffffff`ffd0c000
e00c7000 ffffffff`ffd0d000
e0080000 ffffffff`ffd0e000
107000 ffffffff`ffd25000
108000 ffffffff`ffd26000
109000 ffffffff`ffd27000
10a000 ffffffff`ffd28000
10b000 ffffffff`ffd29000
10c000 ffffffff`ffd2a000
10d000 ffffffff`ffd2b000
10e000 ffffffff`ffd2c000
10f000 ffffffff`ffd2d000
110000 ffffffff`ffd2e000
111000 ffffffff`ffd2f000
112000 ffffffff`ffd30000
113000 ffffffff`ffd31000
114000 ffffffff`ffd32000
115000 ffffffff`ffd33000
116000 ffffffff`ffd34000
117000 ffffffff`ffd35000
118000 ffffffff`ffd36000
119000 ffffffff`ffd37000
11a000 ffffffff`ffd38000
11b000 ffffffff`ffd39000
11c000 ffffffff`ffd3a000
11d000 ffffffff`ffd3b000
11e000 ffffffff`ffd3c000
11f000 ffffffff`ffd3d000
120000 ffffffff`ffd3e000
121000 ffffffff`ffd3f000
122000 ffffffff`ffd40000
fee00000 ffffffff`ffe00000
```

```
1: kd> !ptov 37881000
Amd64PtoV: pagedir 37881000
37881000 ffffff6fb`7dbed000
8d482000 ffffff6fb`7dbee000
19d000 ffffff6fb`7dbef000
199000 ffffff6fb`7dbf0000
b6a04000 ffffff6fb`7dbf1000
b1f57000 ffffff6fb`7dbf2000
29c4000 ffffff6fb`7dbf3000
1c53000 ffffff6fb`7dbf5000
[...]
2e4d8000 ffffffa80`28f2d000
2c3d7000 ffffffa80`28f2e000
30ed6000 ffffffa80`28f2f000
2efd5000 ffffffa80`28f30000
2ded4000 ffffffa80`28f31000
2a5d3000 ffffffa80`28f32000
b4000000 ffffffa80`29600000 (large page)
bb200000 ffffffa80`29800000 (large page)
100000 ffffffff`ffd00000
105000 ffffffff`ffd01000
101000 ffffffff`ffd02000
102000 ffffffff`ffd03000
103000 ffffffff`ffd04000
104000 ffffffff`ffd05000
fec00000 ffffffff`ffd06000
1000 ffffffff`ffd07000
106000 ffffffff`ffd08000
123000 ffffffff`ffd09000
0 ffffffff`ffd0a000
124000 ffffffff`ffd0b000
2000 ffffffff`ffd0c000
e00c7000 ffffffff`ffd0d000
e0080000 ffffffff`ffd0e000
107000 ffffffff`ffd25000
108000 ffffffff`ffd26000
109000 ffffffff`ffd27000
10a000 ffffffff`ffd28000
10b000 ffffffff`ffd29000
10c000 ffffffff`ffd2a000
10d000 ffffffff`ffd2b000
10e000 ffffffff`ffd2c000
10f000 ffffffff`ffd2d000
110000 ffffffff`ffd2e000
111000 ffffffff`ffd2f000
112000 ffffffff`ffd30000
113000 ffffffff`ffd31000
114000 ffffffff`ffd32000
115000 ffffffff`ffd33000
116000 ffffffff`ffd34000
117000 ffffffff`ffd35000
118000 ffffffff`ffd36000
119000 ffffffff`ffd37000
11a000 ffffffff`ffd38000
11b000 ffffffff`ffd39000
11c000 ffffffff`ffd3a000
11d000 ffffffff`ffd3b000
11e000 ffffffff`ffd3c000
11f000 ffffffff`ffd3d000
120000 ffffffff`ffd3e000
121000 ffffffff`ffd3f000
122000 ffffffff`ffd40000
fee00000 ffffffff`ffe00000
```

```
1: kd> !ptov 9d35a000
Amd64PtoV: pagedir 9d35a000
9E587000 10000
6871E000 20000
AF5AA000 30000
AF5AB000 31000
AFAAC000 32000
AFBAD000 33000
AF2F5000 40000
9D66B000 50000
22199000 60000
9D962000 E5000
9D261000 E6000
9DC60000 E7000
9D256000 EA000
9D84F000 EB000
9E4EC000 EC000
9E081000 ED000
9D876000 EE000
9E271000 EF000
B8BFD000 F0000
B8EFE000 F1000
B86FF000 F2000
B5302000 F3000
B5202000 F4000
B5502000 F5000
B7F03000 F6000
B8404000 F7000
B8415000 100000
B8816000 101000
B1B17000 102000
[...]
2CD4000 77512000
5D7000 77515000
5D8000 77516000
4D9000 77517000
B358F000 77590000
AEF04000 77591000
68624000 77592000
64B26000 77593000
4F4C6000 77595000
B2042000 7EFE0000
B2143000 7EFE1000
B1A56000 7EFE2000
B1A57000 7EFE3000
B1B58000 7EFE4000
1AA000 7FFE0000
9DA69000 BFE80000
AEAE0000 FFEA0000
AF191000 FFEA1000
9D76A000 FFEA2000
AE793000 FFEA3000
9DC8E000 FFEA5000
B7EB7000 FFEA6000
9DFFC000 FFEA7000
[...]
2e4d8000 fffffa80`28f2d000
2c3d7000 fffffa80`28f2e000
30ed6000 fffffa80`28f2f000
2efd5000 fffffa80`28f30000
2ded4000 fffffa80`28f31000
2a5d3000 fffffa80`28f32000
bb400000 fffffa80`29600000 (large page)
bb200000 fffffa80`29800000 (large page)
100000 ffffffff`ffd00000
105000 ffffffff`ffd01000
101000 ffffffff`ffd02000
102000 ffffffff`ffd03000
103000 ffffffff`ffd04000
104000 ffffffff`ffd05000
fec00000 ffffffff`ffd06000
1000 ffffffff`ffd07000
106000 ffffffff`ffd08000
123000 ffffffff`ffd09000
0 ffffffff`ffd0a000
124000 ffffffff`ffd0b000
2000 ffffffff`ffd0c000
e00c7000 ffffffff`ffd0d000
e0080000 ffffffff`ffd0e000
107000 ffffffff`ffd25000
108000 ffffffff`ffd26000
109000 ffffffff`ffd27000
10a000 ffffffff`ffd28000
10b000 ffffffff`ffd29000
10c000 ffffffff`ffd2a000
10d000 ffffffff`ffd2b000
10e000 ffffffff`ffd2c000
10f000 ffffffff`ffd2d000
110000 ffffffff`ffd2e000
111000 ffffffff`ffd2f000
112000 ffffffff`ffd30000
113000 ffffffff`ffd31000
114000 ffffffff`ffd32000
115000 ffffffff`ffd33000
116000 ffffffff`ffd34000
117000 ffffffff`ffd35000
118000 ffffffff`ffd36000
119000 ffffffff`ffd37000
11a000 ffffffff`ffd38000
11b000 ffffffff`ffd39000
11c000 ffffffff`ffd3a000
11d000 ffffffff`ffd3b000
11e000 ffffffff`ffd3c000
11f000 ffffffff`ffd3d000
120000 ffffffff`ffd3e000
121000 ffffffff`ffd3f000
122000 ffffffff`ffd40000
fee00000 ffffffff`fffe0000
```

In order to check user space virtual addresses we have to switch to the corresponding process context:

```
1: kd> !pte fffffa80`28f2d000
VA fffffa8028f2d000
PXE at FFFFF6FB7BDEDF88  PPE at FFFFF6FB7DBF5000  PDE at FFFFF6FB7EA00A38  PTE at FFFFF6FD40147968
contains 0000000001C54863  contains 0000000049320863  contains 000000002E4D8963
pfn 1c53  -DA--KWEV  pfn 1c54  -DA--KWEV  pfn 49320  -DA--KWEV  pfn 2e4d8  -G-DA--KWEV

1: kd> .process /r /p fffffa8026bd6f0
Implicit process is now fffffa80`26bd6f0
Loading User Symbols

1: kd> !pte 10000
VA 0000000000010000
PXE at FFFFF6FB7BDED000  PPE at FFFFF6FB7DA00000  PDE at FFFFF6FB40000000  PTE at FFFFF68000000080
contains 03C000009DD62867  contains 031000009D865867  contains 7C2000009DD6867  contains 9CB000009E587867
pfn 9dd62  -DA--UWEV  pfn 9d865  -DA--UWEV  pfn 9dd66  -DA--UWEV  pfn 9e587  -DA-UW-V
```

This pattern came to our attention after seeing memory dumps generated after the growing number of memory allocated for page tables exceeded a gigabyte.

## Process Heap

Memory Leak is another pattern that may be finally manifested as **Insufficient Memory** pattern (page 523) in a crash dump. Here we cover process heap memory leaks. They are usually identified when the process virtual memory size grows over time. It starts with 80Mb and instead of fluctuating normally below 100Mb it suddenly starts growing to 150Mb after some time and then to 300Mb the next day and then grows to 600Mb, and so on.

Usually, a process heap is under suspicion here. To confirm this, we need to sample 2-3 consecutive user memory dumps at process sizes 100Mb, 200Mb, and 300Mb, for example. This can be done by using Microsoft userdump.exe command line tool. Then we can see whether there is any heap growth by using `!heap -s` WinDbg command:

### 1st dump

| Heap | Flags | Reserv (k) | Commit (k) | Virt (k) |
|------|-------|------------|------------|----------|
| 00140000 | 00000002 | 2048 | 1048 | 1112 |
| 00240000 | 00008000 | 64 | 12 | 12 |
| 00310000 | 00001002 | 7232 | 4308 | 4600 |
| 00420000 | 00001002 | 1024 | 520 | 520 |
| 00340000 | 00001002 | 256 | 40 | 40 |
| 00720000 | 00001002 | 64 | 32 | 32 |
| 00760000 | 00001002 | 64 | 48 | 48 |
| 01020000 | 00001002 | 256 | 24 | 24 |
| 02060000 | 00001002 | 64 | 16 | 16 |
| 02070000 | 00001003 | 256 | 120 | 120 |
| 020b0000 | 00001003 | 256 | 4 | 4 |
| 020f0000 | 00001003 | 256 | 4 | 4 |
| 02130000 | 00001003 | 256 | 4 | 4 |
| 02170000 | 00001003 | 256 | 4 | 4 |
| 021f0000 | 00001002 | 1088 | 76 | 76 |
| 021e0000 | 00001002 | 64 | 16 | 16 |
| 02330000 | 00001002 | 1088 | 428 | 428 |
| 02340000 | 00001102 | 256 | 12 | 12 |
| 02380000 | 00001002 | 64 | 12 | 12 |
| 024c0000 | 00001003 | 64 | 8 | 8 |
| 028d0000 | 00001002 | 7232 | 3756 | 6188 |
| 02ce0000 | 00001003 | 64 | 8 | 8 |
| 07710000 | 00001002 | 64 | 20 | 20 |
| 07b20000 | 00001002 | 64 | 16 | 16 |
| 07f30000 | 00001002 | 64 | 16 | 16 |
| 09950000 | 00001002 | 256 | 12 | 12 |
| 09c80000 | 00001002 | 130304 | 102340 | 102684 |
| 007d0000 | 00001003 | 256 | 192 | 192 |
| 00810000 | 00001003 | 256 | 4 | 4 |
| 0bdd0000 | 00001003 | 256 | 4 | 4 |
| 0be10000 | 00001003 | 256 | 4 | 4 |
| 0be50000 | 00001003 | 256 | 4 | 4 |
| 0be90000 | 00001003 | 256 | 56 | 56 |
| 0bed0000 | 00001003 | 256 | 4 | 4 |

