
As for the actual computation of the digits, it is limited here to ![Image](images/B9780443218576000151/fx007.jpg)digits, but I compare these digits with those obtained from an external source: Sagemath, see [here](https://mltblog.com/3uMZQ4s). It shows, as it should, that both methods produce the same digits, for the number `$\sqrt{2}/2$`![Image](images/B9780443218576000151/si124.png) in particular.

The special recursion used for the digit computation is as follows:

```
If z[k] < 2*y[k] then  # ![Image](images/B9780443218576000151/si168.png)
    y[k+1] = 4*y[k] - 2*z[k]  # ![Image](images/B9780443218576000151/si169.png)
    z[k+1] = 2*z[k] + 3  # ![Image](images/B9780443218576000151/si170.png)
    d(k) = 1  # ![Image](images/B9780443218576000151/si92.png)
else
    y[k+1] = 4*y[k]  # ![Image](images/B9780443218576000151/si171.png)
    z[k+1] = 2*z[k] - 1  # ![Image](images/B9780443218576000151/si172.png)
    d(k) = 0  # ![Image](images/B9780443218576000151/si173.png)
```

The bivariate seed (the initial condition) is determined by the values of `y[0]`![Image](images/B9780443218576000151/si174.png) and `z[0]`![Image](images/B9780443218576000151/si175.png). You need `z[0] > y[0]`![Image](images/B9780443218576000151/si176.png) and `z[0] ≠ 2*y[0]`![Image](images/B9780443218576000151/si177.png). Then the binary digits `d(k)`![Image](images/B9780443218576000151/si29.png) are those of the number

$x\_{0} = \\frac{- (z\_{0} - 1) + \\sqrt{{(z\_{0} - 1)}^{2} + 8y\_{0}}}{4},$

![Image](images/B9780443218576000151/si178.png)

see [here](https://mltblog.com/3REtOB9). In particular, if `y[0] = 2, z[0] = 5`![Image](images/B9780443218576000151/si179.png), then `$x\_{0} = - 1 + \\sqrt{2}$`![Image](images/B9780443218576000151/si180.png). Using the change of variables `u[k] = 2*y[k] - z[k]`![Image](images/B9780443218576000151/si181.png) and `v[k] = 2*z[k] + 3`![Image](images/B9780443218576000151/si182.png), the recurrence can be rewritten as:

```
If u[k] > 0 then  # ![Image](images/B9780443218576000151/si183.png)
    u[k+1] = 4*u[k] - v[k]  # ![Image](images/B9780443218576000151/si184.png)
    v[k+1] = 2*v[k] + 3  # ![Image](images/B9780443218576000151/si185.png)
    d(k) = 1  # ![Image](images/B9780443218576000151/si92.png)
else
    u[k+1] = 4*u[k] + v[k] - 2  # ![Image](images/B9780443218576000151/si186.png)
    v[k+1] = 2*v[k] - 5  # ![Image](images/B9780443218576000151/si187.png)
    d(k) = 0  # ![Image](images/B9780443218576000151/si173.png)
```

Now `v[k] - 5`![Image](images/B9780443218576000151/si188.png) is divisible by 8. Let `w[k] = (v[k] - 5)/8`![Image](images/B9780443218576000151/si189.png). We have `d(k) = 1`![Image](images/B9780443218576000151/si92.png) if `w[k+1]`![Image](images/B9780443218576000151/si190.png) is odd, otherwise `d(k) = 0`![Image](images/B9780443218576000151/si173.png). We also have the following one-dimensional backward recursion, allowing you to compute the digits backward all the way down to the first digit:

```
If w[k+1] is odd then  # ![Image](images/B9780443218576000151/si190.png)
    v[k] = (v[k+1] - 3)/2  # ![Image](images/B9780443218576000151/si192.png)
    d(k) = 1  # ![Image](images/B9780443218576000151/si92.png)
else
    v[k] = (v[k+1] + 5)/2  # ![Image](images/B9780443218576000151/si193.png)
    d(k) = 0  # ![Image](images/B9780443218576000151/si173.png)
```

These recursions are reminiscent of the unsolved **Collatz conjecture** [[Wiki](https://en.wikipedia.org/wiki/Collatz_conjecture)]. Below is the source code, also available on GitHub: look for [randomNumbers-sqrt2.py](https://github.com/VincentGranville/Experimental-Math-Number-Theory/blob/main/Source-Code/randomNumbers-sqrt2.py).

![](images/B9780443218576000151/gr008.jpg)

## 11.4 Military-grade PRNG based on quadratic irrationals

If you produce simulations or create synthetic data that requires billions or trillions of random numbers (such as in Section [1.3.4.1](#Chp001_1-34_B9780443218576000059.xhtml)), you need a pseudorandom number generator (PRNG) that is not only fast, but in some cases truly emulates randomness. Usually you cannot have both. Congruential PRNGs are very fast and can be pretty good at emulating randomness. The Mersenne twister available in Python and in other languages has a very large period, more than enough for any practical need. Yet, depending on the seed, it has flaws caused by the lack of perfect randomness in the distribution of prime numbers. These were revealed by the **prime test** in Section [11.2.2](#Chp011_203-228_B9780443218576000151.xhtml#s0040). To the contrary, PRNGs based on irrational numbers exhibit stronger randomness if you skip the first few digits and carefully choose your numbers. But they tend to be very slow.

In this section I propose a new approach to obtain billions of trillions of digits from combinations of **quadratic irrationals** [[Wiki](https://en.wikipedia.org/wiki/Quadratic_irrational_number)] such as `$\sqrt{2}$`![Image](images/B9780443218576000151/si111.png) or `$\sqrt{7583}$`![Image](images/B9780443218576000151/si194.png), based on the algorithm in Section [11.3.3](#Chp011_203-228_B9780443218576000151.xhtml#s0070). The goal is to produce replicable random numbers. If you want to use them for strong encryption, you need to use a seed that is hardware-generated so that the same seed is never used more than once.

### 11.4.1 Fast algorithm rooted in advanced analytic number theory

The idea to get a fast algorithm is simple. Instead of producing `n` digits from a single number, I generate `r` digits from `m` different numbers, with `n = r*m`![Image](images/B9780443218576000151/si195.png). While the Python code relies only on basic additions and very few operations, the computation of `n` binary digits of a single irrational number involves very large integers. The **computational complexity** is `O(n²)`![Image](images/B9780443218576000151/si196.png). If instead you generate `r` digits from `m` numbers, the computational complexity drops to `O(r*m²)`![Image](images/B9780443218576000151/si197.png). In the most extreme and very interesting case where `r = n`![Image](images/B9780443218576000151/si198.png) and `m = 1`![Image](images/B9780443218576000151/si199.png), the computational complexity is `O(n)`![Image](images/B9780443218576000151/si200.png), just as fast as the Mersenne twister. The method is based on two deep results in number theory:

*   •  The binary digits of a quadratic irrational behave as an infinite realization of independent Bernoulli trials with equal proportions of 0 and 1. This unproven conjecture is one of the most difficult unsolved problems in mathematics. Very strong empirical results involving trillions of digits, support this hypothesis.

*   •  Two sequences of digits from irrational numbers that are linearly independent over the set `ℚ`![Image](images/B9780443218576000151/si201.png) of rational numbers have zero cross-correlation. The correlation is defined as the empirical correlation in this case.

The latter is a consequence of the following theorem: the correlation `ρ(p, q)`![Image](images/B9780443218576000151/si202.png) between the sequences (`{p b^k α}`)![Image](images/B9780443218576000151/si203.png) and (`{q b^k α}`)![Image](images/B9780443218576000151/si204.png) indexed by `k = 0, 1`![Image](images/B9780443218576000151/si205.png), and so on, where `p, q`![Image](images/B9780443218576000151/si103.png) are positive integers with no common divisors, `b > 1`![Image](images/B9780443218576000151/si100.png) is an integer, and `α` is a positive irrational, is equal to `ρ(p, q) = (p q)^(-1)`![Image](images/B9780443218576000151/si206.png). Here `{ ⋅ }`![Image](images/B9780443218576000151/si207.png) denotes the fractional part function.
