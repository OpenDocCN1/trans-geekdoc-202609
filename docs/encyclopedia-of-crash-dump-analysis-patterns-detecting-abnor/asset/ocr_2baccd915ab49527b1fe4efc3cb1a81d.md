# Comments

One of the readers sent us this program and corresponding WinDbg output:

```
void func1(void);

void __cdecl main(void)
{
    func1();
}

void func1(void)
{
    func1();
}

0:000> .lastevent
Last event: d0c.e94: Stack overflow - code c00000fd (first chance)

0:000> k L50
ChildEBP RetAddr
00103000 002a1e88 test!func1+0x3
00103008 002a1e88 test!func1+0x8
00103010 002a1e88 test!func1+0x8
00103018 002a1e88 test!func1+0x8
...

0:000> !teb
TEB at 7ffdf000
ExceptionList: 001ffa1c
StackBase: 00200000
StackLimit: 00101000
...

0:000>dds 101000 200000
...[ebp][ret addr]... mainframe...
001ff9d4 002a1e88 test!func1+0x8
001ff9d8 001ff9e0
001ff9dc 002a1e88 test!func1+0x8
001ff9e0 001ff9e8
001ff9e4 002a1f8 test!main+0x8
001ff9e8 001ffa2c
001ff9ec 002a1174 test!__mainCRTStartup+0x122
001ff9f0 00000001
001ff9f4 00551388
001ff9f8 00651928
001ff9fc bc2792b1
001ffa00 00000000
001ffa04 00000000
001ffa08 7ffdc000
001ffa0c 00000000
001ffa10 00000000
001ffa14 001ff9fc
```