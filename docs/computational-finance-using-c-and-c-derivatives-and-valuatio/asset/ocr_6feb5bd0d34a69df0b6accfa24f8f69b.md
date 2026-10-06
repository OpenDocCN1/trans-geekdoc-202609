# 200 CHAPTER | 6 Multi-asset Options

**TABLE 6.9** Computed Values and Absolute Errors for European Options on the Maximum of Four Assets. A Binomial Lattice was used and We Show the Accuracy Depend on the Number of Time Steps. The Parameters are E = 100.0, S1 = S2 = S3 = S4 = 100.0, r = 1.0, σ1 = σ2 = σ3 = σ4 = 0.2, ρ12 = 0.5, ρ13 = 0.5, ρ23 = 0.5, and q1 = q2 = q3 = q4 = 0.0. The Accurates are 0.6309 for a Put and Computed using Monte Carlo Simulation with 10⁷ Paths

| nsteps | Computed value | Error | Computed value | Error |
|---|---|---|---||
| 4 | 0.6548 | 2.386 × 10⁻² | 22.1403 | 3.096 |
| 8 | 0.6268 | 4.129 × 10⁻³ | 23.8640 | 1.372 |
| 12 | 0.6246 | 6.275 × 10⁻³ | 24.3630 | 8.733 × 10⁻¹ |
| 16 | 0.6251 | 5.836 × 10⁻³ | 24.5934 | 6.429 × 10⁻¹ |
| 20 | 0.6257 | 5.167 × 10⁻³ | 24.7270 | 5.093 × 10⁻¹ |
| 24 | 0.6263 | 4.570 × 10⁻³ | 24.8144 | 4.219 × 10⁻¹ |
| 28 | 0.6268 | 4.074 × 10⁻³ | 24.8762 | 3.601 × 10⁻¹ |
| 32 | 0.6272 | 3.665 × 10⁻³ | 24.9222 | 3.141 × 10⁻¹ |

+   3. Use Monte Carlo simulation to value European options on the sum and difference of three-asset prices following correlated GBM. You can correlate variables by using the Cholesky factorization in exercise 5 Chapter 4.
4. Use Monte Carlo simulation to value an option on the sum and difference of the average values over two correlated assets, X and Y, following GBM. If the price is observed at times $t_i, i=1, \dots, n$ and the values are $X_i$ and $Y_i$, then the payoff of a call option on the sum

and on the difference is

```
$C = \max(\sum_{i=1}^{n} X_i - \sum_{i=1}^{n} Y_i - K, 0)$
```

+   5. Use Monte Carlo simulation to value an option on the sum and difference of two-asset prices X and Y following correlated Ornstein-Uhlenbeck