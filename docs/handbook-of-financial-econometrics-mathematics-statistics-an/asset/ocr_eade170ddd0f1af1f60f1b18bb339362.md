we employ two bootstrapping procedures, i.e., (i) Procedure I: Resampling the residuals independently with fixed common risk factors; and (ii) Procedure II: Jointly resampling both the residuals and common risk factors.

# 55.3.3.1 Procedure I: Resampling the residuals independently with fixed common risk factors

Like Kosowski et al. (2006), our first rolling window-based bootstrapping simulation resamples the residuals from a time-series of returns independently, keeps the order of common risk factors fixed, and rolls the procedure forwards throughout a large number of windows. In this section, we demonstrate the time-series bootstrapping simulation method with the Fama and French (1993) three-factor model, but the application of the bootstrapping procedure to other asset pricing models, such as the CAPM, the Carhart (1997) four-factor model, and the Fama and French (2015) five-factor model, is very similar, with the only modification of the steps being the substitution of appropriate models.

Specifically, the time-series bootstrapping simulation method includes five major steps as follows:

+   (i) We estimate the Fama and French (1993) three-factor model to calculate the estimated alphas, factor loadings, and residuals using the time-series of daily excess returns for the portfolio {(R_t - R_{f,t}), t = T_1, ..., T_{253}}, where T_1 and T_{253} are the first and last trading dates, respectively, in each rolling window:
+   
+   R_t - R_{f,t} = \hat{\alpha} + \hat{\beta} (R_{m,t} - R_{f,t}) + \hat{s} SMB_t + \hat{h} HML_t + \hat{\varepsilon}_t.  (55.3)
+   
+   (ii) We save the coefficient estimates, {\hat{\alpha}_p, \hat{\beta}_p, \hat{s}_p, \hat{h}_p}, the time-series of estimated residuals, {\hat{\varepsilon}_t = T_1, ..., T_{253}}, and the t-statistic of alpha, \hat{t}_{\alpha}.
+   
+   (iii) We generate a time-series of pseudo residuals {\varepsilon^b_t = T^b_1, ..., T^b_{253}} by randomly drawing the residuals from the saved residual vector {\hat{\varepsilon}_t} with replacements, where b is the bootstrapping simulation index. It is important to reiterate that only the residuals are reordered, while the common risk factors are not resampled, in line with the Kosowski et al. (2006).
+   
+   (iv) We produce a time-series of pseudo daily excess returns (R_t - R_{f,t})^b in the rolling window, imposing the null hypothesis of zero true