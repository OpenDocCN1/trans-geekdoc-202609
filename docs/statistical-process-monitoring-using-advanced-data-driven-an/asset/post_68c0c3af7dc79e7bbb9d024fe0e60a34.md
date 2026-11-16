
where \(\delta_{k,h}\) is the \(h\)th element of \(\delta_k\), and \(\hat{\delta}_{k,h}^{ls}\) is its least squares estimate. The regularization parameter is selected using the EBIC criterion proposed by [41],

\(\text{EBIC}_{\phi}(\gamma) = np \log \left( \frac{\text{RSS}(\gamma)}{np} \right) + \nu(\gamma) \log(np) + 2\phi \log \binom{np-2}{\nu(\gamma)}, (3.8)\)

where \(\text{RSS}(\gamma)\) is the residual sum of squares of the model for a given \(\gamma\); \(\nu(\gamma)\) is the number of change points detected; \(np - 2\) is the dimension of the searched parameter space, or the number of potential change point locations; and \(\phi \in [0, 1]\) is a user-defined parameter that controls the false signal rate. Setting \(\phi = 1\) controls the number of false signals to be low.

Capizzi and Masarotto [8] study the performance of mphase1 extensively in simulation and find that it performs very well for a variety of underlying multivariate distributions and for a variety of fault types. It achieves the nominal false alarm probability in IC data regardless of distribution, and for data contaminated with multiple faults, it identifies all of the faults exactly or approximately (within five time steps). While the authors do not provide a performance assessment of the method's ability to correctly identify the shifted variables, in practice, the method appears to properly isolate the correct variables when data meet the method's assumptions.

To illustrate mphase1, we simulate 150 observations of ten variables, both from a multivariate normal with an identity variance-covariance matrix. In the first case, data are IC, and Fig. 3.5 shows the \(p\)-value of 0.359 for testing the null hypothesis that the mean of the observations is constant. Thus, there is no significant evidence that the mean differs from zero, and this dataset could then be used to estimate parameters and rejection thresholds for a subsequent Phase II analysis. In a second case, the data are OC with shifts in the mean as shown in Fig. 3.6. Variables x1, x2, and x3 exhibit step shifts, some of which coincide. Variable x10 has a drift fault beginning at observation 100. Fig. 3.7 shows the results. The \(p\)-value to test that the mean has shifted for any of the variables is less than 0.001, indicating significant evidence of at least one shift. The shifts in x1, x2, and x3 are estimated nearly perfectly with the shifts sometimes detected one or two time steps earlier or later than when they actually occur. The drift fault in variable x10 is treated as if multiple step shifts occur, so if a drift is present, it is often manifested with multiple consecutive shifts in the same direction.

While the mphase1 method provides an approach to directly test if a set of observations can be used for estimating parameters for Phase II analysis, another goal may be to isolate variables to diagnose faults that occurred in the past. Klanderman et al. [42] develop a retrospective change-point detection method that is also distribution-free, but relies on fused lasso to drive the difference in adjacent means to zero. Their method is called adjusted flexible fault isolation (aFFI).

### Example method 2, aFFI

Most proposed methods assume that the mean of the process is stationary and constant, but it is often the case in practice that the mean is nonzero. A common approach is to remove the trend by fitting a model to data that are known to be IC, with several examples provided in dynamic screening systems [43–46]. In Sect. 3.5.1, an example of detrending in a complex system is given followed by application of the method in [42], termed *adjusted Flexible Fault Isolation* (aFFI), which is described here. This method does not assume that the observations are stationary, and in addition, temporal dependence in the observations is also allowed. The detrending occurs for a training period, and the estimates of the parameters in the trend model are used to detrend a period for which monitoring is desired. Assuming that the observations, x_i, i = 1, ..., p, have been suitably standardized and detrended, the set

p-value=0.359

![](img/aa2f42c739937b682075082233e335bb_99_0.png)

FIGURE 3.5 Plot of ten variables simulated under IC conditions. The p-value at the top of the figure is for the mphase1 test of the null hypothesis that the observations are location stationary.

of \( p \) linear regression models are fit as

```
\(\mathbf{x}_j^{\text{M}} = \boldsymbol{\beta}_j + \boldsymbol{\epsilon}_j, \quad j=1, \dots, p,\) (3.9)
```

where \(\mathbf{x}_j^{\text{M}}\), \(\boldsymbol{\beta}_j\), and \(\boldsymbol{\epsilon}_j\) are vectors of length \( n \), and the errors \(\boldsymbol{\epsilon}_j\) have mean zero and constant variance. The \(\mathbf{x}_j^{\text{M}}\) is the set of observations for variable \( j \) in the monitoring period. The mean of the response for the \( j \)th variable at time step \( t \) is \( \beta_{j,t} \), and a change in the mean of the process is indicated when \( \beta_{j,t} \neq \beta_{j,t+1} \). When \( \beta_{j,t} \neq \beta_{j,t+1} \), time \( t+1 \) is referred to as a *change point* for variable \( j \). A variable is classified as *shifted* at time \( t+1 \) if there is a change point at time \( t+1 \) versus *unshifted* if no change occurs at \( t+1 \). The \(\boldsymbol{\beta}_j\) for \( j=1, \dots, p \), are estimated with fused lasso.

Fused lasso is used when there is a natural ordering to the parameters, such as parameters that are indexed by time [47]. Fused lasso penalizes the difference between adjacent coefficients rather than penalizing the coefficients themselves, driving the small changes between adjacent coefficients to zero [38]. Zhang et al. [48] also use fused lasso in a Bayesian framework to perform fault isolation by estimating the fault probability for each variable. The theoretical properties of change point detection using fused lasso are in [49].

An algorithm to perform fused lasso [50] is implemented in the `R` package `genlasso` [51]. An estimate for \(\boldsymbol{\beta}_j\) for \( j=1, \dots, p \) is obtained by minimizing

![](img/aa2f42c739937b682075082233e335bb_100_0.png)

FIGURE 3.6 Plot of the mean of the four variables exhibiting OC conditions. The first three variables have transient or sustained shift faults while the last has a drift fault beginning at observation 100.

the following:

```
\frac{1}{2} \sum_{j=1}^p \sum_{t=1}^n (x_{j,t} - \beta_{j,t})^2 + \gamma \sum_{j=1}^p \sum_{t=1}^{n-1} |\beta_{j,t+1} - \beta_{j,t}|.
```

In order to choose \(\gamma\), the EBIC in Eq. (3.8) can be used again. Within this framework, the EBIC is

```
EBIC_\phi(\gamma) = np \log \left( \frac{\text{RSS}(\gamma)}{np} \right) + \nu(\gamma) \log(np) + 2\phi \log \binom{np - p}{\nu(\gamma)}, \quad (3.10)
```

p-value<0.001

![](img/aa2f42c739937b682075082233e335bb_101_0.png)

FIGURE 3.7 Plot of ten variables simulated under OC conditions. The p-value at the top of the figure is for the mphase1 test of the null hypothesis that the observations are location stationary.

where the primary differences are that RSS(\(\gamma\)) is the residual sum of squares of Eq. (3.9), and \(np - p\) is the dimension of the searched parameter space, or the number of potential change point locations. There cannot be a change point detected at the first observation, \(t=1\), so change points can only be detected at a maximum of \(np - p\) locations.

One problem with the EBIC in Eq. (3.10) is that using the sample size, \(n\), in it implies that the observations are independent. However, if \(\mathbf{x}_j\) are autocorrelated, then the effective sample size (ESS), or the equivalent number of independent observations, differs from \(n\). If positive autocorrelation is present, the ESS will be smaller than the actual sample size, and the stronger the positive autocorrelation, the smaller the ESS. Therefore, the ESS is calculated, which is denoted \(n'\), as follows:

\(n' = \frac{n}{1 + \frac{1}{n} \sum_{h>0} R(h)}, \quad (3.11)\)

where \(R(h)\) is a user-selected function that models the autocorrelation when the process is IC between two distinct observations (i.e., \(h \neq 0\)) that are \(h\) time steps apart [52]. Confirming the presence of autocorrelation and determining the most appropriate \(R(h)\) can be done by investigating the sample autocorrelation function (ACF) and partial autocorrelation function (PACF) plots of each \(\mathbf{x}_j\) in the IC training period. This assumes that the strength and structure of the temporal dependence are the same for each variable. Replacing \(n\) with \(n'\) leads to the adjusted EBIC (aEBIC)

\(\text{aEBIC}_\phi(\gamma) = n' p \log \left( \frac{\text{RSS}(\gamma)}{n' p} \right) + \nu(\gamma) \log(n' p) + 2\phi \log \binom{np - p}{\nu(\gamma)}.\)

Then, \(\gamma\) is chosen such that aEBIC is minimized, yielding the estimated coefficients \(\hat{\boldsymbol{\beta}}_j\) for \(j=1, \dots, p\). Clearly, when the standardized residuals are independent, \(R(h) = 0\) for \(h > 0\), then \(n' = n\), so aEBIC can be used to select \(\gamma\) even in the absence of autocorrelation.

Finally, the estimated coefficients must be converted into a list of times at which faults may have occurred and a list of shifted variables associated with each fault. A change point at time \(t+1\) is identified in variable \(j\) when the estimated \(\hat{\beta}_{j,t} \neq \hat{\beta}_{j,t+1}\). To reduce the number of faults detected within a few time steps of each other, change points are ordered from first to last and, if any additional change points are identified within \(\kappa\) time steps of the previous change point, they are combined into a single fault. The parameter \(\kappa\) is set to be relatively small so that shifts in multiple variables detected within a small window in time are associated with the same fault, but two distinct faults are not combined into a single fault.

An estimate of the shift size and direction in the standardized residuals, \(\delta_{j,t}\), for the \(j\)th variable at time \(t\) is

\(\hat{\delta}_{j,t} = \max_{t_1, t_2 \in \{t-l+1, ..., t+\kappa\}} |\hat{\beta}_{j,t_1} - \hat{\beta}_{j,t_2}| \cdot \text{sign}(\max \text{ difference}).
