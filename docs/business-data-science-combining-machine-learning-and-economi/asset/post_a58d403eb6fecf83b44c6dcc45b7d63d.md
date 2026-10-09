
## where, $\hat{\boldsymbol{\beta}} = \boldsymbol{\gamma}\boldsymbol{\tau} + \boldsymbol{\beta}$

Thus $\gamma$ is the same across both models—the effect of $\nu$ on $y$ is the same as the structural effect of $d$ on $y$. Controlling for $\hat{d}$ unpenalized in Equation 6.4 is essentially the same as estimating the treatment effect of residuals $\hat{\nu}$. In both cases, $\hat{\gamma}$ is based on variation in $d$ that is orthogonal to $\hat{d}$ (i.e., independent from $\hat{d}$ in the sample).

Recall the *Freakonomics* abortion example from earlier. Where we left off, we had built a large set of controls $x$ consisting of the original Levitt and Donahue variables (interacted), state-specific cell phone effects, and time. If we run a straight “naïve” lasso onto $d$ and $x$, AICc selects a negative abortion effect.

```r
> x <- sparse.model.matrix(~ t + phone*s + .^2, data=controls)[,-1]
> dim(x)
[1] 624 154

> ## naïve lasso regression
> naive <- cv.gamlr(cBind(d,x),y)
> coef(naive) ["d",] # effect is CV selected <0
[1] -0.1149923
```

But if we follow Algorithm 14 and fit the treatment effect regression, the AICc lasso selects $d$ as highly predictable given $x$.

```r
> treat <- cv.gamlr(x, d, lmr=1e-4)
> dhat <- drop(predict(treat, x, type= "response"))
> cor(d, dhat) ^2
[1] 0.9871682
```

The in-sample $R^2$ is around 99% (see also Figure 6.2) so that there’s almost no *independent* movement of abortion rates to measure as effecting crime. There is little pseudo-experimental variation. Sure enough, after including $\hat{d}$ without penalty in the murder lasso regression, the AICc selects zero residual effect for $d$.

![](img/315929ad4bddd26368466d02e06e2385_240_0.png)

```r
### free=2 here leaves dhat unpenalized
> causal <- gamlr(cBind(d, dhat, x), y, free=2, lmr=1e-3)
> coef (causal) ["d",]
[1] 0
```

Thus, the LTE lasso procedure finds no evidence for effect of abortion on murder.

## PROPENSITY MODELS ARE AN ADAPTATION OF THE LTE FRAMEWORK FOR BINARY TREATMENTS

In this setting, the second line of the LTE system in Equation 6.2 is replaced with a binomial distribution on the treatment equation:

$$y=d\gamma+x'\beta+\varepsilon, \quad \varepsilon|d, x=0,$$

$$d\sim\text{Bernoulli}(q(x)), \quad q(x)=\frac{e^{x'\tau}}{1+e^{x'\tau}}. \quad (6.6)$$

Thus, $d$ is modeled as having been drawn from a Bernoulli distribution (i.e., a coin toss) and the probability that $d=1$ is a function of $x$ through our familiar logistic regression model (there are alternative formulations, but the logit link is most common).

The treatment probability $q$ is called the *propensity score*. Given an estimate of this score—say, $\hat{q}(x)$—there are a variety of treatment effect estimation options. Propensity score adjustment fits the linear regression $\mathbb{E}[y \mid d, \hat{q}(x)] = \alpha + d\gamma + \hat{q}(x)\varphi$, while propensity score weighting estimates $\mathbb{E}[y \mid \hat{q}(x)] = \alpha + d\gamma \mid d]$. See Imbens and Rubin [2015] for more detail, but both of these will work for estimating true $\gamma$ so long as the model in Equation 6.6 is correctly specified. So-called doubly robust methods follow either approach but also include $\boldsymbol{x}$ in these second-stage regressions. I tend to favor a doubly robust procedure that closely resembles the LTE lasso of Algorithm 14: First fit a lasso logistic regression to estimate

$$\mathbb{E}[d \mid \boldsymbol{x}] = q(\boldsymbol{x}) = \frac{e^{\boldsymbol{x}'\boldsymbol{\tau}}}{1 + e^{\boldsymbol{x}'\boldsymbol{\tau}}}. \quad \quad (6.7)$$

Then follow step 2 of Algorithm 14 and fit a lasso to estimate

$$\mathbb{E}[y \mid \boldsymbol{x}, d] = \hat{q}(\boldsymbol{x})\boldsymbol{\vartheta} + d\gamma + \boldsymbol{x}'\boldsymbol{\beta} \quad \quad (6.8)$$

with no penalty on $\boldsymbol{\vartheta}$. Propensity score *matching* is a related approach, common in medicine, where $\hat{q}(\boldsymbol{x}_{i})$ is estimated for each subject and you run a matching algorithm to find pairs of individuals $(i_{0}, i_{1})$ where $\hat{q}(\boldsymbol{x}_{i_{0}}) \approx \hat{q}(\boldsymbol{x}_{i_{1}})$ but $d_{i_{1}} = 1$ while $d_{i_{0}} = 0$. The treatment effect is then estimated as the average difference across $n$ matched pairs, $\hat{\gamma} = \frac{1}{n}\sum_{i}(y_{i^{1}} - y_{i^{0}})$. Matching is a pain to implement because the matching algorithms are computationally expensive for large $n$, and it is unstable because results are highly sensitive to how you choose the matching criterion (i.e., how close is close enough for a match). However, it has the advantage that it is an easy procedure to explain for nonstatisticians: “You have two patients who look identical, one gets treatment and the other gets the control ...” You should feel free to use such explanations to help build intuition around your results (I do this all the time) even if you are actually making use of the regression techniques we advocate in this section.

# ◆ SAMPLE-SPLITTING AND ORTHOGONAL MACHINE LEARNING

The LTE lasso and related approaches can give you point estimates of the treatment effects, but they don't come with the nice *inferential* properties (i.e., standard errors) that you get from OLS. In **Chapter 3**, we introduced the parametric bootstrap and subsampling as methods for uncertainty quantification after model selection, and it is possible to adapt versions of those algorithms for use in treatment effect estimation. However, in the context of the LTE model, there is a nice alternative algorithm for inference: sample splitting.

In a sample splitting algorithm, you split the sample into, say, two pieces. You do model selection on one piece and then, conditional upon that selected model, do standard inference on the second piece. For example, with a linear lasso you could apply OLS (i.e., fit the MLE) in the second stage using only those covariates that had a nonzero selected coefficient in the first-stage lasso regression.

Recall the hockey example from **Chapter 3**. For every goal, coded as $y = 1$ for home-team goals and $y = 0$ for away-team goals, we regressed $y$ onto indicators for the teams, for the game scenarios (e.g., power plays), and for which players were present on the ice. These indicators were signed according to home versus away teams so that, for example, a home player on the ice for goal $i$ has $x_{ij} = 1$ and an away team player on the ice has $x_{ij} = -1$ (and those off the ice are all zeros). We then built a big lasso regression that predicted, given who is on the ice, which team scored every goal.

> Unlike the original analysis of **Chapter 3**, here we will penalize everything (including team and on-ice scenario coefficients). This is just to keep the example simple; you could also use sample splitting with the former specification.

To do inference via sample splitting, we first fit a regression model to half of the data:

```r
> library(gamlr)
> data(hockey) # load the data
> x <- cBind(config, team, player)
> y <- goal$homegoal
> fold <- sample.int(2, nrow(x), replace=TRUE)
> nhlprereg <- gamlr(x[fold==1,], y[fold==1],
+   family= "binomial", standardize=FALSE)
```

We then figure out which columns of $x$ have a nonzero coefficient in this `nhlprereg` and fit an *unpenalized* (i.e., MLE) logistic regression on only those variables using the second half of the data.

```r
> # the -1 to remove the intercept
> selected <- which(coef(nhlprereg)[1,] != 0)
> xnotzero <- as.data.frame(as.matrix(x[,selected]))
> nhllme <- glm(y ~ ., data=xnotzero,
+               subset=which(fold==2), family=binomial)
```

Now, suppose that you want to predict the probability that the home team scored for a given goal. For example, look at the first goal in the dataset, from a 2002 game between the Dallas Stars and the Edmonton Oilers played in Edmonton, Alberta:

```r
> x[1, x[1,]!=0]
```

```text
              DAL.20022003 EDM.20022003  ERIC_BREWER  JASON_CHIMERA  ROB_DIMAIO
[1,]            -1             1             1            1           -1

              DERIAN_HATCHER NIKO_KAPANEN JERE_LEHTINEN JUSSI_MARKKANEN JANNE_NIINIMAA
[1,]                -1           -1             -1              1            1

              RYAN_SMYTH  BRIAN_SWANSON  MARTY_TURCO  SERGEI_ZUBOV
[1,]              1             1           -1          -1
```

To get the home-team score probability and the appropriate standard errors, we apply the standard prediction routine for `glm`. Since the input design `xnotzero` was selected using different data from that used to fit `nhllme`, the standard theory applies out of the box.
