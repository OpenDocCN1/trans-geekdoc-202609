
![](img/d2107fc60629942e7da5355e47fcc33d_180_0.png)

Figure 10.3 Linear regression forecasting.

## 10.3.2 Ridge Regression

The model-tuning technique called as ridge regression can be used to evaluate any data that displays multi-collinearity. This method performs L2 regularization. When the issue of multi-collinearity emerges, least-squares are unbiased, and fluctuations are considerable, predicted values diverge significantly from actual values (Figure 10.4).

In ridge regression, the means of the variables—both dependent and independent—are subtracted, and their standard deviations are divided. Since we need a means to indicate whether the variables in a particular formula are standardised or not, this is a challenge for notation. In terms of standardisation, all ridge regression calculations are based on standardised variables. Before being shown, the computed regression coefficients are scaled back to their initial value [8].

![](img/d2107fc60629942e7da5355e47fcc33d_180_1.png)

Figure 10.4 Ridge regression balancing of data.

## 10.3.3 Decision Tree

Decision trees are used by artificial intelligence to draw conclusions based on the data available from prior judgments. These conclusions are also given values and utilised to predict the expected future course of action.

Decision trees are quantitative, algorithmic models for ML that assess and discover answers to a range of problems and possible outcomes. Decision trees are therefore aware of the rules for making decisions in particular settings based on the information at hand. The learning process is ongoing and feedback-based. As a result, learning outcomes get better over time (Figure 10.5).

### 10.3.3.1 Prediction of Continuous Variables

Continuous variables can be predicted using one or more predictors. A continuous variable decision tree is the name of the decision tree model that is employed to represent such values. Different types of continuous decision trees address regression-type issues. In these circumstances a continuous, variable, and numerical output is predicted using labelled datasets.

![](img/d2107fc60629942e7da5355e47fcc33d_181_0.png)

Figure 10.5 Decision tree structure.

### 10.3.3.2 Prediction of Categorical Variables

Additional categorical variables may also be used to predict categorical variables. However, this topic is about categorizing a new dataset into the existing classes of datasets rather than forecasting a value. Categorical variable decision trees address classification-type issues in which a class rather than a value is the output.

## 10.3.4 Random Forest Regressor

After numerous classifications, decision tree algorithms have now been trained to different datasets, a random forest learning method is made use of, which uses averaging to increase projected accuracy and reduce overfitting.

The outcome is dependent on multiple decision trees instead of just one because each one was precisely trained using that specific sample of data, so there is less volatility when we mix them all at once.

In a classification problem, the solution is determined by the simple majority classifier. In a regression problem, the overall output is the mean of each result. This is described as an aggregation.

Using several decision trees and a process called Bootstrap and Aggregation, sometimes known as bagging, Random Forest is an aggregation technique that can perform both classification and regression tasks.

![](img/d2107fc60629942e7da5355e47fcc33d_182_0.png)

Figure 10.6 Random forest regressor structure.

The key idea behind this strategy is to integrate several decision trees in order to get the desired result rather than depending solely on one decision tree (Figure 10.6).

## 10.3.5 Gradient Boosting Regression

“Boosting” is an ML approach for combining several simple models into a single merged model. Boosting is also described as an additive model since it adds a single basic model while keeping the structure of the model’s existing trees.

Boosting is also described as an additive model since it adds a single basic model while preserving the structure of the model’s existing trees. The final, complete model improves as we merge even more simple models, making it a better predictor. Since the process employs gradient descent to minimize the loss, the term “gradient” in “gradient boosting” refers to this technique [9].

Gradient Boosting Regression finds the difference between the present forecast and the known exact target value. This variation is referred to as residual. After that, a poor model maps the features to that residual and is further trained.

This procedure moves the model closer to the desired outcome by adding the residual forecasted by a weak model to the input of the current model. This process can be repeated numerous times to enhance

![](img/d2107fc60629942e7da5355e47fcc33d_183_0.png)

Figure 10.7 Gradient boosting model.

the overall model forecast. Gradient Boosting is utilized for regression when it is used to predict a continuous value. This differs from applying linear regression. Figure 10.7 shows the working of a generic gradient boosting model, where it moves the model closer to the desired outcome by combining multiple trees.

Gradient Boosting Classification is used to predict classes, such as if a patient has a specific disease, whereas Gradient Boosting Regression is used to forecast continuous variables, such as house price.

### 10.3.5.1 Advantages of Gradient Boosting

- Better accuracy: On average, Gradient Boosting Regression offers more accuracy.
- Less pre-processing: Gradient Boosting Regression involves the least amount of data preparation, allowing us to implement this model more quickly and with less complexity.
- Missing data: One of the problems when training a model is missing data. The missing data is handled by Gradient Boosting Regression on its own; handling it manually is not required.

## 10.4 Model Performance

How much the regression line fits the data set is determined by the goodness of fit. Optimization is the process of selecting the best model from a group of competing models.

### 10.4.1 R-Squared Method

A statistical technique that assesses the goodness of fit is R-squared.

On a scale of 0-100 percent, it evaluates the strength of the correlation between the dependent and independent variables.

A good model is one in which the R-square value is high since it indicates that there is little variation between the predicted and actual values.

It is called coefficient of determination or a coefficient of multiple determination for a multiple regression task.

### 10.4.2 Mean Squared Error (MSE)

The mean squared error tells us how much a regression line fits a set of data points. It is a function that gives the relationship with the anticipated value of the squared error loss. The term “mean square error” refers to the average (or the mean) of mistakes squared from the data relating to the function [10].

A smaller MSE suggests a close clustering of data points around the centre instant (mean), whereas a larger MSE shows the opposite. A smaller MSE is preferred since it demonstrates how the data points are evenly spaced around its central moment (mean). It shows how the values are primarily distributed, are not skewed, and most importantly, have less errors.

### 10.4.3 Root Mean Square Error (RMSE)

RMSE, referred to as root mean square deviation, is a technique used to evaluate the correctness of forecasts. It showcases the Euclidean separation between forecasts and observed true values.

To calculate the root-mean-square error, calculate the residual (difference between prediction and truth) for each data point together with its norm, mean, and square root (RMSE).

When evaluating a model's performance in ML, whether during training, cross-validation, or tracking after deployment, it is very helpful to have a single number. The root mean square error is one of the most widely used metrics for this. It is a suitable scoring system that is easy to understand and coherent with a number of the common statistical hypotheses. RMSE values between 0.2 and 0.5 show that the model can relatively predict the data accurately [11–13].

## 10.5 Conclusion

All categorical data is to be encoded using label encoding, having order set as alphabetical order. This data was then imported into a data frame using the pandas library and empty rows were dropped using the dropna function of the data frame. The data was then trained using five models: Linear Regression, Ridge Regression, Decision Trees, Random Forest Regressor and Gradient Boosting Regressor.

The Decision Tree, Random Forest Regressor and the Gradient Boosting Regressor were found to be the most optimal training models having the highest R Square Value among all the models. The Root Mean Squared Error values for these models were between 0.2 and 0.5, meaning they were accurately predicting the target values. This meant that these models were the best fit for the given data and optimal for using for a forecast model.
