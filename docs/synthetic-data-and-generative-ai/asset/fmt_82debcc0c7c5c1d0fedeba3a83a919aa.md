
Thus the expectation is finite if $\sigma = \Re(z) > \frac{1}{2}$![Image](images/B9780443218576000151/si16.png). A similar argument can be used for the variances.

Now let us replace the random variables `χ(p)`![Image](images/B9780443218576000151/si12.png) by pseudorandom numbers, taking the values +1 or −1 with probability $\frac{1}{2}$![Image](images/B9780443218576000151/si9.png). If these generated numbers are “random enough”, free of dependencies, then one would expect them to satisfy the laws of Rademacher random multiplicative functions. The remaining of this chapter explores this idea in details, with a focus on applications.

## 11.2 Pseudorandom numbers

There is no formal definition of pseudorandom numbers. Intuitively, a good set of pseudorandom numbers is a deterministic binary sequence of digits that satisfies all statistical tests of randomness. Of course, it makes no sense to talk about randomness if the sequence contains very few digits, say one or two. So pseudorandom numbers (PRN) are associated with infinite sequences, even though in practice one only uses finite subsequences.

A rigorous definition of PRN sequences requires the convergence of the multivariate empirical distribution [[Wiki](https://en.wikipedia.org/wiki/Empirical_distribution_function)] of any finite subsequence of `m` digits, to the known theoretical value under the assumption of full randomness. Let the PRN sequence be denoted as `{d(k)}`![Image](images/B9780443218576000151/si17.png) with `k` = 1, 2![Image](images/B9780443218576000151/si18.png), and so on. A subsequence of `m` digits is defined by its indices, denoted as `i[1]`, `i[2]`, …, `i[m]`![Image](images/B9780443218576000151/si19.png). The convergence of the empirical distribution means that regardless of the indices 0 ≤ `i[1]` < `i[2]` < ⋯![Image](images/B9780443218576000151/si20.png) we have

```
\lim_{n\rightarrow\infty}\frac{1}{n}\sum_{k = 1}^{n}I\left\lbrack d(k + i_{1}) = k_{1},d(k + i_{2}) = k_{2},\ldots,d(k + i_{m}) = k_{m} \right\rbrack = 2^{- m}
```

![Image](images/B9780443218576000151/si21.png)(11.3)

for any (`k[1]`, `k[2]`, …, `k[m]`)![Image](images/B9780443218576000151/si22.png) in { − 1,  + 1}^(`m`)![Image](images/B9780443218576000151/si23.png). Here `I` is the indicator function: `I`[`A`] = 1![Image](images/B9780443218576000151/si24.png) if `A` is true, otherwise `I`[`A`] = 0![Image](images/B9780443218576000151/si25.png). The following number `λ` is of particular interest:

```
\lambda = \sum_{k = 1}^{\infty}d^{\prime}(k) \cdot 2^{- k},\quad\text{with~}d^{\prime}(k) = \frac{1 + d(k)}{2} \in \{ 0,1\}.
```

![Image](images/B9780443218576000151/si26.png)(11.4)

Thus the `d'(k)`![Image](images/B9780443218576000151/si27.png)'s are the binary digits of the number `λ`, with 0 ≤ `λ` ≤ 1![Image](images/B9780443218576000151/si28.png).

The connection between the multiplicative function `χ(·)`![Image](images/B9780443218576000151/si2.png) in formula [(11.1)](#Chp011_203-228_B9780443218576000151.xhtml#deq1) and the `d(k)`![Image](images/B9780443218576000151/si29.png)'s is as follows. Denote the `k`th prime as `p[k]`![Image](images/B9780443218576000151/si30.png), with `p[1]` = 2![Image](images/B9780443218576000151/si31.png). Then `d(k)` = `χ(p[k])`![Image](images/B9780443218576000151/si32.png). The traditional definition of PRNs is equivalent to requiring `λ` be a **normal number** in base 2 [[Wiki](https://en.wikipedia.org/wiki/Normal_number)]. I introduce a stronger criterion of randomness in Section [11.2.1](#Chp011_203-228_B9780443218576000151.xhtml#s0020).

### 11.2.1 Strong pseudorandom numbers

Convergence of the empirical joint distributions, as defined by formula [(11.3)](#Chp011_203-228_B9780443218576000151.xhtml#deq3), has a few important implications. The **Kolmogorov–Smirnov test** [[Wiki](https://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Smirnov_test)], the **Berry–Esseen inequality** [[Wiki](https://en.wikipedia.org/wiki/Berry%E2%80%93Esseen_theorem)] and the **law of the iterated logarithm** [[Wiki](https://en.wikipedia.org/wiki/Law_of_the_iterated_logarithm)] can be applied to the PRN sequence `{d(k)}`![Image](images/B9780443218576000151/si17.png). These three fundamental results provide strong limitations on the behavior of finite PRN sequences. If a sequence `{d(k)}`![Image](images/B9780443218576000151/si17.png) or its representation by the number `λ` does no stay within these limits, then it does not emulate pure randomness. However, some quasirandom PRN sequences, with weak dependencies, meet these requirements, yet are not truly “random”. For instance, a number can be normal in base 2, yet have digits that exhibit some dependencies, see [here](https://mathoverflow.net/questions/426815/normal-numbers-and-law-of-the-iterated-logarithm). The purpose of this section is to introduce stronger requirements in order to catch some of these exceptions. This is where the multiplicative function `χ(·)`![Image](images/B9780443218576000151/si2.png) comes into play.

The function `χ(·)`![Image](images/B9780443218576000151/si2.png), initially defined for primes `p`, is extended to all strictly positives integers via `χ(ab)` = `χ(a)χ(b)`![Image](images/B9780443218576000151/si4.png). Because the `χ(p)`![Image](images/B9780443218576000151/si12.png)'s are independent among prime numbers (by construction), the full sequence `{χ(k)}`![Image](images/B9780443218576000151/si33.png) over all `k` must behave in a certain way. Obviously, if `k` is a square integer, `χ(k)` = 1![Image](images/B9780443218576000151/si34.png). But if `k` is not a square, we still have $P[\chi(k) = 1] = P[\chi(k) = - 1] = \frac{1}{2}$![Image](images/B9780443218576000151/si35.png). For instance, `χ(4200)` = `χ(4)χ(25)χ(6)χ(7)` = `χ(6)χ(7)`![Image](images/B9780443218576000151/si36.png). Since the product of two independent random variables with **Rademacher distribution** [[Wiki](https://en.wikipedia.org/wiki/Rademacher_distribution)] has a Rademacher distribution, it follows that `χ(6)` = `χ(2)χ(3)`![Image](images/B9780443218576000151/si37.png) has a Rademacher distribution, and thus `χ(4200)` = `χ(6)χ(7)`![Image](images/B9780443218576000151/si38.png) also has a Rademacher distribution. So, the `χ(k)`![Image](images/B9780443218576000151/si39.png)'s are identically distributed with zero mean, unless `k` is a square integer. However, they are not independently distributed, even after removing square integers, or even if you only keep **square-free integers** [[Wiki](https://en.wikipedia.org/wiki/Square-free_integer)].

I now define three fundamental functions, which are central to my new test of randomness. First, define the following sets:

*   `S₁(n)`![Image](images/B9780443218576000151/si40.png) contains all prime integers ⩽`n`.
*   `S₂(n)`![Image](images/B9780443218576000151/si41.png) contains all positive square-free integers ⩽`n`.
*   `S₃(n)`![Image](images/B9780443218576000151/si42.png) contains all positive nonsquare integers ⩽`n`.

So each of these sets contains at most `n` elements. Then, define the three functions as

```
L_{1}(n) = \sum_{k \in S_{1}(n)}\chi(k),\quad L_{2}(n) = \sum_{k \in S_{2}(n)}\chi(k),\quad L_{3}(n) = \sum_{k \in S_{3}(n)}\chi(k).
```

![Image](images/B9780443218576000151/si43.png)(11.5)

Now, I can introduce my new test of randomness.

#### 11.2.1.1 New test of randomness for PRNGs
