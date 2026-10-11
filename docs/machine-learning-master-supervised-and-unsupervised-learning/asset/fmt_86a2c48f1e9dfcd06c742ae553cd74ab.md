
# Terminologies used in Regression

Following are the terminologies used in regression:

## Dependent Variable

**Dependent variable** is also known as target, output variable, or response. The dependent variable in regression analysis is a variable which we want to predict or understand. It is denoted by `Y`.

Size of house, number of bedrooms, and number of bathrooms are dependent variables (refer to Table).

## Independent Variable

**Independent variable** is also known as the input variable. Independent variables affect the dependent variables, or these are used to predict the values of the dependent variables. It is denoted by `X`.

Price of a house is an independent variable (refer to Table).

## Outliers

**Outliers** are observed data points that are far from the least square line or that differ significantly from other data or observations. In other words, an outlier is an extreme value that differs greatly from other values in a set of values.

In Figure there are a bunch of apples, but one apple is different. This apple is what we call an outlier.

![Figure 2.3: Outlier](image-brlu9h8t.jpg)

Outliers need to be examined closely. Sometimes, for some reason or another, they should not be included in data analysis. It is possible that an outlier is a result of erroneous data. Other times, an outlier may hold valuable information about the population under study and should remain included in the data. The key is to examine carefully what causes a data point to be an outlier.

![Figure 2.4: Outlier in House Price Dataset](image-2pat3cms.jpg)

Consider the following example. Suppose as shown in Figure we sample the number of bedrooms in a house and note the price of each house. We can see from the dataset that ten houses range between 200000 and 875000; but one house is priced at 3000000, that house will be considered as an outlier.

## Multicollinearity

**Multicollinearity** in regression analysis occurs when two or more independent variables are closely related to each other, so as not to provide unique or independent data to the regression model. If the degree of correlation is high enough between variables, it can cause problems when fitting and interpreting the regression model.

For example, suppose we do a regression analysis using variable height, shoe size, and hours spent in practice in a day to predict high jumps for basketball players. In this case, the height and size of the shoes may be closely related to each other because taller people tend to have larger shoe sizes. This means that multicollinearity may be a problem in this regression.

Take another example, suppose we have two inputs `X1` or `X2`:

```
X1 = [0, 3, 4, 9, 6, 2]
X2 = [0, -1.5, -2, -4.5, -3, -1]
X1 = -2 * X2
```

So `X1` & `X2` are collinear. Here it's better to use only one variable, either `X1` or `X2` for the input.

## Underfitting and Overfitting

**Overfitting** and **underfitting** are two primary issues that happen in machine learning and decrease the performance of the machine learning model.

The main goal of each machine learning model is to provide a suitable output by adapting the given set of unknown inputs; this is known as **generalization**. It means after providing training on the dataset, it can produce reliable and accurate output. Hence, underfitting and overfitting are the two terms that need to be checked for the reliability of the machine learning model.

Let us understand the basic terminology for overfitting and underfitting:

- **Signal**: It is about the true base pattern of the data.
- **Noise**: Unnecessary and insignificant data that reduces the performance.
- **Bias**: It is the difference between expected and real values.
- **Variance**: When model performs well on the training dataset but not on the test dataset, variance exists.

![Figure 2.5: Underfitting and Overfitting](image-kcscldgm.jpg)

On the left side of the above Figure anyone easily predicts that the line does not cover all the points shown in the graph. Such a model tends to cause a phenomenon known as **underfitting** of data. In the case of underfitting, the model cannot learn enough from the training data and thus reduces precision and accuracy. There is a high bias and low variance in the underfitted model.

Contrarily, when we consider the right side of the graph in Figure it shows that the predicted line covers all the points in the graph. In such a situation, we might think this is a good graph that covers all the points, but that is not true. The predicted line of the given graph covers all the points including those which are noise and outliers. Such a model tends to cause a phenomenon known as **overfitting** of data. This model is responsible for predicting poor results due to its high complexity. The overfitted model has low bias and high variance. So, this model is also known as the **High Variance** model.

Now, consider the middle graph in Figure it shows a well-predicted line. It covers a major portion of the points in the graph while also maintaining the balance between bias and variance. Such a model tends to cause a phenomenon known as **appropriate fitting**.

# Types of Linear Regression

As shown in Figure linear regression is classified into two categories based on the number of independent variables:

![Figure 2.6: Types of Linear Regression](image-g0jwi1j2.jpg)

## Simple Linear Regression

**Simple Linear Regression** is a type of linear regression where we have only one independent variable to predict the dependent variable. The dependent variable must be a continuous/real value.

The relationship between independent variable (`X`) & dependent variable (`Y`) is shown by a linear or a sloped straight line as shown in Figure hence it is called Simple Linear Regression:

![Figure 2.7: Simple Linear Regression](image-ooj26ng0.jpg)

The Simple Linear Regression model can be represented using the following equation:

```
y = B0 + B1 * X
```

Where:

- `Y`: Dependent Variable
- `X`: Independent variable
- `B0` is the Y-intercept of the regression line where best-fitted line intercepts with the Y-axis.
- `B1` is the slope of the regression line, which tells whether the line is increasing or decreasing.

Therefore, in this graph, the dots are our data and based on this data we will train our model to predict the results. The black line is the best-fitted line for the given data. The best-fitted line is a straight line that best represents the data on a scatter plot. The best-fitted line may pass through all of the points, some of the points or none of the points in the graph.

The goals of simple linear regression are as follows:

- To find out if there is a correlation between dependent & independent variables.
- To find the best-fit line for the dataset. The best-fit line is the one for which total prediction error (all data points) are as small as possible.
- How the dependent variable is changing by changing the independent variable.

Suppose we have a dataset, which contains information about the relationship between `Size` of house and `Price` as shown in Table.

Table 2.2: House Dataset

Here `Size` is the independent variable (`X`) and `Price` is the dependent variable (`Y`). Our aim is to find out the value of `B0` & `B1` such that it produces the best-fitted regression line. This linear equation is then used for new data.

The House dataset is used to train our linear regression model. That is, if we give `Size` as an input, our model should predict `Price` with minimum error.

Here `Y'` is the predicted value of `Y`.

The values `B0` and `B1` must be chosen so that they minimize the error. If the sum of squared error is taken as a metric to evaluate the model, then the goal to obtain a line that best reduces the error is achieved.

![Figure](image-t8txhfdo.jpg)

If we do not square the error, then positive and negative points will cancel out each other.

## Multiple Linear Regression

If there is more than one independent variable for the prediction of a dependent variable, then this type of linear regression is known as **Multiple Linear Regression**.
