# 17.4 Feedback with Carry Shift Registers

101 1
010 1
001 1
000 1
100 0

Note the final internal state (including the contents of the carry register) is the same as the second internal state. The sequence cycles at this point, and has a period of 10.

There are a few things to note here. the first carry register is not a single bit; it is a number. The size of the carry register must be at least $t$, where $t$ is the number of taps. There are only two taps in the previous example, so the carry register only has to be 1 bit wide, and could be either 0, 1, or 3.

Second, there is an initial transient before the FCSR settles into its repeating period. In the previous example, only one state never repeated. For larger and more complicated FCSRs, there may be more.

Third, the maximum period of a FCSR is not $2^n - 1$, where $n$ is the length of the shift register. The maximum period is $q-1$, where $q$ is the connection integer. The number gives the taps and is defined by:

```
$q = q_1 + 2^{q_2} + 2^{q_4} + \dots + 2^{q_n} - 1$
```

{Yes, $q_s$ are numbered from left to right}. Even worse, $q$ has to be a prime for which 2 is a primitive root. The rest of this discussion assumes $q$ is of this form. In this example, $q = 2^0 + 4 \cdot 8 + 1 = 11$. 11 is a prime with 2 as a primitive root. The maximum period is 10.

Not all initial states give you the maximum period. for example, look at the FCSR when the initial value is 101 and the carry register is set to 4.

![](bbox=[0.136, 0.683, 0.568, 0.873])

Figure 17.4 3-bit FCSR.