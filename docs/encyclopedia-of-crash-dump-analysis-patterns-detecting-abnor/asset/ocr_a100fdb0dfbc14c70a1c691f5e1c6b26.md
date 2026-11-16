# # User Mode

Stack Overflow pattern in user mode has its own characteristic exception code and stack trace:

```
FAULTING_IP:
StackOverflow!SoFunction+27
00401317 6a00 push 0

EXCEPTION_RECORD: fffffffd -- (.exr 0xffffffffffffffff)
ExceptionAddress: 00401300 (StackOverflow!SoFunction+0x00000010)
  ExceptionCode: c00000fd (Stack overflow)
  ExceptionFlags: 00000000
NumberParameters: 2
  Parameter[0]: 00000001
  Parameter[1]: 00882ffc

0:000> kL
ChildEBP RetAddr
00083000 00401317 StackOverflow!SoFunction+0x10
00083010 00401317 StackOverflow!SoFunction+0x27
00083020 00401317 StackOverflow!SoFunction+0x27
00083030 00401317 StackOverflow!SoFunction+0x27
00083040 00401317 StackOverflow!SoFunction+0x27
00083050 00401317 StackOverflow!SoFunction+0x27
00083060 00401317 StackOverflow!SoFunction+0x27
00083070 00401317 StackOverflow!SoFunction+0x27
00083080 00401317 StackOverflow!SoFunction+0x27
00083090 00401317 StackOverflow!SoFunction+0x27
000830a0 00401317 StackOverflow!SoFunction+0x27
000830b0 00401317 StackOverflow!SoFunction+0x27
000830c0 00401317 StackOverflow!SoFunction+0x27
000830d0 00401317 StackOverflow!SoFunction+0x27
000830e0 00401317 StackOverflow!SoFunction+0x27
000830f0 00401317 StackOverflow!SoFunction+0x27
00083100 00401317 StackOverflow!SoFunction+0x27
00083110 00401317 StackOverflow!SoFunction+0x27
00083120 00401317 StackOverflow!SoFunction+0x27
00083130 00401317 StackOverflow!SoFunction+0x27
```

There could be thousands of stack frames:

```
0:000> kL 2000
...
000a2fa0 00401317 StackOverflow!SoFunction+0x27
000a2fb0 00401317 StackOverflow!SoFunction+0x27
000a2fc0 00401317 StackOverflow!SoFunction+0x27
000a2fd0 00401317 StackOverflow!SoFunction+0x27
000a2fe0 00401317 StackOverflow!SoFunction+0x27
000a2ff0 00401317 StackOverflow!SoFunction+0x27
```