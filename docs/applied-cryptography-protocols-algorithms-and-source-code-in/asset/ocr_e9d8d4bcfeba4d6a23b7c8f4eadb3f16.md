# 18.5 MD5

![](bbox=[0.137, 0.098, 0.862, 0.433])

on three of $a, b, c$, and $d$. It adds that result to the fourth variable, a sub-block of the text and a constant. It rotates that result to the right variable of bits and adds the result to one of $a, b, c$, or $d$. Finally the result replaces one of $a, b, c$, or $d$. See Figures 18.5 and 18.6.

There are four nonlinear functions, used in each operation (a one for each round).

$\oplus$ is XOR, $\wedge$ is AND, $\vee$ is OR, and $
eg$ is NOT.\ These functions are designed so that the corresponding bits of X, Y, and Z are independent and unbiased, and each bit of the result will be independent and unbiased. The function $F$ is the bit-wise conditional: If X then $Y$ else $Z$. The function $H$ is the bit-wise conditional.

If $M$ represents the $i$th sub-block of the message (from 0 to 15), and $<<<$ represents a left circular shift of $s$ bits, the four operations are:

```
FF(a,b,c,d,M,s,t) denotes $a = b + ((a + F(b,c,d) + M_i) + t_i) <<< s)$
GG(a,b,c,d,M,s,t) denotes $b = c + ((b + G(b,c,d) + M_i) + t_i) <<< s)$
HH(a,b,c,d,M,s,t) denotes $c = d + ((c + H(b,c,d) + M_i) + t_i) <<< s)$
II(a,b,c,d,M,s,t) denotes $d = a + ((d + I(b,c,d) + M_i) + t_i) <<< s)$
```