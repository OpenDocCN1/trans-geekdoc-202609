
## 3. Problem Statement

It is challenging to create a trust portfolio to avoid the risk of investment in a single / minority stock by investing in multiple mutual funds belonging to different economic sectors. It is difficult to manage and analyze many mutual funds at real time. Going forward, we need a framework for working with multiple mutual funds in different business areas to reduce risk factors and increase profits over time. In this work we proposed a framework for portfolio managers to make investments for lots specific time horizons in mutual funds to maximize the profit of investors. Here, the evaluation is carried out in more than one sector to make sure varied portfolio control to lessen traders\` risk. As already discussed, there are numerous views of traders at the same time as making an investment their price range to advantage extra profit. Share markets are particularly sensitive, and there are various elements at once or in an indirect way related to them that manage the market place sentiment (Gottschlich and Hinz 2014). Problem can be solved using different statistical strategies and time-series analyses techniques to get maximum benefit from investment in mutual fund industry. Our goal is to suggest an analytical method to expect the proportion charge of various organizations and make investments overall capital throughout diverse sectors to earn higher income possibilities and mitigate the lowest risk.

## 4. Proposed Model

There are many challenges in developing a model to find a favorable way to help and predict a company’s mutual funds price. The main idea behind this model is `GARCH` (Generalized Autoregressive Conditional Heteroskedasticity) theory where volatility of MFs can be measured and future return can be calculated. However, in reality, it is very difficult to accurately predict a company’s MFs return price because several internal and external factors influence the mutual funds daily prices. Many parameters may not be directly related to the mutual fund market decline and flow, but are indirectly related to the mutual fund market by influencing the parameters that are directly involved in mutual fund price changes. Bad news and good news for a particular sector or company heavily affects the MFs return price. The developed model is based on historical return price of mutual fund as it reflects the impact of all events and factors that affect the mutual fund. There are several statistical techniques; prediction theories and models are developed to help you make right predictions, such as standard deviation, linear regression, non-linear regression, correlation, and time series analysis ([Figure 7.1](#ch7.xhtml#fig7_1)).

![Figure 7.1: Block diagram of proposed model.](images/fig7_1_C.jpg)

[Figure 7.1: Block diagram of proposed model.](#ch7.xhtml#R_fig7_1)

## 5. Data for Proposed Model

In this paper historical mutual fund data of CIPLA company is selected for analysis purpose. The historical mutual fund data of CIPLA from 03-Jan-2011 to 09-Aug-2023 is taken into consideration and the whole data is divided into training and testing segments. The data from 03-Jan.2011 to 06-Aug-2022 is taken for training purpose and from 07-Aug-2022 to 06-Aug-2023 considered for testing purpose. The volatility mutual fund compared and analyzed for prediction of future price of model.

## 6. Research Methodologies

### 6.1 Modeling volatility with ARCH & GARCH

In 1982, Robert Engle developed the autoregressive conditional heteroscedasticity (`ARCH`) model to predict variability over time often found in economic time series data. For this work he was awarded the 2003 Nobel Prize in Economics. The `ARCH` model estimates that the variance of the current error or innovation.

### 6.2 Time series-ARCH

Let `Z[t]` be N (0, 1) the process `X[t]` is an `ARCH(q)` process if it is stationary and if it satisfies, for all t and some strictly positive-valued process `σ[t]`, the equations:

(1)

`X[t] = σ[t]Z[t]`

(2)

```
\sigma^{2}\text{t} = \alpha_{0} + {\sum_{i = 1}^{q}{\alpha_{\text{i}}\text{X}_{\text{t} - \text{i}}^{2}}}
```

where 0 and i, I = 1, 2 …….. q.

`X[t]` is the error term in a time series regression model.

### 6.3 Time series-generalized-ARCH model (GARCH)

Before introducing `GARCH`, we discuss the exponentially weighted moving average (`EWMA`) mode that is represented by the following equation:

(3)

`σ[t]² = λσ[t−1]² + (1−λ)X[t−1]²`

Where `λ` is a constant between 0 and 1.

The `EWMA` approach has the attractive feature that relatively little data need to be stored.

We substitute for `σ²[t−1]`, and then keep doing it for m steps:

(4)

```
\sigma_{t}^{2} = (1 - \lambda){\sum_{i = 1}^{m}{\lambda^{i - 1}X_{t - 1}^{2} + \lambda^{m}\sigma_{t - m}^{2}}}
```

For large m the term `λ^m σ²[t−m]` is sufficiently small to be ignored, so it decreases exponentially.

Time series-`GARCH` processes are generalized `ARCH` processes in the sense that the squared volatility `σ²[t]` is allowed to depend on previous squared volatilities, as well as previous squared values of the process.

Let `Z[t]` be N (0, 1). The process `X[t]` is a `GARCH(p, q)` process if it is stationary and if it satisfies, for all t and some strictly positive-valued process `σ[t]`, the equation:

(5)

```
\sigma_{\text{t}}^{2} = \alpha_{0} + {\sum_{i = 1}^{q}{\alpha_{\text{i}}\text{X}_{\text{t} - \text{i}}^{2}}} + {\sum_{j = 1}^{p}{\beta_{\text{i}}\sigma_{\text{t} - \text{m}}^{2}}}
```

where `α[0] >0` and `α[i] ≥0`, I = 0, 1, 2 … q, `β[j] ≥ 0`, j=0, …., p.

### 6.4 Augmented Dickey Fuller test (ADF test)

`ADF` test is a test for a unit root in a time series sample. `ADF` test is used to test that data is stationary or not.

(6)

`X[t] = α + β[t] + yX[t−1] + ∂[1]ΔX[t−1] + ∂[p]ΔX[t−p−1] + ε[t]`

Null hypothesis: ƴ = 0⇒`X[t]` has unit roots.

## 7. General Statistics of Data

The table shows the value of mean, median, maximum, minimum, standard deviation, skewness, Kurtosis, Jarque-Bera tests. Using these statistical information we can analyze the nature of collected historical data ([Figure 7.2](#ch7.xhtml#fig7_2)).

![Figure 7.2: General statistics of data.](images/fig7_2_C.jpg)

[Figure 7.2: General statistics of data.](#ch7.xhtml#R_fig7_2)

`Hurst` exponent used to check that whether a series is mean reverting, random walking or trending. Here the H< 0.5, so time series is mean reverting. Autocorrelation of a time series measures the relation between lag values of time series and its past values. Partial autocorrelation shows degree of closeness between time series and lagged values of subsequent time intervals is constitute mathematically as autocorrelation ([Figure 7.3](#ch7.xhtml#fig7_3)).

![Figure 7.3: Daily volatility of dataset (Cipla).](images/fig7_3_C.jpg)

[Figure 7.3: Daily volatility of dataset (Cipla).](#ch7.xhtml#R_fig7_3)

## 8. Testing of Heterosecedasticity

One of the important thing assumptions of the everyday regression version is that the mistakes have the identical variance at some stage in the sample. This is likewise known as the homoscedasticity version. If the mistake variance isn’t consistent, the information is stated to be heteroscedastic. The equation is as follows:

(7)

```
Q(q) = T(T + 2){\sum_{i = 1}^{q}\frac{r(i;e_{t}^{2})}{N - i}}
```

where

(8)

```
r(i;e_{\hat{t}}^{2}) = \frac{\sum_{t = i + 1}^{T}(e_{t}^{2} - \sigma^{2})(e_{t - 1}^{2} - \sigma^{2})}{\sum_{t = 1}^{T}{(e_{t}^{2} - \sigma^{2})}^{2}}
```

Portmanteau Q test for non-linear time series models, the portmanteau test statistic based on squared residuals is used to test for independence of the series. The heteroskedasticity test show the arch effect is preset in dataset because the P value < 0.05% at 5% confidence interval and constant variable C is also statically significant because P value is less than 5% level.

## 9. Simulation Test of Model
