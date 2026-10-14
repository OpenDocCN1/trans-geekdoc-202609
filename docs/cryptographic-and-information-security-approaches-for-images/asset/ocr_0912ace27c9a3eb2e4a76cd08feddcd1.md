Table 4.3 Polarity and Walsh Spectrum of a Boolean Function g

| x₁ | x₂ | g | ĥg = (-1)^{g(x)} | Walsh Spectrum = Ω(ĥg)(u) = H₄. ĥg |
|---|---|---|---|---|
| 0 | 0 | 0 | 1 | 2 |
| 0 | 1 | 0 | 1 | 2 |
| 1 | 0 | 0 | 1 | 2 |
| 1 | 1 | 1 | -1 | -2 |

# 4.4 Correlation Immune Boolean Functions

Correlation immune functions were introduced by Siegenthaler [5] in order to protect some shift register based on stream ciphers against correlation attacks.

**Definition 4.35:** [*5*] *A Boolean function g in n variables is said to be correlation immune of order k, 1 ≤ k ≤ n, if any fixed subset of k variables the probability that, given the value of g(x), the k variables have any fixed set of values, is always 2^{-k}, no matter what the choice of the fixed set of k values is. In other words, g is correlation immune of order k if its values are statistically independent of any subset of input variables.*

We can formulate the definition of correlation immunity to an equivalent information theory condition. If the chosen subset of variables is (x(i₁),x(i₂),...,x(iₖ)) then the above definition of correlation immunity of order k is equivalent to the information theory condition that the information obtained about the values of (x(i₁),x(i₂),...,x(iₖ)) given is zero. Now we collect some useful equivalent conditions to correlation immunity of order 1 given in [4,6].

**Lemma 4.36:** [*4*] *A function g in n variables is correlation immune of order k, 1 ≤ k ≤ n, if and only if all of the Walsh transforms*

$$\Omega(\hat{g})(u) = \sum_{x \in \mathbb{Z}_2^n} (-1)^{g(x) \oplus \langle u,x \rangle}, \quad 0 \le \mathbf{wt}(u) \le k, \tag{4.25}$$ 

are equal to zero.

**Lemma 4.37:** [*?*] *For Boolean function g the total square correlation of g with the set of all linear functions is equal to one, that is*

$$\sum_{u \in \mathbb{Z}_2^n} c(g;\alpha_u)^2 = 1. \tag{4.26}$$