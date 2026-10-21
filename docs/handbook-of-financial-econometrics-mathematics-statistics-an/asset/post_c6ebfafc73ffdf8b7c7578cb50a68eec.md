
- Cox, J. C. (1996). The Constant Elasticity of Variance Option Pricing Model. *Journal of Portfolio Management*, 22 (Special issue honoring Fischer Black), 15–17.
- Cox, J. C. and Ross, S. (1976). The Valuation of Options for Alternative Stochastic Processes. *Journal of Financial Economics*, 3, 145–166.
- Cox, J. C., Ingersoll, J. E. and Ross, S. A. (1985). A Theory of the Term Structure of Interest Rates. *Econometrica*, 53, 385–408.
- Davydov, D. and Linetsky, V. (2001). Pricing and Hedging Path-Dependent Options under the CEV Process. *Management Science*, 47(7), 949–965.
- Davydov, D. and Linetsky, V. (2003). Pricing Options on Scalar Diffusions: An Eigenfunction Expansion Approach. *Operations Research*, 51, 185–209.
- Delbaen, F. and Shirakawa, H. (2002). A Note on Option Pricing for the Constant Elasticity of Variance Model. *Asia-Pacific Financial Markets*, 9, 85–99.
- Detemple, J. and Tian, W. (2002). The Valuation of American Options for a Class of Diffusion Processes. *Management Science*, 48, 917–937.
- Dyrting, S. (2004). Evaluating the Noncentral Chi-square Distribution for the Cox-Ingersoll-Ross Process. *Computational Economics*, 24, 35–50.
- Emanuel, D. C. and MacBeth, J. D. (1982). Further Results on the Constant Elasticity of Variance Call Option Pricing Model. *Journal of Financial and Quantitative Analysis*, 17, 533–554.
- Black, F. and Scholes, M. (1973). The Pricing of Options and Corporate Liabilities. *Journal of Political Economy*, 81, 637–659.
- Gibbons, M. and Jacklin, C. (1988). CEV Diffusion Estimation. Working paper, Stanford University.
- Heston, S. L. (1993). A Closed-form Solution for Options with Stochastic Volatility with Applications to Bond and Currency Options. *Review of Financial Studies*, 6, 327–343.
- Hull, J. C. and White, A. (1987). The Pricing of Options on Assets with Stochastic Volatility. *Journal of Finance*, 42, 281–300.
- Hull, J. C. and White, A. (1990). Valuing Derivative Securities Using the Explicit Finite Difference Method. *Journal of Financial and Quantitative Analysis*, 25, 87–100.
- Hull, J. C. (2002). *Options, Futures, and Other Derivatives*, 5th edn., Prentice Hall: Hoboken, NJ.
- Jackwerth, J. C. and Rubinstein, M. (2001). Recovering Stochastic Processes from Option Prices. Working Paper, London Business School.
- Jones, C. S. (2003). The Dynamics of Stochastic Volatility: Evidence from Underlying and Option Markets. *Journal of Econometrics*, 116, 181–224.
- Kamrad, B. and Ritchken, P. (1991). Multinomial Approximating Models for Options with *k*-State Variables. *Management Science*, 37, 1640–1652.
- Lee, C. F., Wu, T. and Chen, R. (2004). The Constant Elasticity of Variance Models: New Evidence from S&P 500 Index Options. *Review of Pacific Basin Financial Markets and Policies*, 7(2), 173–190.
- Leung, K. S. and Kwok, Y. K. (2006). Distribution of Occupation Times for CEV Diffusion and Pricing of α-quantile Options. *Quantitative Finance*, forthcoming.
- Lo, C. F., Tang, H. M., Ku, K. C. and Hui, C. H. (2004). Valuation of CEV Barrier Options with Time-Dependent Model Parameters. In *Proceedings of the 2nd IASTED International Conference on Financial Engineering and Applications*, Cambridge, MA.
- Lo, C. F., Yuen, P. H. and Hui, C. H. (2000). Constant Elasticity of Variance Option Pricing Model with Time-Dependent Parameters. *International Journal of Theoretical and Applied Finance*, 3(4), 661–674.
- MacBeth, J. D. and Merville, L. J. (1980). Tests of the Black–Scholes and Cox Call Option Valuation Models. *Journal of Finance*, 35, 285–301.
- Manaster, S. (1980). Discussion of MacBeth and Merville. *Journal of Finance*, 35, 301-303.
- Mayhew, S. (1995). Implied Volatility. *Financial Analysts Journal*, 51(July-August), 8-20.
- Nelson, D. B. and Ramaswamy, K. (1990). Simple Binomial Processes as Diffusion Approximations in Financial Models. *Review of Financial Studies*, 3, 393-430.
- Rubinstein, M. (1985). Nonparametric Tests of Alternative Option Pricing Models Using All Reported Trades and Quotes on the 30 Most Active CBOE Options Classes from August 23, 1976 Through August 31, 1978. *Journal of Finance*, 40, 455-480.
- Sankaran, M. (1963). Approximation to the Non-Central Chi-Square Distribution. *Biometrika*, June, 199-204.
- Schroder, M. (1989). Computing the Constant Elasticity of Variance Option Pricing Formula. *Journal of Finance*, 44(1), 211-219.
- Scott, L. O. (1987). Option Pricing When the Variance Changes Randomly: Theory, Estimation, and an Application. *Journal of Financial and Quantitative Analysis*, 22, 419-438.
- Scott, L. O. (1997). Pricing Stock Options in a Jump-Diffusion Model with Stochastic Volatility and Interest Rate: Application of Fourier Inversion Methods. *Mathematical Finance*, 7(4), 413-424.
- Stein, E. M. and Stein, J. C. (1991). Stock Price Distribution with Stochastic Volatility: An Analytical Approach. *Review of Financial Studies*, 4, 727-752.
- Tian, Y. (1994). A Re-Examination of Lattice Procedures for Interest Rate-Contingent Claims. *Advances in Futures and Option Research*, 7, 87-111.
- Wiggins, J. B. (1987). Option Values under Stochastic Volatilities. *Journal of Financial Economics*, 19, 351-372.

## Appendix 51A: The Stochastic Volatility, Stochastic Interest Rate and Random Jump Model by Bakshi et al. (1997)

Scott (1997) was the first to derive a closed-form stochastic volatility, stochastic interest rates, and random jump option pricing model (SVSI-J). Here we present the version by Bakshi et al. (1997) and follow their notations. Under the risk-neutral measure, the underlying non-dividend-paying stock price S(t) and its components are, for any t, given by

```
dS(t)/S(t) = [R(t) - λ μ_J] dt + √(V(t)) dω_S(t) + J(t) dq(t), (51A.1)
dV(t) = [θ_v - κ_v V(t)] dt + σ_v √(V(t)) dω_v(t), (51A.2)
ln[1 + J(t)] ~ N( ln[1 + μ_J] - 1/2 σ_J^2, σ_J^2 ), (51A.3)
```

where R(t) is the time-t instantaneous spot interest rate, λ is the frequency of jumps per year, V(t) is the diffusion component of return variance (conditional on no jump occurring), ω_S(t) and ω_v(t) are each a standard Brownian motion, with Cov_t[dω_S(t), dω_v(t)] ≡ ρ dt, J(t) is the percentage jump size (conditional on a jump occurring) that is lognormally, identically, and independently distributed over time, with the unconditional mean μ_J. The standard deviation of ln[1 + J(t)] is σ_J, q(t) is a Poisson jump counter with intensity λ, that is, Pr{dq(t) = 1} = λdt and Pr{dq(t) = 0} = 1 − λdt, κ_v, θ_v/κ_v and σ_v are respectively the speed of adjustment, long-run mean, and variance coefficient of the diffusion volatility V(t), q(t) and J(t) are uncorrelated with each other or with ω_S(t) and ω_v(t).

The interest rate process is assumed to follow the single-factor Cox et al. (1985) process

```
dR(t) = [θ_R − κ_R R(t)]dt + σ_R √R(t) dw_R(t), (51A.4)
```

where κ_R, θ_R/κ_R, and σ_R are the speed of adjustment, long-run mean, and volatility coefficient of the R(t) process, w_R(t) is a standard Brownian Motion assumed to be uncorrelated with any other process in the economy.

Note that the volatility risk V(t), interest rate risk R(t), and jump risk J(t)dq(t) are all rewarded in their valuation framework. The factor prices for V(t) and R(t) are respectively b_v V(t) and b_r R(t) for some constants b_v and b_r. These factors are implicitly reflected in (51A.2) and (51A.4) and adjusted through κ_v and κ_R, respectively. Therefore, the risk premiums have been internalized in the stochastic structure rather than being assumed to be zero.

The European call option price with strike price K and term-to-expiration τ by Bakshi et al. (1997) is shown as follows:

```
C(t, τ) = S(t) Π₁(t, τ; S, R, V) − K B(t, τ) Π₂(t, τ; S, R, V), (51A.5)
```

where the risk-neutral probabilities, Π₁ and Π₂, are recovered from inverting the respective characteristic functions (see Bates, 1996b, 2000; Heston, 1993; for similar treatments)

```
Π_j(t, τ; S(t), R(t), V(t)) = 1/2 + 1/π ∫₀^∞ Re[ e^{-i φ ln[K]} f_j(t, τ, S(t), R(t), V(t); φ) / (i φ) ] dφ, (51A.6)
```

for j = 1,2, with the characteristic functions f_j respectively given in (51A.7) and (51A.8). The price of a European put option on the same stock can be
