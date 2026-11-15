```
KeyGen:
choose random $\lambda$-bit prime $k$
return $k$

Dec($k, c$):
$m' := c/k$
while $m'$ not a multiple of 10:
$m' := \lfloor m'/10 \rfloor$
return $m'/10$

Enc($k, m \in \{0, 1\}^\lambda$):
$m' := 10 \cdot m$
while $m'$ not prime:
$d \leftarrow \{1, \dots, 9\}$
$m' := 10 \cdot m' + d$
return $k \cdot m'$
```

Show an attack breaking CPA-security of the scheme. That is, describe a distinguisher and compute its bias.

+   13.8. Explain why the RSA exponents $e$ and $d$ must always be odd numbers.

+   13.9. Why must $p$ and $q$ be *distinct* primes? Why is it a bad idea to choose $p = q$?

+   13.10. A **simple power analysis (SPA)** attack is a physical attack on a computer, where the attacker monitors precisely how much electrical current the processor consumes while performing a cryptographic algorithm. In this exercise, we will consider an SPA attack against the ModExp algorithm shown in Section 13.2.

The ModExp algorithm consists mainly of squarings and multiplications. Suppose that by monitoring a computer it is easy to tell when the processor is running a squaring vs. a multiplication step (this is a very realistic assumption). This assumption is analogous to having access to the printed output of this modified algorithm:

```
ModExp($m, e, N$): // compute $m^e \% N$
if $e = 0$: return 1
if $e$ even:
  res := ModExp($m, \frac{e}{2}, N)^2 \% N$
  print "square"
if $e$ odd:
  res := ModExp($m, \frac{e-1}{2}, N)^2 \cdot m \% N$
  print "square"
  print "mult"
return res
```

Describe how the printed output of this algorithm lets the attacker *completely* learn the value $e$. Remember that in RSA it is indeed the exponent that is secret, so this attack leads to key recovery for RSA.

+   13.11. The Chinese Remainder Theorem states that there is always a solution for $x$ in the following system of equations, when gcd($r, s$) = 1:

\( x \equiv_r u \)