# Out-of-sample prediction for inflation PC and unemployment PC and first three PCs during crisis period and near zero environment using JSZ model

![](bbox=[0.05, 0.08, 0.95, 0.52])

# Figure 61.4: Out-of-sample forecasts for the Joslin et al. (2013a) Gaussian Macro dynamic term structure model.

+   1. This figure plots forecasts for the five principal components used to estimate the Joslin et al. (2013a) (JLS) Gaussian Macro dynamic term structure model.
+   
+   2. Out-of-sample forecasts were constructed by estimating the model of JLS using the first 78 months of data and corresponding to the normal economic environment and economic boom period and by constructing rolling regression-based out-of-sample forecasts over the remaining 138 months.
+   
+   3. Please see Figure 61.3 for more information.

variable, the other factors do seem to be getting more stable post July 2015. Therefore, taken together, both assessments of empirical performance indicate that the JSZ model is severely affected during the crisis and in near zero environments. We also present a plot of the forecasted zero coupon yield associated with JSZ in Figure 61.3 and it clearly supports the main conclusion from the plot of the principal components. The model does a very poor job at forecasting, out of sample, as it frequently violates the ZLB. As for the JLS model, although it seems to be stable through the measurement of the in-sample fitting error, the rolling window out-of-sample forecasts indicate that it too be severely affected. In the un-reported results, we found that the forecasted yields produced by JLS were impacted more adversely around the ZLB than those produced by JSZ.

> Motivated by JSZ (2011b) who use invariant transformations to demonstrate that the arbitrage free Nelson-Siegel model developed by Christensen, Diebold, and Rudebusch (2011) is a special case of the JSZ normalization, we also estimate the JSZ normalization with
> 
> κ¹X = [0 0 0; 0 -λ λ; 0 0 -λ] r∞^Q = 0 and ρ1 = [1; 0]
> 
> We also assume that the six-month yield, two-year yield, and 10-year yield are priced perfectly in order to “invert” the model to obtain state variables. These assumptions allow us to: (1) Estimate a model equivalent to the model of Christensen, Diebold, and

```
κ_{1X}^Q = \begin{bmatrix} 0 & 0 & 0 \\ 0 & -\lambda & \lambda \\ 0 & 0 & -\lambda \end{bmatrix} \quad r_\infty^Q = 0 \quad \text{and} \quad \rho_1 = \begin{bmatrix} 1 \\ 0 \end{bmatrix}
```