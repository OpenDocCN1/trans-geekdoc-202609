For the portfolio return $R_t$, let $\hat{R}_t$ denote the maximum value of $R_t$ throughout the time period since initial time $t_o$ to time $t$

$$\hat{R}_t = \max_{t_o \le s \le t} \{R_s\}. \tag{43.8}$$

Then the MDD of the portfolio capital as risk measure is defined by

$$\Psi(R(\mathbf{w})) = MDD(R_t(\mathbf{w})) = \max \frac{\hat{R}_t(\mathbf{w}) - R_t(\mathbf{w})}{\hat{R}_t(\mathbf{w})}. \tag{43.9}$$

The three objective functions as defined by formulas (43.5)–(43.7) and the MDD as risk measure are applicable not only for the asset portfolio of (43.1) but also for the strategy portfolios of (43.2).

# 43.3.4 *Multi-factor models for asset and strategy portfolios*

As expressed in formula (43.3), an intelligent portfolio is structured as a tree whose first-level nodes are assets, and second-level nodes are (trading) strategies. Therefore, we have two types of portfolios — assets and strategies — to optimize. Naturally, we need to generalize multi-factor models over assets to strategies.

**Multi-Factor Models for Asset Portfolios:** According to the Arbitrage Pricing Theory (Ross, 1976), irrespective of which of the three objective functions (43.5)–(43.7) is chosen, the capital allocation weight on each asset $w_i$, $i = 1,2,\mathrm{L},n$, can be expressed by a (linear) multi-factor model:

$$w_{it} = a_{i0} + \sum_{k=1}^{K} a_{ik}F_{kt}, \tag{43.10}$$

where the unknown coefficients $a_{ik}$, $k = 0,1,2,\mathrm{L},K$, are to be solved out by an optimization process with the objective function chosen from (43.5)–(43.7). For a strategic asset portfolio, the multiple factors include mainly macro-economic indices reflecting consumption growth, corporate bond spread, industrial production, inflation, commodity prices, real GDP growth, slope of yield curve, unemployment rate, etc. For stock selection, main multiple factors cover fundamental valuation, solvency, operating efficiency, operating profitability, financial risk, and liquidity risk, as well as price-based and volume-based technical factors and overall market movement and sentiment. Additional ones include alternative analyst, corporate finance policy, and social responsibility factors. Chincarini and Kim (2006, pp. 119–130) provides a classification of multiple factors important to equity portfolios. For an equity portfolio of a given country (economy), which economic indicators, fiscal policies, fundamental, technical and sentimental