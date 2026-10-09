
is modeled as having a 100% probability of being spam. This situation is called *perfect separation*; it can mess with your standard errors but is largely benign. It is a symptom of *overfit*, which is covered in **Chapter 3**.

As with linear regression, prediction for logistic regression is easy after you’ve fit the model with `glm`. We call the `predict` function on our fitted `glm` object and provide some `newdata`, with the same variable names as the training data, at the locations where we want to predict. The output will be $x'\hat{\beta}$ for each row $x$ of `mynewdata`.

```r
> predict (spammy, newdata=email[c(1,4000),])
        1        4000
2.029963  -1.726788
```

Of course, these are *not* probabilities. To get those, you need to transform through the logit link as $e^{x'\hat{\beta}} / (1 + e^{x'\hat{\beta}})$. R’s `predict` function lets you add the `type='response'` argument to get predictions on the scale of the response (i.e., in $[0, 1]$ probability space).

```r
> predict(spammy, newdata=email[c(1,4000),], type='response')
        1        4000
0.8839073  0.1509989
```

The first email (true spam) has an 88% chance of being spam, while email #4000 (not spam) has a 15% chance of being spam—in other words, an 85% chance of being important email that George wants to read.

Logistic regression is very similar to linear regression. You still use `glm`, and you just need to adjust your with probabilities $p_{i}=\mathrm{p}(y_{i}=1)$, the likelihood is

$$ \operatorname{lhd}=\prod_{i=1}^{n} \mathrm{p}\left(y_{i} \mid \mathbf{x}_{i}\right)=\prod_{i=1}^{n} p_{i}^{y_{i}}\left(1-p_{i}\right)^{1-y_{i}} . \quad (2.22) $$

Using our logistic regression equation for $p_{i}$, this becomes

$$ \operatorname{lhd}(\boldsymbol{\beta})=\prod_{i=1}^{n}\left(\frac{\exp \left[\mathbf{x}_{i}^{\prime} \boldsymbol{\beta}\right]}{1+\exp \left[\mathbf{x}_{i}^{\prime} \boldsymbol{\beta}\right]}\right)^{y_{i}}\left(\frac{1}{1+\exp \left[\mathbf{x}_{i}^{\prime} \boldsymbol{\beta}\right]}\right)^{1-y_{i}} . \quad (2.23) $$

Taking log and multiplying by $-2$ gives you the logistic regression deviance:

$$ \begin{aligned} \operatorname{dev}(\boldsymbol{\beta}) &= -2 \sum_{i=1}^{n}\left(y_{i} \log \left(p_{i}\right)+\left(1-y_{i}\right) \log \left(1-p_{i}\right)\right) \\ &= -2 \sum_{i=1}^{n}\left[\log \left(1+e^{\mathbf{x}_{i}^{\prime} \beta}\right)-y_{i} \mathbf{x}_{i}^{\prime} \beta\right] . \end{aligned} \quad (2.24) $$

This is the function that `glm` minimizes for logistic regression. The `summary` for `glm` outputs two types of deviance:

```
> summary(spammy) ...
(Dispersion parameter for binomial family taken to be 1)
Null deviance: 6170.2 on 4600 degrees of freedom
Residual deviance: 1548.7 on 4543 degrees of freedom
AIC: 1931.8
```

The *residual deviance*— say, $D=\mathrm{dev}\left(\hat{\beta}'\right)$ — is the deviance for the fitted model as in Equation 2.21 or 2.24. It is what `glm` has fit $\hat{\beta}'$ to minimize. The *null deviance*— say, $D_{0}=\operatorname{dev}(\beta=0)$ — is the deviance for a “null” or basic model, ${}^{9}$ where all of the $\beta_{j}=0$. That is, the null deviance corresponds to the model where you don’t use $x$ and instead just set $\hat{p}_{i}=\bar{p}$.

- $D_{0}=\sum\left(y_{i}-\bar{p}\right)^{2}$ in linear regression;
- $D_{0}=-2 \sum\left[y_{i} \log (\bar{p})+\left(1-y_{i}\right) \log \left(1-\bar{p}\right)\right]$ in logistic regression.

The difference between $D$ and $D_{0}$ is due to information contained in the covariates. An important metric of how tightly your regression fits is the *proportion of deviance explained by $x$*, commonly labeled the $R^{2}$:

$$ R^{2} =\frac{D_{0}-D}{D_{0}}=1-\frac{D}{D_{0}} . $$

This measures how much response variability you are able to model as a function of the regression inputs. In these two examples,

- Spammy: $R^{2} =1-\frac{1549}{6170}=0.75$ and
- OJreg: $R^{2} =1-\frac{13975}{30079}=0.54$,
