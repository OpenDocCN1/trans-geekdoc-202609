
Simulation of an ARCH (1) and GARCH (1, 1) time series done respectively using a function `simulate_GARCH(n, omega, alpha, beta = 0)`. Recall the difference between an ARCH (1) and a GARCH (1, 1) model is: besides an autoregressive component of *α* multiplying lag-1 residual squared, a GARCH model includes a moving average component of *β* multiplying lag-1 variance. The function will simulate an ARCH/GARCH series based on `n` (number of simulations), `omega`, `alpha`, and `beta` (0 by default). It will return simulated residuals and variances ([Figure 7.4](#ch7.xhtml#fig7_4)).

![Figure 7.4: Simulation test of data.](images/fig7_4_C.jpg)

[Figure 7.4: Simulation test of data.](#ch7.xhtml#R_fig7_4)

## 10. Simulation Impact of Parameters on Model

For simulation purpose function `simulate_GARCH()` called and the impact of GARCH model parameters on simulated results is analyzed. Specifically, we have simulated two GARCH (1, 1) time series; they have the same `omega` and `alpha`, but different `beta` as input. Recall in GARCH (1, 1), since *β* is the coefficient of lag-1 variance, if *α* is fixed, the larger the *β*, the longer the duration of the impact. In other words, high or low volatility periods tend to persist. Pay attention to the plotted results and see whether we can verify the *β* impact ([Figures 7.5](#ch7.xhtml#fig7_5) and [7.6](#ch7.xhtml#fig7_6)).

![Figure 7.5: Simulation impact of (beta=0.2) on GARCH model.](images/fig7_5_C.jpg)

[Figure 7.5: Simulation impact of (beta=0.2) on GARCH model.](#ch7.xhtml#R_fig7_5)

![Figure 7.6: Simulation impact of (beta=0.6) on GARCH model.](images/fig7_6_C.jpg)

[Figure 7.6: Simulation impact of (beta=0.6) on GARCH model.](#ch7.xhtml#R_fig7_6)

## 11. Forecast Evaluation

At 90% confidence interval the performance of model is evaluated and different types of error is calculated. The lower value of root means squared (RMS) proves the supremacy of forecasting model. In proposed model the RMSE value is 0.018777 that is very low so we can say that our model’s forecasting value is very close to actual value and proves the accuracy of our model. The second error estimation parameter is Thiel inequality coefficient is 0.900024 that is 0.90% shows the perfect fit between actual open price and forecasting open price of the mutual fund. Third parameter is bias proportion which is also proves the accuracy of model in our proposed model. The value of error term is 0.000150 which shows the systematic error value of bias proportion is very low also shows the accuracy of proposed model. Another performance parameter mean absolute error also shows value 0.014534 and proves the accuracy of our proposed model ([Table 7.1](#ch7.xhtml#tab7_1), [Figures 7.7](#ch7.xhtml#fig7_7) and [7.8](#ch7.xhtml#fig7_8)).

[Table 7.1 : Performance matrices of model](#ch7.xhtml#R_tab7_1)

| RMSE || Thiel inequality coefficient || Bias proportion || Mean absolute Error |
| --- | --- | --- | --- |
| 0.018777 || 0.900024 || 0.000150 || 0.014534 |
| --- | --- | --- | --- |

![Figure 7.7: Forecast evaluation of model.](images/fig7_7_C.jpg)

[Figure 7.7: Forecast evaluation of model.](#ch7.xhtml#R_fig7_7)

![Figure 7.8: Forecast comparison graph.](images/fig7_8_C.jpg)

[Figure 7.8: Forecast comparison graph.](#ch7.xhtml#R_fig7_8)

## 12. Conclusions

This paper uses GARCH volatility models to analyze and predict conditional deviations. The proposed methodology helps build a long-term robust portfolio by analyzing historical data based on time-series analysis. The low RMSE value of 0.018777 indicates that the GARCH model’s predictions are quite accurate, with minimal variance from the actual data. This suggests that the model is effective in capturing the underlying patterns of mutual fund volatility. The Thiel inequality coefficient of 0.900024 is close to 1, implying a high degree of accuracy in the forecasts. This coefficient measures the relative accuracy of predictions, and a value close to 1 suggests a strong predictive capability of the GARCH model. The bias proportion of 0.000150 is indicative of a negligible bias in the model’s predictions. This means that the GARCH model’s forecasts are not systematically overestimating or underestimating the mutual fund volatility, resulting in unbiased predictions. The MAE of 0.014534 further supports the accuracy of the GARCH model. It represents the average absolute difference between predicted and actual values. A low MAE indicates that the model’s forecasts closely align with the observed data. Analytical outcomes show that it is an acceptable model. The proposed model can be used by portfolio managers to compare the performance of investment trusts over a considerable period of time. The experiment was conducted using Indian mutual fund data, but it can also be applied to various mutual funds around the world. It is also recommend for future researchers to investigate various sectors mutual funds with external factors that badly affects the Indian mutual fund market. Further improvements can be made to improve the accuracy of proposed framework for analysis of other different factors that influence the volatility of Indian mutual fund.

## References

1. [Wang, X., Tsokos, C. P., and Saghafi, A.](#ch7.xhtml#R_ref7_1) (2018). Improved parameter estimation of time dependent kernel density by using artificial neural networks. J Fin Data Sci., 4(3), 172–182, [https://doi.org/10.1016/j.jfds.2018.04.002](http://dx.doi.org/10.1016/j.jfds.2018.04.002).

2. [Matsatsinis, N. F. and Manarolis, E. A.](#ch7.xhtml#R_ref7_2) (2009). New hybrid recommender approaches: an application to equity funds selection. Int. Conf. Algorith. Dec. Theory, 156–167.

3. [Zheng, Y.](#ch7.xhtml#R_ref7_3) (2021). Multi-objective recommendations: A tutorial. arXiv preprint arXiv:2108.06367. Cornell University, 1, 1–9. [https://doi.org/10.48550/arXiv.2108.06367](http://dx.doi.org/10.48550/arXiv.2108.06367).

4. [Yera, R. and Martinez, L.](#ch7.xhtml#R_ref7_4) (2017). Fuzzy tools in recommender systems: A survey. Int. J. Comput. Intel. Sys., 10(1), 776.

5. [Wang, Y., Wang, M., and Xu, W.](#ch7.xhtml#R_ref7_5) (2018). A sentiment-enhanced hybrid recommender system for movie recommendation: A big data analytics framework. Wireless Comm. Mob. Comput., Volume 2018, 1–9. [https://doi.org/10.1155/2018/8263704](http://dx.doi.org/10.1155/2018/8263704).

6. [Fayyaz, Z., Ebrahimian, M., Nawara, D., Ibrahim, A., and Kashef, R.](#ch7.xhtml#R_ref7_6) (2020). Recommendation systems: Algorithms, challenges, metrics, and business opportunities. Appl. Sci., 10(21), 7748, doi: [10.3390/app10217748](http://dx.doi.org/10.3390/app10217748).

7. [Chen, H. and Lian, Q.](#ch7.xhtml#R_ref7_7) (2021). Poverty/investment slow distribution effect analysis based on Hopfield neural network. Fut. Gener. Comp. Sys., 122, 63–68.

8. [Wang, S., Huang, C., Li, J., Yuan, Y., and Wang, F. Y.](#ch7.xhtml#R_ref7_8) (2019). Decentralized construction of knowledge graphs for deep recommender systems based on block chain-powered smart contracts. IEEE Acc., 7, 136951–136961.

9. [Das, S. G. and Nayak, B.](#ch7.xhtml#R_ref7_9) (2020). Financial inclusion: An application of machine learning in collaborative filtering recommender systems. Int. J. Recent Technol. Engg., 8(6), Online publication. DOI:[10.35940/ijrte.F9361.038620](http://dx.doi.org/10.35940/ijrte.F9361.038620).

10. [Maji, G., Mondal, D., Dey, N., Debnath, N. C., and Sen, S.](#ch7.xhtml#R_ref7_10) (2021). Stock prediction and mutual fund portfolio management using curve fitting techniques. J. Ambient Intel. Human. Comput., 12(10), 9521–9534, [https://doi.org/10.1007/s12652-020-02693-6](http://dx.doi.org/10.1007/s12652-020-02693-6).
