```
1: kd> x srv!memcpy
fffff980`0eafdf20  srv!memcpy = <no type information>

1: kd> x win32k!memcpy
fffff960`000c1b40  win32k!memcpy = <no type information>
```

Therefore, we see that when compiling for x86 platform Visual C++ compiler decided to inline memcpy code but AMD compiler on the x64 platform did not inline it. The overall stack trace without offsets is very similar, and we can suppose that the problem was identical.