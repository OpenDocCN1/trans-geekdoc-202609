# 20.1 Digital Signature Algorithm (DSA)

# Table 20.3

# Comparison of RSA and DSA Computation Times

| | DSA | RSA | DSA with Common p, q, g |
|---|---|---|---|n| Global Computations | Off-card (P) | N/A | Off-card (P) |
| Key Generation | 14 sec | Off-card (S) | 4 sec |
| Precomputation | 14 sec | N/A | 4 sec |
| Signature | .03 sec | 15 sec | .03 sec |
| Verification | 16 sec | 1.5 sec | 10 sec |
1-5 sec off-card (P) |

Off-card computations were performed on 80386 33 MHz, personal computer. [P] indicates public parameters off-card and [S] indicates parameters off-card. Both algorithms use 512-bit modulus.

long, some multiple of 64 bits. The prime q is 160 bits long. $L-1 = 160n+b$, where $L$ is the length of $p$, and $n$ are two numbers and $b$ is less than 160.

+   (1) Choose an arbitrary sequence of at least 160 bits and call it $S$. Let $g$ be the length of $S$ in bits.
(2) Choose $U = 	ext{SHA}[S] \oplus [S+1] \pmod{2^g}$; SHA is the Secure Hash Algorithm (see Section 18.7).
n(3) Form $q$ by setting the most significant bit and the least significant bit of $U$ to 1.
(4) Check whether $q$ is prime.
(5) If $q$ is not prime, go back to step (1).
(6) Let $C=0$ and $N=2$.
(7) For $k=0, 1, \dots, n$, $V_k = 	ext{SHA}\{[S+k] \pmod{2^g}\}$
(8) Let $W$ be the integer
W$W = V_0 + 2^{160}V_1 + \dots + 2^{160(n-1)}V_{n-1} + 2^{160n}V_n$
and
W$X = W+2^{L-1}$
That $X$ is an $L$-bit number.
(9) Let $p = X-[X \pmod{2q}] - 1$. Note that $p$ is congruent to $1 \pmod{2q}$.n(10) If $p < 2^{L-1}$, then go to step (13).
(11) Check whether $p$ is prime.
(12) If $p$ is prime, go to step [15).
(13) Let $C = C+1$ and $N = N+n+1$.