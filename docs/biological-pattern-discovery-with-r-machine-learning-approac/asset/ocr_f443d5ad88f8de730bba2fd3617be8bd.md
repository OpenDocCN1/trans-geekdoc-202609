significant contribution to the dependent variable, another statistical test is required. This is done by testing a null hypothesis, $\mathcal{H}_0: eta_i = 0$ for a significance test for each regression coefficient. It calculates the following statistic [Weisberg, 2005], where $\hat{eta}_i$ is the estimated regression coefficient for the $i^{th}$ independent variable,

```
$t = \frac{\hat{eta}_i}{se(\hat{eta}_i)} \quad (4.20)$
```

where $se(\hat{eta}_i)$ is calculated using the following formula and $\mu_{x_i} = \sum_{n=1}^N x_i/N$,

```
$se(\hat{eta}_i) = \sqrt{\frac{\sum_{n=1}^N(\hat{y}_n - y_n)^2}{\sum_{n=1}^N(x_i - \mu_{x_i})^2}} \quad (4.21)$
```

Two regression models are shown in Figure 4.9. Both had a large degree of noise (variance). The regression coefficient was 0.3606 in Figure 4.9(a) and was 0.0102 in Figure 4.9(b). Their $p$ values were 0.0192 and 0.9328 in Figures 4.9(a) and (b), respectively. This answered the question whether an independent variable was significantly correlated with the dependent variable or whether an independent variable had a significant contribution to the dependent variable in a regression model. If a $p$ value for a regression coefficient was very small, a null hypothesis was rejected claiming that the contribution from the corresponding independent variable to the dependent variable was significant.

![](bbox=[0.203, 0.658, 0.796, 0.876])

Figure 4.9. The significance of a regression coefficient in two regression models.