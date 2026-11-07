
![Figure 10.5 Time Series directed acyclic graph. (The most recent relationships between nodes and their parents are shown in black arrows; the gray arrows mirror these relationships in earlier periods.) ⏎](images/fig10_5.jpg)

Figure 10.5 Time Series directed acyclic graph. (The most recent relationships between nodes and their parents are shown in black arrows; the gray arrows mirror these relationships in earlier periods.) [⏎](#chapter10.xhtml#b10fig10_5)

## 10.5 Problems with Granger Causality

The tests for Granger causality are only compelling if several underlying conditions hold. The series under consideration needs to be continuous, so the technique does not apply to, for instance, binary variables. The relationship between a variable and its lagged values must be linear. The time periods need to be discrete; the number of lags should ideally be known; the series must be stationary; there should be no measurement errors; and the `VAR` should be complete, in the sense of including all relevant variables.

These conditions are stringent, and so it is no surprise that they rarely, if ever, hold. This explains the assertion by [Shojaie and Fox (2022)](#chapter10.xhtml#ref10_10), in their review of Granger causality, that “while limited and not generally informative about causal effects, the notion of Granger causality can lead to useful insights about interactions among random variables observed over time” (p. 5).

## 10.6 Business and Finance Applications

While there have been many applications of such techniques in macroeconomics, for instance, to try to determine whether `consumption` Granger causes `GDP`, or the reverse (e.g., [Wen 2007](#chapter10.xhtml#ref10_12)), applications to business are less common, but by no means unheard of. For instance, [Banerjee and Siddhanta (2015)](#chapter10.xhtml#ref10_1) try to tease out the “causal” relations between spending on marketing and profit for firms in the personal care industry in India, using quarterly data from 2001:Q2 through 2011:Q1. In plain English, they want to know whether spending on marketing works to raise profit. While it might seem self-evident that causality runs from marketing expenditure to profit, it is also possible that higher profit enables more spending on marketing, in which case (Granger) causality might flow in the other direction.

Banerjee and Siddhanta first check for stationarity and find that the two series – `ln(profit)` and `ln(spending on marketing)` – are nonstationary, but the differenced series are stationary. They then use the `AIC` criterion to determine the best lag length for the `VAR`, which they find to be nine quarters. This is relevant because marketing spending may have a lagged effect on profits – indeed, spending more on marketing now may reduce profits in the short-run, but boost them in a year or two.

Their next step is to check whether the two series are co-integrated, which will be the case if the residuals of a levels regression that includes the two (and lags) are stationary. It turns out that they are, so the errors from the cointegrating equation need to be included in the `VAR`, which is now, technically, a Vector Error-Correction (`VEC`) model. Their final step is to test for Granger causality. They find that they cannot reject the null hypothesis that profits do not drive marketing spending, but they do reject the null hypothesis that marketing spending does not drive profit. In other words, marketing spending Granger causes profit (with a lag of one-and-a-half to two years), but not vice versa.

Another example is to understand the advertising patterns of competitive firms. For example, in a consulting engagement for the telecom industry using weekly advertising spend data, we have studied whether a corporation's advertising spend is followed by its major competitor's or vice versa. If it is the former, for example, such insight enables the corporation to adjust or “optimize” advertising spend more holistically by taking into account its competitor's reaction.

## 10.7 Media Mix Modeling

More generally, time-series data are widely used in `MMM`. The idea is to quantify the impact of measures such as marketing spend for different media on performance indicators such as sales or profits. The standard technique is regression, which is “used to infer causation from observational data” ([Sun et al. 2017](#chapter10.xhtml#ref10_11)), although as we have seen, regression can only measure association, not causality.

Media mix models typically use weekly or monthly data over a period that rarely exceeds five years; older data may reflect a different market structure. This makes for small datasets unless there is regional information, in which case the analysis can be pursued at a subnational level, and benefits from a larger sample, which in turn may give greater precision. Even so, such models are often overfit, as analysts are under pressure to find strong fits (“hunting for `R`”) and high statistical significance (“p-hacking”).

A common weakness of media mix models is that they lack information on campaign spending by their competitors. [Haughton et al. (2014)](#chapter10.xhtml#ref10_4) show how it is sometimes possible to infer information about whether competitors are spending on a marketing campaign by applying a `Hidden Markov Chain`. In their study of marketing a drug to physicians, [Haughton et al. (2014)](#chapter10.xhtml#ref10_4) first use a regression approach and then formulate a directed acyclic graph (`DAG`), as discussed in [Chapter 5](#chapter5.xhtml). But they also note that their data do not incorporate autocorrelation effects, which are at the heart of trying to identify Granger causality.

## References

* Banerjee, Neelotpaul, and Somroop Siddhanta. 2015. “An Empirical Investigation on the Impact of Marketing Communication Expenditure on Firms’ Profitability: Evidence from India”. Global Business Review, 16(4): 609–622. [⏎](#chapter10.xhtml#b10ref10_1)
* Enders, W. 2010. Applied Econometric Time Series, 3rd edition. Hoboken, NJ: John Wiley & Sons. [⏎](#chapter10.xhtml#b10ref10_2)
* Gujarati, Damodar N., and Dawn Porter. 2009. Basic Econometrics, 5th edition. Boston, MA: McGraw-Hill Irwin. [⏎](#chapter10.xhtml#b10ref10_3)
* Haughton, Dominique, Guangying Hua, Danny Jin, John Lin, Qizhi Wei, and Changan Zhang. 2014. “Imputing Unknown Competitor Marketing Activity with a Hidden Markov Chain”. Journal of Direct, Data and Digital Marketing Practice, 15: 276–287. [⏎](#chapter10.xhtml#b10ref10_4)
* Johnston, John. 1972. Econometric Methods, 2nd edition. New York, NY: McGraw-Hill. [⏎](#chapter10.xhtml#b10ref10_5)
* MacKay, Alexander, and Nathan Miller. 2024. “Estimating Models of Supply and Demand: Instruments and Covariance Restrictions”. Working Paper 19-051, Harvard Business School. [⏎](#chapter10.xhtml#b10ref10_6)
* Ozcicek, Omeer, and W. Douglas McMillin. 1999. “Lag Length Selection in Vector Autoregressive Models: Symmetric and Asymmetric Lags”. Applied Economics, 31: 517–524. [⏎](#chapter10.xhtml#b10ref10_7)
* Palshikar, Girish Keshav, Manoj Ape, Sushodhan Vaishampayan, and Akshada Shinde. 2023. Causality in Time-Series: A Short Review. In Satyasai Jagannath Nanda, and Rajendra Prasad Yadav (eds.), Data Science and Intelligent Computing Techniques, India: SCRS, 723–748. [⏎](#chapter10.xhtml#b10ref10_8)
* Runge, Jakob, Andreas Gerhardus, Gherardo Varando, Veronika Eyring, and Gustau Camps-Valls. 2023. “Causal Inference for Time Series”. Nature Reviews Earth & Environment, 4: 487–505. [⏎](#chapter10.xhtml#b10ref10_9)
* Shojaie, Ali, and Emily B. Fox. 2022. “Granger Causality: A Review and Recent Advances”. Annu Rev Stat Appl, 9(1): 289–319. [⏎](#chapter10.xhtml#b10ref10_10)
* Sun, Yunting, Yueqing Wang, Yuzue Jin, David Chan, and Jim Koehler. 2017. Geo-Level Bayesian Hierarchical Media Mix Modeling. Google Inc, Mountain View, CA. [⏎](#chapter10.xhtml#b10ref10_11)
