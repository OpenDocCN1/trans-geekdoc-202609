
## 12.5 Summary

In this tutorial, you discovered time series decomposition and how to decompose time series data with Python. Specifically, you learned:

- The structure of decomposing time series into level, trend, seasonality, and noise.
- How to automatically decompose a time series dataset with Python.
- How to decompose an additive or multiplicative model and plot the results.

### 12.5.1 Next

In the next lesson you will discover how to identify and model trends in time series data.

## Chapter 13

## Use and Remove Trends

Our time series dataset may contain a trend. A trend is a continued increase or decrease in the series over time. There can be benefit in identifying, modeling, and even removing trend information from your time series dataset. In this tutorial, you will discover how to model and remove trend information from time series data in Python. After completing this tutorial, you will know:

- The importance and types of trends that may exist in time series and how to identify them.
- How to use a simple differencing method to remove a trend.
- How to model a linear trend and remove it from a sales time series dataset.

Let’s get started.

### 13.1 Trends in Time Series

A trend is a long-term increase or decrease in the level of the time series.

> In general, a systematic change in a time series that does not appear to be periodic is known as a trend.
>
> — Page 5, *Introductory Time Series with R*.

Identifying and understanding trend information can aid in improving model performance; below are a few reasons:

- **Faster Modeling:** Perhaps the knowledge of a trend or lack of a trend can suggest methods and make model selection and evaluation more efficient.
- **Simpler Problem:** Perhaps we can correct or remove the trend to simplify modeling and improve model performance.
- **More Data:** Perhaps we can use trend information, directly or as a summary, to provide additional information to the model and improve model performance.

#### 13.1.1 Types of Trends

There are all kinds of trends. Two general classes that we may think about are:

- **Deterministic Trends**: These are trends that consistently increase or decrease.
- **Stochastic Trends**: These are trends that increase and decrease inconsistently.

In general, deterministic trends are easier to identify and remove, but the methods discussed in this tutorial can still be useful for stochastic trends. We can think about trends in terms of their scope of observations.

- **Global Trends**: These are trends that apply to the whole time series.
- **Local Trends**: These are trends that apply to parts or subsequences of a time series.

Generally, global trends are easier to identify and address.

#### 13.1.2 Identifying a Trend

You can plot time series data to see if a trend is obvious or not. The difficulty is that in practice, identifying a trend in a time series can be a subjective process. As such, extracting or removing it from the time series can be just as subjective. Create line plots of your data and inspect the plots for obvious trends. Add linear and nonlinear trend lines to your plots and see if a trend is obvious.

#### 13.1.3 Removing a Trend

A time series with a trend is called non-stationary. An identified trend can be modeled. Once modeled, it can be removed from the time series dataset. This is called detrending the time series. If a dataset does not have a trend or we successfully remove the trend, the dataset is said to be trend stationary.

#### 13.1.4 Using Time Series Trends in Machine Learning

From a machine learning perspective, a trend in your data represents two opportunities:

- **Remove Information**: To remove systematic information that distorts the relationship between input and output variables.
- **Add Information**: To add systematic information to improve the relationship between input and output variables.

Specifically, a trend can be removed from your time series data (and data in the future) as a data preparation and cleaning exercise. This is common when using statistical methods for time series forecasting, but does not always improve results when using machine learning models. Alternately, a trend can be added, either directly or as a summary, as a new input variable to the supervised learning problem to predict the output variable.

One or both approaches may be relevant for your time series forecasting problem and may be worth investigating. Next, let's take a look at a dataset that has a trend.

## 13.2 Shampoo Sales Dataset

In this lesson, we will use the Shampoo Sales dataset as an example. This dataset describes the monthly number of sales of shampoo over a 3 year period. You can learn more about the dataset in Appendix **A.1**. Place the dataset in your current working directory with the filename `shampoo-sales.csv`.

## 13.3 Detrend by Differencing

Perhaps the simplest method to detrend a time series is by differencing. Specifically, a new series is constructed where the value at the current time step is calculated as the difference between the original observation and the observation at the previous time step.

$$value(t) = observation(t) - observation(t - 1) \quad (13.1)$$

This has the effect of removing a trend from a time series dataset. We can create a new difference dataset in Python by implementing this directly. A new list of observations can be created. Below is an example that creates the difference detrended version of the Shampoo Sales dataset.

```python
# detrend a time series using differencing
from pandas import read_csv
from pandas import datetime
from matplotlib import pyplot

def parser(x):
    return datetime.strptime('190'+x, '%Y-%m')

series = read_csv('shampoo-sales.csv', header=0, index_col=0, parse_dates=True,
    squeeze=True, date_parser=parser)
X = series.values
diff = list()
for i in range(1, len(X)):
    value = X[i] - X[i - 1]
    diff.append(value)
pyplot.plot(diff)
pyplot.show()
```

**Listing 13.1:** Difference the Shampoo Sales dataset.

Running the example creates the new detrended dataset and then plots the time series. Because no difference value can be created for the first observation (there is nothing for it to be subtracted from), the new dataset contains one less record. We can see that indeed the trend does appear to have been removed (compared to original plot in the Appendix).

![](img/da419ed7447ef051ee9d00167b7274cf_127_0.png)

Figure 13.1: Line plots differenced Shampoo Sales dataset.

This approach works well for data with a linear trend. If the trend is quadratic (the change in the trend also increases or decreases), then a difference of the already-differenced dataset can be taken, a second level of differencing. This process can be further repeated if needed. Because differencing only requires the observation at the previous time step, it can easily be applied to unseen out-of-sample data to either pre-process or provide an additional input for supervised learning. Next, we will look at fitting a model to describe the trend.

## 13.4 Detrend by Model Fitting

A trend is often easily visualized as a line through the observations. Linear trends can be summarized by a linear model, and nonlinear trends may be best summarized using a polynomial or other curve-fitting method. Because of the subjective and domain-specific nature of identifying trends, this approach can help to identify whether a trend is present. Even fitting a linear model to a trend that is clearly super-linear or exponential can be helpful.

In addition to being used as a trend identification tool, these fit models can also be used to detrend a time series. For example, a linear model can be fit on the time index to predict the observation. This dataset would look as follows:

| x | y |
|---|---|
| 1 | obs1 |
