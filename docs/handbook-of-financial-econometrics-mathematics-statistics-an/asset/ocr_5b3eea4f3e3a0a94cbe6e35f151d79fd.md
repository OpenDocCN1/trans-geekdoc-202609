Table 102.1: Binomial OPM estimates of different numbers of periods.

| Number of period (n) | Increase factor (u) | Decrease factor (d) | Theoretical value of binomial OPM |
|---|---|---|---|
| 3 | 1.0460 | 0.9560 | 4.1285 |
| 4 | 1.0397 | 0.9618 | 3.8844 |
| 5 | 1.0355 | 0.9657 | 4.0306 |
| 6 | 1.0323 | 0.9687 | 3.9122 |
| 7 | 1.0299 | 0.9710 | 3.9888 |
| 8 | 1.0279 | 0.9728 | 3.9232 |
| 9 | 1.0263 | 0.9744 | 3.9657 |
| 10 | 1.0250 | 0.9757 | 3.9282 |

Previous examples show that the Excel program can be used to demonstrate the binomial option pricing model and can converge to the Black-Scholes model when the number of periods approaches infinity.

# 102.4 Compare Cox et al. and Rendleman and Bartter Methods to Derive OPM

Both Cox et al. (1979) and Rendleman and Bartter (1979) employ equation (102.13) to show how the binomial model can be reduced to the Black-Scholes model when the number of observation n approaches infinity. In this section, we briefly discuss the methods employed by these two papers.

# 102.4.1 Cox et al. method

Cox et al. (1979) used the following binomial option pricing model to derive the Black-Scholes model:

$$C = S \left[ \sum_{j=a}^{n} \frac{n!}{j!(n-j)!} p^{j} (1-p)^{n-j} \frac{u^{j} d^{n-j}}{\hat{r}^{n}} \right] - X \hat{r}^{-n} \left[ \sum_{j=a}^{n} \frac{n!}{j!(n-j)!} p^{j} (1-p)^{n-j} \right] = S B_{1}(a; n, p') - X \hat{r}^{-n} B_{2}(a; n, p),$$ (102.23)