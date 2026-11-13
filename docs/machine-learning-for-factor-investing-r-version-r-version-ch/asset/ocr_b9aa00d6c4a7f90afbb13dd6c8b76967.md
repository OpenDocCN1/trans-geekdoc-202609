is the only predictor with positive median correlation (this particular example seems to refute the low risk anomaly).

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

![](bbox=[0.25, 0.26, 0.69, 0.47])

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