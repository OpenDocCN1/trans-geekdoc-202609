
Posterior to the discovery of these stylized facts, some contributions have aimed at building theoretical models that capture these properties. We cite a handful below:

- size and value: Berk et al. (1999), Daniel et al. (2001b), Barberis and Shleifer (2003), Gomes et al. (2003), Carlson et al. (2004), Arnott et al. (2014);
- momentum: Johnson (2002), Grinblatt and Han (2005), Vayanos and Woolley (2013), Choi and Kim (2014).

In addition, recent bridges have been built between risk-based factor representations and behavioural theories. We refer essentially to Barberis et al. (2016) and Daniel et al. (2020a) and the references therein.

While these factors (i.e., long-short portfolios) exhibit time-varying risk premia and are magnified by corporate news and announcements (Engelberg et al. (2018)), it is well-documented (and accepted) that they deliver positive returns over long horizons. We refer to Gagliardini et al. (2016) and to the survey Gagliardini et al. (2019), as well as to the related bibliography for technical details on estimation procedures of risk premia and the corresponding empirical results. A large sample study that documents regime changes in factor premia was also carried out by Ilmanen et al. (2019). Moreover, the predictability of returns is also time-varying (as documented in Farmer et al. (2019), Tsiaras et al. (2020) and Liu et al. (2020)), and estimation methods can be improved (Johnson (2019)).

In Figure 3.2, we plot the average monthly return aggregated over each calendar year for five common factors. The risk free rate (which is not a factor per se) is the most stable, while the market factor (aggregate market returns minus the risk-free rate) is the most volatile. This makes sense because it is the only long equity factor among the five series.

```
FF_factors %>%
mutate(date = year(date)) %>% # Turn date into year
gather(key = factor, value = value, - date) %>% # Put in tidy shape
group_by(date, factor) %>% # Group by year and factor
summarise(value = mean(value)) %>% # Compute average return
ggplot(aes(x = date, y = value, color = factor)) + # Plot
geom_line() + coord_fixed(500) # Fix x/y ratio
```

The individual attributes of investors who allocate towards particular factors is a blossoming topic. We list a few references below, even though they somewhat lie out of the scope of this book. Betermier et al. (2017) show that value investors are older, wealthier and face lower income risk compared to growth investors who are those in the best position to take financial risks. The study Cronqvist et al. (2015b) leads to different conclusions: it finds that the propensity to invest in value versus growth assets has roots in genetics and in life events (the latter effect being confirmed in Cocco et al. (2020), and the former being further detailed in a more general context in Cronqvist et al. (2015a)). Psychological traits can also explain some factors: when agents extrapolate, they are likely to fuel momentum (this topic is thoroughly reviewed in Barberis (2018)). Micro- and macro-economic consequences of these preferences are detailed in Bhamra and Uppal (2019). To conclude this paragraph, we mention that theoretical models have also been proposed that link agents' preferences and beliefs (via prospect theory) to market anomalies (see for instance Barberis et al. (2020)).

Finally, we highlight the need of replicability of factor premia and echo the recent editorial by Harvey (2020). As is shown by Linnainmaa and Roberts (2018) and Hou et al. (2020), many proclaimed factors are in fact very much data-dependent and often fail to deliver sustained profitability when the investment universe is altered or when the definition of variable changes (Asness and Frazzini (2013)).

![](img/8861a37f775d09b4ba7a5151f604d9f5_40_0.png)

**FIGURE 3.2:** Average returns of common anomalies (1963-2020). Source: Ken French library.

Campbell Harvey and his co-authors, in a series of papers, tried to synthesize the research on factors in Harvey et al. (2016), Harvey and Liu (2019a) and Harvey and Liu (2019b). His work underlines the need to set high bars for an anomaly to be called a ‘true’ factor. Increasing thresholds for $p$-values is only a partial answer, as it is always possible to resort to data snooping in order to find an optimized strategy that will fail out-of-sample but that will deliver a $t$-statistic larger than three (or even four). Harvey (2017) recommends to resort to a Bayesian approach which blends data-based significance with a prior into a so-called Bayesianized $p$-value (see subsection below).

Following this work, researchers have continued to explore the richness of this zoo. Bryzgalova et al. (2019a) propose a tractable Bayesian estimation of large-dimensional factor models and evaluate all possible combinations of more than 50 factors, yielding an incredibly large number of coefficients. This combined with a Bayesianized Fama and MacBeth (1973) procedure allows to distinguish between pervasive and superfluous factors. Chordia et al. (2020) use simulations of 2 million trading strategies to estimate the rate of false discoveries, that is, when a spurious factor is detected (type I error). They also advise to use thresholds for $t$-statistics that are well above three. In a similar vein, Harvey and Liu (2020) also underline that sometimes *true* anomalies may be missed because of a one time $t$-statistic that is too low (type II error).

The propensity of journals to publish positive results has led researchers to estimate the difference between reported returns and *true* returns. Chen and Zimmermann (2020) call this difference the *publication bias* and estimate it as roughly 12%. That is, if a published average return is 8%, the actual value may in fact be closer to (1-12%)8%=7%. _Qualitatively, this estimation of 12% is smaller than the out-of-sample reduction in returns found in McLean and Pontiff (2016)._

## Predictive regressions, sorts, and _p_-value issues

For simplicity, we assume a simple form:

```
$r = a + bx + e$,
(3.2)
```

where the vector $\boldsymbol{r}$ stacks all returns of all stocks and $\boldsymbol{x}$ is a lagged variable so that the regression is indeed predictive. If the estimate $\hat{b}$ is significant given a specified threshold, then it can be tempting to conclude that $\boldsymbol{x}$ does a good job at predicting returns. Hence, long-short portfolios related to extreme values of $\boldsymbol{x}$ (mind the sign of $\hat{b}$) are expected to generate profits. This is unfortunately often false because $\hat{b}$ gives information on the past ability of $\boldsymbol{x}$ to forecast returns. What happens in the future may be another story.

Statistical tests are also used for portfolio sorts. Assume two extreme portfolios are expected to yield very different average returns (like very small cap versus very large cap, or strong winners versus bad losers). The portfolio returns are written $r_t^+$ and $r_t^-$. The simplest test for the mean is $t = \sqrt{T} \frac{m_{r^+} - m_{r^-}}{\sigma_{r_+ - r_-}}$, where $T$ is the number of points and $m_{r_\pm}$ denotes the means of returns and $\sigma_{r_+ - r_-}$ is the standard deviation of the difference between the two series, i.e., the volatility of the long-short portfolio. In short, the statistic can be viewed as a scaled Sharpe ratio (though usually these ratios are computed for long-only portfolios) and can in turn be used to compute $p$-values to assess the robustness of an anomaly. As is shown in Linnainmaa and Roberts (2018) and Hou et al. (2020), many factors discovered by researchers fail to survive in out-of-sample tests.

One reason why people are overly optimistic about anomalies they detect is the widespread reverse interpretation of the $p$-value. Often, it is thought of as the probability of one hypothesis (e.g., my anomaly exists) given the data. In fact, it’s the opposite; it’s the likelihood of your data sample, knowing that the anomaly holds.

$p - \text{value} = P[D|H]$

\(\text{target prob.} = P[H|D] = \frac{P[D|H]}{P[D]} \times P[H],\)

where $H$ stands for hypothesis and $D$ for data. The equality in the second row is a plain application of Bayes’ identity: the interesting probability is in fact a transform of the $p$-value.

Two articles (at least) discuss this idea. Harvey (2017) introduces **Bayesianized** $p$-values:

\(\text{Bayesianized } p - \text{value} = \text{Bpv} = e^{-t^2/2} \times \frac{\text{prior}}{1 + e^{-t^2/2} \times \text{prior}}, \quad (3.3)\)

where $t$ is the $t$-statistic obtained from the regression (i.e., the one that defines the $p$-value) and prior is the analyst’s estimation of the odds that the hypothesis (anomaly) is true. The prior is coded as follows. Suppose there is a p% chance that the null holds (i.e., (1-p)% for the anomaly). The odds are coded as $p/(1-p)$. Thus, if the $t$-statistic is equal to 2 (corresponding to a $p$-value of 5% roughly) and the prior odds are equal to 6, then the Bpv is equal to $e^{-2} \times 6 \times (1 + e^{-2} \times 6)^{-1} \approx 0.448$ and there is a 44.8% chance that the null is true. This interpretation stands in sharp contrast with the original $p$-value which cannot be viewed as a probability that the null holds. Of course, one drawback is that the level of the prior is crucial and solely user-specified.

The work of Chinco et al. (2020) is very different but shares some key concepts, like the introduction of Bayesian priors in regression outputs. They show that coercing the predictive regression with an $L^2$ constraint (see the ridge regression in Chapter 5) amounts to introducing views on what the true distribution of $b$ is. The stronger the constraint, the more the estimate $\hat{b}$ will be shrunk towards zero. One key idea in their work is the assumption of a distribution for the true $b$ across many anomalies. It is assumed to be Gaussian and centered. The interesting parameter is the standard deviation: the larger it is, the more frequently significant anomalies are discovered. Notably, the authors show that
