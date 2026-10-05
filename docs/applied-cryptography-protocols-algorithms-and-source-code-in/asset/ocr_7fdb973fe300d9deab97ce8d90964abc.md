# 11.3 Number Theory

$4^2 = 16 \equiv 2 \text{ mod } 7$
$5^2 = 25 \equiv 4 \text{ mod } 7$
$6^2 = 36 \equiv 1 \text{ mod } 7$

Note that each quadratic residue appears twice in this list.
There are no values of $x$ which satisfy any of these equations:

$x^2 = 3 \text{ mod } 7$
$x^2 = 5 \text{ mod } 7$
$x^2 = 6 \text{ mod } 7$

**The quadratic nonreuses modulo 7**, the numbers that are not quadratic residues, are 3, 5, and 6.
Although I will not do here, it is easy to prove that, when $p$ is odd, there are quadratic residues mod $p$ and the same number of quadratic nonresidues mod $p$. Also, if $a$ is a quadratic residue mod $p$, then $a$ has exactly two square roots, one of them between $0$ and $(p-1)/2$, and the other between $(p-1)/2$ and $(p-1)$. One of these square roots is a quadratic residue mod $p$; this is called the **principal root**.
If $n$ is the product of two primes, $p$ and $q$, then there are $(p-1)(q-1)/4$ quadratic residues mod $n$. A quadratic residue mod $n$ is a perfect square modulo $n$. This is because to a square mod $n$, the residue must be a square mod $p$ and a square mod $q$. For example, there are 11 quadratic residues mod 35: 1, 4, 9, 11, 14, 15, 16, 25, 29, and 30. Each quadratic residue has exactly four square roots.

# **Legendre Symbol**

The **Legendre symbol**, written $L(a,p)$, is defined when $a$ is any integer and $p$ is a prime greater than 2. It is equal to 0, 1, or -1.

$L(a,p) = 0$ if $a$ is divisible by $p$.
$L(a,p) = 1$ if $a$ is a quadratic residue mod $p$.
$L(a,p) = -1$ if $a$ is a quadratic nonresidue mod $p$.

One way to calculate $L(a,p)$:

$L(a,p) = a^{(p-1)/2} \text{ mod } p$

Or you can use the following algorithm:

+   1. If $a=1$, then $L(a,p) = 1$
2. If $a$ is even, then $L(a,p) = L(a/2,p) \cdot (-1)^{(p-1)/8}$
3. If $a$ is odd (and $
eq 1$), then $L(a,p) = L(a \text{ mod } p,a) \cdot (-1)^{(a-1)(p-1)/4}$

Note that this is also an efficient way to determine whether $a$ is a quadratic residue mod $p$ (when $p$ is prime).