
long-short portfolio of these two sets, with uniform weights. Note that Fama and French (1993) use a more complex approach which also takes market capitalization into account both in the weighting scheme and also in the composition of the portfolios.

One of the advances enabled by machine learning is to automate the construction of the factors. It is for instance the approach of Feng et al. (2019). Instead of building the factors heuristically, the authors optimize the construction to maximize the fit in the cross-section of returns. The optimization is performed via a relatively deep feed-forward neural network and the feature space is lagged so that the relationship is indeed predictive, as in Equation (3.7). Theoretically, the resulting factors help explain a substantially larger proportion of the in-sample variance in the returns. The prediction ability of the model depends on how well it generalizes out-of-sample.

A third approach is that of Kelly et al. (2019) (though the statistical treatment is not machine learning per se).$^3$ Their idea is the opposite: factors are latent (unobserved) and it is the betas (loadings) that depend on the characteristics. This allows many degrees of freedom because in $r_{t,n} = \alpha_n + (\boldsymbol{\beta}_{t,n}(\mathbf{x}_{t-1,n}))'\mathbf{f}_t + \epsilon_{t,n}$, only the characteristics $\mathbf{x}_{t-1,n}$ are known and both the factors $\mathbf{f}_t$ and the functional forms $\boldsymbol{\beta}_{t,n}(\cdot)$ must be estimated. In their article, Kelly et al. (2019) work with a linear form, which is naturally more tractable.

Lastly, a fourth approach (introduced in Gu et al. (2020a)) goes even further and combines two neural network architectures. The first neural network takes characteristics $\mathbf{x}_{t-1}$ as inputs and generates factor loadings $\boldsymbol{\beta}_{t-1}(\mathbf{x}_{t-1})$. The second network transforms returns $\mathbf{r}_t$ into factor values $\mathbf{f}_t(\mathbf{r}_t)$ (in Feng et al. (2019)). The aggregate model can then be written:

```
$\mathbf{r}_t = \boldsymbol{\beta}_{t-1}(\mathbf{x}_{t-1})'\mathbf{f}_t(\mathbf{r}_t) + \boldsymbol{\epsilon}_t.$ (3.9)
```

The above specification is quite special because the output (on the l.h.s.) is also present as input (in the r.h.s.). In machine learning, autoencoders (see Section 7.6.2) share the same property. Their aim, just like in principal component analysis, is to find a parsimonious nonlinear representation form for a dataset (in this case, returns). In Equation (3.9), the input is $\mathbf{r}_t$ and the output function is $\boldsymbol{\beta}_{t-1}(\mathbf{x}_{t-1})'\mathbf{f}_t(\mathbf{r}_t)$. The aim is to minimize the difference between the two just as is any regression-like model.

Autoencoders are neural networks which have outputs as close as possible to the inputs with an objective of dimensional reduction. The innovation in Gu et al. (2020a) is that the pure autoencoder part is merged with a vanilla perceptron used to model the loadings. The structure of the neural network is summarized below.

```
returns ($\mathbf{r}_t$) \xrightarrow{NN_1} factors ($\mathbf{f}_t = NN_1(\mathbf{r}_t)$)
characteristics ($\mathbf{x}_{t-1}$) \xrightarrow{NN_2} loadings ($\boldsymbol{\beta}_{t-1} = NN_2(\mathbf{x}_{t-1})$) \big\} \longrightarrow returns ($r_t$)
```

A simple autoencoder would consist of only the first line of the model. This specification is discussed in more details in Section 7.6.2.

As a conclusion of this chapter, it appears undeniable that the intersection between the two fields of asset pricing and machine learning offers a rich variety of applications. The literature is already exhaustive and it is often hard to disentangle the noise from the great ideas in the continuous flow of publications on these topics. Practice and implementation is the only way forward to extricate value from hype. This is especially true because agents often tend to overestimate the role of factors in the allocation decision process of real-world investors (see Chinco et al. (2019b) and Castaneda and Sabat (2019)).

## 3.6 Coding exercises

- 1. Compute annual returns of the growth versus value portfolios, that is, the average return of firms with above median price-to-book ratio (the variable is called ‘Pb’ in the dataset).
- 2. Same exercise, but compute the monthly returns and plot the value (through time) of the corresponding portfolios.
- 3. Instead of a unique threshold, compute simply sorted portfolios based on quartiles of market capitalization. Compute their annual returns and plot them.

## Data preprocessing

The methods we describe in this chapter are driven by financial applications. For an introduction to non-financial data processing, we recommend two references: chapter 3 from the general purpose ML book by Boehmke and Greenwell (2019) and the monograph on this dedicated subject by Kuhn and Johnson (2019).

### 4.1 Know your data

The first step, as in any quantitative study, is obviously to make sure the data is trustworthy, i.e., comes from a reliable provider (a minima). The landscape in financial data provision is vast to say the least: some providers are well established (e.g., Bloomberg, Thomson-Reuters, Datastream, CRSP, Morningstar), some are more recent (e.g., Capital IQ, Ravenpack) and some focus on alternative data niches (see https://alternativedata.org/data-providers/ for an exhaustive list). Unfortunately, and to the best of our knowledge, no study has been published that evaluates a large spectrum of these providers in terms of data reliability.

The second step is to have a look at **summary statistics**: ranges (minimum and maximum values), and averages and medians. Histograms or plots of time series carry of course more information but cannot be analyzed properly in high dimensions. They are nonetheless sometimes useful to track local patterns or errors for a given stock and/or a particular feature. Beyond first order moments, second order quantities (variances and covariances/correlations) also matter because they help spot colinearities. When two features are highly correlated, problems may arise in some models (e.g., simple regressions, see Section 15.1).

Often, the number of predictors is so large that it is unpractical to look at these simple metrics. A minimal verification is recommended. To further ease the analysis:

- focus on a subset of predictors, e.g., the ones linked to the most common factors (market-capitalization, price-to-book or book-to-market, momentum (past returns), profitability, asset growth, volatility);
- track outliers in the summary statistics (when the maximum/median or median/minimum ratios seem suspicious).

Below, in Figure 4.1, we show a box plot that illustrates the distribution of correlations between features and the one month ahead return. The correlations are computed on a date-by-date basis, over the whole cross-section of stocks. They are mostly located close to zero, but some dates seem to experience extreme shifts (outliers are shown with black circles). The market capitalization has the median which is the most negative while volatility is the only predictor with positive median correlation (this particular example seems to refute the low risk anomaly).

```
data_ml %>%
dplyr::select(c(features_short, "R1M_Usd", "date")) %>%  # Keep few features, label & date
group_by(date) %>%  # Group: dates!
summarise_all(funs(cor(., R1M_Usd))) %>%  # Compute correlations
dplyr::select(-R1M_Usd) %>%  # Remove label
gather(key = Predictor, value = value, -date) %>%  # Put in tidy format
ggplot(aes(x = Predictor, y = value, color = Predictor)) +  # Plot
geom_boxplot(outlier.colour = "black") + coord_flip() +
theme(aspect.ratio = 0.6) + xlab(element_blank())
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_56_0.png)

**FIGURE 4.1:** Boxplot of correlations with the 1M forward return (label).

More importantly, when seeking to work with supervised learning (as we will do most of the time), the link of some features with the dependent variable can be further characterized by the smoothed **conditional average** because it shows how the features impact the label. The use of the conditional average has a deep theoretical grounding. Suppose there is only one feature \(X\) and that we seek a model \(Y = f(X) + \text{error}\), where variables are real-valued. The function \(f\) that minimizes the average squared error \(\mathbb{E}[(Y - f(X))^2]\) is the so-called regression function (see Section 2.4 in Hastie et al. (2009)):

\(f(x) = \mathbb{E}[Y|X=x].\) (4.1)

In Figure 4.2, we plot two illustrations of this function when the dependent variable (\(Y\)) is the one month ahead return. The first one pertains to the average market capitalization over the past year and the second to the volatility over the past year as well. Both predictors have been uniformized (see Section 4.4.2 below) so that their values are uniformly distributed in the cross-section of assets for any given time period. Thus, the range of features is \([0, 1]\) and is shown on the \(x\)-axis of the plot. The grey corridors around the lines show 95% level confidence interval for the computation of the mean. Essentially, it is narrow when both (i) many data points are available and (ii) these points are not too dispersed.

```
data_ml %>%  # From dataset:
ggplot(aes(y = R1M_Usd)) +  # Plot
geom_smooth(aes(x = Mkt_Cap_12M_Usd, color = "Market Cap")) +  # Cond. Exp. Mkt_cap
geom_smooth(aes(x = Vol1Y_Usd, color = "Volatility")) +  # Cond. Exp. Vol
```
