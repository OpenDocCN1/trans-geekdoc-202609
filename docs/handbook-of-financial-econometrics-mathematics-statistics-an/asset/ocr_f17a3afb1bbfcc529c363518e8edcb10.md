(OTM) if $S/K \leq 0.97$; and in-the-money (ITM) if $S/K \geq 0.97$. A finer partition resulted in six moneyness categories. By the term to expiration, an option contract can be classified as (i) short-term (<60 days); (ii) medium-term (60–180 days); and (iii) long-term (>180 days). The sample properties of the S&P 500 call prices are reported in the paper of Bakshi *et al.* (1997) and not repeated here.

# §1.4.1.2  *Option pricing models*

We follow the framework of Bakshi *et al.* (1997) and conduct the empirical tests in the CEV model. The testing results will then be compared with those of Bakshi *et al.* (1997): (i) the Black–Scholes (BS) model, (ii) the square root stochastic-volatility (SV) model, (iii) the stochastic-volatility and stochastic-interest-rate (SVSI) model, and (iv) the stochastic-volatility random-jump (SVJ) model. The empirical results will focus on the CEV and four models as described above.

In this chapter, the CEV formula in terms of the non-central Chi-square distribution expressed by Schroder (1989) is adopted to compute option prices. IMSL (International Mathematical and Statistical Library) is used for the computation of the non-central Chi-square probabilities.

# §1.4.1.3  *Structural parameter estimation and in-sample performance*

# §1.4.1.3.1  Estimation procedure

**Step 1.** Collect $N$ option prices on the same stock and taken from the same point in time (or same day), for any $N$ greater than or equal to one plus the number of parameters to be estimated. For each $n = 1, \ldots, N$, let $\tau_n$ and $K_n$ be respectively the time-to-expiration and the strike price of the $n$-th option. Let $\hat{C}_n(t, \tau_n, K_n)$ be its observed price, and $C_n(t, \tau_n, K_n)$ its model price as determined by, for example, (equation (51.9)) with $S(t)$ and $R(t)$ taken from the market. The difference between $\hat{C}_n$ and $C_n$ is a function of the values taken by $V(t)$ and by $\Phi = \{k_R, \theta_R, \sigma_R, \kappa_V, \theta_V, \sigma_V, \lambda, \mu_J, \sigma_J\}$. For each $n$, define

$$\varepsilon_n[V(t),\Phi] \equiv \hat{C}_n(t,\tau_n,K_n)-C_n(t,\tau_n,K_n). \tag{51.16}$$

**Step 2.** Find $V(t)$ and parameter vector $\Phi$, to solve

$$\operatorname{SSE}(t) \equiv \min_{V(t),\Phi} \sum_{n=1}^{N} [\varepsilon_n[V(t),\Phi]]^2. \tag{51.17}$$