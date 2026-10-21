
This page intentionally left blank

## Chapter 73

## Copulas and Tail Dependence in Finance

Wing-Choong Lai and Kim-Leng Goh

## Contents

- 73.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . 2500
- 73.2 Review of Studies on Copulas . . . . . . . . . . . . . 2501
- 73.2.1 Applications of elliptical copulas . . . . . . . 2503
- 73.2.2 Applications of Archimedean copulas . . . . . . 2505
- 73.3 Definition of a Copula and Transformation . . . . . 2507
- 73.4 Definition of a Copula: A Two-Dimensional Case . . 2508
- 73.4.1 Elliptical copulas (two-tail) . . . . . . . . . . 2509
- 73.4.2 Archimedean copulas (one-tail) . . . . . . . 2510
- 73.5 Tail Dependence . . . . . . . . . . . . . . . . . . . . 2512
- 73.6 An Application . . . . . . . . . . . . . . . . . . . . . 2513
- 73.7 Conclusion . . . . . . . . . . . . . . . . . . . . . . . 2516
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . 2517
- Appendix 73A: Standardized Student’s t-Distribution . . 2521
- Appendix 73B: Density Functions for Elliptical Copulas . 2521
- Appendix 73C: Maximum Likelihood Estimation . . . . . 2522

## Abstract

This chapter discusses the copula methods for application in finance. It provides an overview of the concept of copula, and the underlying statistical theories as well as theorems involved. The focus is on two copula families, namely, the elliptical and Archimedean copulas. The Gaussian and Student’s t copulas in the family of elliptical copulas which have symmetrical tails in their distributions are explained. The Clayton and Gumbel copulas in the family of Archimedean copulas whose distributions are asymmetrical are also described. Elaborations are given on tail dependence and the associated measures for these copulas. The estimation process is illustrated using an application of the methods on the returns of two exchange series.

## Keywords

Elliptical copula • Archimedean copula • Gaussian copula • Student’s t copula • Clayton copula • Gumbel copula • Tail dependence • Maximum likelihood estimation • Sklar’s theorem • Probability integral transform • Standardized student’s t-distribution.

### 73.1 Introduction

The integration of financial markets at both the regional and global levels has introduced greater dependency in prices of financial assets. Financial markets are increasingly sensitive to news and movements in other markets. Spillover effects thus can cause financial asset prices to fluctuate excessively. One of the outcomes is that financial data are not normally distributed, and financial returns follow distributions with fat tails, as demonstrated by many recent empirical works. This poses methodological challenges in the analysis of financial returns. Methods that take into account heteroscedastic, fat tailed, and non-normally distributed financial returns are increasingly popular. One of such methods is copulas.

Following the introduction to this chapter, a quick overview of copula and a brief review of relevant past studies are presented in Section 73.2. This part also highlights the shortcoming of using copulas that assume symmetrical tails in applications in finance, especially for risk measurements in the occurrence of extreme events, such as financial crises. The associated theoretical concept, in particular, the Sklar’s theorem is explained in Section 73.3. An important key component of the method, probability integral transform and standardized Student’s t-distribution is also discussed. Subsequently, the definition of a copula for a 2D case is then presented in Section 73.4. The families of copulas, including the two-tailed elliptical copulas (Gaussian copula and Student’s t copula) and one-tailed Archimedean copulas (Clayton copula and Gumbel copula) are further introduced. Following that, the exploration of tail dependence by using copula is studied in Section 73.5. The exploration focuses on both higher and lower tail dependence, i.e., the conditional. Least squares regression or other linear correlation may under-estimate the tail dependence between financial assets, as these methods typically assume a multivariate normal distribution. However, financial data are usually not normally distributed, and the dependence between different financial time series cannot be adequately represented by linear relationships.

To overcome this problem, the copula approach is introduced. To apply this method, the standardized financial returns (e.g., stock returns and foreign exchange returns) are firstly transformed into a uniform distribution, so that a nonlinear copula can be used to model the nonlinear and non-normally distributed financial data to capture their tail dependence structure.

Copula methods are particularly relevant for study of crises, contagion and other events that lead to excessive price fluctuations of financial assets. The properties of copulas and methods of constructing multivariate copulas are explained by Czado (2010) and Durante and Sempi (2010). The econometrics aspects of the methods for dependence modeling using copulas are explained by Ibragimov and Prokhorov (2017). A review of the development of copula theory in finance and also early contributors in the field can be found in Genest et al. (2009). A broader review of the literature especially on copula based models for financial time series applications is provided by Bouye et al. (2000) and Patton (2012). Dependence structure between asset prices may vary across time. Copulas that build in time varying structure are explained by Manner and Reznikova (2012), and they conducted a simulation study to assess the performance of eight different time-varying copulas.

Applications of copula-based models in finance are increasingly popular and there is a growing body of related literature. Among others, these include the studies on financial markets and risk modeling (Du and Lai, 2017; Han and Zhou 2017; Ibragimov and Prokhorov, 2016; Karimalis and Nomikos, 2018; Kresta and Tichý, 2012; Lu et al., 2017; Lux and Papapantoleon, 2017; Min and Czado, 2014; Oh and Patton, 2018; Weiss and Supper, 2013), degree of asset dependence for portfolio diversification (Chollete et al., 2011; Tachibana, 2018; Wang et al., 2014), and cross-dependence between equity markets and other markets (Aloui and Aïssa, 2016; Delatte and Lopez, 2013; Liu et al., 2017; Nguyen and Bhatti, 2012; Ning, 2010).

This chapter considers two general groups of copulas that are commonly applied in finance, namely, the elliptical copulas and Archimedean copulas. They are illustrated in Figure 73.2. Some applications of these copulas in past studies on financial markets are highlighted next. All these studies provide clear empirical evidence of the importance of copula models for applications in finance. Underestimation of risks and dependence of financial assets typically occur when correlation methods are applied. The use of copula methods will help to avoid wrong inferences about risks that arise from extreme co-movements in different markets and modeling of dependence structure of financial time series particularly when market conditions are highly volatile.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2629_0.png)

Figure 73.2: Copula families.

### 73.2.1 Applications of elliptical copulas

Fermanian and Scaillet (2004) discussed modeling cross-dependence structures between financial assets by using copulas, including stock returns and credit spreads. They found that “the Gaussian copula is almost always chosen”, as the returns of financial assets display non-normality and strong nonlinearities. The nonlinear Gaussian copula model is also used by other researchers to capture the dependence structure between financial assets, mainly for risk controlling, pricing and hedging purposes. Bouye et al. (2000) suggested that the copula method could be broadly applied in finance, such as for asset returns modeling, as the returns of financial assets are habitually fat-tailed. Bouye, Durrleman, Nikeghbali, Riboulet, and Roncalli (2001) further highlighted that the concept of dependence in a copula function may help to aggregate risks and support the risk management industry, such as for estimating value-at-risk (VaR) for portfolios by using Gaussian copula and Student’s t copula. Credit risk measurement by using the copula approach is also introduced by Li (2000), who calibrated the parameter in the Gaussian copula based on asset default correlation. Fang and Madsen (2013) modified the Gaussian copula to be a function of random variables. They applied the modified copula on insurance and finance data, and reported that the modification improves its performance compared to other commonly used copulas.
