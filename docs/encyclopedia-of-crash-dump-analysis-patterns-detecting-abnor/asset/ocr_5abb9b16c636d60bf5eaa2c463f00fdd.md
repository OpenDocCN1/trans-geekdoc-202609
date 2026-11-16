```
61e84410 i.o.n...P.r.o.f.
61e84420 e.s.s.i.o.n.a.l.
61e84430 .V.e.r.s.i.o.n.
61e84440 ..2.1 ..B.u.i.
61e84450 l.d._.2.1.0....
61e84460 D...V.a.r.F.i.
...
...
...
```

```
0:000> du 61e843a0+C
61e843ac "Microsoft Research Detours Packa"
61e843ec "ge"
```

We can also see that 3rdPartyHook module imports this library and lots of kernel32 API related to memory allocation, file mapping and loading DLLs (see No Component Symbols pattern, page 734):

```
0:000> !dh 60000000
...
...
...
OPTIONAL HEADER VALUES
 10B magic #
 8.00 linker version
 18000 size of code
 F000 size of initialized data
 0 size of uninitialized data
 13336 address of entry point
 1000 base of code
 ---- new ----
60000000 image base
 1000 section alignment
 1000 file alignment
 2 subsystem (Windows GUI)
 4.00 operating system version
 0.00 image version
 4.00 subsystem version
29000 size of image
 1000 size of headers
 3376F checksum
00100000 size of stack reserve
00001000 size of stack commit
00100000 size of heap reserve
00001000 size of heap commit
 0 [ 0] address [size] of Export Directory
218C [ 8C] address [size] of Import Directory
2500 [ 5F4] address [size] of Resource Directory
 0 [ 0] address [size] of Exception Directory
28000 [ 19E0] address [size] of Security Directory
26000 [ 2670] address [size] of Base Relocation Directory
19320 [ 1C] address [size] of Debug Directory
 0 [ 0] address [size] of Description Directory
 0 [ 0] address [size] of Special Directory
 0 [ 0] address [size] of Thread Storage Directory
1F3C0 [ 40] address [size] of Load Configuration Directory
 0 [ 0] address [size] of Bound Import Directory
```