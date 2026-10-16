
ICV valves. These techniques have shown promising results in finding the optimal ICV settings and improving the performance of oil and gas reservoirs. Overall, the literature review suggests that combining ICV data and machine learning techniques can be an effective approach for optimising production in oil and gas reservoirs. Machine learning algorithms can be used to model the relationship between ICV settings and production rates and to predict the optimal ICV settings for a given set of conditions. This can help to increase ultimate recovery, reduce capital and operating expenditures, and improve the performance of oil and gas reservoirs.

## 3. Methodology

In the context of ICV design, the process usually relies on the production capacity of individual laterals. Notwithstanding, some oil companies opt for a simplified approach by utilising the mean production rate of the field rather than individual lateral rates.

- 1. Data acquisition: For this research, data is to be acquired from the production technology team in the subsurface department. The data required from multiple wells are SPFM WI Rate, Annulus Pressure, Tubing Pressure, ICV dP, ICV position, Annulus Temperature for the separate reservoir zones (lower, middle and upper), MPFM Rate, THT (tubing head temperature), Annulus Pressure, THP (tubing head pressure), Tubing dP (differential pressure). Having some ICV mappings in the wells of interest is also essential. The data from the mapping helps gain insight and train the machine learning model on accurate data. The data were grouped per hour and within a two-year range.
- 2. Data preprocessing and preparation: Based on the collected data, preprocessing techniques are used to clean the data. Missing values and data variables were removed to prepare the data for further analysis. The total number of data used, based on the descriptive statistics after the removal of missing data, is 3,767 data points.
- 3. Exploratory data analysis: The most critical and time-consuming part of any machine learning project is the exploratory data analysis. It is the first direct encounter with the data towards understanding it. Initial data investigations were carried out to discover patterns in data, spot anomalies, and check assumptions with the help of summary statistics, heatmaps, and pair plot visualisation.
- 4. Explainable AI and feature selection: In this step, the various input features are inspected and checked for their importance. Based on the results from the data analysis, feature selection is to be performed using explainable AI techniques (model agnostic metrics). The approach is different from the standard methods that operate on correlation. Since correlation does not mean causation, the model agnostic metric is used to indicate the variables that have a causal effect on estimating zonal rates.
- 5. Machine Learning: Several advanced machine learning models were used to estimate the zonal rates for each reservoir from the data provided. A holdout cross-validation of 10% was applied to segregate the data into training (3,390), and test (377) sets. The performance of these models will be compared using several error metrics and visualisation techniques. The model with the least errors, high accuracy, and high probability of fit will be selected and deployed.

The aim is to assess when the empirical correlation goes out of sync and if the model performance deteriorates over time, assuming all conditions remain the same. A suitable machine learning model that can estimate zonal rates can be used to estimate the required injection volumes needed for specific zones. This model can help production technologists plan the optimum ICV positions and tubing head injected volumes required to sustain pressures in the relevant zones. This approach will also limit the need for strategic ICV mapping during pressure build up (PBU) and delays in bringing production up to the required optimal level before shut-in. A schematic of the workflow is illustrated in Fig. 6.1.

![](img/80b94770dd572ad559c67fa9921bb887_127_0.png)

Fig. 6.1. Detailed schematic workflow of the methodology.

### 3.1 A Brief Overview of Models Used in This Study

The summary analysis of the reviewed models used in estimating zonal rates in this study is summarised in Table 6.1.

Table 6.1. Summary of models used in this study.

| Base learner | Description | Developed or Implemented by Authors |
|---|---|---|
| Bootstrap aggregation (Bagging) | Bootstrap aggregation of trees is used to reduce the variance for algorithms that have high variance. | Breiman (1996) |
| Ridge Regression | Ridge regression is a robust technique against multicollinearity. The algorithm minimises standard errors by applying some bias to the model estimates, resulting in a more reliable prediction. The algorithm calculates the difference between the means of the standardised dependent and independent variables and dividing by their standard deviations. | Kuhn and Johnson (2013) |
| Least absolute shrinkage and selection operator (Lasso) Regression | Adds a penalty term to the regression equation that forces the sum of the absolute values of the regression coefficients to be less than a specific value. This has the effect of shrinking the coefficients of less important variables to zero, effectively removing them from the model. | Tibshirani (1996) |
| KNeighbors Regressor | It is based on the idea that data points with similar features tend to have similar output values. The KNN regressor predicts the output value for a new data point by looking at the K-nearest training data points and averaging their output values. The value of K determines the number of neighbours considered in the prediction, and the distance metric used to measure the similarity between data points can be chosen based on the problem at hand. | Silverman and Jones (1989) |
| Decision Tree | It uses induction and pruning techniques to build hierarchical decision boundaries and remove unnecessary structures from the decision tree to battle overfitting. | Gordon et al. (1984) |
| Extreme Gradient Boosting (XGBoost) | An implementation of gradient boosted decision trees of the first and second-order to maximise the loss function adding an extra regularisation term to adjust the final weights acquired to avoid overfitting. | Chen and Guestrin (2016) |
| Extremely Randomised Trees (Extra tree) | Potentially performs better than the random forest, although it uses a simpler algorithm to construct the decision trees used as ensemble members. | Geurts et al. (2006) |
| Random Forest | An advanced decision tree that is robust against overfitting and offers easy interpretability. | Breiman (2001) |

### 3.2 Criteria for Model Evaluation

Successfully training a model and achieving a good convergence does not signify the end of the model process. In model regression analysis, the model’s error is the difference between the actual data points and the best fit line produced by the algorithm. There is not a single statistic that can analyse all forms of data. The metrics are impacted by a number of components, including but not limited to the presence of outliers, the machine learning algorithm used, the ease with which derivatives can be discovered, and the prediction confidence. Therefore, the model errors were evaluated using the following standards to determine whether the models utilised in this research were appropriate;

- 1. *Mean Absolute Error (MAE)*: The MAE is a well-established evaluation metric used to quantify the accuracy of predictive models. It is defined as the L1 loss, representing the sum of absolute differences between the predicted output and the target variable. By measuring the average magnitude of errors without taking into account the direction of errors, the MAE provides a reliable measure of model performance. Additionally, this metric is particularly sensitive to relative errors, making it a useful tool for assessing performance in applications where errors of all sizes are equally important. The MAE is also robust against global scaling of the predicted output and the presence of outliers, making it a versatile metric for evaluating model performance in various settings. Mathematically, the MAE is written as;
  
  $$MAE = \frac{\sum_{i=1}^{n} |y_i - \hat{y}_i|}{n}$$ 
  (6.1)
  
- 2. *Root Mean Squared Error (RMSE)*: This performance evaluation metric is popular because it is interpretable as the standard deviation of the model’s prediction errors and specifies the closeness of predicted data to actual data. This function is written as follows;
  
  $$RMSE = \sqrt{\frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{n}}$$
  (6.2)
  
- 3. *Akaike Information Criterion (AIC)*: This evaluation standard was developed using a frequentist probability framework that assigns a model a score based on its maximum likelihood estimation. This technique assesses models’ quality and accuracy, resulting in a better model fit of the data. This criterion is expressed as;
  
  $$AIC = 2K - 2(log - likelihood)$$
  (6.3)

In order to assess the accuracy of prediction models based on the number of input features, various evaluation metrics are employed. However, except for R², a lower value for the performance evaluation criteria indicates better model performance. If a conclusion cannot be drawn based on these
