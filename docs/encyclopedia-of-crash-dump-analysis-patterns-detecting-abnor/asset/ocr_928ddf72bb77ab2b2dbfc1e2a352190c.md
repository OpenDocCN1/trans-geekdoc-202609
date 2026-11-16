# Comments

# Another example:

```
4: kd> !chkimg -lo 50 -d !nt
8083351c-80833520  5 bytes - nt!NtYieldExecution
 [ 8b ff 55 8b ec:e9 5c 03 e6 73 ]
808345d0-808345d3  4 bytes - nt!KiServiceTable+440 (+0x10b4)
 [ 9c c2 8b 80:5c d7 f1 f4 ]
808eeb1e-808eeb22  5 bytes - nt!NtCreateFile
 [ 8b ff 55 8b ec:e9 1c 4d da 73 ]
809233b0-809233b4  5 bytes - nt!NtUnmapViewOfSection (+0x34892)
 [ 8b ff 55 8b ec:e9 f2 04 d4 77 ]
8092d3ae-8092d3b4  7 bytes - nt!NtMapViewOfSection (+0x9ffe)
 [ 6a 38 68 8b 41 80 80:e9 de 64 d6 73 90 90 ]
80931c90-80931c96  7 bytes - nt!NtProtectVirtualMemory (+0x48e2)
 [ 6a 44 68 8b 43 80 80:e9 1b d6 73 90 90 ]
8094af32-8094af36  5 bytes - nt!NtCreateProcess (+0x192a2)
 [ 8b ff 55 8b ec:e9 32 89 d4 73 ]
8094c714-8094c718  5 bytes - nt!NtTerminateProcess (+0x17e2)
 [ 8b ff 55 8b ec:e9 12 71 d4 73 ]
43 errors : !nt (8083351c-8094c718)
4: kd> u 8094af32
nt!NtCreateProcess:
*** ERROR: Symbol file could not be found. Defaulted to export symbols for 3rdPartyAVDriver.sys -
8094af32 e93289d473      jmp     3rdPartyAVDriver+0x13869 (f4693869)
8094af37 3c3c xor     eax,eax
8094af39 f6451c01 test    byte ptr [ebp+1Ch],1
8094af3d 7401 je       nt!NtCreateProcess+0xe (8094af40)
8094af3f 40 inc     eax
8094af40 f6452001 test    byte ptr [ebp+20h],1
8094af44 7403 je       nt!NtCreateProcess+0x17 (8094af49)
8094af46 83c802 or      eax,2
```

The simplified version of the command:

```
!chkimg -db -v ModuleName
```

For example:

```
!chkimg -db -v nt
```

This allows to use !for_each_module command

To include the mismatch summary use this simplified version of the command:

```
!chkimg -db -d -v ModuleName
```

For example:

```
!chkimg -db -d -v ntdll
```