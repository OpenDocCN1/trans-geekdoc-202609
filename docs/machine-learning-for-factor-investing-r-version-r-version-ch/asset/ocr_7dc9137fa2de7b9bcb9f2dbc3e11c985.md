+   - the probability of outperforming a benchmark (computed over a given time frame);
+   - the binary version of the above: YES (outperforming) versus NO (underperforming);
+   - risk-adjusted versions of the above: Sharpe ratios, information ratios, MAR or CALMAR ratios (see Section 12.3).

When creating binary variables, it is often tempting to create a test that compares returns to zero (profitable versus non profitable). This is not optimal because it is very much time-dependent. In good times, many assets will have positive returns, while in market crashes, few will experience positive returns, thereby creating very unbalanced classes. It is a better idea to split the returns in two by comparing them to their time-_t_ median (or average). In this case, the indicator is relative and the two classes are much more balanced.

As we will discuss later in this chapter, these choices still leave room for additional degrees of freedom. Should the labels be rescaled, just like features are processed? What is the best time horizon on which to compute performance metrics?

# 4.5.2 Categorical labels

In a typical ML analysis, when _y_ is a proxy for future performance, the ML engine will try to minimize some distance between the predicted value and the realized values. For mathematical convenience, the sum of squared error (_L_<sup>2</sup> norm) is used because it has the simplest derivative and makes gradient descent accessible and easy to compute.

Sometimes, it can be interesting not to focus on raw performance proxies, like returns or Sharpe ratios, but on discrete investment decisions, which can be derived from these proxies. A simple example (decision rule) is the following:

```
y_{t,i} = \left\{\begin{array}{ c c }
-1 & \text{if } \hat{r}_{t,i} < r_- \\
0 & \text{if } \hat{r}_{t,i} \in [r_-, r_+] \\
+1 & \text{if } \hat{r}_{t,i} > r_+
\end{array}\right., \quad (4.2)
```

where \(\hat{r}_{t,i}\) is the performance proxy (e.g., returns or Sharpe ratio) and \(r_\pm\) are the decision thresholds. When the predicted performance is below _r_<sub>-</sub>, the decision is -1 (e.g., _sell_), when it is above _r_<sub>+</sub>, the decision is +1 (e.g., _buy_) and when it is in the middle (the model is neither very optimistic nor very pessimistic), then the decision is neutral (e.g., _hold_). The performance proxy can of course be relative to some benchmark so that the decision is directly related to this benchmark. It is often advised that the thresholds \(r_\pm\) be chosen such that the three categories are relatively balanced, that is, so that they end up having a comparable number of instances.

In this case, the final output can be considered as categorical or numerical because it belongs to an important subgroup of categorical variables: the ordered categorical (**ordinal**) variables. If _y_ is taken as a number, the usual regression tools apply.

When _y_ is treated as a non-ordered (**nominal**) categorical variable, then a new layer of processing is required because ML tools only work with numbers. Hence, the categories must be recoded into digits. The mapping that is most often is used called ‘**one-hot encoding**’. The vector of classes is split in a sparse matrix in which each column is dedicated to one class. The matrix is filled with zeros and ones. A one is allocated to the column corresponding to the class of the instance. We provide a simple illustration in the table below.