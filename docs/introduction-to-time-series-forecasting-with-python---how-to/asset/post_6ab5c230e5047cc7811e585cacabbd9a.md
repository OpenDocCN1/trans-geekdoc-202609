
## Part VI
### Projects

## Chapter 29
### Time Series Forecast Projects

A time series forecast process is a set of steps or a recipe that leads you from defining your problem through to the outcome of having a time series forecast model or set of predictions. In this lesson, you will discover time series forecast processes that you can use to guide you through your forecast project. After reading this lesson, you will know:

- The 5-Step forecasting task by Hyndman and Athanasopoulos to guide you from problem definition to using and evaluating your forecast model.
- The iterative forecast development process by Shmueli and Lichtendahl to guide you from defining your goal to implementing forecasts.
- Suggestions and tips for working through your own time series forecasting project.

Let’s get started.

### 29.1 5-Step Forecasting Task

The 5 basic steps in a forecasting task are summarized by Hyndman and Athanasopoulos in their book *Forecasting: principles and practice*.[^1] These steps are:

1. **Problem Definition.** The careful consideration of who requires the forecast and how the forecast will be used. This is described as the most difficult part of the process, most likely because it is entirely problem specific and subjective.
2. **Gathering Information.** The collection of historical data to analyze and model. This also includes getting access to domain experts and gathering information that can help to best interpret the historical information, and ultimately the forecasts that will be made.
3. **Preliminary Exploratory Analysis.** The use of simple tools, like graphing and summary statistics, to better understand the data. Review plots and summarize and note obvious temporal structures, like trends seasonality, anomalies like missing data, corruption, and outliers, and any other structures that may impact forecasting.
4. **Choosing and Fitting Models.** Evaluate two, three, or a suite of models of varying types on the problem. Models may be chosen for evaluation based on the assumptions they make and whether the dataset conforms. Models are configured and fit to the historical data.
5. **Using and Evaluating a Forecasting Model.** The model is used to make forecasts and the performance of those forecasts is evaluated and skill of the models estimated. This may involve back-testing with historical data or waiting for new observations to become available for comparison.

![Figure 29.1](img/da419ed7447ef051ee9d00167b7274cf_263_0.png)

**Figure 29.1:** 5-Step Forecasting Task.

This 5-step process provides a strong overview from starting off with an idea or problem statement and leading through to a model that can be used to make predictions. The focus of the process is on understanding the problem and fitting a good model.

Each model is itself an artificial construct that is based on a set of assumptions (explicit and implicit) and usually involves one or more parameters which must be “fitted” using the known historical data.

> — Page 22, *Forecasting: principles and practice*.

### 29.2 Iterative Forecast Development Process

The authors Shmueli and Lichtendahl in their book *Practical Time Series Forecasting with R: A Hands-On Guide*[^2] suggest an 8-step process. This process extends beyond the development of a model and making forecasts and involves iterative loops. Their process can be summarized as follows:

1. Define Goal.
2. Get Data.
3. Explore and Visualize Series.
4. Pre-Process Data.
5. Partition Series.
6. Apply Forecasting Method/s.
7. Evaluate and Compare Performance.
8. Implement Forecasts/Systems.

Below are the iterative loops within the process:

- *Explore and Visualize Series* ⇒ *Get Data*. Data exploration can lead to questions that require access to new data.
- *Evaluate and Compare Performance* ⇒ *Apply Forecasting Method/s*. The evaluation of models may raise questions or ideas for new methods or new method configurations to try.

![Figure 29.2](img/da419ed7447ef051ee9d00167b7274cf_265_0.png)

The process is more focused on the ongoing development and refinement of one or more models on the problem until an acceptable level of performance is achieved. This process can continue where models are revised and updated as new data and new insights are made available.

Of course, the process does not end once forecasts are generated, because forecasting is typically an ongoing goal. Hence, forecast accuracy is monitored and sometimes forecasting method is adapted or changed to accommodate changes in the goal or the data over time.

> — Page 16, Practical Time Series Forecasting with R: A Hands-On Guide.

### 29.3 Suggestions and Tips

This section lists 10 suggestions and tips to consider when working through your time series forecasting project. The thrust of these suggestions is centered on the premise that you cannot know what will work, let alone which methods will work well on your problem beforehand. And that the best source of knowledge on a forecasting project comes from the results of trial and error with real historical data.

- Select or devise a time series forecast process that is tailored to your project, tools, team, and level of expertise.
- Write down all assumptions and questions you have during analysis and forecasting work, then revisit them later and seek to answer them with small experiments on historical data.
- Review a large number of plots of your data at different time scales, zooms, and transforms of observations in an effort to help make exploitable structures present in the data obvious to you.
- Develop a robust test harness for evaluating models using a meaningful performance measure and a reliable test strategy, such as walk-forward validation (rolling forecast).
- Start with simple naive forecast models to provide a baseline of performance for more sophisticated methods to improve upon.
- Create a large number of perspectives or views on your time series data, including a suite of automated transforms, and evaluate each with one or a suite of models in order to help automatically discover non-intuitive representations and model combinations that result in good predictions for your problem.
- Try a suite of models of differing types on your problem, from simple to more advanced approaches.
- Try a suite of configurations for a given problem, including configurations that have worked well on other problems.
- Try automated hyperparameter optimization methods for models to flush out a suite of well-performing models as well as non-intuitive model configurations that you would not have tried manually.
- Devise automated tests of performance and skill for ongoing predictions to help to automatically determine if and when a model has become stale and requires review or retraining.

### 29.4 Summary

In this lesson, you discovered processes that you can use to work through time series forecasting problems. Specifically, you learned:

- The 5 steps of working through a time series forecast task by Hyndman and Athanasopoulos.
- The 8 step iterative process of defining a goal and implementing a forecast system by Shmueli and Lichtendahl.
- The 10 suggestions and practical tips to consider when working through your time series forecasting project.

#### 29.4.1 Next

In the next project you will develop models to forecast Monthly Armed Robberies in Boston.

## Chapter 30
### Project: Monthly Armed Robberies in Boston

Time series forecasting is a process, and the only way to get good forecasts is to practice this process. In this tutorial, you will discover how to forecast the number of monthly armed robberies in Boston with Python. Working through this tutorial will provide you with a framework for the steps and the tools for working through your own time series forecasting problems. After completing this tutorial, you will know:

- How to check your Python environment and carefully define a time series forecasting problem.
- How to create a test harness for evaluating models, develop a baseline forecast, and better understand your problem with the tools of time series analysis.
- How to develop an autoregressive integrated moving average model, save it to file, and later load it to make predictions for new time steps.

Let’s get started.

### 30.1 Overview

In this tutorial, we will work through a time series forecasting project from end-to-end, from downloading the dataset and defining the problem to training a final model and making predictions. This project is not exhaustive, but shows how you can get good results quickly by working through a time series forecasting problem systematically. The steps of this project that we will work through are as follows:

1. Problem Description.
2. Test Harness.
3. Persistence.
4. Data Analysis.
5. ARIMA Models.

[^1]: http://www.amazon.com/dp/0987507109?tag=inspiredalgor-20
[^2]: http://www.amazon.com/dp/0997847913?tag=inspiredalgo-r-20
