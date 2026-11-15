
Example Let's take the example r = 3359 and s = 2953, which are relatively prime (so the CRT applies). Suppose we want to compute 3141592 + 6535897 % rs. Doing it the usual way in Sage looks like this:

```
sage: r = 3359
sage: s = 2953
sage: (3141592 + 6535897) % (r*s)
9677489
```

Doing it in the CRT way looks like this.

```
sage: u = (3141592 + 6535897) % r
sage: v = (3141592 + 6535897) % s
sage: crt(u, v, r, s)
9677489
```

Both methods give the same answer!

## Application to RSA

You might be wondering what the point of all of this is. The CRT method seems like a very indirect and wasteful way to compute anything. This impression might be true for simple operations like addition and single multiplications. However, the CRT method is faster for exponentiation mod N, which is the main operation in RSA.

Example In Sage, we can do basic exponentiation mod n as follows:

```
sage: def modexp(x,e,n): # x^e mod n
....:     return Mod(x,n)^e
```

If we are working over an RSA modulus and know its factorization pq, then we use the CRT method for exponentiation mod pq as follows. We simply do the exponentiation mod p and (separately) mod q, then use the crt function to convert back to Z_pq.

```
sage: def crtmodexp(x,e,p,q): # x^e mod pq, using CRT speedup
....:     u = Mod(x,p)^e
....:     v = Mod(x,q)^e
....:     return crt(u.lift(), v.lift(), p, q)
```

We need to use u.lift() and v.lift() to convert u and v from Mod-objects into integers, because that is what crt expects.

We can use both methods to perform an exponentiation, and measure how long it takes with the timeit function. In this example, N is about 2000 bits long, and the difference in speed is noticeable:

7 I'm talking about the CRT method for arithmetic mod rs, not life in general.

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

## 13.5 The Hardness of Factoring N

As previously mentioned, the best known way to break the security of RSA as a trapdoor function (i.e., to compute the inverse RSA function given only the public information N and e) involves factoring the RSA modulus.

Factoring integers (or, more specifically, factoring RSA moduli) is believed to be a hard problem for classical computers. In this section we show that some other problems related to RSA are “as hard as factoring.” What does it mean for a computational problem to be “as hard as factoring”? More formally, in this section we will show the following:

Theorem 13.12 Either *all* of the following problems can be solved in polynomial-time, or **none** of them can:

- 1. Given an RSA modulus N = pq, compute its factors p and q.

- 2. Given an RSA modulus N = pq compute \(\phi(N) = (p - 1)(q - 1)\).

- 3. Given an RSA modulus $N = pq$ and value $e$, compute the corresponding $d$ (satisfying $ed \equiv_{\phi(N)} 1$).

- 4. Given an RSA modulus $N = pq$, find any $x \not\equiv_N \pm 1$ such that $x^2 \equiv_N 1$.

To prove the theorem, we will show:

- if there is an efficient algorithm for (1), then we can use it as a subroutine to construct an efficient algorithm for (2). This is straight-forward: if you have a subroutine factoring $N$ into $p$ and $q$, then you can call the subroutine and then compute $(p - 1)(q - 1)$.
- if there is an efficient algorithm for (2), then we can use it as a subroutine to construct an efficient algorithm for (3). This is also straight-forward: if you have a subroutine computing $\phi(N)$ given $N$, then you can compute $d$ exactly how it is computed in the key generation algorithm.
- if there is an efficient algorithm for (3), then we can use it as a subroutine to construct an efficient algorithm for (4).
- if there is an efficient algorithm for (4), then we can use it as a subroutine to construct an efficient algorithm for (1).

Below we focus on the final two implications.

## Using square roots of unity to factor N

Problem (4) of Theorem 13.12 concerns a new concept known as square roots of unity:

Definition 13.13 (Sqrt of unity) $x$ is a **square root of unity modulo** $N$ if $x^2 \equiv_N 1$. If $x \not\equiv_N 1$ and $x \not\equiv_N -1$, then we say that $x$ is a **non-trivial** square root of unity.

Since $(\pm 1)^2 = 1$ over the integers, it is also true that $(\pm 1)^2 \equiv_N 1$. In other words, $\pm 1$ are always square roots of unity modulo $N$, for any $N$. But some values of $N$ have even more square roots of unity. If $N$ is the product of distinct odd primes, then $N$ has 4 square roots of unity: two trivial and two non-trivial ones (and you are asked to prove this fact in an exercise).

Claim 13.14 Suppose there is an efficient algorithm for computing nontrivial square roots of unity modulo $N$. Then there is an efficient algorithm for factoring $N$. (This is the $(4) \implies (1)$ step in Theorem 13.12.)

Proof The reduction is rather simple. Suppose NTSRU is an algorithm that on input $N$ returns a non-trivial square root of unity modulo $N$. Then we can factor $N$ with the following algorithm:

```
FACTOR(N):
x := NTSRU(N)
return gcd(N, x + 1) and gcd(N, x - 1)
```

The algorithm is simple, but we must argue that it is correct. When $x$ is a nontrivial square root of unity modulo $N$, we have the following:

\(x^2 \equiv_{pq} 1 \Rightarrow pq \mid x^2 - 1 \Rightarrow pq \mid (x + 1)(x - 1);\)
\(x \not\equiv_{pq} 1 \Rightarrow pq \nmid (x - 1);\)
\(x \not\equiv_{pq} -1 \Rightarrow pq \nmid (x + 1).\)

The prime factorization of \((x + 1)(x - 1)\) contains a factor of \(p\) and a factor of \(q\). But neither \(x + 1\) nor \(x - 1\) contain factors of both \(p\) and \(q\). Hence \(x + 1\) and \(x - 1\) must each contain factors of exactly one of \(\{p, q\}\). In other words, \(\{\gcd(pq, x - 1), \gcd(pq, x + 1)\} = \{p, q\}\). ■

## Finding square roots of unity

**Claim 13.15** If there is an efficient algorithm for computing \(d \equiv_{\phi(N)} e^{-1}\) given \(N\) and \(e\), then there is an efficient algorithm for computing nontrivial square roots of unity modulo $N$. (This is the \((3) \Rightarrow (4)\) step in Theorem 13.12.)

**Proof** Suppose we have an algorithm FIND\_D that on input \((N, e)\) returns the corresponding exponent \(d\). Then consider the following algorithm which uses FIND\_D as a subroutine:

```
SRU(N):
choose e as a random n-bit prime
d := FIND\_D(N, e)
write ed - 1 = 2^s r, with r odd
// i.e., factor out as many 2s as possible
w <-_R Z_N
if gcd(w, N) != 1: // w \notin Z_N^*
   use gcd(w, N) to factor N = pq
   compute a nontrivial square root of unity using p & q
x := w^r % N
if x ==_N 1 then return 1
for i = 0 to s:
   if x^2 ==_N 1 then return x
   x := x^2 % N
```

There are several return statements in this algorithm, and it should be clear that all of them indeed return a square root of unity. Furthermore, the algorithm does eventually return within the main for-loop, because \(x\) takes on the sequence of values:

\(w^r, w^{2r}, w^{4r}, w^{8r}, \dots, w^{2^s r}\)

and the final value of that sequence satisfies

\(w^{2^s r} = w^{ed-1} \equiv_N w^{(ed-1)\% \phi(N)} = w^{1-1} = 1.\)

Although we don't prove it here, it is possible to show that the algorithm returns a square root of unity _chosen uniformly at random_ from among the four possible square roots of unity. So with probability 1/2 the output is a nontrivial square root. We can repeat this basic process \(n\) times, and eventually encounter a nontrivial square root of unity with probability \(1 - 2^{-n}\). ■
