# Actual prediction: 0.04
Average prediction: 0.01

![](bbox=[0.338, 0.114, 0.873, 0.413])

**FIGURE 13.6:** Illustration of the Shapley method.

In the output shown in Figure 13.6, we again obtain the two crucial insights: **sign** of the impact of the feature and **relative importance** (compared to other features).

# 13.2.3 Breakdown

Breakdown (see, e.g., Staniak and Biecek (2018)) is a mixture of ideas from PDPs and Shapley values. The core of breakdown is the so-called **relaxed model prediction** defined in Equation (13.4). It is close in spirit to Equation (13.1). The difference is that we are working at the local level, i.e., on one particular observation, say \(x^*\). We want to measure the impact of a set of predictors on the prediction associated to \(x^*\), hence, we fix two sets **k** (fixed features) and -**k** (free features) and evaluate a **proxy** for the average prediction of the estimated model \(\hat{f}\) when the set **k** of predictors is fixed at the values of \(x^*\), that is, equal to \(x_\mathbf{k}^*\) in the expression below:

```
\(\tilde{f}_\mathbf{k}(x^*) = \frac{1}{M} \sum_{m=1}^M \hat{f} \, x_{-\mathbf{k}}^{(m)}, x_\mathbf{k}^* \quad .\) (13.4)
```

The \(x^{(m)}\) in the above expression are either simulated values of instances or simply sampled values from the dataset. The notation implies that the instance has some values replaced by those of \(x^*\), namely those that correspond to the indices **k**. When **k** consists of all features, then \(\tilde{f}_\mathbf{k}(x^*)\) is equal to the raw model prediction \(\hat{f}(x^*)\) and when **k** is empty, it is equal to the average sample value of the label (constant prediction).