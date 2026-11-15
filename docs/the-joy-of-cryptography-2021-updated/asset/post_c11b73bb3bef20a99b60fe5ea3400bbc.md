
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

## The Totient Function

Euler’s totient function is defined as $\phi(n) \stackrel{\text{def}}{=} |\mathbb{Z}_n^*|$; that is, the number of elements of $\mathbb{Z}_n$ that have multiplicative inverses.

As an example, if $n$ is a prime, then $\mathbb{Z}_n^* = \mathbb{Z}_n \setminus \{0\}$ because every integer in $\mathbb{Z}_n$ apart from zero is relatively prime to $n$. Therefore, $\phi(n) = n - 1$ in this case.

RSA involves a modulus $n$ that is the product of two distinct primes $n = pq$. In that case, $\phi(n) = (p - 1)(q - 1)$. To see why, let’s count how many elements in $\mathbb{Z}_{pq}^*$ share a common divisor with $pq$ (i.e., are $not$ in $\mathbb{Z}_{pq}^*$).

- The multiples of $p$ share a common divisor with $pq$. These include $0, p, 2p, 3p, ..., (q - 1)p$. There are $q$ elements in this list.

- The multiples of $q$ share a common divisor with $pq$. These include $0, q, 2q, 3q, ..., (p - 1)q$. There are $p$ elements in this list.

We have clearly double-counted element 0 in these lists. But no other element is double counted. Any item that occurs in both lists would be a common multiple of both $p$ and $q$, but since $p$ and $q$ are relatively prime, their least common multiple is $pq$, which is larger than any item in these lists.

We count $p + q - 1$ elements of $\mathbb{Z}_{pq}$ which share a common divisor with $pq$. The rest belong to $\mathbb{Z}_{pq}^*$, and there are $pq - (p + q - 1) = (p - 1)(q - 1)$ of them. Hence $\phi(pq) = (p - 1)(q - 1)$.

General formulas for $\phi(n)$ exist, but they typically rely on knowing the prime factorization of $n$. We will see more connections between the difficulty of computing $\phi(n)$ and the difficulty of factoring $n$ later in this part of the course.

The reason we consider $\phi(n)$ at all is this fundamental theorem from abstract algebra:

## Theorem 13.5 (Euler’s Theorem)

$If\ x \in \mathbb{Z}_n^*\ then\ x^{\phi(n)} \equiv_n\ 1.$

Example Using the formula for $\phi(n)$, we can see that $\phi(15) = \phi(3 \cdot 5) = (3 - 1)(5 - 1) = 8$. Euler’s theorem says that raising any element of $\mathbb{Z}_{15}^*$ to the 8 power results in $1$: We can use Sage to verify this:

```
sage: for i in range(15):
....:     if gcd(i,15) == 1:
....:         print("%d^8 mod 15 =%d" % (i, i^8 % 15))
...:
1^8 mod 15 = 1
2^8 mod 15 = 1
4^8 mod 15 = 1
7^8 mod 15 = 1
8^8 mod 15 = 1
11^8 mod 15 = 1
13^8 mod 15 = 1
14^8 mod 15 = 1
```

## 13.2 The RSA Function

The RSA function is defined as follows:

- Let $p$ and $q$ be distinct primes (later we will say more about how they are chosen), and let $N = pq$. $N$ is called the **RSA modulus**.

- Let $e$ and $d$ be integers such that $ed \equiv_{\phi(N)} 1$. That is, $e$ and $d$ are multiplicative inverses mod $\phi(N)$ — not mod $N$!

- The RSA function is: $x \mapsto x^e \% \, N$, where $x \in \mathbb{Z}_N$.

- The inverse RSA function is: $y \mapsto y^d \% \, N$, where $x \in \mathbb{Z}_N$.

Essentially, the RSA function (and its inverse) is a simple modular exponentiation. The most confusing thing to remember about RSA is that $e$ and $d$ “live” in $\mathbb{Z}^*_{\phi(N)}$, while $x$ and $y$ “live” in $\mathbb{Z}_N$.

![](img/da79fa21b263fe549aecaabd2a0a41c8_242_0.png)

Let’s make sure the function we called the “inverse RSA function” is actually an inverse of the RSA function. Let’s start with an example:

**Example** In Sage, we can sample a random prime between 1 and $k$ by using `random_prime(k)`. We use it to sample the prime factors $p$ and $q$:

```
sage: p = random_prime(10^5)
sage: q = random_prime(10^5)
sage: N = p*q
sage: N
36486589
```

Then we can compute the exponents e and d. Recall that they must be multiplicative inverses mod $\phi(N)$, so they cannot share any common factors with $\phi(N)$. An easy way to ensure this is to choose $e$ to be a prime:

```
sage: phi = (p-1)*(q-1)
sage: e = random_prime(phi)
sage: e
28931431
sage: d = 1/Mod(e,phi)
sage: d
31549271
```

We can now raise something to the e power and again to the d power:

```
sage: x = 31415926
sage: y = x^e % N
sage: y
1798996
sage: y^d % N
31415926
```

As you can see, raising to the e power and then d power (mod N) seems to bring us back to where we started (x).

We can argue that raising-to-the-e-power and raising-to-the-d-power are inverses in general: Since $ed \equiv_{\phi(N)} 1$, we can write $ed = t\phi(N) + 1$ for some integer $t$. Then:

$(x^e)^d = x^{ed} = x^{t\phi(N)+1} = (x^{\phi(N)})^t x \equiv_N 1^t x = x$

Note that we have used the fact that $x^{\phi(N)} \equiv_N 1$ from Euler's theorem.

## How [Not] to Exponentiate Huge Numbers

When you see an expression like “x^e % N”, you might be tempted to implement it with the following algorithm:

| NaiveExponentiate(x, e, N): |
| --- |
| result = 1 |
| for i = 1 to e: // compute x^e |
|   result = result × x |
| return result % N |

While this algorithm would indeed give the correct answer, it is a really bad way of doing it. In practice, we use RSA with numbers that are thousands of bits long. Suppose we run the NaiveExponentiate algorithm with arguments x, e, and N which are around a thousand bits each (so the magnitude of these numbers is close to 2^1000):

- 1. The algorithm will spend approximately $2^{1000}$ iterations in the for-loop!

- 2. The algorithm computes $x^e$ as an *integer* first, and then reduces that integer mod $N$. Observe that $x^2$ is roughly 2000 bits long, $x^3$ is roughly 3000 bits long, etc. So it would take about $2^{1000} \cdot 1000$ bits just to write down the integer $x^e$.

As you can see, there is neither enough time nor storage capacity in the universe to use this algorithm. So how can we actually compute values like $x^e \% N$ on huge numbers?

- 1. Suppose you were given an integer $x$ and were asked to compute $x^{17}$. You can compute it as:

$x^{17} = \underbrace{x \cdot x \cdot x \cdot \cdots \cdot x}_{16 \text{ multiplications}}$ .

But a more clever way is to observe that:

$x^{17} = x^{16} \cdot x = (((x^2)^2)^2)^2 \cdot x$ .

This expression can be evaluated with only 5 multiplications (squaring is just multiplying a number by itself).

More generally, you can compute an expression like $x^e$ by following the recurrence below. The method is called **exponentiation by repeated squaring**, for reasons that are hopefully clear:

$x^e = \begin{cases} 1 & \text{if } e = 0 \\ (x^{\frac{e}{2}})^2 & \text{if } e \text{ even} \\ (x^{\frac{e-1}{2}})^2 \cdot x & \text{if } e \text{ odd} \end{cases}$

```
BETTEREXP(x, e):
if e = 0: return 1
if e even:
    return BETTEREXP(x, e/2)^2
if e odd:
    return BETTEREXP(x, (e-1)/2)^2 * x
```

BETTEREXP divides the $e$ argument by two (more or less) each time it recurses, until reaching the base case. Hence, the number of recursive calls is $O(\log e)$. In each recursive call there are only a constant number of multiplications (including squarings). So overall this algorithm requires only $O(\log e)$ multiplications (compared to $e - 1$ multiplications by just multiplying $m$ by itself $e$ times). In the case where $e \sim 2^{1000}$, this means only a few thousand multiplications.

- 2. We care about only $x^e \% N$, not the intermediate integer value $x^e$. One of the most fundamental features of modular arithmetic is that you can **reduce any intermediate values mod $N$** if you care about the final result only mod $N$.

Revisiting our previous example:

$x^{17} \% N = x^{16} \cdot x \% N = (((x^2 \% N)^2 \% N)^2 \% N)^2 \cdot x \% N$ .

More generally, we can reduce all intermediate values mod $N$:

```
ModExp(x, e, N): // compute x^e % N
if e = 0: return 1
if e even:
    return ModExp(x, e/2, N)^2 % N
if e odd:
    return ModExp(x, (e-1)/2, N)^2 * x % N
```

This algorithm avoids the problem of computing the astronomically huge integer $x^e$. It never needs to store any value (much) larger than $N$.

**Warning:** Even this ModExp algorithm isn't an ideal way to implement exponentiation for cryptographic purposes. Exercise 13.10 explores some unfortunate properties of this exponentiation algorithm.

Example Most math libraries implement exponentiation using repeated squaring. For example, you can use Sage to easily calculate numbers with huge exponents:

```
sage: 427^31415926 % 100
89
```

However, this expression still tells Sage to compute $427^{31415926}$ as an integer, before reducing it mod 100. As such, it takes some time to perform this computation.

If you try an expression like x^e % N with a larger exponent, Sage will give a memory error. How can we tell Sage to perform modular reduction at every intermediate step during repeated squaring? The answer is to use Sage's Mod objects, for example:

```
sage: Mod(427, 100)^314159265358979
63
```

This expression performs repeated squaring on the object Mod(427, 100). Since a Mod-object's operations are all overloaded (to give the answer only mod n), this has the result of doing a modular reduction after every squaring and multiplication. This expression runs instantaneously, even with very large numbers.

## Security Properties & Discussion

RSA is what is called a **trapdoor function**.

- One user generates the RSA parameters (primarily $N$, $e$, and $d$) and makes $N$ and $e$ public, while keeping $d$ private.

- Functionality properties: Given only the public information $N$ and $e$, it is easy to compute the RSA function ($x \mapsto x^e \% N$). Given the private information ($d$) it clearly easy to compute the RSA inverse ($y \mapsto y^d \% N$).

- **Security property:** Given only the public information, it should be hard to compute the RSA inverse ($y \mapsto y^d \% N$) on randomly chosen values. In other words, the only person who is able to compute the RSA inverse function is the person who generated the RSA parameters.
