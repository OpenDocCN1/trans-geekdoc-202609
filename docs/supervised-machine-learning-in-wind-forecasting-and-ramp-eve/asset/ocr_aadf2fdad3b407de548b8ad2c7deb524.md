![](bbox=[0.12, 0.1, 0.83, 0.34])

# Figure 4.13 Riverflow forecasting based on $\epsilon$-TSVR.

where $S = [K(X, X^T) e]$, and $\alpha, \gamma$ are the Lagrangian multipliers, which enable the finding of local maxima and/or minima of the function subject to equality constraints. The end regressor $f_{\epsilon-TSVR}(x)$ is given as the mean of the two functions:

\( f_{\epsilon-TSVR}(x) = \frac{1}{2}((w_1^T + w_2^T)K(X, X^T) + (b_1 + b_2)). \quad (4.41) \)

# River flow forecasting: a case study for Nile river

Next, we discuss the river flow volume forecasting based on $\epsilon$-TSVR model. Monthly mean for river flow volume is collected from https://people.sc.fsu.edu/~jburkardt/datasets/time_series/. A total of 570 samples are taken and are segmented into training (470) and testing (100) sets. The input set for the regression is constructed by wavelet decomposition of river flow time series. The detailed and approximate signals are then treated as predictor variables. Figs. 4.13 and 4.14 illustrate the predicted time-series plots and scatter plots for $\epsilon$-TSVR and persistence models.

Based on the manual tuning of the hyperparameters, from Table 4.4 we obtain the RMSE 0.0257 of $\epsilon$-TSVR model and 0.6150 of the persistence model.

In this chapter, we primarily discussed SVR and its variants for regression analysis. These supervised learning models are applied for wind speed time-series datasets from different places around the globe to assess the performance of each model. The forecasting performance in terms of