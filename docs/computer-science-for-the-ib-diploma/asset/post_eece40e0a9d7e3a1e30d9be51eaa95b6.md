
## REVIEW QUESTIONS

1. A marketing firm uses machine learning to analyse customer survey data to improve targeting strategies.
   a. Describe one common issue in survey data that would necessitate data cleaning.
   b. Describe how feature selection could impact the performance of a machine learning model in this scenario.
   c. Outline the role of dimensionality reduction in handling high-dimensional data such as survey responses.

2. A financial analytics firm uses machine learning to predict stock-market trends based on historical data.
   a. List one common data-quality issue that might require cleaning in this historical stock data.
   b. Describe the role of feature selection in improving model performance in financial predictions.
   c. Describe the importance of dimensionality reduction on model complexity and performance.

3. A school district analyses standardized test results to predict student performance and identify at-risk students.
   a. List one common data issue that might arise with standardized test-result data.
   b. Describe the possible implications if the school district was to import raw test data for all questions completed by students into the machine learning model.
   c. Outline two commonly used methods of feature selection that could be beneficial in this educational context.

## SYLLABUS CONTENT

By the end of this chapter, you should be able to:

- A4.3.1 Explain how linear regression is used to predict continuous outcomes
- A4.3.2 Explain how classification techniques in supervised learning are used to predict discrete categorical outcomes
- A4.3.3 Explain the role of hyperparameter tuning when evaluating supervised learning algorithms
- A4.3.4 Describe how clustering techniques in unsupervised learning are used to group data based on similarities in features
- A4.3.5 Describe how association rule learning techniques are used to uncover relations between different attributes in large data sets
- A4.3.6 Describe how an agent learns to make decisions by interacting with its environment in reinforcement learning
- A4.3.7 Describe the application of genetic algorithms in various real-world examples
- A4.3.8 Outline the structure and function of artificial neural networks (ANNs) and how multi-layer networks are used to model complex patterns in data sets
- A4.3.9 Describe how convolutional neural networks (CNNs) are designed to adaptively learn spatial hierarchies of features in images
- A4.3.10 Explain the importance of model selection and comparison in machine learning

## Key information

Before proceeding into this chapter, it is important to note that the syllabus content statements above are limited to “Explain”, “Describe” and “Outline”.

This chapter intentionally contains additional detail that is beyond the syllabus, such as programming code samples demonstrating the use of various algorithms. **You do not need to be able to read or write programming code for the different algorithms presented here in your IB examinations.**

The additional detail has been provided due to machine learning being an extremely popular subset of Computer Science. In discussions with students, many expressed a desire to learn beyond descriptive theory for these topics, and a wish to know how these algorithms work and how to use them. Students also commonly express an intention to experiment with machine learning algorithms within their internal assessments. For these reasons, this introduction is more in-depth than is required solely for the examinations.

## A4.3.1 Supervised learning: linear regression

Linear regression: a machine learning algorithm that seeks a linear line of best fit for a given data set, from which extrapolations can be made.

Linear regression refers to calculating the correlation and line (or plane) of best fit among the values of a data set, and then using the resulting *equation of the line* to make predictions for new, unseen data.

Linear regression is one of the earliest machine learning algorithms to be developed, and can even be calculated manually for limited data sets as they are purely mathematical constructs.

**Top tip!**

Always check the relationship between variables with scatter plots to see whether they are roughly linear. There is no point using linear regression if it doesn't fit the data.

Linear regression can be used to help answer such questions as:

- Given a person's height, is it possible to predict their weight?
- Given the number of hours a student studies for a test, is it possible to predict their result?
- Given the dollars spent on advertising a product, is it possible to predict the sales volume?
- Given the size of a home in square meters, is it possible to predict its sale price?

As you can hopefully infer from the name, linear regression is only suitable where there is a linear relationship between the independent and dependent variables.

The graph below illustrates a simple form of linear regression with one independent variable (the predictor) and one dependent variable (the response).

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_233_0.png)

Linear regression example

To explore the process involved for linear regression of one independent and one dependent variable, the equation for the line of best fit can be calculated using the least squares regression line, which will minimize the distance between the line and individual data points.

By assigning the independent variable to x, and the dependent to y, you can use the standard equation of a line to make predictions.

```
y = a + bx
```

The slope, or gradient, of the line, b, represents the amount that the prediction will change for every increment of one in the independent variable. To calculate b, you find the sum of the difference between each point of the line from the mean:

```
b = \frac{\Sigma(x - \bar{x})(y - \bar{y})}{\Sigma(x - \bar{x})^2}
```

The point of intercept, a, is the baseline value for the dependent variable when the independent variable is 0. To calculate a, take the coefficient multiplied by the mean of x and subtract it from the mean of y.

```
a = \bar{y} - b\bar{x}
```

As linear regression is such a common and popular task, both NumPy and scikit-learn libraries have tools built in to perform these calculations for you. The following example uses scikit-learn, as we will use the library a lot for other algorithms coming up.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
# Sample data
x = np.array([45,48,65,68,68,10,84,22,37,88,71,89,89,13,59,66,40,88,47,89])
y = np.array([98,92,134,135,136,30,175,54,70,182,148,169,187,20,126,142,90,186,99,176])
# Using scikit, calculate the model
# Convert the 1D array of 20 columns, to a 2D array of 20 rows 1 column each
x = x.reshape(-1, 1)
model = LinearRegression()
model.fit(x, y)

intercept = model.intercept_
slope = model.coef_[0]
# Using scikit, generate a prediction where the independent variable is 70
x_test = np.array([[70]]) # New single data point for prediction
y_test_predict = model.predict(x_test)
print("Prediction for independent variable value 70: {y_test_predict[0]}")
# Using matplotlib, plot the data and the line of best fit
x_line = np.array([[0], [100]])
y_line = np.array([[intercept], [intercept+100*slope]])
plt.scatter(x, y, color="blue")
plt.plot(x_line, y_line, color="red", linewidth=2)
plt.xlabel("Independent variable")
plt.ylabel("Dependent variable")
plt.title("Linear Regression example")
plt.show()
```

## See also

Reference the scikit-learn documentation for supervised linear regression by searching online for scikit-learn's “LinearRegression” (https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html).

R-squared value (or coefficient of determination): a statistical measure that indicates how well the linear regression model fits the data points given.

## Measuring accuracy

Assessing the accuracy of the model can be performed by calculating the R-squared value, also known as the coefficient of determination. It is a measure of the proportion of variation in values from the independent variable data, and what the model would have predicted for that point. A value close to 0 indicates the model does a poor job of explaining the relationship of the data, whereas a value close to 1 indicates the model does an excellent job of mapping the relationship of the data.

Why use a measure that relies on squaring? Why not just take the average of the absolute value of the difference between the predicted and actual values? There are a few reasons:

- Squaring means larger errors will become more pronounced than smaller errors. Absolute differences would treat all variations the same.
- Squaring results in a function that can be differentiated; a very handy benefit for optimization algorithms that rely on derivatives. Absolute values in a function cannot be differentiated.
- Squared differences are used within classical statistics with respect to assumptions around normalization, so it is convenient to stick with that approach.

There are approaches, other than R-squared value, that can be used, including:

- adjusted R-squared: modifies the formulae to account for the number of predictors in the model
- mean squared error: the average of the squares of the errors
- mean absolute error: the average of the absolute value of the errors
- mean absolute percentage error: the average of the absolute percentage errors of predictions.
