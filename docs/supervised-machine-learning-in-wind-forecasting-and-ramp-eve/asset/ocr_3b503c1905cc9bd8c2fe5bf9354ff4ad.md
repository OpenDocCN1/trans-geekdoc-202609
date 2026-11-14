# CHAPTER 3

# Paradigms in wind forecasting

With increasing human demands for electricity consumption, the supply side management has taken a pivotal role in regulatory markets. Fossil fuel-based power generation is facing stern competition from renewable energy sources. The penetration of wind power, specifically, has increased owing to pollution free power generation and flexibility with transmission. The balance between demand and supply of power is an important criterion for power system regulators.

For optimal power dispatch, the generation companies have a reserve capacity in case the power flow from main generation entity ceases. However, the reserve capacity of power has some limits in terms of size and dispatchability. Therefore forecasting the load ahead of time can ascertain the operator to plan the power dispatch optimally.

# 3.1 Introduction to time series

Forecasting a particular variable can depend upon temporal or spatial scale. Temporal variations with time reflect the stochasticity present in the variable. Spatial variations usually are dominant in climatology and meteorology. A temporal scale for a variable can be modeled in terms of time series. A time series is a successively ordered sequence of numerical data points and can be taken on any variable changing with time.

A time-series-based analysis helps the operator to identify the dynamic behavior of the variable in terms of relative dependence of each time-step with respect to another. Fundamentally, a time series S_t can be defined as a set of observations for a particular variable s_t at each time-step t. As an example of time series, Fig. 3.1 illustrates the opening stock price of Facebook, Inc., from January 3, 2018, to June 3, 2019. Each data point in this time series indicates a unique value of stock price.

Essentially, time series can be categorized into stationary and nonstationary time-series. The statistical nature of a stationary time series in terms of mean and variance does not change over time. Mathematically, a stationary time series S_t can be expressed as