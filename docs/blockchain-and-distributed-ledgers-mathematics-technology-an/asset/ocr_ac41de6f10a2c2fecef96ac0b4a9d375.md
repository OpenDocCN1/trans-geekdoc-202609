# Chapter Essential Cryptographic Tools | 99

To ensure that the above equation is valid, we assume that $p$ is a prime (as the notation suggests), and $a$ is a primitive root $mod p$. We consider primitive roots $p$ in detail in the following section. Here, briefly mention that $a$ primitive root $mod p$, provided that any $q, 0 < q < p$, is an integer $r$, such that

```
$q = a' \mod p. \qquad (4.65)$
```

Thus, given $(p, \alpha, y)$, we need to find $x$. Make $x$ unique, we always choose the smallest solution. Discrete logarithms are additive; why $L_{\alpha}(yz)$?

```
$L_{\alpha}(yz) = (L_{\alpha}(y) + L_{\alpha}(z)) \mod (p-1). \qquad (4.66)$
```

# 4.6.2 Primitive roots

In general, $a$ is a primitive root $mod n$ if every primitive root $m$ is congruent to a power of $a$, $m = a^{(n)} \mod n$. When $n$ is prime, every primitive $m, 0 < m < n$, is a power of $a$. For example, we see in Table 4.3 that $2, 6, 7, 11$ are primitive roots mod 13.

This table shows for every $n', 1 \le n' \le 12$ we have a power $r'$ such that $a^{(r')} = n'$ for $a=2, 6, 7, 11$ that they are primitive roots. It is easy to check that there are no other primitive roots for $p = 13$.

For a given $n$, finding primitive roots is difficult. First, compute the totient function $\phi(n)$. Second, determine its prime factors $p_1,\dots,p_t$. Third, for each $p_i$, compute

```
$z_i = a^{\phi(p_i)} \mod n. \qquad (4.67)$
```

If $z_i \neq 1$, then $a$ is a primitive root.

For example, $\phi(13) = 12 = 2^2 \times 3$; $6^3 \mod 13 = 12 \neq 1$; $6^4 = 9 \neq 1 \mod 13$; $6$ is a primitive root.

In general, the calculation of discrete logarithms is very involved, although one can quickly them in some instances. We are not going to discuss details here since we need them for later. In Figure 4.5 (a), (b), we show $5^n \mod 97$ for $n=1,\dots,96$, and $3^n \mod 127$ for $n=1,\dots,126$, as points on a unit circle according to the mapping

Table 4.3 demonstrates that 2, 6, 7, 11 are primitive roots mod 13.

| r | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---||
| 2' mod 13 | 2 | 4 | 8 | 3 | 6 | 12 | 11 | 9 | 5 | 10 | 7 | 1 |
| 6' mod 13 | 6 | 10 | 8 | 9 | 12 | 7 | 3 | 5 | 4 | 11 | 1 | 1 |
| 7' mod 13 | 7 | 10 | 5 | 9 | 11 | 12 | 6 | 3 | 8 | 4 | 2 | 1 |
| 11' mod 13 | 11 | 4 | 5 | 3 | 7 | 12 | 2 | 9 | 8 | 10 | 6 | 1 |