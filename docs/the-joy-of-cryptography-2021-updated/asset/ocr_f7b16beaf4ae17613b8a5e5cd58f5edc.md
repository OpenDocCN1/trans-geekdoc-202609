to-do
The security property is not natural to express in our language of security definitions (libraries).

Currently the best known attacks against RSA (i.e., ways to compute the inverse RSA function given only the public information) involve factoring the modulus. If we want to ensure that RSA is secure as a trapdoor function, we must understand the state of the art for factoring large numbers.

Before discussing the performance of factoring algorithms, remember that we measure performance as a function of the **length** of the input — how many bits it takes to write the input. In a factoring algorithm, the input is a large number $N$, and it takes roughly $n = \log_2 N$ bits to write down that number. We will discuss the running time of algorithms as a function of $n$, not $N$. Just keep in mind the difference in cost between *writing down* a 1000-bit number ($n = 1000$) vs *counting up to* a 1000-bit number ($N = 2^{1000}$)

Everyone knows the “trial division” method of factoring: given a number $N$, check whether $i$ divides $N$, for every $i \in \{2, \dots \sqrt{N}\}$. This algorithm requires $\sqrt{N} = 2^{n/2}$ divisions in the worst case. It is an exponential-time algorithm since we measure performance in terms of the bit-length $n$.

If this were the best-known factoring algorithm, then we would need to make $N$ only as large as $2^{256}$ to make factoring require $2^{128}$ effort. But there are much better factoring algorithms than trial division. The fastest factoring algorithm today is called the Generalized Number Field Sieve (GNFS), and its complexity is something like $O\Big(n^{\left(\frac{n}{\log n}\right)^{\frac{1}{3}}}\Big)$. This is not a polynomial-time algorithm, but it’s much faster than trial division.

# Example

Sage can easily factor reasonably large numbers. Factoring the following 200-bit RSA modulus on my modest computer takes about 10 seconds:

```
sage: p = random_prime(2^100)
sage: q = random_prime(2^100)
sage: N = p*q
sage: factor(N)
206533721079613722225064934611 * 5175820805637266211301114148123
```

As of January 2020, the largest RSA modulus that has been (publicly) factored is a 795-bit modulus.$^5$ Factoring this number required the equivalent of 900 CPU-core-years, or roughly $2^{66}$ total clock cycles.

All of this is to say, the numbers involved in RSA need to be quite large to resist factoring attacks (i.e., require $2^{128}$ effort for state-of-the-art factoring algorithms). Current best practices suggest to use 2048- or 4096-bit RSA moduli, meaning that $p$ and $q$ are each 1024 or 2048 bits.

to-do
“What about quantum computers?” is a common FAQ that I should address here.

$^5$https://en.wikipedia.org/wiki/RSA_numbers#RSA-240