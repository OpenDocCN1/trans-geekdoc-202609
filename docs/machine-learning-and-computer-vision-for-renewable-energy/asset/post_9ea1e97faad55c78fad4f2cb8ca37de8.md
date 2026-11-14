
## Detecting Aberrations in Renewable Energy

Figure 2. Hourly thermal generation

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_212_0.png)

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_212_1.png)

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_212_2.png)

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_212_3.png)

electricity demand data is not distributed normally, as exhibited by the normal kernel density histogram. Moreover, the Normal Q-Q plots show minor deviations from normalcy. The time series display makes complex non-linear patterns in the data much more apparent.

Table 2 presents a detailed summary of the attributes of the dataset through descriptive statistics. The dataset's minimum value, 9.530611, represents the lowest observed value. 25% of the data is below the value of 9.860006 at the 25th percentile. The average, which denotes the dataset's average value, is determined to be 9.929916. At 0.106237, the standard deviation, which quantifies the range of values around the mean, is rather low. The midway value of the dataset is represented by the median, or 50th percentile, which is found at 9.935374. Turning now to the 75th percentile, 75% of the data is below the 10.007803 threshold. At 33065.91, the dataset's maximum value is noticeably high. Last but not least, the distribution's skewness, or asymmetry, is somewhat positively skewed at 0.36336, implying a tail that extends to higher values. When taken as a whole, these statistics offer insightful information about the distributional features and attributes of the dataset, facilitating comprehension of its shape, central tendency, and dispersion.

## Trend Analysis Results

The trend that was extracted from the hourly thermal production data using classical decomposition, a statistical method for finding fundamental recurring trends in a time series data set is depicted in Figure 3. This finding confirms that the trend that was seen over the chosen sample period is waning. This pattern of decline suggests a gradual decrease or reduction in the amount of heat generated over time. Decisions on thermal scheduling, allocation of resources, and infrastructure development can be influenced by these insights, which are crucial for grasping the long-term patterns and efficacy of thermal energy-producing systems (Smith and Johnson, 2020).

The Mann-Kendall test findings for the variable of electricity demand are displayed in Table 3. The power demand for the observed time appears to have had a substantial decrease trend, as indicated by the Mann-Kendall test statistic of -114.7675. Kendall's Tau coefficient of -0.3750, which shows a high negative connection between time and electricity usage, lends more evidence to this. The observed trend is statistically significant, as indicated by the Mann-Kendall test p-value of 0.001, which is less than the 0.05 traditional level of significance. Sen's slope estimator, which has a value of -0.0882, also offers an estimate of the rate at which electricity consumption changes over time. The results of the Mann-Kendall test are supported by this negative figure, which points to a declining trend in power demand. All things considered, these findings point to a notable decline in the demand for energy within the studied time frame.

We extract a nonlinear trend by fitting the cubic smoothing spline function with cubic smoothing spline constraints represented by the equation;

```
min_g p * \sum_{i=1}^{n} (y_i - g(x_i))^2 + (1 - p) * \int (g^{..}(x_i))^2 dx, p \in [0, 1]. (1.7)
```

Table 2. Descriptive statistics

| Min | 25% | Mean | sd | 50% | 75% | Max | Kurtosis | Skewness |
|---|---|---|---|---|---|---|---|---|
| 9.530611 | 9.860006 | 9.929916 | 0.106237 | 9.935374 | 10.007803 | 33065.91 | -0.02405 | 0.36336 |

## Detecting Aberrations in Renewable Energy

Figure 3. Trend for hourly thermal generation

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_214_0.png)

Table 3. Mann-Kendall test statistic and Sen's slope estimator

| Variable | M-K Test Statistic | Kendall's Tau τ | p-Value | Sen's Slope |
|---|---|---|---|---|
| Electricity demand | -114.7675 | -0.3750 | 0.001 | -0.0882 |

The nonlinear trend for the hourly thermal generation time series data shows irregular cycles instead of regular seasonality. The peaks are sometimes smaller or larger. Thus, modelling this time series data requires the inclusion of the lag features to allow our forecasters to react dynamically to the changing conditions. This study includes lag variables as explanatory variables to allow varying amounts of the recent history into the forecast.

## EXPERIMENTAL RESULTS AND ANALYSIS

In addition to hierarchies that we constructed as follows, the experiment makes use of residuals from a multiplicative classical decomposition as further features; (1) hourly, daily, weekly, monthly, quarterly, bi-annual, and yearly time series plots of these hierarchies appear in Figure 5. However, distinct kernels,

Figure 4. Depersonalized hourly thermal generation superimposed with a nonlinear trend variable from a regression spline

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_215_0.png)

as covered in the preceding section, are linear, polynomial, and RBF. A hyperparameter, which we have set at 0.15%, governs the trade-off between categorizing additional points as outliers and maintaining a smooth decision border. The model's performance with various kernels is displayed in Table 4.

Table 4 displays the classification accuracy of the One-Class SVM model using different kernel functions. The results show that the performance of the different kernels varies. For example, the model with the linear kernel identified 5495 outliers in the testing set, with a silhouette score of 0.5578 and an accuracy of 0.6119. When the model was used with the polynomial kernel, the number of outliers detected increased to 7784, with a slightly higher silhouette score of 0.6197 and an improved accuracy of 0.6491. The most noteworthy performance was seen with the RBF kernel, which recognized only 835 outliers, yielding a substantially greater silhouette score of 0.7805 and the highest accuracy of all kernels, at 0.8343. In contrast, 877 outliers were found using the sigmoid kernel, which had an accuracy of 0.8046 and a silhouette score of 0.6354. The RBF kernel performed better overall in outlier identification and classification accuracy, indicating that it can be used effectively for anomaly detection applications. This emphasizes how crucial it is to choose the right kernel function for One-Class SVM models to get the best outcomes.

Figure 6 displays the ability to differentiate between normal and abnormal data, and Figure 7 shows how outliers appeared at this boundary. These results underscore the effectiveness of the RBF kernel in anomaly identification and emphasize its potential to improve operational reliability and efficiency in renewable energy systems.

## Detecting Aberrations in Renewable Energy

Figure 5. Thermal generation hierarchies

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_216_0.png)

Table 4. Classification accuracy

| Kernel | Number of Outliers in the Testing Set | Silhouette score | Accuracy |
|---|---|---|---|
| Linear | 5495 | 0.5578 | 0.6119 |
| Polynomial | 7784 | 0.6197 | 0.6491 |
| RBF | 835 | 0.7805 | 0.8343 |
| sigmoid | 877 | 0.6354 | 0.8046 |

Figure 6. Thermal time series and detected anomalies using RBF kernel

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_217_0.png)

## FINDINGS AND CONCLUSIONS

We compiled the most important conclusions and revelations from the investigation on the identification of anomalies in renewable energy systems in the study’s final analysis. This study has explored the challenges of incorporating renewable energy sources into the current infrastructure, emphasizing the urgent requirement for proactive anomaly control techniques. Through the application of sophisticated statistical techniques, including the One-Class-SVM, we attempted to improve the dependability and operational efficiency of renewable energy systems. Our investigation of practical data and testing of several anomaly detection methods has allowed us to acquire a substantial understanding of the fluctuations in the production and use of renewable energy. These results highlight the significance of using creative strategies to deal with the difficulties presented by the integration of renewable energy.
