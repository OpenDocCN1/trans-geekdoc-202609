```
\begin{equation}\texttt{dev}_{IS}(\hat{\boldsymbol{\beta}})=\sum_{i=1}^{n}(y_{i}-\boldsymbol{x}_{i}^{t}\hat{\boldsymbol{\beta}})^{2}.\tag{3.1}\end{equation}
```

For out-of-sample R2, β̂ is the same (still fit with observations 1 . . . n), but the deviance is now calculated over new observations; for example:

```
\begin{equation}\texttt{dev}_{OOS}(\hat{\boldsymbol{\beta}})=\sum_{i=n+1}^{n+m}(y_{i}-\boldsymbol{x}_{i}^{t}\hat{\boldsymbol{\beta}})^{2}\tag{3.2}\end{equation}
```

This distinction is massively important. When you have big data and many inputs, it is easy to overfit the training data so that your model is being driven by noise that will not be replicated in future observations. That adds errors to your predictions, and it is possible that the overfit model becomes worse than no model at all.

As an example, let's consider quality-control data from a semi-conductor manufacturing process. This industrial setting involves many complicated operations with little margin for error. There are hundreds of diagnostic sensors along the production line, measuring various inputs and outputs in the process. Our goal is to build a model that maps from this sensor data to a prediction for chip failure. Then chips at risk of failure can be flagged for further (expensive, human) inspection.

For training data we have 1500 observations of a length-200 vector x of diagnostic signals, along with binary data on whether the chip was a failure.1 The logistic regression model is then

```
\begin{equation}p_{i}=\texttt{p}(\texttt{fail}_{i}\vert \boldsymbol{x}_{i})=\frac{e^{\alpha+\boldsymbol{x}_{i}\boldsymbol{\beta}}}{(1+e^{\alpha+\boldsymbol{x}_{i}\boldsymbol{\beta}})}\tag{3.2}\end{equation}
```

We can fit this in R and calculate the in-sample deviance using glm.2

```
```r
> full <- glm(FAIL ~ ., data=SC, family=binomial)
Warning message:
glm.fit: fitted probabilities numerically 0 or 1 occurred
> 1 - full$deviance/full$null.deviance
[1] 0.5621432
```
```