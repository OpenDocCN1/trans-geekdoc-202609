F(K) is the value of the cumulative function at the strike price K.

Proof. See Appendix. □

# Corollary 7.1.1. R̃c1 has the maximum ½η¹/⁴ at F(K) = 1/2.

Proof. Taking derivatives of R̃C1 given in Proposition 7.1 with respect to F(K) yields

\frac{\partial \tilde{R}_{c1}}{\partial F(K)} = \frac{3s^{2}(1-s)^{2}[(1-s)^{2}+s^{2}](1-2s)}{(1-3s+s^{2})^{2}},

(7.34)

where s = F(K), 0 < s < 1.

It can be shown that the denominator of the right-hand side of equation (7.34), (1 - 3s + s²)² is always greater than 1/16 > 0. Thus, equation (7.34) is greater than zero for s < 1/2, zero for s = 1/2, and smaller than zero for s > 1/2. Therefore, R̃c1 has maximum at s = F(K) = 1/2. Substituting s = 1/2 into R̃c1 yields ½η¹/⁴. □

The bounds given in Proposition 7.1 depend on the cumulative distribution function F(.). Corollary 7.1.1 is similar to Theorem 7 in Zhang (1994) which proves the semi-parametric upper bound of R̃c1(t). The semi-parametric bound, ½η¹/⁴, does not depend on the specific distribution function F(.) and is always greater than any distribution-dependent-bound X with the exception of one distribution F(K) = 1/2 with which R̃c1(t) = ½η¹/⁴. These results are intuitive in the sense that with some information about the cumulative function F(K), the upper bounds become higher.

# Proposition 7.2. If μ > K and the asset price is continuously distributed, then upper bounds of Rc(t) and Rp(t) subject to constraints equations (7.28)–(7.32) with the known first four moments are given by

R̃c42 = x4(μ - K), (7.35)

and R̃p42 = R̃c42(t) - μ + K, (7.36)

where x4 is the largest real root of the quartic equation

```
a x^4 - 4 x^3 + 6 x^2 - 4 x + b = 0,
```

where b = 1 - θ F^3(K),