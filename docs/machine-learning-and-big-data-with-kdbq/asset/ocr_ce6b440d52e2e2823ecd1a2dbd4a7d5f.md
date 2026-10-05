# 250 DATA SCIENCE

The minimisation of the information criteria gives an intuitive explanation to two terms forming the AIC. The first term corresponds to a penalty which might discriminate favour of complex models and prevent overfitting. The second term, on the other hand, corresponds to the quality of the fit. The AIC thus balances the bias-variance trade-off and guide towards models which are truthful but not too complex.

The concept of comparing information criteria for two competing models does not constitute any form of hypothesis testing. The comparison brings a relative measure without any significance. Let us assume we have two models $f_1$ and $f_2$ with similar information criteria $AIC_1$ and $AIC_2$. Without loss of generality, let us assume that $AIC_1 < AIC_2$. Then, the:

```
$exp\frac{AIC_1 - AIC_2}{2}$
(13.66)
```

is proportional to probability that model $f_2$ minimises the information loss relative to $f_1$.

For linear OLS-based models, the comparison based on the AIC results in similar comparison. The advantage of the AIC is that it can be used for non-nested models while measures derived from $R^2$ ($F$-test) can be used to compare nested models only.

Once we have obtained log-likelihood, we can calculate the AIC for a given model. We can stick to $\ln(beta) = -\frac{n}{2}\log(\sigma^2)$ as this is the term which will vary across models for a given sample. In the implementation below, however, we keep the full formula for log-likelihood:

```
logL::log[2*acos -1]+count[y%2.0]+neg[log[sqrt[SSR%count[y]]]+count[y]]+neg[(1.0%(2.0%count[y])]];
logL
```

895.9121

It is convenient to create a function which calculates the log-likelihood, as it is one of the main concepts used in modern econometrics:

```
.quantQ ols.logL::[(n;RSS]
// -- size of the sample
// -- Residual sum of squares
:neg[log[2*acos-1]+n%2.0]+neg[log[sqrt[SSR%n]]+neg[(1.0%(2.0%n))]];
);
```

We can verify the function:

```
.quantQ.ols.logL[count[y];RSS]
```

895.9121