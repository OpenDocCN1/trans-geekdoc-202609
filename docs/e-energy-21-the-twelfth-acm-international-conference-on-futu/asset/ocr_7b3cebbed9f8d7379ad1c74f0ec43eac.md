is calculated by passing the input to each of the trained regressors and then collecting their results into the output vector Ŷ.

SARIMAX. Autoregressive Integrated Moving Average (ARIMA) is a classical, widely used and explored time series forecasting model first introduced more than 4 decades ago [5, 27]. SARIMAX is an extension of classical ARIMA models, improving on them by adding additional parameters, accounting for repeating trends in the time series. Also, unlike ARIMA, SARIMAX are multivariate models, capable of using more than one input variable to predict the output [10, 32]. SARIMAX models have several parameters which define the relationship between input and output. Non-negative integer parameters p, d, q ∈ ℤ define the relationship between past observations and the output. Non-negative parameters P, D, Q, m ∈ ℤ, known as seasonal terms, define the seasonal trends within time series as well as the number of time steps in a single season. Traditionally, optimal parameter values are found by manually analysing the time series with statistical methods [10]. However, modern time series forecasting libraries automate this process by performing an parameter search without requiring human intervention [27].

# 5.2 Metrics for quantitative evaluation

Several metrics have been selected for quantitative evaluation of indoor temperature predictive models trained during experiments. Widely used Root Mean Square Error (RMSE) and Mean Absolute Error (MAE) metrics have been selected for evaluating average predictive model performance over the test set [7]. Maximum error metric (MAXE) has been selected to showcase the worst-case predictive error of the model.

$$RMSE(Y, \hat{Y}) = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(Y_i - \hat{Y}_i)^2} \tag{7}$$

$$MAE(Y, \hat{Y}) = \frac{1}{n}\sum_{i=1}^{n}|Y_i - \hat{Y}_i| \tag{8}$$

$$MAXE(Y, \hat{Y}) = \max(|Y - \hat{Y}|) \tag{9}$$

where y and ŷ are ground truth and predicted one-dimensional vectors, y_i is the i-th element in the vector (starting from 1), n is the number of elements in y and ŷ.

# 6 FLEXIBILITY PREDICTION

Heat pump flexibility will be predicted by using TEMP_FORECAST to forecast indoor temperature Ŷ and calculating how long can the heat pump be in mode ForcedOn or mode Off before violating user predefined indoor temperature comfort bounds T_ind_lower and T_ind_upper.

# 6.1 Prediction method

In this paper, flexibility will be predicted in two scenarios Off and ForcedOn, as described in Section 4. To predict flexibility in either scenario, the control signal U has to be appropriately defined before forecasting temperature with TEMP_FORECAST. When predicting flexibility for Off, U should consist of values P_hp_min, where P_hp_min is the average power consumption of the heat pump being in idle. In most cases, P_hp_min > 0 and can be determined using the

specification of the heat pump. In this case, Model(X, U) forecasts indoor temperature Ŷ_off if the heat pump will remain in mode Off for prediction horizon h time steps. When predicting flexibility for ForcedOn, U should consist of values P_hp_max, where P_hp_max is the average power consumption of the heat pump operating at its maximum capacity, usually below maximum rated power. In this case, Model(X, U) forecasts indoor temperature Ŷ_on if the heat pump will remain in mode ForcedOn for prediction horizon h time steps.

```
Algorithm 1 Flexibility prediction algorithm FLEX_PREDICT
INPUT:
Ŷ - forecasted indoor temperature
T_ind_lower - lower bound of temperature
T_ind_upper - upper bound of temperature
ε - absolute temperature forecasting error used for adjustment
OUTPUT:
F̂ - predicted flexibility
1: procedure FLEX_PREDICT
2:   F̂ ← 0
3:   N ← length(Ŷ)
4:   for i ← 1 to N do
5:     if (T_ind_lower + ε) ≤ Ŷ(i) ≤ (T_ind_upper - ε) then
6:       F̂ ← F̂ + 1   ▷ If temperature is within bounds
7:     else
8:       break       ▷ If temperature violates bounds
9:   return F̂
```

Once indoor temperature Ŷ is forecasted, flexibility will be predicted using FLEX_PREDICT, as defined in Algorithm 1, using Ŷ and predefined user temperature bounds T_ind_lower and T_ind_upper. Optionally, an absolute forecasting error parameter ε, where ε >= 0 can be used to adjust for average TEMP_FORECAST error. As seen in Algorithm 1, ε effectively shrinks the temperature bounds by subtracting ε from the upper bound T_ind_upper and adding ε to lower bound T_ind_lower. If ε > 0, this results in a more pessimistic prediction of potential heat pump flexibility. If error adjustment is not preferred, ε = 0 is used.

# 6.2 Metrics for evaluating flexibility

In this paper, we propose several metrics for evaluating flexibility prediction performance. Flexibility prediction performance can be numerically evaluated by comparing predicted flexibility F̂ calculated using forecasted indoor temperature Ŷ and potential flexibility F calculated using ground-truth indoor temperature Y.

Mean Absolute Flexibility Error (MAFE) is an adaptation of MAE for evaluating average absolute error for predicted flexibility.

$$MAFE(Z, \hat{Z}) = \frac{1}{n}\sum_{i=1}^{n}|Z_i - \hat{Z}_i| \tag{10}$$

where Z = ⟨F₁, F₂, …, Fₙ⟩ and Ẑ = ⟨F̂₁, F̂₂, …, F̂ₙ⟩ are vectors of predicted flexibility from predicted and ground-truth temperatures, respectively. n is the number of elements in Z and Ẑ.

Two types of errors are possible while predicting flexibility: underestimation when F̂ < F (predict that the heat pump can operate