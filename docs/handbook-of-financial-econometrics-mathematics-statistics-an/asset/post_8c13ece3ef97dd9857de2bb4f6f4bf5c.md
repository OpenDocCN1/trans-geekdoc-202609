
Taylor, S. J. (2007). Modelling Financial Time Series (Stephen J. Taylor, Modelling Financial Time Series (Second Edition), World Scientific Publishing).

Taylor, S. J. and Xu, X. (1997). The Incremental Volatility Information in One Million Foreign Exchange Quotations. Journal of Empirical Finance, 4(4), 317-340.

Tetlock, P. C., Saar-Tsechansky, M. and Macskassy, S. (2008). More than Words: Quantifying Language to Measure Firms' Fundamentals. J. Finance 63, 3, pp. 1437-1467.

Viswanath, B., Mislove, A., Cha, M. and Gummadi, K. P. (2009). On the Evolution of User Interaction in Facebook. In Proceedings of the 2nd ACM workshop on Online social networks (ACM), 37-42.

Wang, C., Cao, L., Wang, M., Li, J., Wei, W. and Ou, Y. (2011). Coupled Nominal Similarity in Unsupervised Learning. In Proceedings of the 20th ACM International Conference on Information and Knowledge Management (CIKM-11), ACM, 973-978.

Wang, S., He, L., Stenneth, L., Yu, P. S. and Li, Z. (2015). Citywide Traffic Congestion Estimation with Social Media. In Proceedings of the 23rd SIGSPATIAL International Conference on Advances in Geographic Information Systems, ACM, 34.

Wang, W. Y. and Hua, Z. (2014). A Semiparametric Gaussian Copula Regression Model for Predicting Financial Risks from Earnings Calls. In The 51st Annual Meeting of the Association for Computational Linguistics (ACL-14), 1155-1165.

Wichard, J. D., Merkwirth, C. and Ogorzałek, M. (2004). Detecting Correlation in Stock Market. Physica A: Statistical Mechanics and its Applications, 344(1), 308-311.

Xie, B., Passonneau, R. J., Wu, L. and Creamer, G. G. (2013). Semantic Frames to Predict Stock Price Movement. In Proceedings of the 51st Annual Meeting of the Association for Computational Linguistics, 873-883.

Zhang, X., Shi, J., Wang, D. and Fang, B. (2017a). Exploiting Investors Social Network for Stock Prediction in China's Market.

Zhang, X., Su, Y., Qu, S., Xie, S., Fang, B. and Yu, P. S. (2017b). IAD: Interaction-Aware Diffusion Framework in Social Networks. Tech. rep., Beijing University of Posts and Telecommunications, Key Laboratory of Trustworthy Computing and Service.

Zhang, X. and Yao, Y. (2011). Guba Dataset, https://pan.baidu.com/s/1i5zAW h3, (accessed 17.01.15).

Zhang, X., Yao, Y., Ji, Y. and Fang, B. (2016). Effective and Fast Near Duplicate Detection via Signature-based Compression Metrics. Mathematical Problems in Engineering 2016.

Zhang, X. and Yunjia, Z. (2017). Financial Web News Dataset, https://pan.baidu.com/s/1mhCLJ Ji, (accessed 17.01.15).

Zhang, X., Zhang, Y., Wang, S., Yao, Y., Fang, B. and Yu, P. S. (2018). Improving Stock Market Prediction via Heterogeneous Information Fusion. Knowledge-Based Systems, 143, 236-247. doi:https://doi.org/10.1016/j.knosys.2017.12.025, http://www.sciencedirect.com/science/article/pii/S0950705117306032.

Zhao, W. X., Jiang, J., Yan, H. and Li, X. (2010). Jointly Modeling Aspects and Opinions with a Maxent-Ida Hybrid. In Proceedings of the 2010 Conference on Empirical Methods in Natural Language Processing, Association for Computational Linguistics, 56-65.

## Chapter 19

## Sourcing Alpha in Global Equity Markets: Market Factor Decomposition and Market Characteristics

Subhransu S. Mohanty

## Contents

- 19.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 738
- 19.1.1 Market risk, factor risk and sources of alpha . . . . . 739
- 19.2 Dataset . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 741
- 19.3 Working with the Capital Asset Pricing Model (CAPM) and the Market Factor Models . . . . . . . . . . . . . . . . . . 742
- 19.3.1 The capital asset pricing model (CAPM) . . . . . . . . . . . 742
- 19.3.2 The Fama–French 3-factor model . . . . . . . . . . . . . . 743
- 19.3.3 Carhart’s 4-factor model . . . . . . . . . . . . . . . . . . . 744
- 19.3.4 Fama and French 5-factor model . . . . . . . . . . . . . . . 745
- 19.3.5 Asness, Frazzini and Pedersen’s 5-factor and 6-factor models . . . . . . . . . . . . . . . . . . . . . . . . . . . . 746
- 19.4 Working with Market and Market Factor Models: Where They Work, Where Not (Data Analysis and Interpretation) . . . 747
- 19.4.1 Market characteristics: Market risk and factor risks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 748

are diversifiable based on the variation in risks, rather than holding a market where risk is non-diversifiable.

Hence, we assume that each and every investor would like to create a portfolio with an optimal combination of risky assets which maximizes return. An investor would keep cash in the composition of investments only if there is a fear of loss on risky assets. In Keynesian terms of liquidity preference theory and elasticity of demand for cash, this explains the speculative motives of investors.

### 19.1.1 Market risk, factor risk and sources of alpha

Though the origin of asset price behavior is the random walk theory, there are criticism to its independent incremental assumption (Cootner) and stationarities (Osborne). Similarly, Sharpe-Lintner’s capital asset pricing model (CAPM), being the most significant development in modern capital market theory is also subject to criticism of assuming homogeneity of investors’ return expectations within the Markowitz’s mean–variance optimization framework. While the model predicts that the expected excess return from holding an asset is proportional to the covariance of its return with the market portfolio (its “beta”), empirical work of Black, Jensen, and Scholes demonstrated that “low beta” assets earn a higher return on average and “high beta” assets earn a lower return on average. Further as Tobin observes, “for a given amount of risk, an investor always prefers a greater to a smaller expectation of return”. The utility theorists, behavioral finance researchers and psychologists have a number of explanations to investors’ varied risk and return preferences. Secondly, the model also assumes a single period, i.e., the investment opportunity sets do not change over time, though in reality, they do. Intertemporal studies show that risk and return associated with assets and markets as well as their correlations change over time. Despite the above, the CAPM provides a strong basis of the relationship among asset returns and explains a significant fraction of the variation in asset returns.

Continued academic and non-academic empirical research shows there are many anomalies to counter the risk-return efficiency of assets and their markets. Merton’s (1973) says up to four unspecified state variables lead to risk premiums that are not captured by the market risk. Since these unspecified state variables haven’t been identified and measured, the later empirical studies mostly deal with excess return (Alpha) generation

through factor portfolios providing different combinations of exposures to the unknown state variables within the relevant multifactor efficient set along with the market portfolio and the risk-free asset. Notable among them are the Fama–French 3-factor model, the Carhart 4-factor model, the Fama–French 5-factor model and the Asness and Frazzini’s 6-factor model. All these models are highly intuitive and provide additional cross-sectional risk-return dimensions to the market risk. These factors are size, value, momentum, profitability, investment, quality and low beta. These factors may have some interrelationship with each other, as there may be some common characteristics between them too. In fact, many of these factors have been used by practicing investment managers in order to achieve excess return and subsequently, index developers have started creating factor-specific (style) indices so that investors and investment managers can have an alternative way of enhancing Alpha by harvesting the risk-premia tilt associated with such factors. The decomposition of factor Alphas also helps in measuring and monitoring risk exposure and performance attribution of investment portfolios in a more granular and accurate fashion.

Summarizing the above, in a market context and within the risk-return efficiency framework, the size (Small Minus Big — SMB) factor typically divides the market into two segments, small and big. Hence it covers the entire market and in our case, the country market representative — the index. Similarly, the valuation (High minus Low — HML) factor divides an entire market into two segments, i.e., based on their book-to-market price ratio. When these two factors are taken into account, we are evaluating the impact of these factor betas on overall market risk and these factors have interrelationship among themselves, as there could be high or low valuation situations both in the small as well as big-sized companies. In general, small companies are considered more risky than the big ones as they are less liquid, though some of them may be highly profitable, stable and growing at a faster rate. Similarly, high book-to-market, though technically pointing to the possibility of delivering better returns in the future, could instead be due to higher retention policy, not having enough opportunities to grow further and so on. Hence, the impact of these two factor (SMB and HML) betas could be positive or negative on market risk.

The two factors, such as RMW (profitability premium) and CMA (investment premium) provide another dimension to stock characteristics, i.e., more profitable companies are expected to have a higher valuation compared to the less profitable ones and high book-equity growth means a lower valuation
