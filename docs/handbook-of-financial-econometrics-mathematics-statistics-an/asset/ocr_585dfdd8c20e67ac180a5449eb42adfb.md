```
H_i = \frac{\bar{R}_i - R_f}{\sigma_{\varepsilon i}^2} - \frac{\beta_i \sigma_m^2}{\sigma_{\varepsilon i}^2} \sum_{j=1}^{n} \beta_j H_j + \mu_i, \tag{82C.1}
```

where $H_i \ge 0, \mu_i \ge 0$, and $\mu_i H_i = 0$ for all $i$.

The justification of this equation can be found in Elton et al. (1976). Assuming all stocks that would be in an optimal portfolio (called $d$) can be found, and then arranging these stocks as $i = 1,2,\dots,d$, for the subpopulation of stocks that make up the optimal portfolio:

```
H_i = \frac{\bar{R}_i - R_f}{\sigma_{\varepsilon i}^2} - \frac{\beta_i \sigma_m^2}{\sigma_{\varepsilon i}^2} \sum_{j=1}^{d} H_j \beta_j \text{ and } \mu_i = 0. \tag{82C.2}
```

Multiplying both sides by $\beta_j$, summing over all stocks in $d$, and rearranging yields

```
\sum_{j=1}^{d} H_j \beta_j = \frac{\sum_{j=1}^{d} \left( \frac{\bar{R}_j - R_f}{\sigma_{\varepsilon j}^2} \right) \beta_j}{1 + \sigma_m^2 \sum_{j=1}^{d} \frac{\beta_j^2}{\sigma_{\varepsilon j}^2}}. \tag{82C.3}
```

Note since the set $d$ contains all stocks with positive $H_i$,

```
\sum_{j=1}^{n} H_j \beta_j = \sum_{j=1}^{d} H_j \beta_j,
```

and let

```
C^* = \sigma_m^2 \frac{\sum_{j=1}^{d} \frac{\bar{R}_j - R_f}{\sigma_{\varepsilon j}^2} \beta_j}{1 + \sigma_m^2 \sum_{j=1}^{n} \frac{\beta_j^2}{\sigma_{\varepsilon j}^2}}. \tag{82C.4}
```

Using (82C.4), the following equation for $H_i$ is obtained after substitution and rearranging from equation (82C.1):

```
H_i = \frac{\beta_i}{\sigma_{\varepsilon i}^2} \left( \frac{\bar{R}_i - R_f}{\beta_i} - C^* \right) + \mu_i. \tag{82C.5}
```

Since $\mu_i \ge 0$, the inclusion of $\mu_i$ can only increase the value of $H_i$. Therefore, if $H_i$ is positive, $\mu_i = 0$ can never make it zero and the security should be included, if $H_i < 0$, when $\mu_i = 0$, positive values of $\mu_i$ can increase $H_i$. However, because the product of $\mu_i$ and $H_i$ must equal zero, as indicated in equation (82C.1), positive values of $\mu_i$ imply $H_i = 0$. Therefore, any security $H_i < 0$ when $\mu_i = 0$ must be rejected. Therefore, equation (82.15) in the text can be used to estimate the optimal weight of a portfolio.