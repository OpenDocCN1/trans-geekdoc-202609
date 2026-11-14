
predictions to give a better output. In this chapter, we use the recurrent neural network, long short-term memory, and convolutional neural network models as the base learners. See Figure 4. The stacking-ensemble approach to time series forecasting is when heterogeneous base models are trained and tested on the dataset in parallel or stacking. The assumption is that prediction from the base models is weak.

In the following section, we will specify which learning algorithms have been used in the scheme we propose. We can define a stacking ensemble scheme more formally in the following way. Given a set of N different learning algorithms Lk, k=1,...,N, and the pair (x,y), with x=(x1,...,xw) representing the w recorded values and y=(xw+1,...,xw+h) the h values to predict. Let mt_kp, k=1,...,N, j=1,...,h be the model induced by the learning algorithm Lk on x to predict xw+jp and let fj be the generalizer function responsible for combining the models for predicting such value. It is worth noting that fj can be a generic function, such as the average, or a model induced by a learning algorithm. Then, the estimated x^w+w+j value is given by the expression

$\hat{x}_{w+j} = f_j(m_{1j}, \cdots, m_{nj})$. (10)

Ensemble methods have been successfully applied to solving pattern classification, regression, and forecasting in time series problems (Jin and Dong, 2016). Adhikari (2015), for instance, presented a linear combination method for time series forecasting that uses a unique neural network topology to compute the combining weights. Bagnall et al. (2015) proposed a method using an ensemble of classifiers on different data transformations to improve the accuracy of time-series classification. The authors demonstrated that the simple combination of all classifiers in one ensemble obtained better performance than any of its components. To classify biomedical data, Jin and Dong (2016) developed an ensemble approach based on deep neural networks that incorporates filtering views, local views, distorted views, explicit and implicit training, sub-view prediction, and Simple Average. In particular, they used the Chinese Cardiovascular Disease cardiograms database.

In stacking, the algorithm takes the outputs of the base models as input and attempts to learn the best way of combining the heterogeneous predictions to give a better output. Predictions from these base models are combined using either the Linear Quantile regression Averaging (LQRA) or the Weighted Averaging methods. However, this chapter proposed a generalized additive model. A comparison of the performance of these models is done using the Key Performance Indicators KPIs. The KPIs are discussed at the end of this section. The meta-model combines predictions from these base models using either the stacking-ensemble approach. A comparison of the performance of these models is done using the Key Performance Indicators KPIs.

## Selection of Error Metrics for Assessment

The selection of appropriate error metrics is crucial for evaluating the performance of forecasting models. Error metrics provide a quantitative measure of the accuracy of predictions and help assess how well the model is capturing the underlying patterns in the data. Here are some error metrics that are relevant to this topic:

**Mean Squared Error (MSE):** MSE is a fundamental and extensively employed error metric in the realm of predictive modeling. It serves as a robust measure to quantify the overall quality of predictions by assessing the magnitude of the discrepancies between predicted values and actual observations. At

## A Deep Learning Framework for Modeling Temporal Dependencies

its core, the MSE operates by calculating the average of the squared differences between the predicted values and the corresponding actual values. This squaring of differences magnifies larger errors, accentuating the impact of deviations between predictions and actual outcomes. By summing up these squared errors and dividing by the number of observations, the MSE provides a comprehensive perspective on the model's accuracy. Mathematically, the Mean Squared Error is given by

```
MSE = \frac{1}{n} \sum_{i=1}^{n} \left( y_i - \hat{y}_i \right)^2 . \quad \text{(11)}
```

In model (5), \( n \) is the number of observations while \( y_i \) represents the actual observed value at time \( t \) and \( \hat{y}_i \) represents the predicted value at time \( t \).

**Mean Absolute Error (MAE)**: MAE measures the average absolute difference between predicted and actual values. It is less sensitive to outliers compared to MSE and provides a more balanced view of prediction accuracy (Willmott and Matsuura, 2005). This test stands as a fundamental error metric that gauges the average absolute disparity between predicted values and actual observations. In contrast to Mean Squared Error (MSE), MAE's distinctive characteristic lies in its robustness against outliers and its ability to present a well-balanced evaluation of prediction accuracy. The equation of MAE is

```
MAE = \frac{1}{n} \sum_{i=1}^{n} \left| y_i - \hat{y}_i \right| \quad \text{(12)}
```

**Symmetric Mean Absolute Percentage Error (SMAPE)**: SMAPE presents itself as an insightful error metric that builds upon the foundation of percentage-based evaluation while incorporating a symmetrical consideration of both overestimation and underestimation errors. This symmetry empowers SMAPE to offer a balanced and comprehensive appraisal of prediction accuracy. (Makridakis and Hibon, 2000). In mathematical form, this error metric is expressed as

```
SMAPE = \frac{100}{n} \sum_{i=1}^{n} \frac{\left| y_i - \hat{y}_i \right|}{\left( \left| y_i \right| + \left| \hat{y}_i \right| \right) / 2} \quad \text{(13)}
```

SMAPE's symmetric nature ensures that no bias is introduced towards either overestimation or underestimation. This balanced assessment makes SMAPE an ideal choice when the objective is to comprehend prediction accuracy without favoring one direction of error over the other. It particularly suits scenarios where both overestimation and underestimation have equal consequences, such as demand forecasting or resource allocation.

**Mean Forecast Error (MFE)**: MFE is the average difference between predicted and actual values. It provides a measure of the average error without considering the direction of errors (Tashman, 2000). Furthermore, MFE plays a pivotal role in assessing the performance of forecasting models. It quantifies the average difference between predicted values and their corresponding actual observations, shedding light on the average error magnitude, regardless of the direction of errors.

Unlike other error metrics that consider the direction of errors, such as overestimation or underestimation, MFE focuses solely on the magnitude of deviations. This characteristic makes MFE a direction-agnostic measure that offers insights into the general accuracy of predictions without discerning the tendencies of errors. The MFE statistic is expressed as

```
MFE = \frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)
```

The interpretability of MFE is straightforward. A lower MFE value indicates that, on average, the predictions are closer to the actual values. Conversely, a higher MFE value implies a greater average discrepancy between predictions and observations. MFE is a valuable metric when the primary concern is to grasp the typical error magnitude without delving into the nuances of directional errors.

## APPLICATION TO HOURLY ELECTRICITY DEMAND LOAD

The data used in this chapter is the hourly electricity demand load (Dispatchable Generation) by ESKOM for the period of 2019-04-01 to 2023-10-22. This makes a total of 39960 observations¹. The data is split into two sets: training and testing sets. The stacking-ensemble algorithm coupled with Gumbel copulas is developed from the base learner models namely recurrent neural network (RNN), convolutional neural network (CNN) and long short-term memory (LSTM). Figure 5 presents a univariate data analysis for the variable of interest: the hourly electricity demand for South Africa. The normal histogram with kernel density (a nonparametric method used for estimating probability distributions), normal Q-Q, and box and whisker plot and time series are presented in this Figure.

The normal kernel density with a histogram plot shows that the hourly electricity demand data is not normally distributed. Normal Q-Q plots also show slight deviations from normality. Time series plot further show complex non-linear patterns.

## Trend Analysis Results

Prior main analysis, the data underwent classical decomposition, and Figure 6 illustrates the resulting trend from decomposed hourly electricity demand data. The visual inspection of Figure 6 demonstrates that the extracted trend is decreasing for the sample period. Moreover, Mann-Kendall test statistic and Sen's slope estimator are used to analyze the long-term trends of hourly electricity demand load in South Africa. The Mann-Kendall test statistic and Sen's slope in Table 2 present these results. The outcome of the Mann-Kendall test results revealed that hourly electricity demand load has a significant monotonic decreasing long-term trends because it is negative. The Sen's slope value shows significant decreasing magnitudes of trends, which are corresponding with the Mann-Kendall test results.

We extract a nonlinear trend by fitting the cubic smoothing spline function with cubic smoothing spline constraints represented by the equation

```
min_g p * \sum_{i=1}^n (y_i - g(x_i))^2 + (1-p) * \int (g''(x_i))^2 dx, p \in [0,1]
```
