
- M. S. Chow (1987). A Complete Class Theorem for Estimating a Noncentrality Parameter. *The Annals of Statistics*, 15, 800–804.
- J. Cochrane and J. Saa-Requejo (2000). Beyond Arbitrage: Good-Deal Asset Price Bounds in Incomplete Markets. *Journal of Political Economy*, 108, 79–119.
- M. R. Gibbons, S. A. Ross, and J. Shanken (1989). A Test of the Efficiency of a Given Portfolio. *Econometrica*, 57, 1121–1152.
- J. D. Jobson and B. M. Korkie (1981). Performance Hypothesis Testing with the Sharpe and Treynor Measures. *Journal of Finance*, 36, 889–908.
- N. L. Johnson, S. Kotz, and N. Balakrishnan (1995). *Continuous Univariate Distributions*, Vol. 2, Wiley, New York.
- R. Kan and D. R. Smith (2008). The Distribution of the Sample Minimum Variance Frontier. *Management Science*, 54, 1364–1380.
- A. W. Lo (2002). The Statistics of Sharpe Ratios. *Financial Analysts Journal*, 58, 36–52.
- A. C. MacKinlay (1995). Multifactor Models do not Explain Deviations from the CAPM. *Journal of Financial Economics*, 38, 3–28.
- R. A. Maller, R. B. Durand, and H. Jafarpour (2010). Optimal Portfolio Choice Using the Maximum Sharpe Ratio. *Journal of Risk*, 12, 49–73.
- R. C. Merton (1980). On Estimating the Expected Return on the Market: An Exploratory Investigation. *Journal of Financial Economics*, 8, 323–361.
- M. D. Perlman and U. A. Rasmussen (1975). Some Remarks on Estimating a Noncentrality Parameter. *Communications in Statistics*, 4, 455–468.
- C. Zhang (2009). Testing the APT with the Maximum Sharpe Ratio of Extracted Factors. *Management Science*, 55, 1255–1266.

## Appendix 74A: Detailed Derivations

For standard Normal distribution, we have

$$\frac{1}{\sqrt{2\pi}} \int_{y_1}^{+\infty} e^{-\frac{y^2}{2}} dy = 1 - N(y_1), \tag{74A.1}$$ $$\int_{y_1}^{+\infty} y e^{-\frac{y^2}{2}} dy = e^{-\frac{y_1^2}{2}}, \tag{74A.2}$$ $$\frac{1}{\sqrt{2\pi}} \int_{y_1}^{+\infty} y^2 e^{-\frac{y^2}{2}} dy = 1 - N(y_1) + \frac{1}{\sqrt{2\pi}} y_1 e^{-\frac{y_1^2}{2}}. \tag{74A.3}$$

For a normal distributed random variable $\tilde{x} \sim N(\mu, \sigma^2)$

$$\int_0^{+\infty} x^2 f(x) dx = \int_{-\frac{\mu}{\sigma}}^{+\infty} \frac{(\mu + \sigma y)^2}{\sqrt{2\pi}} e^{-\frac{y^2}{2}} dy$$ $$= \mu^2 \left[1 - N\left(-\frac{\mu}{\sigma}\right)\right] + \frac{2}{\sqrt{2\pi}} \mu\sigma e^{-\frac{\mu^2}{2\sigma^2}} - \frac{1}{\sqrt{2\pi}} \left(\mu\sigma e^{-\frac{\mu^2}{2\sigma^2}} + \sigma^2 \left[1 - N\left(-\frac{\mu}{\sigma}\right)\right]\right)$$ $$= (\mu^2 + \sigma^2) \left[1 - N\left(-\frac{\mu}{\sigma}\right)\right] + \frac{\mu\sigma}{\sqrt{2\pi}} e^{-\frac{\mu^2}{2\sigma^2}}. \tag{74A.4}$$

Substitute $\mu$ with $\mu_g$ and $\sigma^2$ with $\frac{\sigma_g^2(1+\hat{\psi}^2)}{T}$

$$E\left[\int_0^{+\infty} x^2 f\left(x|\hat{\psi}^2\right) dx\right] = E\left[\left(\mu_g^2 + \frac{\sigma_g^2\left(1+\hat{\psi}^2\right)}{T}\right)\left[1 - N\left(-\frac{\mu_g\sqrt{T}}{\sigma_g\sqrt{1+\hat{\psi}^2}}\right)\right] + \frac{\mu_g\sigma_g\sqrt{1+\hat{\psi}^2}}{\sqrt{2\pi}\sqrt{T}}e^{-\frac{\mu_g^2 T}{2\sigma_g^2(1+\hat{\psi}^2)}}\right]. \quad (74A.5)$$

Let $U = -\frac{\mu_g\sqrt{T}}{\sigma_g\sqrt{1+\hat{\psi}^2}}$. Using integration by parts

$$E\left[\int_0^{+\infty} x^2 f\left(x|\hat{\psi}^2\right) dx\right] = \mu_g^2\left\{\left[E[1 - N(U)]\right] + E\left[\frac{1}{U^2}[1 - N(U)]\right] + E\left[-\frac{1}{\sqrt{2\pi}U}e^{-\frac{U^2}{2}}\right]\right\}. \quad (74A.6)$$

## Chapter 75: Errors-in-Variables and Reverse Regression

Shafiqur Rahman and Cheng Few Lee

### Contents

- 75.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . 2548
- 75.2 Errors-in-Variables Problems . . . . . . . . . . . . . . . 2552
- 75.3 Direct and Reverse Regression Technique . . . . . . . . . 2554
- 75.4 Standard Error of Reverse Regression Estimates . . . . . . 2556
- 75.5 Application to Capital Market Research . . . . . . . . . . 2557
- 75.6 Conclusions . . . . . . . . . . . . . . . . . . . . . . . . . 2559
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . 2559
- Appendix 75A . . . . . . . . . . . . . . . . . . . . . . . . . . 2561

### Abstract

Errors-in-variables (EIVs) and measurement errors are commonly encountered in asset prices and returns in capital market. This study examines the explanatory power of direct and reverse regression technique to bound the true regression estimates in the presence of EIVs and measurement error. We also derive standard error of reverse regression estimates to compute t-ratio of these estimates for the purpose of testing their statistical significance.

### Keywords

Measurement error ● Errors-in-variables ● Direct and reverse regression.

### 75.1 Introduction

Measurement error in observed variables of regression models causes a biased estimate of regression coefficients. Measurement error results in coefficient estimates being biased downward in simple regression and biased downward or upward in multiple regression (Cready *et al.*, 2001). Reverse regression technique (Maddala, 1977; Leamer, 1978; Greene, 2012) is used to mitigate biases resulting from the measurement error. It provides a means of drawing inferences that are robust to measurement error biases. In an analysis of the errors-in-variables (EIVs) problem in which both dependent and independent variables are measured with error, Frisch (1934) demonstrated that direct and reverse regression estimates could be used together to consistently bound the true regression coefficients.

Klepper and Leamer (1984) extended Frisch’s (1934) work by presenting a complete *k*-variable generalization of direct and reverse regression. Several studies applied the *k*-variable direct and reverse regression technique (see, for example, Conway and Roberts, 1983, 1984; Goldberger, 1984; Klepper *et al.*, 1993; Cready *et al.*, 2001). Reverse regression technique has also been employed in examining information content of security prices with respect to accounting earnings (Beaver *et al.*, 1987), cross-sectional variations in earnings response coefficient (Collins and Kothari, 1989), the small-firm effect (Booth and Smith, 1985) and mutual fund performance evaluation (Rahman *et al.*, 1991), to overcome the bias-associated measurement errors in observed variables.[^1] Table 75.1 presents a list of studies that applied the reverse regression technique along with their models and empirical results.

Rahman *et al.* (1991) derived the standard error of reverse regression estimates of Frisch’s (1934) two-variable regression. However, there is no prior research in the extant literature calculating and reporting the standard error of reverse regression estimates for a *k*-variable case. This study fills the void in the literature. The purpose of this study is to derive standard error of reverse regression estimates of a *k*-variable generalization of Klepper and Leamer (1984). The rest of the chapter is organized as follows. Section 75.2 discusses EIVs in asset returns and benchmark returns and their impact

### Table 75.1: Survey of reverse regression studies.

| Study | Model | Description and results |
|-------|-------|-------------------------------------|
| Beaver et al. (1987) | Simple Regression | Examined the incremental explanatory power of lagged values of percentage change in price on percentage change in accounting earnings and concluded that reverse regression provides a more intuitive and efficient way to assess the information content of security prices. |
| Booth and Smith (1985) | Simple Regression | Examined whether the small-firm effect can be attributed to nonsynchronous trading or benchmark error and concluded that the small-firm effect cannot be attributed to either nonsynchronous trading or benchmark error. |
| Rahman et al. (1991) | Simple Regression | Used direct and reverse regression to provide interval estimates of performance and risk measures for mutual funds in the presence of specification error and measurement error. The empirical results support the conclusion of prior studies that mutual fund managers are unable to outperform the market. These results are free of specification and measurement errors. |
| Collins and Kothari (1989) | Multiple Regression | Examined cross-sectional and temporal variation in stock price change associated with a given unexpected earnings change (the earnings response coefficient) and employed reverse regression to address the measurement error problem and to significantly improve earnings/returns relationship. The results show that the earnings response coefficient (ERC) is a function of risk-free rate and the riskiness, growth and/or persistence of earnings. |
| Conway and Roberts (1983); Conway and Roberts (1984) | Multiple Regression | Employed direct and reverse regression to investigate fairness and employment discrimination in the presence of measurement errors in recorded job qualification. Income or salary was regressed on several measures of productivity or job qualification and gender dummy. The main conclusion is that examination of salary discrimination necessitates data from both direct and reverse regression for determining what the data should reveal about fairness. |

[^1]: Beaver *et al.* (1987), Booth and Smith (1985), and Rahman *et al.* (1991) used Frisch’s two-variable reverse regression technique while Collins and Kothari (1989) used a *k*-variable reverse regression technique. However, reverse regression technique used in Collins and Kothari (1989) differs from Klepper and Leamer’s (1984) reverse regression technique because of interdependence among explanatory variables in Collins and Kothari (1989). See Cready *et al.* (2001) for details.
