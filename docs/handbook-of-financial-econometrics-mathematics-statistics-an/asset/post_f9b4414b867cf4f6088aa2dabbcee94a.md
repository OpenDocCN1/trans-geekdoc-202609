
## 79.4.3 Variance in EBIT

The variance in EBIT ($X$) can be defined as

$$\frac{\sum_{t=1}^{n} (X_t - \bar{X})^2}{n - 1},$$

in which $X_t$ is the earnings before interest and taxes in period $t$, and $\bar{X}$ is the average EBIT.

The total variance of EBIT can be used to measure the overall fluctuation of accounting earnings for a firm.

## 79.4.4 Capital–labor ratio

The capital–labor ratio has an impact upon the magnitude of the beta coefficient. In order to examine this impact, it is necessary to examine the capital–labor ratio.

A production function is a function that can be seen as a function of labor and capital:

$$Q = f(K, L), \qquad (79.18)$$

where $K$ is the capital and $L$ is the labor. $K/L$ (the capital–labor ratio) is generally used to measure a firm’s degree of capital intensity. Corporations often choose between increasing their capital intensity through installation of computers, use of robotics in the place of labor and increase in labor inputs. Small industries that specialize in hand-crafted or hand-tooled goods will have to increase their capital ratio in order to increase production. However, it has been the trend in recent years for many growth-oriented firms, whether manufacturers or other members of the business sector, to increase their efficiencies through increased investments in capital. Auto manufacturers are finding that robots can assemble cars of high and consistent quality at only a fraction of the cost of workers.

Capital intensity results in increased total risks and generally results in an increase in beta. Large investments are often needed to fully automate a plant or to computerize a bank completely. Taking on debt or issuing securities is normally how these capitalization increases are financed. If the capital–labor ratio is greater than one, that is, if $K$ is greater than $L$, a firm is capital intensive. If the capital–labor ratio is less than one, that is, if $K$ is less than $L$, then there is a reduction in capital intensity and a shift toward human-resource investment.

data is fine because the beta today is the same as the beta in the future. However, if the beta coefficient and standard deviation are unstable or vary through time, the analyst or manager must forecast a beta’s future value before employing it.

The available evidence on the stability of beta indicates that the beta on an individual security is generally not stable, whereas portfolios have stable betas. Hence, we are faced with the problem of forecasting future betas in order to use the CAPM for individual securities. *Beta forecasting* refers to using the historical beta estimates or other historical financial information to forecast future betas.

Beaver *et al.* (1970) argue that if it is possible to find the underlying determinants of beta, such knowledge can be used to help forecast future betas. Beaver *et al.* used accounting information from the financial statements of firms to help in the estimation of beta. They concluded that using both price and accounting information shows promise for better beta estimates.

Rosenberg and Marathe (1975) used 54 factors in six categories to estimate betas. Their factors included historical price information, price/earnings (P/E) ratios, financial ratios, and statistical measures associated with the market model. They support the notion that betas are determined by fundamental factors related to firms in addition to market pricing data.

Given that the most useful beta is one that can be forecasted correctly and that the beta is related to the financial and business risk of the firm as well as the degree to which a firm’s businesses co-vary with the total economy, it becomes necessary to determine the best way to forecast beta. The following section addresses this issue.

## 79.4.7 Market-based versus accounting-based beta forecasting

Market-based beta forecasts are based upon market information alone. Historical betas of firms are used as a proxy for their future betas. This implies that the unadjusted sample beta, $\hat{\beta}_t$, is equal to the population value of future beta:

$$\beta_{t+1}=\hat{\beta}_t.$$  (79.19a)

Alternatively, there may be a systematic relationship between the estimated betas for the first period and those of the second period, as shown by Blume (1971):

$$\hat{\beta}_{i,t+1}=a_0+a_1\hat{\beta}_{i,t}.$$  (79.19b)

in which \(\hat{\beta}_{i,t+1}\) and \(\hat{\beta}_{i,t}\) are the estimated betas for the \(i\)th firm in period \(t+1\) and \(t\), respectively. Example 79.5 provides further illustration.

**Example 79.5.** If \(\hat{a}_0 = 0.35\), \(\hat{a}_1 = 0.80\), and \(\hat{\beta}_{i,t} = 1.2\), then the future beta can be either

$$\beta_{t+1}=1.2 \quad \text{or}$$

$$\hat{\beta}_{t+1}=0.35+(0.80)(1.2)=1.31.$$

It is worthwhile to note that Value Line uses equation (79.19b) to estimate the future beta.

*Accounting-based beta forecasts* rely upon the relationships of accounting information such as the growth rate of the firm, EBIT, leverage, and the accounting beta as a basis for forecasting beta. To use accounting information in beta forecasts, the historical beta estimates are first cross-sectionally related to accounting information such as growth rate, variance of EBIT, leverage, accounting beta, and so on:

$$\beta_i=a_0+a_1X_{1i}+a_2X_{2i}+a_jX_{ji}+\cdots+a_mX_{mi}, \qquad (79.20)$$

where \(X_{ji}\) is the \(j\)th accounting variable for the \(i\)th firm, and \(a_j\) is the regression coefficient.

Some researchers have found that the historically based beta is the best forecast, whereas others have found that the accounting-based beta is best. Lee *et al.* (1986) used composite concepts to show that both accounting and market information are useful for beta forecasting. They found that neither beta forecasts based upon market information nor those based on accounting information are conditionally more efficient with respect to each other. It can be inferred, then, that each set of forecasts contains useful information for the prediction of systematic risk. The composite method can be found in Appendix 79B.

The statistical procedure used by Lee *et al.* (1986) is the ordinary least-squares method. Ordinary least squares is a statistical procedure for finding the best fitting straight line for a set of points; it seems in many respects a formalization of the procedure employed when fitting a line by eye. For instance, when visually fitting a line to a set of data, the ruler is moved until it appears that the deviations of the points from the prospective line have been minimized. If the predicted value of \(y_i\) (dependent variable) obtained from the fitted line is denoted as \(\hat{y}_i\), the prediction equation becomes

$$\hat{y}_i = \hat{\beta}_0 + \hat{\beta}_1 x_i,$$

where \(\hat{\beta}_0\) and \(\hat{\beta}_1\) represent estimates of the true \(\beta_0\) and \(\beta_1\), and \(x_i\) is an independent variable.

Graphically, the vertical lines drawn from the prediction line to each point represent the deviations of the points from the predicted value of \(y\). Thus, the deviation of the \(i\)th point is \(y_i - \hat{y}_i\).

In order to find the best fit, it is necessary to minimize the deviations of the points. A criterion of best fit that is often employed is known as the principle of least squares. It may be stated as follows: Choose the best fitting line as the one that minimizes the sum of squares of the errors (SSE) of the observed values of \(Y\) from those predicted. Expressed mathematically,

$$SSE = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2.$$

Further, the mean sum of squares of the error (MSSE) of the observed values of \(Y\) from the predicted mean could be minimized. Expressed mathematically,

$$MSSE = \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{n}.$$

Mincer and Zarnowitz (1969) suggest a decomposition of the mean squared error term into the three components representing bias, inefficiency, and random error. Mathematically, this is represented as

$$\frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{n} = (\bar{y} - \bar{\hat{y}})^2 + (S_{\hat{y}} - \rho S_y)^2 + (1 - \rho^2) S_y^2,$$

where \(\bar{y}\), \(\bar{\hat{y}}\), \(S_y\), \(S_{\hat{y}}\), and \(\rho\) represent the mean of \(y\), the mean of \(\hat{y}\), the standard deviation of \(y\), the standard deviation of \(\hat{y}\), and the correlation coefficient between \(y\) and \(\hat{y}\), respectively.

Using the ordinary least-squares method, Lee *et al.* (1986) showed that it is possible to achieve better forecasts by combining two types of betas: Using an ordinary least-squares estimate of \(\beta_{OLS}\) and a Bayesian adjustment procedure of Vasicek (1973) as defined in equation (79.21):

$$\beta_V = \frac{\frac{\bar{\beta}}{V(\bar{\beta})} + \frac{\hat{\beta}_{OLS}}{V(\hat{\beta}_{OLS})}}{\frac{1}{V(\bar{\beta})} + \frac{1}{V(\hat{\beta}_{OLS})}}, \tag{79.21}$$

where \(\beta_{OLS}\) is the least-squares estimate of a first-period individual beta, \(V(\hat{\beta}_{OLS})\) is the variance estimate of \(\beta_{OLS}\), \(\bar{\beta}\) is the cross-sectional mean value
