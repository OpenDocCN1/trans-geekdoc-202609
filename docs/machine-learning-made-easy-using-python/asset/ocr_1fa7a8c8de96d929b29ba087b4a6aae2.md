# 200 PERFORMANCE & METRICS

We calculated the Maximum Error(Maximum residual error), MAE(Mean absolute error i.e. average vertical distance between each point and the regression line), MSE(mean of the squared distance from each point to the regression line) and R2 (Explained variation / Total variation) using the max_error(), mean_absolute_error(), mean_squared_error() and r2_score() functions and printed them respectively. The lesser the Max Error, MAE and MSE is the better performance of the model. Where R2 is a percentage more closer to 1.0 is better. But a constant model like ours's always predicts the expected value of y, disregarding the input features, would get a R2 score closer to 0.0

# Improving the model

Upon calculating the metrics of an algorithm we can perform the following steps to improve the performance of our models:

+   - Make sure to train the model with adequate data. The dataset shouldn’t have abnormal distribution of features or labels like 5 samples of Yes and 95 samples of No
- After loading data we should always practice the best and suitable preprocessing methods on our data to improve it’s quality like encoding labels
- We shouldn’t save much data for testing but don’t too lo. For datasets with samples over 10k, 20% or less is adequate
- In cases of very less data you can create random values for testing instead of splitting the scarce data
- You can always test different algorithms to solve a problem, compare them with their metrics and choose the best and improve it

![](bbox=[0.635, 0.611, 0.813, 0.755])