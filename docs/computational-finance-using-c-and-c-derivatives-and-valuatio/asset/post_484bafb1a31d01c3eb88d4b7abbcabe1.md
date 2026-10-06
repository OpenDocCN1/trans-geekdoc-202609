
$P_{duuu} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(\frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} + \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} - \rho_{13} + \rho_{23} + \rho_{24} - \rho_{34},$

$P_{duud} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(\frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} - \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} - \rho_{13} + \rho_{23} - \rho_{24} - \rho_{34},$

$P_{dudu} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(\frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} + \rho_{14} - \rho_{23} + \rho_{24} - \rho_{34},$

$P_{ddud} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(-\frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} - \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} + \rho_{13} + \rho_{14} - \rho_{24} + \rho_{34},$

$P_{dduu} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(-\frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} - \rho_{13} - \rho_{14} - \rho_{24} + \rho_{34},$

$P_{dddu} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(-\frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} - \rho_{13} + \rho_{14} - \rho_{24} + \rho_{34},$

$P_{dddd} = \frac{1}{16}\left(1 + \sqrt{\Delta t}\left(-\frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} - \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4}\right)\right) - \rho_{12} + \rho_{13} - \rho_{14} + \rho_{23} + \rho_{34},$

## 6.8 SELECTED EXERCISES

- 1. Write a program that computes the value of European and American options on the sum and difference of two-asset prices following correlated GBM.
- 2. Check your result for problem 1 by using Monte Carlo simulation to compute the value for a European option. You can generate correlated variables by using the method given in exercise 4 Chapter 4.

## TABLE 6.7 The Computed Values and Absolute Errors for European Options on the Maximum of Three Assets. A Binomial Lattice was used and We Show How Our Accuracy Depends on the Number of Time Steps. The Parameters are E = 100.0, S_1 = S_2 = S_3 = 100.0, r = 0.1, \tau = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = 0.2, \rho_{12} = -0.5, \rho_{13} = -0.5, \rho_{23} = 0.5, and q_1 = q_2 = q_3 = 0.0. The Accurate Values are 0.0526 for a Put and for Call were Computed using Monte Carlo Simulation with 10^7 Paths

| nsteps | Computed value | Error | Computed value | Error |
| :--- | :--- | :--- | :--- | :--- |
| 10 | 0.0122 | 4.041 \times 10^{-2} | 27.3180 | 5.091 \times 10^{-1} |
| 20 | 0.0295 | 2.314 \times 10^{-2} | 27.5743 | 2.528 \times 10^{-1} |
| 30 | 0.0366 | 1.600 \times 10^{-2} | 27.6589 | 1.682 \times 10^{-1} |
| 40 | 0.0404 | 1.221 \times 10^{-2} | 27.7010 | 1.261 \times 10^{-1} |
| 50 | 0.0427 | 9.868 \times 10^{-3} | 27.7263 | 1.008 \times 10^{-1} |
| 60 | 0.0443 | 8.280 \times 10^{-3} | 27.7431 | 8.396 \times 10^{-2} |

## TABLE 6.8 The Computed Values and Absolute Errors for European Options on the Minimum of Three Assets. A Binomial Lattice was used and We Show How Our Accuracy Depends on the Number of Time Steps. The Parameters are E = 100.0, S_1 = S_2 = S_3 = 100.0, r = 0.1, \tau = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = 0.2, \rho_{12} = -0.5, \rho_{13} = -0.5, \rho_{23} = 0.5, and q_1 = q_2 = q_3 = 0.0. The Accurate Values are 9.2776 for a Put and for Call were Computed using Monte Carlo Simulation with 10^7 Paths

| nsteps | Computed value | Error | Computed value | Error |
| :--- | :--- | :--- | :--- | :--- |
| 10 | 8.9646 | 3.130 \times 10^{-1} | 14.4047 | 1.800 \times 10^{-1} |
| 20 | 9.1231 | 1.545 \times 10^{-1} | 14.4963 | 8.836 \times 10^{-2} |
| 30 | 9.1749 | 1.027 \times 10^{-1} | 15.5261 | 5.857 \times 10^{-2} |
| 40 | 9.2007 | 7.694 \times 10^{-2} | 15.5409 | 4.382 \times 10^{-2} |
| 50 | 9.2161 | 6.151 \times 10^{-2} | 15.5497 | 3.499 \times 10^{-2} |
| 60 | 9.2264 | 5.123 \times 10^{-2} | 15.5556 | 2.913 \times 10^{-2} |

## TABLE 6.9 Computed Values and Absolute Errors for European Options on the Maximum of Four Assets. A Binomial Lattice was used and We Show the Accuracy Depend on the Number of Time Steps. The Parameters are E = 100.0, S_1 = S_2 = S_3 = S_4 = 100.0, r = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = \sigma_4 = 0.2, \rho_{12} = 0.5, \rho_{13} = 0.5, \rho_{23} = 0.5, and q_1 = q_2 = q_3 = q_4 = 0.0. The Accurate Values are 0.6309 for a Put and Computed using Monte Carlo Simulation with 10^7 Paths

| nsteps | Computed value | Error | Computed value | Error |
| :--- | :--- | :--- | :--- | :--- |
| 4 | 0.6548 | 2.386 \times 10^{-2} | 22.1403 | 3.096 |
| 8 | 0.6268 | 4.129 \times 10^{-3} | 23.8640 | 1.372 |
| 12 | 0.6246 | 6.275 \times 10^{-3} | 24.3630 | 8.733 \times 10^{-1} |
| 16 | 0.6251 | 5.836 \times 10^{-3} | 24.5934 | 6.429 \times 10^{-1} |
| 20 | 0.6257 | 5.167 \times 10^{-3} | 24.7270 | 5.093 \times 10^{-1} |
| 24 | 0.6263 | 4.570 \times 10^{-3} | 24.8144 | 4.219 \times 10^{-1} |
| 28 | 0.6268 | 4.074 \times 10^{-3} | 24.8762 | 3.601 \times 10^{-1} |
| 32 | 0.6272 | 3.665 \times 10^{-3} | 24.9222 | 3.141 \times 10^{-1} |

- 3. Use Monte Carlo simulation to value European options on the sum and difference of three-asset prices following GBM. You can correlate variables by using the Cholesky factorization in exercise 5 Chapter 4.
- 4. Use Monte Carlo simulation to value an option on the sum and difference of two correlated assets, X and Y, following GBM. If the price is observed at times $t_i, i=1, \dots, n$ and the values are $X_i$ and $Y_i$, then the payoff of a call option on the sum and the difference is
$C = \max(\sum_{i=1}^{n} X_i - \sum_{i=1}^{n} Y_i - K, 0)$
- 5. Use Monte Carlo simulation to value an option on the sum and difference of two-asset prices X and Y following Ornstein-Uhlenbeck processes.

## TABLE 6.10 The Computed Values and Absolute Errors for European Options on the Minimum of Four Assets. A Binomial Lattice was used and We Show How the Accuracy Depend on the Number of Time Steps. The Parameters are E = 100.0, S_1 = S_2 = S_3 = S_4 = 100.0, r = 0.1, \tau = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = \sigma_4 = 0.2, \rho_{12} = 0.5, \rho_{13} = 0.5, and q_1 = q_2 = q_4 = 0.0. The Accurate Values are 8.5394 and 4.0662 for a Call and were Computed using Monte Carlo Simulation with 10^7 Paths

| nsteps | Computed value | Error | Computed value | Error |
| :--- | :--- | :--- | :--- | :--- |
| 4 | 7.8274 | 7.120 \times 10^{-1} | 3.5676 | 4.986 \times 10^{-1} |
| 8 | 8.1571 | 3.823 \times 10^{-1} | 3.8528 | 2.134 \times 10^{-1} |
| 12 | 8.2794 | 2.600 \times 10^{-1} | 3.9300 | 1.362 \times 10^{-1} |
| 16 | 8.3429 | 1.965 \times 10^{-1} | 3.9659 | 7.944 \times 10^{-1} |
| 20 | 8.3815 | 1.579 \times 10^{-1} | 3.9868 | 1.003 \times 10^{-2} |
| 24 | 8.4075 | 1.319 \times 10^{-1} | 4.0004 | 6.577 \times 10^{-2} |
| 28 | 8.4262 | 1.132 \times 10^{-1} | 4.0101 | 5.612 \times 10^{-2} |
| 32 | 8.4402 | 9.920 \times 10^{-2} | 4.0173 | 4.894 \times 10^{-2} |

That is, using notation of Section 2.10,

$dX = \alpha_X(\mu_X - X)dt + \sigma_X dW_X,$
$dY = \alpha_Y(\mu_Y - Y)dt + \sigma_Y dW_Y,$
$\rho = \langle dW_X, dW_Y \rangle.$

## Chapter 7
# Other Financial Derivatives

## 7.1 INTRODUCTION

In the preceding sections of the book, we have only dealt with the valuation of equity derivatives. We are now going to consider some of the other types of trades such as the following:

- Interest rate derivatives.
- Foreign exchange derivatives.
- Credit derivatives.

A selection of these trades will be used by the portfolio pricing example in Chapter 8.

## 7.2 INTEREST RATE DERIVATIVES

It is not possible to make real profit without risk. For example, if we (without risk) invest £1 in a bank account, then allowing for inflation, the total number of pounds at time T will be $1+\Delta(t,T)$, where $\Delta(t,T)$ is the amount of interest accrued from t to time. Since our investment growth by the riskless interest rate, the real value which allows for inflation must still be £1, so

$DF(t,T) = \{1 + \Delta I(t,T)\} = 1,$

where $DF(t,T)$ is the discount factor from t to.

### Continuously Compounded Spot Rate

When continuous compounding is used $1 + \Delta(t,T) = \exp\{R(t,T)(T-t)\}$, where $R(t,T)$ is the annual continuously compounded spot rate between times t and T. We have

$DF(t,T)\exp\{R(t,T)(T-t)\} = 1, \quad (7.2.1)$

so the discount factor is given by

$DF(t,T) = \exp\{-R(t,T)(T-t)\}, \quad (7.2.2)$

and the continuously compounded rate is

$R(t,T) = -\frac{\log(DF(t,T))}{(T-t)}, \quad (7.2.3)$
