# Time Series Analysis

```
geom_line(aes(y = DALYS), color = "brown") +
geom_line(aes(y = response), linetype = "dashed") +
facet_wrap(vars(location_id, c(`182` = "Malawi",
\t\tlabeller = as_labeller(c(\t\t`191` = "Zambia",
\t\t`169` = "Central African Republic")),
\tscales = "free_y") +
labs(title = "Dengue Predictions for 2017-2021: xgboost")
```

# Dengue Predictions for 2017-2021: xgboost

![](bbox=[0.106, 0.28, 0.893, 0.519])

Figure 9.2 Dengue Predictions for 2017-2021: xgboost. The solid line shows the historical data, the brown line shows the new data, and the dashed line shows the predictions.

In conclusion, predictive modelling is a valuable tool for forecasting future trends and making informed decisions based on historical data. By leveraging the insights gained from the models, we can anticipate the trajectory of infectious diseases, estimate disease burden, and evaluate the impact of interventions on population health. The models can be further refined and optimised to improve their predictive performance and provide more accurate forecasts.
By combining predictive modelling with time series analysis and mixed models, we can gain a comprehensive understanding of the complex dynamics of public health and make data-driven decisions to improve population health outcomes.

# 9.3 Time Series Analysis

One important side of the analysis is to consider the evolution of the phenomenon in time. We can do this by using time as a factor in the model. Time series analysis serves as a tool for understanding and forecasting temporal patterns. Techniques such as AutoRegressive