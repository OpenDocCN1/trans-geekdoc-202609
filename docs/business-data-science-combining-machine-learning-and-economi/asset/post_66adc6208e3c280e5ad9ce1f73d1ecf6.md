
In the previous example, if you regress sales on prices, you will find a *positive* relationship: sales increase with higher prices. This is the economist's dreaded “upward sloping demand curve.” Such results are garbage: they don't describe any real economic system. But it is easy to see how this happens. Consider a simple linear demand system where demand shocks *e* and prices *p* increase and decrease sales, *y*:

```r
> yfun <- function(e,p){
+   y = 2 + 10*e-3*p + rnorm(length(e),0,.1)
+   y[y<0] <- 0
+   return(y) }
```

For this illustration, the demand shocks will be random and independent.

```r
> e <- rgamma(100,1,1)
```

We will draw two separate price sets. In the first “observed” case, imagine that you have past data from a price setter who was able to execute targeted price discrimination—they charged prices that were positively correlated with the demand shocks (they are equal to *e* up to a random error *z*):

```r
> z <- rgamma(100,1,1)
> p_observed <- e + z
```

In the second case, imagine that you were able to run an experiment where prices are completely randomized:

```r
> p_ind <- rgamma(100,2,1)
```

Finally, you feed the demand shocks and both of these sets of prices through the sales function:

```r
y_observed <- yfun(e, p_observed)
y_counterfactual <- yfun(e, p_counterfactual)
```

The results are shown in Figure 5.9. On the left, we see that the endogenously determined prices lead to a positive correlation between prices and sales. The OLS line fit to observed price data erroneously predicts an upward-sloping demand curve. On the right, random price variation allows OLS to pick up the correct (downward-sloping) demand relationship. The additional “2SLS” line is a fit that was able to recover the correct price/sales relationship from observational data. The analysis behind this line took advantage of the available instruments $z$, the random variation in prices.

![](img/315929ad4bddd26368466d02e06e2385_219_0.png)

**FIGURE 5.9:** Illustration of the cartoon demand system. On the left, prices were determined endogenously (jointly) with the unobserved demand shocks. On the right, prices are determined randomly independent of demand. The two lines labeled OLS are OLS fit to each dataset. On the left you also see the 2SLS fit line, which matches up closely to the counterfactual OLS fit on the right.

TWO-STAGE LEAST SQUARES (2SLS) is a simple procedure for recovering causal effects from IV variation. Recall the regression equation in Equation 5.23, and take expectation of both sides of this equation after conditioning upon the instrument $z$. For now, we’ll ignore the covariates $x$ so that $y = g(p) + e$. Taking the conditional expectation yields

$\mathbb{E}[y \mid z] = \mathbb{E}[g(p) \mid z] + \mathbb{E}[e \mid z] = \mathbb{E}[g(p) \mid z]. \tag{5.25}$

This is because $e$ is independent of $z$ (a key feature of an IV) and so $\mathbb{E}[e \mid z] = \mathbb{E}[e] = 0$ under the standard assumption of zero-mean errors. Thus, given $z$, $y$ has conditional distribution with mean equal to the average of $g(p)$ given $z$. Note that $p$ is a random variable in this equation. For example, with binary treatment, you have

$\mathbb{E}[g(p) \mid z] = g(0)\mathbb{P}(p = 0 \mid z) + g(1)\mathbb{P}(p = 1 \mid z). \tag{5.26}$

Making life even simpler, consider the usual linear treatment model where $gp = \eta p$ and Equation 5.23 becomes

$$\gamma p + e \quad \text{(5.27)}$$

Combining this with Equation 5.25 yields the key equation for 2SLS:

$$\mathbb{E}[y|\boldsymbol{z}]=\boldsymbol{\gamma}\mathbb{E}[\boldsymbol{p}|\boldsymbol{z}] \quad \text{(5.28)}$$

Thus, you can estimate $\gamma$ with a two-step algorithm (and any covariates $x$ are just added to the conditioning set).

## ALGORITHM 13  Two-Stage Least Squares (2SLS)

-   Fit the first-stage expectation $\mathbb{E}[\boldsymbol{p}~|~x_{i},\boldsymbol{z}]=\boldsymbol{\alpha}_{\boldsymbol{p}}+\boldsymbol{z}_{i}\boldsymbol{\tau}+\boldsymbol{x}_{i}^{\prime}\boldsymbol{\beta}_{\boldsymbol{p}}$ using OLS for $\boldsymbol{p}$ on $\boldsymbol{x}$ and $\boldsymbol{z}$.

    For each observed $(\boldsymbol{p}_{i}, \boldsymbol{x}_{i}, \boldsymbol{z}_{i}, \boldsymbol{y}_{i})$ tuple, this provides the *predicted* policy $\hat{\boldsymbol{p}}_{i}=\hat{\boldsymbol{\alpha}}_{\boldsymbol{p}}+\boldsymbol{z}_{i}\hat{\boldsymbol{\tau}}+\boldsymbol{x}_{i}^{\prime}\hat{\boldsymbol{\beta}}_{\boldsymbol{p}}$.

-   Run a second-stage regression for your response onto the predicted policy and the covariates, using OLS to estimate:

$$\mathbb{E}[y|\hat{\boldsymbol{p}}_{i},\boldsymbol{x}_{i}]=\boldsymbol{\alpha}_{y}+\hat{\boldsymbol{p}}_{i}^{\prime}\boldsymbol{\gamma}+\boldsymbol{x}_{i}^{\prime}\boldsymbol{\beta}_{y} \quad \text{(5.29)}$$

You can then interpret the resulting $\hat{\gamma}$ estimate as the *causal* effect of $\boldsymbol{p}$ on $\boldsymbol{y}$.

In our earlier simulated pricing example, this algorithm proceeds in two simple steps. Recall that the observed prices were set as the sum of demand shocks and an independent random error: `p_observed = e + z`. Treating the $\boldsymbol{z}$ term as an observable instrument, we can run 2SLS:

```r
> preg <- lm(p_observed ~ z)
> phat <- predict(preg, data.frame(z=z))
> lin2SLS <- lm(y_observed ~ phat)
> summary(lin2SLS)
```

Coefficients:

|   | Estimate | Std. Error | t value | Pr(>|t|) |
|---|---|---|---|---|
| (Intercept) | 11.9030 | 1.7697 | 6.726 | 1.17e-09 *** |
| phat | -2.2023 | 0.8168 | -2.696 | 0.00825 ** |

The procedure recovers an estimate of $\gamma$ within one standard deviation of the true value (–3):

```r
> summary(lm(y_observed ~ p_observed))
```

Coefficients:

|   | Estimate | Std. Error | t value | Pr(>|t|) |
|---|---|---|---|---|
| (Intercept) | 1.3751 | 1.0701 | 1.285 | 0.202 |
| p_observed | 3.0502 | 0.4503 | 6.774 | 9.37e-10 *** |

This succeeds despite the fact that naive regression of sales on prices yielded a completely different (wrong) model.

THE OREGON INSURANCE EXPERIMENT, which we looked at to start this chapter, is actually an intent-to-treat setup. Although *access* to Medicaid insurance was randomized through the state’s lottery, not all of those who became eligible for Medicaid took advantage of this and enrolled. For some people the enrollment process was just too inconvenient, and others likely had alternative insurance available. Thus, the earlier results describe not the treatment effect of enrolling in Medicaid but rather the indirect effect of expanded access. We can refine these results through an IV analysis.

As in our earlier analysis of the OHIE, the response of interest is $y_{i}=1$ if the subject visited a primary care physician (PCP) and $y_{i}=0$ otherwise. The treatment of interest was access to Medicaid health insurance. Now, this access to insurance will be the instrument $z=1$ for those *selected* for enrollment and $z=0$ otherwise. Our new treatment, $p$, is whether the patient actually *enrolls* in Medicaid. Since the $z$ is randomized (assigned in a lottery) and it only affects PCP visits through its influence on Medicaid enrollment, this satisfies the definition of an instrumental variable. We can look at how the change in enrollment $p$ changes with the lottery access $z$ and infer the treatment effect of enrollment on PCP visitation.

In the simulated IV analysis shown earlier, $z$ was perfectly randomized. But in the OHIE analysis, we need to control for the household size, $\text{numhh}$, since people from larger households were more likely to obtain eligibility (any household member selected in the lottery makes all members eligible). As shown in Algorithm 13, this just means we need to include $\text{numhh}$ in both the first- and second-stage regressions. We can run everything via calls to `lm` (or, equivalently, `glm`):

```R
> stage1 <- lm( medicaid ~ selected + numhh, data=P)
> phat <- predict(stage1, newdata=P)
> stage2 <- lm(doc_any_12m ~ phat + numhh, data=P, x=TRUE)
> coef(stage2)
   (Intercept)        phat      numhh2      numhh3+
0.55883837 0.21259703 -0.05302372 -0.14483052
```

The estimated treatment effect, $\hat{\gamma}$, is the coefficient on $\hat{p}$: 0.21. This implies that enrollment in Medicaid makes the probability that you see a PCP 21 percentage points higher than if you don’t enroll in Medicaid. Compare this to the earlier analysis, which found that being *eligible* for Medicaid enrollment raised the probability of PCP visitation by only five to six points. The earlier analysis gave an attenuated version of the IV results because eligibility is one step removed from actual enrollment and because those who are unlikely to enroll even if eligible are also less likely to visit a PCP.

STANDARD ERRORS FOR IV ESTIMATES require a bit of care. We intuitively want to use the “sandwich” HC variance estimator, but for subtle reasons$^{16}$ the “meat” of the sandwich needs to be residuals from the second-stage regression using the true treatment inputs (as opposed to using the $\hat{P}$ inputs that we actually used to fit this second stage regression). It makes for a fairly complicated sandwich construction:
