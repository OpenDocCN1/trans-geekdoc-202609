![](bbox=[0.134, 0.118, 0.563, 0.26])

Figure 17.9 is a 3-bit shift register with the following feedback function: The new bit is the first bit times the second bit. If it is initialized with the value 110, it produces the following sequence of internal states:

```
110
011
101
010
001
000
000
```

And so on forever.
The output sequence is the string of least significant bits:
011010000000....

# 17.7 OTHER STREAM CIPHERS

Many other stream ciphers have appeared in the literature here and there. Here are some of them.

Pless Generator

This generator is designed around the capabilities of the J-K flip-flop [1250]. Eight LFSRs drive four J-K flip-flops; each flip-flop acts as a nonlinear combiner for two ,