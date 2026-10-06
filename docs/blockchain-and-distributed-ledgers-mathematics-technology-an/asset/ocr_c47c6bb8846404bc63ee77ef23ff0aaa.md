# Chapter 4 Essential Cryptographic Tools | 133

message is divided into chunks of 512-bit blocks, viewed as 16 32-bit words. If the need occurs, the message is padded so that its length is divisible by 512. When processing the first 512-bit input, the output is initialized to a set of eight 32-bit initial values. When processing subsequent 512-bit inputs, the output is initialized to the set of four 32-bit values.
obobtained from the previous calculations.

Thus, it is enough to understand how 512-bit input is transferred to a 128-bit hash. The input is divided into 16 32-bit words, by $W_0, ..., W_{15}$. The set of 16 words in expanded to the set of 64 words $M_{i,j}$, $1 \leq i \leq 4, 0 \leq j \leq 15$, according to the following rule:

```
$M_{1,j} = W_j, M_{2,j} = W_k, k = (Sj + 1) \pmod{16},
```

```
$W_{3,j} = W_k, k = (3j + 5) \pmod{16}, W_{4,j} = W_k, k = 7j \pmod{16}$
(4.1773)
```

Since there are 64 words, there are 64 rounds. The flowchart for MD5 is shown in Figure 4.18.
The transformation of a message block consists of four stages or rounds. Each round is composed of 16 similar sub-rounds using every one of 16 sub-messages; they rely on non-linear functions $F_1, ..., F_4$ operating on bits as follows:

```
$F_1(B, C, D) = (B \wedge C) \vee (B \wedge D), F_2(B, C, D) = (B \wedge D) \vee (C \wedge D)$
(4.1774)
```

```
$F_3(B, C, D) = B \oplus C \oplus D, F_4(B, C, D) = C \oplus (B \vee D)$
```

Here, $\wedge, \vee, \oplus$ are XOR, OR, NOT bitwise operations.

![](bbox=[0.145, 0.617, 0.831, 0.883])

**Figure 4.18** Flow chart for MD5. Own graphics. Source: Wikipedia.