Example Sage implements the extended Euclidean algorithm as “xgcd”:

```
sage: xgcd(427,529)
(1, 223, -180)
sage: 223*427 + (-180)*529
1
```

You can then see that 223 and 427 are multiplicative inverses mod 529:

```
sage: 427*223 % 529
1
```

# The Totient Function

Euler’s totient function is defined as $\phi(n) \stackrel{\text{def}}{=} |\mathbb{Z}_n^*|$; that is, the number of elements of $Z_n$ that have multiplicative inverses.

As an example, if $n$ is a prime, then $\mathbb{Z}_n^* = \mathbb{Z}_n \setminus \{0\}$ because every integer in $\mathbb{Z}_n$ apart from zero is relatively prime to $n$. Therefore, $\phi(n) = n - 1$ in this case.

RSA involves a modulus $n$ that is the product of two distinct primes $n = pq$. In that case, $\phi(n) = (p - 1)(q - 1)$. To see why, let’s count how many elements in $\mathbb{Z}_{pq}^*$ share a common divisor with $pq$ (i.e., are $not$ in $\mathbb{Z}_{pq}^*$).

+   ▶ The multiples of $p$ share a common divisor with $pq$. These include $0, p, 2p, 3p, ..., (q - 1)p$. There are $q$ elements in this list.

+   ▶ The multiples of $q$ share a common divisor with $pq$. These include $0, q, 2q, 3q, ..., (p - 1)q$. There are $p$ elements in this list.

We have clearly double-counted element 0 in these lists. But no other element is double counted. Any item that occurs in both lists would be a common multiple of both $p$ and $q$, but since $p$ and $q$ are relatively prime, their least common multiple is $pq$, which is larger than any item in these lists.

We count $p + q - 1$ elements of $\mathbb{Z}_{pq}$ which share a common divisor with $pq$. The rest belong to $\mathbb{Z}_{pq}^*$, and there are $pq - (p + q - 1) = (p - 1)(q - 1)$ of them. Hence $\phi(pq) = (p - 1)(q - 1)$.

General formulas for $\phi(n)$ exist, but they typically rely on knowing the prime factorization of $n$. We will see more connections between the difficulty of computing $\phi(n)$ and the difficulty of factoring $n$ later in this part of the course.

The reason we consider $\phi(n)$ at all is this fundamental theorem from abstract algebra:

# Theorem 13.5 (Euler’s Theorem)

$If\ x \in \mathbb{Z}_n^*\ then\ x^{\phi(n)} \equiv_n\ 1.$

Example Using the formula for $\phi(n)$, we can see that $\phi(15) = \phi(3 \cdot 5) = (3 - 1)(5 - 1) = 8$. Euler’s theorem says that raising any element of $\mathbb{Z}_{15}^*$ to the 8 power results in $1$: We can use Sage to verify this: