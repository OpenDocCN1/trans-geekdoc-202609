statistical properties of the data observed, over time, across the different time series.

+   - **No exogenous variables**: Another weakness of VAR models is that the time series, when the variables are obtained, contains exogenous variables which can affect the time series, but cannot be used in the models with ease.
+   - **Limited forecast horizon**: VAR models are normally more appropriate for short-term forecasts, and there can be a considerable decline in the accuracy while extended to cover long-term periods.
+   - **Model identification**: One of the serious problems with the VAR model is the question of how to choose the lag order. This selection can be subjective, which may lead to model misspecification.
+   - **High-dimensional data**: Thus, while using VAR models, there is a possibility of overfitting the data or getting less interpretable results, especially where there are many variables of interest.

In sum, despite the availability of numerous methods for VAR models to analyze the multivariate time series, the models have many constraints that one should consider while working on real-world data.

# **Question 13: Can you describe the concept of state space models for multivariate time series analysis?**

**Answer**: State space models are models that are commonly applied to the process of modeling time series data, specifically multivariate time series data. They consist of two main components: The observation equation and the state equation:

+   - **Observation equation**: Explores how the collected data are connected to the hidden processes, whereby