
H. M. Markowitz (1952). Portfolio Selection, Journal of Finance, 7(1), 77–91.

D. F. Morrison (1976). Multivariate Statistical Methods, 2nd ed., New York: McGraw-Hill.

J. D. O'Pdyke (2007). Comparing Sharpe Ratio: So Where are the p-Values? Journal of Asset Management, 8(5), 208–336.

R. Roll (1977). A Critique of the Asset Pricing Theory's Tests; Part I: On Past and Potential Testability of the Theory. Journal of Financial Economics, 4, 129–176.

R. Roll and S. A. Ross (1994). On the Cross-Sectional Relation Between Expected Returns and Betas. Journal of Finance, 49, 101–121.

J. Shanken (1985). Multivariate Tests of the Zero-Beta CAPM. Journal of Financial Economics, 14, 327–348.

J. Shanken (1987). A Bayesian Approach to Testing Portfolio Efficiency. Journal of Financial Economics, 19, 195–215.

J. Shanken (1996). Statistical Methods in Tests of Portfolio Efficiency: A Synthesis. In Handbook of Statistics, 14, Elsevier Science, 693–711.

W. F. Sharpe (1964). Capital Asset Prices: A Theory of Market Equilibrium Under Conditions of Risk. Journal of Finance, 19(3), 425–442.

## Appendix 93A: Derivation of F-Test Statistics Vu by Gibbons, Ross and Shanken

Rewrite the multivariate normal system (93.1) as

r_t = α + βR_t + ε_t,

where r_t = (r_{1t},..., r_{Nt})' and R_t are the time-t excess returns of the N risky assets and the test portfolio p, respectively, α = (α_1,..., α_N)' are the N intercepts, β = (β_1,..., β_N)' are the N slopes, 1 ≤ t ≤ T. The cross-sectional disturbances ε_t = (ε_{1t},..., ε_{Nt})'~MN(0, Σ), 1 ≤ t ≤ T. In addition, the time series of random disturbances ε_1, ..., ε_T are i.i.d. Thus, the ordinary least-squares estimators â = (â_1,..., â_N)' of the N intercepts α conditional on test portfolio p's excess returns R = (R_1,..., R_T)' have a multivariate normal distribution with

```
\sqrt{\frac{T}{1 + S\hat{R}^2}}\hat{\alpha} \sim MN \left( \sqrt{\frac{T}{1 + S\hat{R}^2}}\alpha, \Sigma \right).
```

Note â and the maximum likelihood estimator of the covariance matrix Σ̂ are independent. As (T − 2)Σ̂ has a Wishart distribution, by Morrison (1976, p. 131), the F-test statistics

```
V_u = \frac{T (T - N - 1)}{N (T - 2)} \frac{\hat{\alpha}' \hat{\Sigma}^{-1} \hat{\alpha}}{(1 + S\hat{R}^2)}
```

## Bayesian Portfolio Mean-Variance Efficiency Test

has a non-central F distribution with degrees of freedom N and (T – N – 1), with the non-centrality parameter

λ = T (SR*² – SR²) / (1 + SR²),

where SR is the ex ante Sharpe ratio of the test portfolio p, and SR* is the ex ante maximum Sharpe ratio attainable by the N risky assets and the test portfolio p.

## Appendix 93B: Bayesian Test Using Posterior-Odds Ratio or Bayes Factor

The posterior-odds ratio summarizes a prior belief as well as evidence provided by the sample data about the hypotheses being tested. Specifically, let pr(H0) and pr(H1) = 1-pr(H0) denote the prior probabilities for the null and alternative hypothesis, respectively, and D is the sample dataset. The posterior-odds ratio is defined as

Posterior – odds = pr(H0|D) / pr(H1|D) = [pr(D|H0) / pr(D|H1)] × [pr(H0) / pr(H1)]. (93B.1)

Note that when the priors pr(H1) = pr(H0) = 1/2 are even, i.e., the prior-odds is one, the posterior-odds ratio can be expressed as the Bayes factor B10 as

B10 = p(D|H1) / p(D|H0). (93B.2)

From Bayes theorem, the posterior probabilities are

pr(Hk|D) = pr(D|Hk) pr(Hk) / [pr(D|H0) pr(H0) + pr(D|H1) pr(H1)].

where pr(D|Hk) is the likelihood under Hk for k = 0,1. When the hypothesis Hk , k = 0,1, is composite that involves an unknown parameter θ, the likelihood pr(D|Hk) becomes

pr(D|Hk) = ∫ pr(D|θ, Hk) π(θ) dθ , (93B.3)

where π(•) is the prior distribution of the parameter θ (Kass and Raftery, 1995).

non-centrality parameter can be rewritten as

λ(s) = T (SR*² - s²) / (1 + ŜR²),

where SR* is the ex ante maximum Sharpe ratio by the N risky assets. As the ex ante Sharpe SR = s, the joint likelihood pr(D|Hk), k = 0, 1, is
g(ŜR|SR = s) fN,T-N-1 (Vu | λ(s)), (93D.1)

where g(•|•) is the p.d.f. of ŜR, and fN,T-N-1(•|λ(s)) is the p.d.f. of the non-central F distribution. Note as λ(s) = 0 under the null H0: ρ = 1, the non-central F distribution fN,T-N-1(•|λ(s)) becomes a central F distribution fN,T-N-1(•) with N and (T – N – 1) degrees of freedom, respectively.

The joint likelihood pr(D|H1) for the composite alternative hypothesis H1: ρ < 1 is derived as follows. Let π(•) be the prior distribution of the ex ante Sharpe ratio SR, and assume the ex ante Sharpe ratio SR* equals the ex post Sharpe ratio ŜR*. By (93A.2), the joint likelihood p(D|H1) is

∫ g(ŜR|SR = w) fN,T-N-1 (Vu|λ*(w)) π(w) dw, (93D.2)

where λ*(w) = T (ŜR*² – w²) / (1 + ŜR²). The integration (93D.2) can be approximated via Monte Carlo numerical integration by drawing K realizations of the ex ante Sharpe ratio SR, namely, w1, …, wK, for sufficient large K from its prior distribution π(•) to yield

p(D|H1) = ∑j=1K g(ŜR|wj) fN,T-N-1 (Vu|λ*(wj)/K). (93D.3)

The Bayes factor in (93.8) can be obtained accordingly from (93D.2) and (93D.3).

This page intentionally left blank

- 94.4 Empirical Results of Univariate Momentum Strategies . . . . 3278
- 94.5 Interrelation of Revenue, Earnings, and Price Momentum . . 3281
- 94.5.1 Testing for dominance among the momentum strategies . . . . . . . . . . . . . . . . . . . . . . . 3281
- 94.5.2 Two-way sorted portfolio returns and momentum cross-contingencies . . . . . . . . . . . . . . . . . 3290
- 94.5.3 Combined momentum strategies . . . . . . . . . . . . 3299
- 94.6 Persistency and Seasonality . . . . . . . . . . . . . . . . . . . . 3303
- 94.6.1 Persistence of momentum effects . . . . . . . . . . . . 3303
- 94.6.2 Seasonality . . . . . . . . . . . . . . . . . 3311
- 94.7 Conclusions . . . . . . . . . . . . . . . . . . . . . . . . 3312
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . 3313
- Appendix 94: Measures of Earnings and Revenue Surprises . . . . 3316

## Abstract

This chapter examines the profits of revenue, earnings, and price momentum strategies in an attempt to understand investor reactions when facing multiple information of firm performance in various scenarios. We first offer evidence that there is no dominating momentum strategy among the revenue, earnings, and price momentums, suggesting that revenue surprises, earnings surprises, and prior returns each carry some exclusive unpriced information content. We next show that the profits of momentum driven by firm fundamental performance information (revenue or earnings) depend upon the accompanying firm market performance information (price), and vice versa. The robust monotonicity in multivariate momentum returns is consistent with the argument that the market does not only underestimate the individual information but also the joint implications of multiple information on firm performance, particularly when they point in the same direction. A three-way combined momentum strategy may offer monthly return as high as 1.44%. The information conveyed by revenue surprises and earnings surprises combined account for about 19% of price momentum effects, which finding adds to the large literature on tracing the sources of price momentum.

## Keywords

Revenue surprises ● Earnings surprises ● Post-earnings-announcement drift ● Momentum strategies.

## 94.1 Introduction

Financial economists have long been puzzled by two robust and persistent anomalies in the stock market: price momentum (see Jegadeesh and Titman, 1993, 2001; Rouwenhorst, 1998), and post-earnings-announcement drift (see Ball and Brown, 1968; Foster et al., 1984; Bernard and Thomas, 1989; Chan et al., 1996). More recently, Jegadeesh and Livnat (2006b) also find that

price reactions to revenue surprises on announcement dates only partially reflect the incremental information conveyed by the surprises. The information contents carried by revenue, earnings and stock prices are intrinsically linked through firm operations and investor evaluation, and there is evidence of mutual predictability for respective future values (e.g., see Jegadeesh and Livnat, 2006b). Nonetheless, investors, aware of the linkages among the information content conveyed by revenue, earnings and prices (see Ertimur et al., 2003; Raedy et al., 2006; Heston and Sadka, 2008), may still fail to take full account of their joint implications when pricing the stocks.

This chapter investigates how investors price securities when facing multiple information contents of a firm, particularly those firm performance information that are most accessible for investors — price, earnings, and revenue.¹ The long-short strategy of momentums, widely used in the literature, provides a venue to detect market reactions toward individual and multiple information contents. Accordingly, this study will start with documenting the revenue momentum profits and reconfirming the earnings and price momentums profits. Explorations with momentum strategies expect to yield implications that answer our two research questions. First, among the performance information of revenue surprises, earnings surprises, and prior returns, does each carry some exclusive information content that is not priced by the market? Second, do investors misreact toward the joint implications as well as individual information of firm revenue, earnings, and price?

Our first research question is explored by testing momentum dominance. One momentum strategy is said to be dominated if its payoffs can be fully captured by the information measure serving as the sorting criterion of another momentum strategy. Note that our emphasis here is not asset pricing tests; instead, as in Chan et al. (1996) and Heston and Sadka (2008), we focus on the return anomalies based on revenue surprises, earnings surprises, and

¹ Researches in the literature offer some evidence on the information linkage among revenue, earnings and prices. For example, Lee and Zumwalt (1981) find that revenue information is complementary to earnings information in security rate of return determination. Bagnoli et al. (2001) find that revenue surprises but not earnings surprises can explain stock prices both during and after the internet bubble. Swaminathan and Weintrop (1991) and Ertimur et al. (2003) suggest that the market reacts significantly more strongly to revenue surprises than to expenses surprises. Rees and Sivaramakrishnan (2001) and Jegadeesh and Livnat (2006b) also find that, conditional on earnings surprises, there is still a certain extent of market reaction to the information conveyed by revenue surprises. Ghosh et al. (2005) find that sustained increases in earnings are supported by sustained increases in revenues rather than by cost reductions.
