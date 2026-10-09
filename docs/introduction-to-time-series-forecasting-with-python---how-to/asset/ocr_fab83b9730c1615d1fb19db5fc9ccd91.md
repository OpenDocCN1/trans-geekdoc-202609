# Chapter 29

# Time Series Forecast Projects

A time series forecast process is a set of steps or a recipe that leads you from defining your problem through to the outcome of having a time series forecast model or set of predictions. In this lesson, you will discover time series forecast processes that you can use to guide you through your forecast project. After reading this lesson, you will know:

+   - The 5-Step forecasting task by Hyndman and Athanasopoulos to guide you from problem definition to using and evaluating your forecast model.
- The iterative forecast development process by Shmueli and Lichtendahl to guide you from defining your goal to implementing forecasts.
- Suggestions and tips for working through your own time series forecasting project.

Let’s get started.

# 29.1 5-Step Forecasting Task

The 5 basic steps in a forecasting task are summarized by Hyndman and Athanasopoulos in their book *Forecasting: principles and practice*<sup>1</sup>. These steps are:

+   1. **Problem Definition.** The careful consideration of who requires the forecast and how the forecast will be used. This is described as the most difficult part of the process, most likely because it is entirely problem specific and subjective.
2. **Gathering Information.** The collection of historical data to analyze and model. This also includes getting access to domain experts and gathering information that can help to best interpret the historical information, and ultimately the forecasts that will be made.
3. **Preliminary Exploratory Analysis.** The use of simple tools, like graphing and summary statistics, to better understand the data. Review plots and summarize and note obvious temporal structures, like trends seasonality, anomalies like missing data, corruption, and outliers, and any other structures that may impact forecasting.

<sup>1</sup>http://www.amazon.com/dp/0987507109?tag=inspiredalgor-20