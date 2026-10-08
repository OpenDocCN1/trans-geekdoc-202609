# 7.2.4.1 Introduction to nested cross-validation

A method for evaluating a model's generalization performance is called nested cross-validation, also referred to as double cross-validation. When inner and outer cross-validation cycles are necessary to calculate a model's generalization error, this technique is used. The hyperparameters of a machine learning model are optimized using the results of a conventional *k*-fold cross-validation that is carried out in the inner loop of this method. The outer loop then runs a second *k*-fold cross-validation once the inner loop is finished to calculate the generalization error of the model using the optimized hyperparameters.

# 7.2.4.2 Utilizing nested cross-validation for hyperparameter tuning

For hyperparameter adjustment in machine learning, nested cross-validation is a strategy. Using different combinations of hyperparameter values for each iteration, a dataset is repeatedly separated into training and testing sets. The average of each iteration's results is used to determine the ideal set of hyperparameters, which is then chosen [13]. This approach works well because it lowers the likelihood of overfitting and guarantees that the model is resilient to unobserved data. It also offers a method that can be used universally to determine the ideal set of hyperparameters for every given dataset.

# 7.2.5 Time series cross-validation

When working with time series data, a cross-validation approach known as time series cross-validation is employed. The process is splitting the data into two or more separate, nonoverlapping subgroups, training a model on one of those subsets, and testing it on the other. The model can learn temporal information through this type of cross-validation, which also evaluates the model's capacity for generalization across time. It is especially helpful when working with lengthy time series, as creating more subsets for traditional cross-validation methods like *k*-fold cross-validation can take a lot of time [14]. Additionally, time series cross-validation can be used to assess the impact of using a different window size for training or testing, as well as the impact of using various training and testing datasets.

# 7.2.5.1 Handling time-dependent data using time series cross-validation

Time series cross-validation is a technique used to evaluate machine learning models on time-dependent data for further analysis. It works by dividing the time series into