
## 总结：针对偏离主题的回答进行修正

本工作提出了一种新方法，将全新的 “主题语言建模” 目标引入原始的“前缀语言建模”（Prefix Language Modeling, PLM）中，有效解决现有 PLM 在文本生成过程中容易偏离主题的问题。

- 提出了主题语言建模作为前缀语言建模的插件目标，不改动原有训练的流畅性等优势。
- 通过 “共同注意力模块” 有效捕获主题先验信息，并采用逐步生成的方式更好地建模篇章结构。

本文旨在修正此前工作中偏离主题的回答，通过嵌入主题建模，使得模型生成的内容在逻辑性、连贯性以及与主题的相关性上均有提升。

| 方法 | 主题相关性 | 逻辑性 | 连贯性 |
| --- | --- | --- | --- |
| 原始 PLM | 较低 | 一般 | 较好 |
| 主题 PLM (本文) | 高 | 强 | 好 |

> 主题语言建模的重点不在于“写得多”，而在于“写得准”，确保内容紧扣主题。

实验结果进一步表明，该方法在多个数据集上均取得一致性提升，尤其在长文本生成场景下，减少了内容冗余和偏题现象。

```python
# 主题语言建模伪代码
def topic_language_modeling(prompt, topic):
    context = encode(prompt + topic)
    output = generate(context, attention=co_attention)
    return output
```

- 74.6 Conclusion ................................ 2543
- Acknowledgments ................................ 2543
- Bibliography ................................ 2543
- Appendix 74A: Detailed Derivations ................ 2544

## Abstract

By assuming multivariate normal distribution of excess returns, we find that the sample maximum squared Sharpe ratio (MSR) has a significant upward bias. We then construct estimators for MSR based on Bayes estimation and unbiased estimation of the squared slope of the asymptote to the minimum variance frontier (ψ²). While the often used unbiased estimator may lead to unreasonable negative estimates in the case of finite sample, Bayes estimators will never produce negative values as long as the prior is bounded below by zero although it has a larger bias. We also design a mixed estimator by combining the Bayes estimator with the unbiased estimator. We show by simulation that the new mixed estimator performs as good as the unbiased estimator in terms of bias and root mean square errors and it is always positive. The mixed estimators are particularly useful in trend analysis when MSR is very low, for example, during crisis or depression time. While negative or zero estimates from unbiased estimator are not admissible, Bayes and mixed estimators can provide more information.

Keywords
Sharpe ratio • Finite sample • Unbiased estimation • Bayes estimation.

## 74.1 Introduction

While the Sharpe ratio is widely used as a performance measure for portfolio managers, we are interested in the maximum squared Sharpe ratio (MSR) for a set of risky assets in this chapter. In theoretical studies, MSR is widely used in testing the arbitrage pricing theory.¹ Under the assumption of multivariate normal distribution of excess returns on assets, MSR can be explicitly expressed as a function of the squared slope of the asymptote to the minimum variance frontier (ψ²), the expected value and variance of excess return of the global minimum variance portfolio (μg and σg² respectively). Since ψ², μg and σg² are functions of the mean (μ) and the covariance matrix (V) of excess return, the sample maximum squared Sharpe ratio $\hat{S}^2$ is a natural estimator by simply plugging the sample mean $\hat{\mu}$ and sample covariance $\hat{V}$ into the expression of MSR. If we have large sample, $\hat{S}^2$ may be a good estimator as the sample mean and sample covariance matrix are maximum likelihood estimators (MLEs). However, MLEs may not perform well due to sampling errors when we have only a limited sample period, such as in emerging markets, or when we are interested in its time-varying nature.

Despite the importance of the sample maximum squared Sharpe ratio, little efforts are devoted to studying its issues and its improvement. Kan and Smith (2008) find that the sample minimum variance frontier is on average too optimistic. We find that the optimistic bias also affects $\hat{S}^2$ because a large part of error comes from the large upward bias of the sample squared slope of the asymptote to the minimum variance frontier ($\hat{\psi}^2$). In the theoretical literature, MSR is used for establishing a bound for the sum of squared pricing errors in beta pricing equations (Chamberlain and Rothschild, 1983). The significant upward bias of the sample maximum squared Sharpe ratio will lead to a higher probability of not rejecting a false pricing model.

The objective of this chapter is to search for improved estimators of MSR in finite sample. We find that a large part of error in $\hat{S}^2$ comes from the upward bias in $\hat{\psi}^2$. The bias is more significant in the case of the finite sample. By subtracting the bias from $\hat{\psi}^2$ and with some scale adjustment, we can get uniformly minimum variance unbiased estimator (UMVUE) of $\psi^2$, denoted by $\hat{\psi}_u^2$. The upward bias in $\hat{S}^2$ can be greatly reduced when $\hat{\psi}^2$ is replaced by $\hat{\psi}_u^2$. However, the chances of having negative estimates of $\psi^2$ and hence negative $\hat{S}^2$ increase. To show the impact on estimation of $S^2$, we evaluate the probability of getting negative estimates with the parameters derived from US market.² Our simulation shows that using $\hat{\psi}_u^2$ will result in the chance of having negative estimates for $S^2$ as high as 33% when the sample period is five years. Moreover, in the Japanese market, $\psi^2$ is very low due to long-term sagging economy. When we calculate $\hat{\psi}_u^2$ over rolling five years from 7/1990 to 12/2017, there are 192 negative values out of 271 estimates.

Because $\psi^2$ and $S^2$ are squared variables, negative estimates are inadmissible. One simple way is to truncate the negative estimates of $\psi^2$ to guarantee non-negative results, but zero value estimates of ψ² are still unreasonable. To solve this problem, we construct estimators based on Bayes estimation of ψ². The Bayes estimator is derived from the distribution given by Bordnar and Schmid (2006) and Kan and Smith (2008). The pure Bayes estimator has a smaller root mean squared error (RMSE) but has a larger bias if the prior distribution is an uninformed uniform distribution. We then design a mixed estimator to combine the Bayes estimator with UMVUE. Our simulation shows that even if we know little about ψ, the mixed estimator performs as good as estimators involving ψ̂_u² (“less-biased” estimators). The most important advantage of Bayes estimator and mixed estimator is that they always produce admissible estimates as long as the prior of Bayes is bounded below by zero.

We then compare the trend of MSR on the US, Global, Asian (except Japan), Japanese and European markets using these estimators. We calculate estimates using the “less-biased” estimator, Bayes estimator and mixed estimator over rolling five years from July 1990 to December 2017. We find that Bayes or mixed estimator is particularly useful when the MSR is very low, for example, from October 2001 to July 2003 in the US market and from January 1998 to December 2017 in the Japanese market. During these periods, “less-biased” estimators produce many negative or zero values which make a trend analysis difficult. Meanwhile, Bayes or mixed estimator can produce reasonable estimates and provides meaningful information.

We distinguish from Kan and Smith (2008) in that they construct a better estimator for minimum variance frontier with finite sample, but they do not consider the MSR. While Maller et al. (2010) study the asymptotic distribution of the MSR under the asymptotic normality assumption, their concern is on large sample instead of finite sample. Our study is related to Gibbons et al. (1989) where they develop the finite sample test statistics for the efficiency of a given portfolio relative to the portfolio with the ex post maximum Sharpe ratio. We instead focus on the finite sample properties of the ex post maximum Sharpe ratio.

This chapter is divided into six sections. Section 74.2 investigates the distribution of maximum squared Sharpe ratio and shows a large upward bias of the sample estimate using a plug-in approach. Various alternative estimators for MSR are proposed in Section 74.3 and their performances are compared by simulation in Section 74.4. Using several proposed estimators, we compare MSR across different markets in Section 74.5. The chapter concludes in Section 74.6.

¹ For example, Chamberlain and Rothschild (1983) find that no arbitrage condition requires a finite squared maximum Sharpe ratio. MacKinlay (1995) uses it to examine the plausibility for multi-factor models to explain anomalies to the CAPM. With a similar idea of restricting the Sharpe ratio, Cochrane and Saa-Requejo (2000) derive good-deal bounds in pricing derivatives in an incomplete market setting. Zhang (2009) develops test statistics based on the sample maximum squared Sharpe ratio of the factors extracted from individual stocks.

² ψ², μ_g, and σ_g² are derived from 25 size and book-to-market (BM) portfolios value-weighted monthly return from 7/1926 to 12/2017. All portfolio return data are obtained from Professor Kenneth French's data library: http://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html.
