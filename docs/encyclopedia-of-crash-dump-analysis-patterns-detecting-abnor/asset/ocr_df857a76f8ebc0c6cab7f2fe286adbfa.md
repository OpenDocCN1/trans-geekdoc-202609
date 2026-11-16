# Wild Pointer

This pattern was briefly mentioned in Local Buffer Overflow (page 611) which shows examples of pointers having UNICODE structure in their values. We can also observe pointers with ASCII structure as .formats WinDbg command indicates:

```
FAILED_INSTRUCTION_ADDRESS:
 65747379`735c5357  ??
          ???
IP_ON_HEAP:  65747379735c5357
0:012> .formats rip
Evaluate expression:
  Hex:     65747379`735c5357
  Decimal: 7310595060592825175
  Octal:   0625643467456327051527
  Binary:  01100101 01110100 01110011 01110011 01110111 00110100 01011100 01010111
  Chars:   etsys\Sw
  Time:    Wed May 10 22:00:59.282 24767 (GMT+1)
  Float:   low 1.7456e+031 high 7.21492e+022
  Double:  5.30388e+180
```

Here is another example of a pointer having UNICODE structure:

```
FAILED_INSTRUCTION_ADDRESS:
 0045004c`00490046  ??
          ???
0:014> .formats rip
Evaluate expression:
  Hex:     0045004c`00490046
  Decimal: 19422099815333958
  Octal:   0010505004600022200106
  Binary:  00000000 01000101 00000000 01001100 00000000 01001001 00000000 01000110
  Chars:   ..E.L.I.F
  Time:    Wed Jul 19 07:46:21.533 1662 (GMT+1)
  Float:   low 6.70409e-039 high 6.33676e-039
  Double:  2.33646e-307
```

When we have EIP or RIP pointers, we have another pattern to name when the value coincidentally lies inside some valid region of memory: Wild Code (page 1148). Here is one example of the latter pattern:

```
IP_ON_STACK:
 +e11ffa8
STACK_TEXT:
 0e11ff7c 098eefe2 0xe11ffa8
 0e11ff84 77b6b530 dll1!StartWorking+0xcab
 0e11ffb8 7c826063 msvcrt!_endthreadex+0xa3
 0e11ffec 00000000 kernel32!BaseThreadStart+0x34
```