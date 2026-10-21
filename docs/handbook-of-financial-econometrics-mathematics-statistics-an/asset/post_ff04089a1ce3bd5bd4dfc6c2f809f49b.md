
model for $h_{it}$. Then, the first-stage quasi-likelihood function is

$$L_1(\phi|r_t)= -\frac{1}{2}\sum_{t=1}^{T}\big(k\log(2\pi)+\log(|I_k|)+2\log(|D_t|)+r_t' D_t^{-1} I_k D_t^{-1} r_t\big)$$
$$= -\frac{1}{2}\sum_{i=1}^{k}\Big(T\log(2\pi)+\sum_{t=1}^{T}\big(\log(h_{it})+\frac{r_{it}^2}{h_{it}}\big)\Big).$$

Let $\hat\phi = \arg\max L_1(\phi|r_t)$. Then, in the second stage, the DCC parameters in equation (129.6) are estimated using the original likelihood in (129.8) conditional on the first-stage GARCH parameter estimates $\hat\phi$. And, the quasi-likelihood function is

$$L_2(\psi|\hat\phi, r_t)= -\frac{1}{2}\sum_{t=1}^{T}\big(k\log(2\pi)+2\log(|D_t|)+\log(|R_t|)+r_t' D_t^{-1} R_t^{-1} D_t^{-1} r_t\big)$$
$$= -\frac{1}{2}\sum_{t=1}^{T}\big(k\log(2\pi)+2\log(|D_t|)+\log(|R_t|)+\varepsilon_t' R_t^{-1} \varepsilon_t\big).$$

The estimated parameter $\hat\psi$ in $L_2(\psi|\hat\phi, r_t)$ is

$$\hat\psi = \arg\max L_2(\psi|\hat\phi, r_t).$$

From Engle (2002), we know that $\hat\theta_T = (\hat\phi_T, \hat\psi_T)$ has asymptotic normality. Thus, the estimates of parameters can be easily tested for their significance.

## 129.3 The Test of the Difference in Different Stages for Simple Average Correlations and Variance

From the graphs of correlations, especially of simple average correlations Figure 129.1, we notice that there are some sharp values of correlations. Moreover, before the first sharp points and between two sharps, the values change stably. This phenomenon is even more obvious for simple average variances, which enlightens us to test if the mean correlations and variances in different stages are the same. In this part we divide the data of correlations into two groups and express them as two variables $X_1$ and $Y_1$ with unknown distributions. Then we can test whether their means are the same or not by an efficient test proposed by Brunner and Munzel (2000). In their paper, Brunner and Munzel (2000) discuss how to test the difference between two separated random variables and how to compute the

probability p = P(X₁ < Y₁) + ½ P(X₁ = Y₁). Similarly, for the data of variances, we expressed them as two random variables X₂ and Y₂, and calculate p = P(X₂ < Y₂) + ½ P(X₂ = Y₂). We use this test method to obtain the probability of the difference between correlations and variances separately.

We next discuss the Brunner–Munzel test briefly. Assume that a general non-parametric model, as in Brunner and Munzel (2000), has N = n₁ + n₂ independent random variables,

$$X_{k_1} \sim F_1(x),\, Y_{k_2} \sim F_2(x),\quad k_1 = 1,\dots,n_1,\,k_2 = 1,\dots,n_2.\tag{129.9}$$

The distribution functions F₁(x) and F₂(x) are arbitrary (with exception of the trivial case of one-point-distributions). Moreover, the hypothesis of no treatment effect is commonly formulated as H₀^F : F₁ = F₂, which implies homoscedasticity under the hypothesis. To formulate a non-parametric hypothesis of no treatment effect, the relative treatment effect p = P(X₁ < Y₁) + ½ P(X₁ = Y₁) is considered. It is known that Fᵢ(x) = ½[Fᵢ⁻(x) + Fᵢ⁺(x)], where Fᵢ⁻(x) is the left-continuous version and Fᵢ⁺(x) is the right-continuous version. Thus, p can be written as p = ∫ F₁ dF₂ and the hypothesis of no treatment effect is written as H₀^p : p = ∫ F₁ dF₂ = ½ since H₀^F : F₁ = F₂ = F implies H₀^p : p = ½ by ∫ F dF = ½.

To estimate p, the distribution functions F₁ and F₂ are replaced by their empirical counterparts \hat Fᵢ(x) = ½[\hat Fᵢ⁻(x) + \hat Fᵢ⁺(x)]. Let

$$\hat H(x) = \sum_{i=1}^{2} \frac{n_i}{N} \hat F_i(x).$$

Then R₁ₖ = N · \hat H(Xₖ) and R₂ₖ = N · \hat H(Yₖ) + ½ are the rank of Xₖ and Yₖ. Let \bar R_{i.} = n_i^{-1} \sum_{k=1}^{n_i} R_{ik}, i = 1,2, denote the mean of the ranks R_{ik}. It follows that

$$\hat p = \int \hat F_1 d\hat F_2 = \frac{1}{n_1} \left( \bar R_{2.} - \frac{n_2 + 1}{2} \right)$$

is an unbiased and consistent estimator for p.

For any data of correlation or variance, it is known that they are auto-correlated. But in Brunner and Munzel (2000), the random variables X_{k1} and Y_{k2} are assumed to be N independent variables. In order to satisfy independence, the sample sizes of two separated groups need to be large enough so that the dependencies among them can be ignored. In this chapter, the

sample size is more than 700, which is large enough to satisfy the requirement of variable independence.

In conducting the Brunner–Munzel test, since we do not know the optimal breaking points at which the samples are separated into two groups, we need to make a choice. The basic idea is that we select one starting point x_s and one ending point x_e as the break points of two groups. In this process, we need to keep the sample sizes of two groups large enough for independence. We first pick any point x_a, between x_s and x_e, as breaking point, and then perform the Brunner–Munzel test to get an estimate of \hat{p}. For all values of \hat{p}, we can obtain the local maximums, which can be considered as the best breaking points. If the distance of two neighborhood breaking points is not far enough to satisfy independence for the samples between these two neighborhood breaking points, we just keep the breaking points with bigger value of \hat{p}, and drop the other ones. In practice, we may get several breaking points, which is consistent with the fact that there are several sharp points in the data, such as correlations and variance in this study.

We further check these breaking points by performing the Brunner–Munzel test again for the samples and its neighborhood samples to see if the means of these two samples are the same. If we accept the hypothesis, then we give up this breaking point of these two samples; otherwise, this breaking point is kept. In the end, it stops after we get all possible left breaking points, between any two of which the mean of sub-samples is significantly different from that of its neighborhood sub-samples. Then, all of the breaking points are obtained. This allows us to obtain the precise dates for structural changes.

For brevity, we only provide two graphs with respect to simple average correlations and variances. For other graphs, we can do the same test and get similar results. In the attached figure, we can see that the probability of difference reaches two local maximum points around February 2007 and September 2008, respectively, which are greater than 90%. This result is consistent with the patterns we observed earlier. For these two points of local maximum values, they are treated as the stage breaking points. In the graphs of simple average correlation and variance, we use dash vertical lines to denote the dates of them. These two points are very important and useful in empirical implementation as they provide a method for us to divide the correlations and variances into different stages. In addition, for the probability of the differences for variance, if it is very high, greater than 90%, we need to consider the risk in different stages. This is another reason why it is important to determine the stage breaks.

## 129.4 Data and Empirical Results

The data consist of the daily returns of S&P 500 companies. The sample covers the period from January 3, 2006 to October 31, 2008. The stock returns are calculated from the daily closing prices on the website: http://finance.yahoo.com. In this chapter, we consider the correlations of returns on firms in the banking, insurance and trading industries to see whether the correlation of returns have been affected by the subprime crisis. For the banking industry, ten banks are selected and the ticker names are: AXP, BBT, BK, C, CIT, COF, KEY, NCC, PNC, USB. For the insurance industry, we also select ten large insurance companies and their ticker names are: ABK, AET, AIG, ALL, HIG, MET, PRU, ANAT, ASI, and HCC. Moreover, we choose eight companies in trading industry, whose ticker names are: AMTD, BPSG, CS, GS, JPM, NMR, OPY, and AMP.

Tables 129.1 and 129.2 list the names of companies and their tickers. Table 129.3 reports means, standard deviations, skewness and kurtosis of

**Table 129.1:** The names and tickers of banks and insurance companies.

| Banks Name | Banks Ticker | Insurance companies Name | Insurance companies Ticker |
|---|---|---|---|
| American Express Co | AXP | Ambac Finl Grp Inc | ABK |
| BB&T Corp | BBT | Aetna Inc | AET |
| Bank of NY Mellon Corp | BK | American International Group | AIG |
| Citigroup Inc | C | Allstate Corp | ALL |
| CIT Group Inc | CIT | Hartford Fin Services Group | HIG |
| Capital One Financial Corp | COF | MetLife Inc | MET |
| KEY Corp | KEY | Prudential Financial Inc | PRU |
| PNC Financial Svcs Group Inc | PNC | American National Insurance Co | ANAT |
| U S Bancorp | USB | American Safety Insurance Holdings Ltd | ASI |
|  |  | HCC Insurance Holdings Inc | HCC |

**Table 129.2:** The names and tickers of trading firms.

| Name | Ticker |
|---|---|
| TD Ameritrade Holding Corp | AMTD |
| Broadpoint Securities Group Inc | BPSG |
| Credit Suisse Group | CS |
| Goldman Sachs Group Inc | GS |
| JPMorgan Chase & Co | JPM |
| Nomura Holdings Inc | NMR |
| Oppenheimer Holdings Inc | OPY |
| Ameriprise Financial Inc | AMP |
