
# Backward elimination

Backward elimination begins with the predictors in your model, and the least significant variable is removed in each step.

The goal of this prediction technique is to maximize the power of prediction using the minimum number of predictor variables. It is one of the best ways of handling higher dimensionality in any data set.

A good application of this model is determination of factors which affect IQ (intelligence quotient) in human beings. IQ will be the dependent variable, while the independent variables for this problem can be height, weight and brain size.

With stepwise regression, you can create a model which works in such a way that the independent variable with the least (or no) contribution to the dependent variable (IQ) will be dropped.

1.  Ridge Regression

This regression technique is good for use with data which suffers from multicollinearity, that is, the independent variables are closely related.

Although least square estimates (OLS) in multicollinearity are not biased, they have large variances which normally deviate the observed value largely from true value. If a degree of bias is added to regression estimates, the standard errors will be reduced by ridge regression.

The equation for linear regression should be as follows:

y=a+ b\*x

To the above equation we must add an error term. Below is the complete equation:

y=a+b\*x+e (error term)

The error term is the value needed to correct the error between predicted and observed values. For the case of multiple independent variables, we should have the following:

y=a+y= a+ b1x1+ b2x2+....+e

The shrinkage parameter, lambda (λ) is used in ridge regression for the purpose of solving the multicollinearity problem.

1.  Lasso Regression

Lasso stands for Least Absolute Shrinkage and Selection Operator. It is also good in penalizing the absolute size of regression coefficients just like the ridge regression. It can also reduce the variability and improve the accuracy of the linear regression models.

However, unlike the ridge regression, lasso regression uses absolute values in penalty function rather than squares.

Values that cause some parameter estimates to be zero are penalized. If a larger penalty is applied, the estimates shrink towards absolute zero, and this leads to a variable selection out of the given n variables.

## Advantages of Regression Algorithms

The following are the advantages of regression analysis:

*   With regression algorithms, we can determine the relative variation in a series.

*   Helps us determine the relationship between two or more variables. From this, we can find unknown values for a variable from the known values.

*   It is a technique widely applicable to everyday life. We can use it to estimate trends such as death rate, tax rate, birth rate, yield rate etc.

## Disadvantages of Regression Algorithms

*   There is a necessary assumption that the relationship between variables will not change. In real life this may not always hold true, and any changes in the relationship will likely lead to erroneous predictions.

*   The calculation and analysis procedure for regression algorithms is lengthy and complex.

*   Regression algorithms cannot be used to estimate qualitative variables such as crime, honesty etc.

## When to use Regression Algorithms

Regression can also help you understand how various factors interact with one another.

Regression is a good technique which should be used when one needs to know the factors which matter most and the ones which should be ignored.

Regression algorithms are heavily applied by businesses and companies to predict future events or to determine what how they can increase sales and retain or recruit the highest quality employees.

Chapter 9  

KNN Algorithms 

KNN, which stands for K-Nearest Neighbors, is a simple algorithm that works well in practical situations.

The algorithm is non- parametric, meaning that no assumption is made regarding the underlying distribution of your data. The algorithm can be applied either to regression or to classification problems.

## How KNN Algorithm works

In KNN, complex data structures such as k-d trees can be used for data storage. This will help to make look-ups and matching for discovery of new patterns during predictions.

Once you have stored the whole of the data training set, you should consider how consistent your data is. Update it after getting new data, then make sure that any erroneous data is removed.

For KNN to make predictions, it directly uses the dataset. The predictions are made for some new instance (x) by means of a search through the whole training set for K similar instances (neighbors) and the output variable is summarized for the K instances.

For the case of regression, this will be the mean or median output variable, while for a classification problem, this will be the mode-class (or most common) variable.

In order to identify the K instances in a training dataset which are most similar to the new input, we use a distance measure.

For input variables which are real values, the common distance measure is the Euclidean distance. To calculate this distance, we have to find the square root of sum of squared differences between new point (X) and the existing point (Xi) across all the input variables j.

This can be expressed using the following formula:

EuclideanDistance(x, xi) = sqrt( sum( (xj – xij)^2 ) )

Other distances which can be used include the following:

Hamming distance - involves calculation of distance between the binary vectors.

Manhattan distance \- involves calculation of the distance between the real vectors by use of the sum of their absolute difference. It is also referred to as City Block Distance.

Minkowski distance - this is a generalization of the above two distances.

The kind of distance measure to use should be determined by your data. If you are not sure which is best for your data, you may need to experiment with the different measures and different values for K, and choose the one which gives you the most accurate model.

Euclidian distance should be used where the input variables are of similar type. For example, the measurement of heights and widths, are of similar type (meters).

The Manhattan distance should be used where the input variables are of different types. For example, age, height, gender.

The best way to select a value for K, is through experimentation. Try different values for K, and choose the one which gives you the best model. 

The KNN’s computational complexity normally increases with the size of the data set. If the training dataset is too large, you can make KNN stochastic by taking some sample from your training dataset from which you will calculate K most similar instances.

## Using KNN for Regression

If the KNN algorithm is used for a regression problem, the prediction will be based on the median or mean of K most similar instances.

## Using KNN for Classification

When KNN is used for a classification problem, the output may be calculated as the class which has the highest frequency from K-most similar instances.

Every instance will vote for its own class, and the class receiving the most votes will be taken for prediction.

Class probabilities can be calculated as normalized frequencies of occurrence (number of samples belonging to every class in a set of K similar instances for the new data).

The calculation for the case of a binary classification problem, for example, is:

p(class=0) = count(class=0) / (count(class=0)+count(class=1))

In case you are using K and the number of classes is even, avoid a tie by choosing an odd number for the value of K. If the number of classes takes an odd number, take an even number for the value of K.

For you to break ties, you can expand the K consistently by 1 then have a look at the class of next most similar instance in your training dataset.
