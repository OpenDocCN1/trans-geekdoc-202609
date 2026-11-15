```
sage: p = random_prime(2^1000)
sage: q = random_prime(2^1000)
sage: N = p*q
sage: x = 12345678901234567
sage: e = randint(0,N) # random integer between 0 & N-1
sage: timeit('modexp(x,e,N)')
125 loops, best of 3: 5.34 ms per loop
sage: timeit('crtmodexp(x,e,p,q)')
125 loops, best of 3: 2.86 ms per loop
```

And just for good measure, we can check that both approaches give the same answer:

```
sage: modexp(x,e,N) == crtmodexp(x,e,p,q)
True
```

To understand why the CRT method is faster, it's important to know that the cost of standard modular exponentiation over a k-bit modulus is O(k^3). For simplicity, let's pretend that exponentiation takes exactly k^3 steps. Suppose p and q are each k bits long, so that the RSA modulus N is 2k bits long. Hence, a standard exponentiation mod N takes (2k)^3 = 8k^3 steps.

With the CRT method, we do an exponentiation mod p and an exponentiation mod q. Each of these exponentiations takes k^3 steps, since p and q are only k bits long. Overall, we are only doing 2k^3 steps in this approach, which is 4x faster than the standard exponentiation mod N. In this simple analysis we are not counting the cost of converting the CRT encoding back to the typical mod-N representation. But this cost is much smaller than the cost of an exponentiation (both in practice and asymptotically).

It's worth pointing out that this speedup can only be done for RSA signing, and not verification. In order to take advantage of the CRT method to speed up exponentiation mod N, it's necessary to know the prime factors p and q. Only the person who knows the signing key knows these factors.

# 13.5 The Hardness of Factoring N

As previously mentioned, the best known way to break the security of RSA as a trapdoor function (i.e., to compute the inverse RSA function given only the public information N and e) involves factoring the RSA modulus.

Factoring integers (or, more specifically, factoring RSA moduli) is believed to be a hard problem for classical computers. In this section we show that some other problems related to RSA are “as hard as factoring.” What does it mean for a computational problem to be “as hard as factoring”? More formally, in this section we will show the following:

Theorem 13.12 Either *all* of the following problems can be solved in polynomial-time, or **none** of them can:

+   1. Given an RSA modulus N = pq, compute its factors p and q.

+   2. Given an RSA modulus N = pq compute \(\phi(N) = (p - 1)(q - 1)\).