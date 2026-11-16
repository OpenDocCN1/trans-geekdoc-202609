# Mac OS X

This is a Mac OS X / GDB counterpart to Divide by Zero (user mode) described for Windows platforms (page 259):

```
(gdb) bt
#0 0x000000010d3ebe9e in bar (a=1, b=0)
#1 0x000000010d3ebec3 in foo ()
#2 0x000000010d3ebeeb in main (argc=1, argv=0x7fff6cfeab18)

(gdb) x/i 0x000000010d3ebe9e
0x10d3ebe9e : idiv %esi

(gdb) info r rsi
rsi 0x0 0
```

The modeling application source code:

```
int bar(int a, int b)
{
    return a/b;
}

int foo()
{
    return bar(1,0);
}

int main(int argc, const char * argv[])
{
    return foo();
}
```