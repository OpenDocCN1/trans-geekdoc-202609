
digital marketing in other cases, especially when the advertiser is not well known or would not occur in the organic results.

If the clustered standard errors are unintuitive, note that you can get a similar result by *controlling* for the DMA-specific revenue levels in the regression mean equation itself. That is, you replace Equation 5.13 with a model including DMA-specific intercepts (i.e., what economists would call “DMA fixed effects”):

$$\mathbb{E}[y_{it}] = \alpha_i + d_{it}\beta_d + t\beta_t + \gamma d_{it}. \qquad\qquad\qquad\qquad\qquad\qquad (5.14)$$

Since we’re now assuming independence conditional upon the DMA-specific levels, the usual regression standard errors apply.

```r
> dmareg <- glm(y ~ dma + d*t, data=semavg)
> summary(dmareg)$coef[“d: t”,]

Estimate Std. Error t value Pr(>|t|)
-0.006586852 0.005571899 -1.182155571 0.238493640
```

The estimates for $\gamma$ and its standard errors are practically unchanged from our earlier regression analysis using clustered standard errors.

Our derivation and analysis here should convince you that the diff-in-diff procedure is just an example of applied regression modeling. However, the estimator is often presented in an alternative formulation that takes advantage of the *pairing* between pre- and post-treatment observations. In this form, you would first calculate the sample of pre-post *differences* for each DMA:

$$r_i = y_{i1} - y_{i0} \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (5.15)$$

You then collect the average difference for the treated and control groups, say $\bar{r}_1$ and $\bar{r}_0$, and use the difference between these averages as the ATE estimate, as shown here:

$$\hat{\gamma} = \bar{r}_1 - \bar{r}_0 \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (5.16)$$

This routine is the source of the “difference in differences” name. Independence between DMAs implies independence for each $r_i$, and you can apply the usual formula to get the standard error for a difference in means: $\text{se}(\hat{\gamma}) = \text{se}(\bar{r}_1) + \text{se}(\bar{r}_0)$.

```r
> r <- tapply(semavg$y, semavg$dma, function(y) y[2]-y[1])
> d <- semavg[match(names(r), semavg$dma), "d"]
> rbar <- tapply(r,d,mean)
> rbarvar <- tapply(r, d, function(r) var(r)/length(r))
> rbar[2] - rbar[1]

1
-0.006586852
> sqrt(sum(rbarvar))
[1] 0.005555082
```

The results are unchanged from our previous regression analyses.

REGRESSION DISCONTINUITY ESTIMATORS take advantage of another common near-experimental design: treatment allocation is determined by a threshold on some “forcing variable,” and subjects that are close to the threshold, on either side, are comparable for causal estimation purposes. For example, Hahn et al. [1999] evaluate the causal effect of a discrimination law that applies only to firms with more than 15 employees. Here, the number of employees is the forcing variable and the authors compare firms on either side of the 15-employee threshold. Similar situations arise all over the place: grade thresholds determine access to education programs, income thresholds influence availability of social programs, and my kids had free entry at the museum until they turned 4. We’ll consider a common digital marketing setting where the rules for ad display depend upon whether the highest (or second highest) ad auction “score” passes a reserve threshold.

The nice thing about a regression discontinuity (RD) design is that you know the only confounding variable that you need to control for: the forcing variable. Recall our earlier discussion of imperfect experimental designs. You need to control for (i.e., include in the regression) any variable that is correlated with both treatment allocation and the response. In a strict RD, the treatment is *fully determined* by the forcing variable so you just need to control for that variable. In the examples just given, you’d need to control for each firm’s number of employees or each advertiser’s score in the ad auction.

An RD analysis requires an assumption about how the response varies with the forcing variable near the treatment threshold. You must assume that if the threshold were to move slightly, subjects switching treatment groups will behave similarly to those near them in their new treatment group. This is a *continuity* assumption. It means that you can look at the relationship between the forcing variable and the response on one side of the threshold and extrapolate to the other side.

Figure 5.4 shows observed (solid) and unobserved (dashed) expected response functions for each of two treatment groups. The RD continuity assumption implies the behavior that we see around the treatment threshold (where the solid line jumps). Even though there is a discontinuity (i.e., a jump) in the observed mean response, the underlying treatment group functions are each continuous around this point (i.e., each group mean response is smooth over the transition from solid to dashed). This allows you to compare the counterfactual response across the two treatment groups.

![](img/315929ad4bddd26368466d02e06e2385_207_0.png)

FIGURE 5.4: Illustration of the RD continuity assumption, taken from Imbens and Lemieux [2008]. Solid lines are the observed mean response (y-axis) given the forcing variable (x-axis), and dashed lines show the unobserved mean response for each group.

We can make this all more precise using the potential outcomes notation. Recall that $y_i(d)$ is the potential outcome for user $i$ under treatment $d$, and $d_i$ is their treatment group so that $y_i(d_i)$ is their observed response. For RD designs, we add the forcing variable $r$: the location of $r$ relative to your treatment threshold determines the treatment status. For simplicity, we will assume that this threshold of interest is always zero. You can just subtract a nonzero threshold from the forcing variable to make this true. Limiting ourselves to binary treatments, the treatment allocation with forcing variable $r_i$ is then

$$d_{i}=\mathbb {1}_{[r_{i}>0]}. \tag{5.17}$$

This is a near experimental design because you need to control only for the forcing variable—treatment allocation is independent of the response given $r_{i}$:

$$[y_{i}(0),y_{i}(1)]\perp d_{i}\mid r_{i}. \tag{5.18}$$

Finally, the important continuity assumption can be written (recalling that your treatment threshold is at $r_{i}=0$) as follows for small $\varepsilon$:

$$\mathbb{E}[y_{i}(d) \mid r=-\varepsilon] \approx \mathbb{E}[y_{i}(d) \mid r=0] \approx \mathbb{E}[y_{i}(d) \mid r=\varepsilon]. \tag{5.19}$$

With all of these pieces in place, you can estimate the causal effect of treatment by fitting regression models on either side of the threshold and comparing their predictions at $r=0$. For example, we will usually estimate separate linear regressions within some distance $\delta$ of the threshold:

$$\begin{array}{c} \mathbb{E}[y_{i} \mid r_{i},-\delta<r_{i}<0]=\alpha_{0}+\beta_{0}r_{i},\\ \mathbb{E}[y_{i} \mid r_{i}, 0<r_{i}<\delta]=\alpha_{1}+\beta_{1}r_{i}, \end{array} \tag{5.20}$$

Here, the first regression will have $d_{i}=0$ and the second $d_{i}=1$. The treatment effect estimate at $r_{i}=0$ is then

$$\mathbb{E}[y_{i}(1)-y_{i}(0) \mid r_{i}=0]=\alpha_{1}-\alpha_{0}. \tag{5.21}$$

This gives you a *conditional* ATE for those subjects whose $r_{i}$ is close to zero. The estimated treatment effect corresponds to the gap between potential outcomes at the jump in Figure 5.4. You will learn nothing about the fact that this gap closes (and potential outcomes even cross) away from this threshold; in an RD design, you learn about the treatment effect only at the threshold. This is a limitation, but so long as you are aware that you are getting a conditional ATE, the results are often useful nonetheless.

Treatment assignment for our digital marketing example is illustrated in Figure 5.5. The data correspond to sponsored search, as in the previous SEM diff-in-diff example, but here we have details on the process through which ads are assigned to positions on the search page. In an ad auction, the advertiser bids a certain amount for their ad to be shown. These bids are then combined with information from the ad platform (i.e., the search engine
