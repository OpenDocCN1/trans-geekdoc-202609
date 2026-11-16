Inspection of the raw stack shows ASCII-like memory values around `foo` symbolic reference instead of expected `main` and `start` functions:

```
```(gdb) info r rsp
rsp 0x7fff656d79d8 0x7fff656d79d8
(gdb) x/100a 0x7fff656d79d8
0x7fff656d79d8: 0x7fff83288b6c <__abort+193> 0x0
0x7fff656d79e8: 0x0 <ffffffdff
0x7fff656d79f8: 0x7fff656d70a0 0x7fff656d7a00
0x7fff656d7a08: 0x7fff83285070 <__guard_setup> 0x6675426c61636f4c
0x7fff656d7a18: 0x7265764f7265666 0x0
0x7fff656d7a28: 0x0 0x0
0x7fff656d7a38: 0x0 0x73205d343336325b
0x7fff656d7a48: 0x65766f206b636174 0x776f6c66672
0x7fff656d7a58: 0x0 0x0
0x7fff656d7a68: 0x0 0x343336326d7ab0
0x7fff656d7a78: 0x0 0x7fff656d7ab0
0x7fff656d7a88: 0x105ad8f7 0xb1887b8452358ac4
0x7fff656d7a98: 0x794000000000000 0x67694422077654e20
0x7fff656d7aa8: 0x6666675420202000 0x7265
0x7fff656d7ab8: 0x0 0x0
0x7fff656d7ac8: 0x0 0x0
0x7fff656d7ad8: 0x0 0x0
0x7fff656d7ae8: 0x0 0x0
[...]```
```

The modeling application source code:

```
```void bar(char *buffer)
{
    char data[100] = "My New Bigger Buffer";
    memcpy (buffer, data, sizeof(data));
}

void foo()
{
    char data[10] = "My Buffer";
    bar(data);
}

int main(int argc, const char * argv[])
{
    foo();
    return 0;
}```
```