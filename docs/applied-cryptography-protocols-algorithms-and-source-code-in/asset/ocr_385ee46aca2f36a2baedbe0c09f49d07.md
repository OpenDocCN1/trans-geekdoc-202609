# 14.8 RC5

For $i = 1$ to $r$:

```
A = (\|A \oplus B\) <<< B) + S_{2i}
B = (\|B \oplus A\) <<< A) + S_{2i+1}$
```

The output is in the registers A and B.
ryption is just as easy: Divide the plaintext block into two words, A and B, and then:

For $i = r$ down to 1:

```
B = (\|B - S_{2i+1}\) >>> A) \oplus A
A = (\|A - S_{2i}\) >>> B) \oplus B
B = B - S_1
A = A - S_0$
```

The symbol ">>>" is a right circular shift. Of course, all addition and subtraction are mod $2^{32}$.

Creating the array is more complicated, but also straightforward. First, copy the bytes of the key into array L, of 32-bit words, padding the final word with zeros if necessary. Then, initialize array S, using a linear congruential generator mod $2^{32}$.

```
$S_0 = P
for $i = 1$ to $2(r+1)-1$:
S_i = (S_{i-1} + Q)$ mod $2^{32}$
```

$P = 0x7e151613$ and $Q = 0x9c3779b9$, these constants are based on the binary representation of e and phi.
Finally, mix L into S:

```
$i = 0
A = 0
doo $3n$ times (where $n$ is the maximum of $2(r+1)$ and $c$):
$S_i = (S_i + A + B) <<< B
B = (L_i + A + B) <<< (A + B)
i = (i+1)$ mod $2(r+1)
jj = (j+1)$ mod $c$
```

RC5 is actually a family of algorithms. There is no reason why the same algorithm can't have a 32-bit word size and 64-bit block size or 64-bit/128-bit block size. For $w=64$, $P$ and $Q$ are $0x7e15161328ae2a6b$ and $0x9c3779b97a47c15$, respectively. Rivest designates particular implementations of RC5 as RC5-$w/b$, where $w$ is the word size, $r$ is the number of rounds, and $b$ is the length of the key in bits.

RC5 is new, but RSA Laboratories has spent considerable time analyzing it with a 64-bit block. After 5 rounds, the statistics look very good. After 8 rounds, every