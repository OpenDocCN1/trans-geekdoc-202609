![](bbox=[0.1, 0.07, 0.82, 0.44])

FIGURE 5.9: Centered ICE plots of predicted number of bikes by weather condition. The lines show the difference in prediction compared to the prediction with the respective feature value at its observed minimum.

# ## 5.2.1.3 Derivative ICE Plot

Another way to make it visually easier to spot heterogeneity is to look at the individual derivatives of the prediction function with respect to a feature. The resulting plot is called the derivative ICE plot (d-ICE). The derivatives of a function (or curve) tell you whether changes occur and in which direction they occur. With the derivative ICE plot, it is easy to spot ranges of feature values where the black box predictions change for (at least some) instances. If there is no interaction between the analyzed feature \(x_{S}\) and the other features \(x_{C}\)), then the prediction function can be expressed as:

```
\(\hat{f}(x)=\hat{f}(x_{S},x_{C})=g(x_{S})+h(x_{C}),\quad \text{with}\quad \frac{\delta \hat{f}(x)}{\delta \{ \} x_{S}}=g'(x_{S})\)
```

Without interactions, the individual partial derivatives should be the same for all instances. If they differ, it is due to interactions and it becomes visible in the d-ICE plot. In addition to displaying the individual curves for the derivative of the prediction function with respect to the feature in S, showing the standard deviation of the derivative helps to highlight regions in feature in S with heterogeneity in the estimated derivatives. The derivative ICE plot takes a long time to compute and is rather impractical.

# ## 5.2.2 Advantages

Individual conditional expectation curves are **even more intuitive to understand** than partial dependence plots. One line represents the predictions for one instance if we vary the feature of interest.

Unlike partial dependence plots, ICE curves can **uncover heterogeneous relationships**.