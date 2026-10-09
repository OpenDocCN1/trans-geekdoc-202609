# # Chapter 20

# # Reframe Time Series Forecasting Problems

You do not have to model your time series forecast problem as-is. There are many ways to reframe your forecast problem that can both simplify the prediction problem and potentially expose more or different information to be modeled. A reframing can ultimately result in better and/or more robust forecasts. In this tutorial, you will discover how to reframe your time series forecast problem with Python. After completing this tutorial, you will know:

+   - How to reframe your time series forecast problem as an alternate regression problem.
- How to reframe your time series forecast problem as a classification prediction problem.
- How to reframe your time series forecast problem with an alternate time horizon.

Let's get started.

# ## 20.1 Benefits of Reframing Your Problem

Reframing your problem is the idea of exploring alternate perspectives on what is to be predicted. There are two potential benefits to exploring alternate framings of your time series forecast problem:

+   1. Simplify your problem.
2. Provide the basis for an ensemble forecast.

Both benefits ultimately have the result of leading to more skillful and/or more robust forecasts.

# ### 20.1.1 Simplify Your Problem

Perhaps the largest wins on a forecasting project can come from a reframing of the problem. This is because the structure and type of prediction problem has so much more impact than the choice of data transforms, choice of model, or the choice of model hyperparameters. It is the biggest lever in a project and must be carefully considered.