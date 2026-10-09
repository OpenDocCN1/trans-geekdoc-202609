
Beyond controlling for the effect of who else is on the ice, we also want to control for things unrelated to player ability (crowd, coach, schedule, etc.). To this end, we add a “fixed effect” for each team season, $a_{team,season}$. In addition, special-teams configurations (e.g., a five-on-four power play) are controlled for through $a_{config}$ effects. The full logistic regression model is then

![](img/315929ad4bddd26368466d02e06e2385_138_0.png)

We interpret $\beta_j$ as the $j$th player’s partial effect: when a goal is scored and player $j$ is on ice, odds are multiplied by $e^{\beta_j}$ that his team scored. This is a regression-based improvement on the traditional PM score.

You can run the model and use CV selection with a call to cv.gamlr.

```
> x <- cBind(config, team, player) # cBind binds together two sparse matrices
> y <- goal$homegoal
> cv.nhlreg <- cv. gamlr(x, y, verb=TRUE, # verb prints progress
+     free=1: (ncol(config)+ncol(team)), # free denotes unpenalized columns
+     family="binomial", standardize=FALSE)
fold 1,2,3,4,5,done.
```

The cv.gamlr object stores a gamlr object (the full data path fit) as one of its entries, and you can plot both the regularization paths and the CV experiment as in Figure 3.11:

![](img/315929ad4bddd26368466d02e06e2385_139_0.png)

![](img/315929ad4bddd26368466d02e06e2385_139_1.png)

FIGURE 3.11: OOS error (left) and path (right) plots for the hockey regression.

```
> par(mfrow=c(1,2))
> plot(cv.nhlreg)
> plot(cv.nhlreg$gamlr)
```

Both AICc and CV-min choose a $\lambda$ that is a bit smaller than $e^{-9}$. The CV-lse rule chooses a bigger lambda (more simple model) at around $e^{-8}$. The AIC chooses a $\lambda$ near the AICc choice; it is not overfit because $n/df$ is large: we have $n \approx 70,000$ goals and 2400 players.

```
> log(cv.nhlreg$gamlr$lambda) [which.min(AIC(cv.nhlreg$gamlr))]
seg55
-9.165555
```

On the other hand, the BIC is conservative and selects the null model where $\hat{\beta}=0$.

```
> which.min(BIC(cv.nhlreg$gamlr))
seg1
1
```

The BIC is trying to find $\lambda$ with the highest probability of having the minimum OOS error, which is subtly different than finding the $\lambda$ corresponding to the lowest expected OOS error. For example, if there is more uncertainty about OOS error at the $\lambda$ with minimum expected error, then it could be that another value with higher expected error but lower uncertainty around this value will have a higher probability of being best. However, on a more practical level, the BIC simply tends to mechanically underfit as $n$ gets large.

The null model here is not just an intercept but rather includes on-ice configuration info along with indicators for the team and season. So, the BIC is not saying that no players matter but rather that it cannot confidently tell them apart from their team's average level of play in a given season.

Taking a quick look at the regression, we see that the AICc selects 646 nonzero measurable player effects.

```r
> Baicc <- coef(nhlreg)[colnames(player),]
> sum(Baicc!=0)
[1] 646
```

There are a few things to note here. First, we’ve introduced the `free` argument. This denotes columns of the design matrix that we *do not* want penalized. In this case, we’re using it to keep the special-teams and team-season variables unpenalized—we know that we want them in the model, and so we let them enter without restriction.

Second, notice that we’ve used `standardize=FALSE`. This is one of the special cases where all of our penalized variables are on the same scale (player presence or absence). Without `standardize=FALSE`, we’d be multiplying the penalty for each coefficient (player effect) by that player’s standard deviation in the `player` matrix. The players with big standard deviation are guys who play a lot. Players with small standard deviation are those who play little (almost all zeros). Hence, weighting penalty by standard deviations in this case is exactly what we don’t want: a bigger penalty for people with many minutes on ice, a smaller penalty for those who seldom play. Indeed, running the regression without `standardize=FALSE` leads to a bunch of farm-team players coming up on top.

```r
> nhreg.std <- gamIr(x, y,
+    free=l:(ncol(config)+ncol(team)), family="binomial")
> Bstd <- coef(nhreg.std) [colnames(player),]
> Bstd [order(Bstd, decreasing=TRUE) [1:10]]
  JEFF_TOMS   RYAN_KRAFT   COLEJARRETT   TOMAS_POPPERLE
  1.7380706   1.4826419   1.2119318   1.1107806
  DAVID_LIFFITON   ALEKSY_MARCHENKO   ERIC_SELLECK   MIKE_MURPHY
  1.0974872   1.0297324   1.0060015   0.9600939
  DAVID_GOVE   TOMAS_KANA
  0.9264895   0.8792802
```

In contrast, the top players from the main analysis are almost all recognizable stars.

```r
> # Here are the top 10 players
> Baicc [order(Baicc, decreasing=TRUE) [1:10]]
  PETER_FORSBERG   TYLER_TOFFOLI   ONDREJ PALAT   ZIGMUND PALFFY   SIDNEY_CROSBY
  0.7548254   0.6292577   0.6284040   0.4426997   0.4131174
  JOE_THORNTON   PAVEL_DATSYUK   LOGAN COUTURE   ERIC_FEHR   MARTIN GELINAS
  0.3837632   0.3761981   0.3682103   0.3677283   0.3577613
```

The bottom players from the main analysis are not those with little ice time, but rather those with much ice time who underperform.

```r
> # Here are the bottom 10
> Baicc [order(Baicc)[1:10]]
  TIM_TAYLOR   JOHN MCCARTHY   P. J. AXELSSON   NICLAS_HAVELID   THOMAS POCK
  -0.8643214   -0.5651886   -0.4283811   -0.3854583   -0.3844128
  MATHT EU_BIRON   CHRIS DINGMAN   DARROLL POWE   RAITIS_IVANANS   RYAN HOLLWEG
  -0.3512101   -0.3342243   -0.3339906   -0.3129481   -0.2988769
```

Digging a little more, we see that whenever a goal is scored, Pittsburgh's odds of having scored (rather than having been scored on) increase by $51%$ if Sidney Crosby is on the ice.

```
> exp(Baicc["SIDNEY_CROSBY"])
SIDNEY_CROSBY
1.511523
```

Meanwhile, the Blue Jackets (or Kings, before 2011–2012) odds of having scored drop by around 22% if Jack Johnson is on the ice.

```
> exp(Baicc ["JACK_JOHNSON"])
JACK_JOHNSON
0.7813488
```

Finally, as a simple gut-check, we can look at the intercept for a *home-ice advantage*.

```
> exp(coef (nhlreg) [1])
[1] 1.084987
```

This says that, without conditioning on any of the other covariates, the home team is around 8% more likely to have scored any given goal. That is a big home-ice advantage!

# ◆ UNCERTAINTY QUANTIFICATION FOR THE LASSO

At the beginning of Chapter 1, we discussed how there are two high-level approaches to dealing with uncertainty about model parameters. You can, as we did in that chapter, attempt to quantify the uncertainty around parameter estimates and use this uncertainty in your decision-making process. Alternatively, you can do as we have in this chapter and use regularization to denoise your estimates without doing an explicit accounting of uncertainty. That is, you use procedures that give reliable point estimates in the presence of uncertainty by shrinking toward the safe null hypothesis. Rather than the classical dichotomy between estimation and testing, your decision-making around whether a variable is zero or nonzero has been incorporated into a single optimization objective.

In this section, we introduce a hyrid scenario: you have used the lasso to perform high-dimensional analysis but then need to provide some measure of the uncertainty around the lasso estimates. This will be relevant, for example,

if the analysis goals are more complex than basic prediction, if you have asymmetric losses for over- and underestimation, or if the audience expects to see something like a confidence interval around any results.

Uncertainty quantification for tools like the lasso is not easy. The presence of a penalty term wreaks havoc with the usual estimators for sampling distributions and standard errors. Moreover, it is impossible to accurately quantify uncertainty for very high-dimensional objects: you can build marginal intervals for a single $\beta_j$, not a joint interval for the full vector $\boldsymbol{\beta}$. However, there are a couple of tools that you can use to get good approximations to frequentist uncertainty after lasso estimation. We will discuss two here: the parametric bootstrap and subsampling. Refer also to **Chapter 6** for the method of sample splitting.

You need to look beyond the uncertainty quantification methods of **Chapter 1** because these fail for the lasso. First, there are no good theoretical standard errors available for lasso estimates. The CLT-based results that we rely upon for MLE regression are invalid for estimation under penalization and in high dimensions. Second, the nonparametric bootstrap will not work well in scenarios where you are doing model selection. To see why this happens, imagine executing one fold of a cross-validation routine on a bootstrap sample. Since the observations have been resampled *with-replacement*, you are likely to have some of the same observations in both the training sample and in the left-out fold. This makes prediction seem easier than it would be in reality since the same (unpredictable) random noise is in both your training and validation fold. As a result, the bootstrapped CV routine will tend to select a smaller penalty than it would on the full sample. That is, the bootstrap samples will be overfit relative to the actual estimator, and thus they cannot be used to quantify uncertainty for this estimator.

However, the alternative *parametric* bootstrap algorithm can be made to work with the lasso. Recall that, instead of sampling from the data for each bootstrap sample, the parametric bootstrap generates *new* observations from an estimate of your assumed data-generating process. Because these are new unrepeated observations, the overfit described earlier will not occur.

For the parametric bootstrap, you might not want to sample from the full sample lasso fit. One way to think about your decision to use regularization is that you are trading variance for bias: you push the coefficients toward zero so that they are more stable and move around less with random noise. However, in an ideal world, the model generating simulated data in your parametric bootstrap should be an *unbiased* estimate of the true data generating process. In low dimensions, you can just simulate from the MLE fitted model (most theory on parametric bootstrapping assumes such a
