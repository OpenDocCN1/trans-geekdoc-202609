In contrast to local variables are global variables, which have application throughout a program. Global variables are set using the “ ! ” symbol, an alias for SETV, and evaluated using the “ @ ” symbol, an alias for GETV. For example:

```
5 x !
x @ . ( emits 5 )
```

As you can see, local variables as defined above are more complex than global variables. Local variables also require relatively more system resources, which is one reason Forth founder Chuck Moore tries to avoid their use.2

# B.12 EPOP WORD SUMMARY

More than two-hundred epop word definitions are described in the epop Syntax Reference, on the web at https://sherpa.systemgoats.com.

2Source: https://www.ultratechnology.com/moore4th.htm