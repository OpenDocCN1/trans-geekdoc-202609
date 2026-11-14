
## Table 11.1

| Method | Param | N | Win% | Value | Result |
|--------|-------|---|------|-------|--------|
| Dirichlet4 | 3 | 70 | 49.65% | 0.4715 | Fail |
| Logistic | 0.181517 | 115 | 49.82% | 0.539 | Pass |
| Logistic | 0.72 | 254 | 49.37% | 1.1905 | Pass |
| Python | 0 | 220 | 49.71% | 1.0311 | Pass |
| Python | 1 | 150 | 50.03% | 0.7031 | Pass |
| Python | 2 | 279 | 49.46% | 1.3077 | Pass |
| Python | 4 | 365 | 50.81% | 1.7108 | Fail |
| Python | 100 | 386 | 49.10% | 1.8092 | Fail |
| Python | 200 | 922 | 52.29% | 4.3214 | Fail |
| Python | 500 | 258 | 49.67% | 1.2093 | Pass |
| SQRT | (2,5) | 146 | 49.63% | 0.6843 | Pass |
| SQRT | (90,91) | 1236 | 53.07% | 5.7932 | Fail |

![Table 11.1](images/B9780443218576000151/t0010.png)

## Figure 11.1

![Figure 11.1 Orbit of L(z,χ) at σ = 1/2, with 0 < t < 200 and χ = χ4 (left) versus pseudorandom χ (right).](images/B9780443218576000151/gr001.jpg)

Figure 11.1 Orbit of `L(z,χ)` at `σ = 1/2`, with `0 < t < 200` and `χ = χ4` (left) versus pseudorandom `χ` (right).

## Discussion

If the Euler product in formula [(11.1)](#Chp011_203-228_B9780443218576000151.xhtml#deq1) converges for some `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png), it is equal to its series expansion when `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png), it converges for all `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png), and `L(z, χ)`![Image](images/B9780443218576000151/si61.png) satisfies GRH when `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png). When `σ` < 1![Image](images/B9780443218576000151/si70.png), the convergence is `conditional` [[Wiki](https://en.wikipedia.org/wiki/Conditional_convergence)], making things more difficult. Another example that trivially satisfies GRH if `$\sigma > \frac{1}{2}$`![Image](images/B9780443218576000151/si66.png) is when `χ(·)`![Image](images/B9780443218576000151/si2.png) is a random variable with `$P[\chi(p) = 1] = P[\chi(p) = -1] = \frac{1}{2}$`![Image](images/B9780443218576000151/si71.png) for primes `p`. In this case convergence means that `L(z, χ)`![Image](images/B9780443218576000151/si61.png) has finite expectation as proved by formula [(11.2)](#Chp011_203-228_B9780443218576000151.xhtml#deq2), and finite variances. This function `χ(·)`![Image](images/B9780443218576000151/si2.png) is called a `random Rademacher multiplicative function`, see [[7]](#Chp011_203-228_B9780443218576000151.xhtml#br0035). Here the `χ(p)`![Image](images/B9780443218576000151/si12.png)'s are identically and independently distributed over the set of all primes, and the definition is extended to all strictly positive integers with the formula `χ(ab) = χ(a)χ(b)`![Image](images/B9780443218576000151/si4.png).

So, if we were able to find a “nice enough” pseudorandom, yet deterministic function `χ(·)`![Image](images/B9780443218576000151/si2.png) with convergence of the Euler product when `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) for some `σ`[0] < 1![Image](images/B9780443218576000151/si72.png), a function `χ(·)`![Image](images/B9780443218576000151/si2.png) that is random enough over the primes (like its sister, the truly stochastic version) to guarantee the convergence of the product, then it would be a major milestone towards proving GRH. Convergence of the product would imply that:

*   `L(z, χ)`![Image](images/B9780443218576000151/si61.png) is `analytic` [[Wiki](https://en.wikipedia.org/wiki/Analytic_function)], because the product is equal to its series expansion, which trivially satisfies the `Cauchy–Riemann equations` [[Wiki](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Riemann_equations)],
*   `L(z, χ)`![Image](images/B9780443218576000151/si61.png) has no root if `σ` > `σ`[0]![Image](images/B9780443218576000151/si69.png) since the product has no root.

As discussed, examples that are “not so nice” exist; “nice enough” means that `L(z, χ)`![Image](images/B9780443218576000151/si61.png) satisfies a `Dirichlet functional equation` [[Wiki](https://en.wikipedia.org/wiki/Functional_equation_\(L-function\))]). Typically, “nice enough” means that `L(z, χ)`![Image](images/B9780443218576000151/si61.png) is a `Dirichlet-L function` [[Wiki](https://en.wikipedia.org/wiki/Dirichlet_L-function)]. Besides the `Riemann zeta function` where `χ(p) = 1`![Image](images/B9780443218576000151/si73.png) is the trivial `Dirichlet character`, the most fundamental example is when `χ = χ4`![Image](images/B9780443218576000151/si74.png) is the nontrivial `Dirichlet character modulo` 4 [[Wiki](https://en.wikipedia.org/wiki/Dirichlet_character)]. This example is featured in [Fig. 11.1](#Chp011_203-228_B9780443218576000151.xhtml#f0010) where `σ = 1/2`![Image](images/B9780443218576000151/si75.png) (left plot) and contrasted with a not so nice example on the right plot, corresponding to a pseudorandom sequence `{χ(p_k)}`![Image](images/B9780443218576000151/si68.png). The `χ4`![Image](images/B9780443218576000151/si76.png) example is referred to as `Dirichlet4` in [Table 11.1](#Chp011_203-228_B9780443218576000151.xhtml#t0010). Note that for `σ = 1/2`![Image](images/B9780443218576000151/si75.png), `L(z, χ4)`![Image](images/B9780443218576000151/si77.png) has infinitely many roots just like the Riemann zeta function, though its roots are different: this is evident when looking at the left plot in [Fig. 11.1](#Chp011_203-228_B9780443218576000151.xhtml#f0010). The (conjectured) absence of root is when `1/2 < σ < 1`![Image](images/B9780443218576000151/si78.png).

I went as far as to compute the Euler product for `L(z, χ4)`![Image](images/B9780443218576000151/si77.png) when `z = σ = 0.99`![Image](images/B9780443218576000151/si79.png). It nicely converges to the correct value, without the typical growing oscillations associated to lack of convergence, agreeing with the value computed using the series expansion in formula [(11.1)](#Chp011_203-228_B9780443218576000151.xhtml#deq1). It means that the product converges at least for all `z` with `σ = ℜ(z) ≥ 0.99`![Image](images/B9780443218576000151/si80.png). Thus there is no root for `L(z, χ4)`![Image](images/B9780443218576000151/si77.png) if `σ ≥ 0.99`![Image](images/B9780443218576000151/si81.png). This would be an immense milestone compared to the best known result (no root if `σ ≥ 1`![Image](images/B9780443218576000151/si82.png)) if it was theoretically possible to prove the convergence in question, supported only by empirical evidence. Convergence implies that the sequence `{χ4(p_k)}`![Image](images/B9780443218576000151/si83.png) is random enough over the primes `p1, p2`![Image](images/B9780443218576000151/si84.png), and so on. That is, the gap between +1 and −1 in the sequence never grows too large (that is, runs of same value can only grow so fast), and the proportion of +1 and −1 tends to `1/2`![Image](images/B9780443218576000151/si9.png) fast enough, despite the known `Chebyshev's bias` [[Wiki](https://en.wikipedia.org/wiki/Chebyshev%27s_bias)]. The fact that the proportion eventually converges to `1/2`![Image](images/B9780443218576000151/si9.png) when using more and more terms in the sequence, is a consequence of `Dirichlet's theorem` [[Wiki](https://en.wikipedia.org/wiki/Dirichlet%27s_theorem_on_arithmetic_progressions)]. This is how close we are – or you may say how far – to proving GRH.
