in all samples

$$RMSE = \sqrt{\frac{\sum_{i=1}^{n} (O_i - P_i)^2}{n}}.$$

It is a nonnegative metric that has no upper bound and for a perfect model, the result would be zero (Dawson et al., 2007). The method is more sensitive to larger errors due to the square component in the residual error, afterward the mean and the square root are computed to bring the error in the same units as the value to be predicted.

+   2. Nash-Sutcliffe efficiency (NSE): It is used to assess the predictive power of hydrological models and is defined as

$$NSE = 1 - \frac{\sum_{i=1}^{n} (O_i - P_i)^2}{\sum_{i=1}^{n} (O_i - \bar{O})^2}.$$

NSE can lie between 1.0 (a perfect match of modeled discharge) and $-\infty$. If NSE is zero, it indicates that the model predictions are as accurate as the mean observed data. When lower than zero, it indicates that the mean value of the observed time series would have been a better predictor than the model (Krause et al., 2005).

+   3. Persistence Index (PERS): The persistence index focuses on the relationship between the model performance and the performance of a naïve model, a model that assumes as the forecasted value the same current value.

$$PERS = 1 - \frac{SSE}{SSE_{naive}};\text{ where } SSE_{naive} = \sum_{i=1}^{n} (O_{t+L} - O_t)^2.$$

Other error metrics were also computed, such as mean absolute error (MAE), normal root mean square error (NRMSE), correlation coefficients (Cor), StdT, StdP, MuT, MuP, RMSEN, NRM SEN, MARE.

# 9.4. Case Study

In the present study, the Bagmati catchment is being analyzed. A main river with a drainage area of about 3,640 km², located in central Nepal. Springs and monsoon rainfall contribute to the streamflow. The catchment originates in the north of Kathmandu Valley and flows downstream to the Gangetic plain (see Table 9.2).