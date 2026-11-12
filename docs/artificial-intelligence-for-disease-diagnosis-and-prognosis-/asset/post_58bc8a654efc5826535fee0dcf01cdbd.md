
three different types of nodes in a decision tree. The top of the tree is called the root node or root. Arrows are positioned pointing from them. The nodes in the middle are called internal nodes. Arrows pointing to and from them. The last nodes that provide the classified results are called leaf nodes or leaves. Arrows will be pointing to them.

When there are many stacked nodes, each node separates the data in the best possible way depending on different parameters. This can be determined in many different ways among which the “Gini impurity” approach is considered the best.

![](img/bffdb4a72252285ac92f0fad78a7f104_30_0.png)

## Figure 2.5 Decision trees.

Let us assume we can find out if a person is healthy based on gender and bone density. First, we need to ask if the person is male or female. Then we want to ask if the lean mass is greater than 92% for males and greater than 79% for females. The decision tree is figured in Figure 2.5. From this, we can determine whether a person is healthy or not.

- Regression Analysis: Regression analysis is an estimation process that is formed using a set of statistical methods. In general, there is a dependent variable that is to be estimated and there are one or more independent variables that will determine the output of the dependent variable. It is very effective for modeling the future relationship between those variables and predicting the future outcome of any event.

The first step for training a dataset using regression analysis is to plot the data points on a chart. This gives an idea of the dataset and helps figure out if there is any actual relationship between the dependent and independent data. The dependent variable is plotted on the Y-axis and the independent variable is plotted on the X-axis. After plotting the data, the correlation between the variables is figured out. Then a line is drawn to define the relationship between the dependent and independent variables. This line is called the regression line. Based on the type of regression analysis it can be a linear function or a polynomial function. Moreover, if the number of dependent variables increases, then the dimension of the data pool also increases making the function more complex. There are three types of regression analysis–linear regression, multiple linear regression, and nonlinear regression.

In linear regression, there is only one independent function. There is a linear relationship between the slope and the intercept due to dependent and independent variables. The independent value is not random. The value of residual error is zero, constant across all observations, not correlated among observations, and follows the normal distribution. If we formulate simple linear regression, the equation will be

$Y = a + bX + \epsilon$

where:

- Y : Dependent variable
- X : Independent (explanatory) variable
- a : Intercept
- b : Slope
- ε : Residual (error)

![](img/bffdb4a72252285ac92f0fad78a7f104_31_0.png)

## Figure 2.6 Simple linear regression analysis.

Multiple linear regression analysis is a lot like the simple linear model. The only crucial difference is that there are multiple independent variables used in the model. If we formulate multiple linear regression, the equation will be

$Y = a + bX_1 + cX_2 + \cdots + dX_n + \epsilon$

where:

- Y : Dependent variable
- X1, X2, ..., Xn : Independent (explanatory) variable
- a : Intercept
- b, c, d : Slopes
- ε : Residual (error)

![](img/bffdb4a72252285ac92f0fad78a7f104_32_0.png)

## Figure 2.7 Multiple linear regression

In nonlinear regression, the dependent variable is correlated with the independent variables using nonlinear functions. Nonlinear functions like logarithm, exponential, polynomial, etc., are used to define the relationship between the variables.

Suppose, we want to find the number of people who will be affected by COVID in the upcoming days based on the places that are in lockdown, the number of people properly using hand sanitizer, and the number of people properly wearing a mask. In this case, we took three dependent variables and the independent variable is the number of people that could get infected in the upcoming week or month. Now, based on the previous data we can create a multiple linear regression model and find the value of the people that could get infected. This will help us to maintain the medical supplies according to the need so that the hospitals don't get overwhelmed or saturated.

- *Random Forest (RF)*: Random forest is a popular ML technique that is considered a stepped-up version of decision trees. It is used to solve both regression and classification problems. The ensemble learning technique is used as the base of the random forest algorithm. Ensemble learning is a technique that is used to solve a complex problem by combining many classifiers.

Many decision trees make up a random forest algorithm. Bagging, also known as bootstrap aggregating, is an ensemble meta-algorithm that is used to train the “forest” generated by the random forest algorithm. Bagging reduces the variance within a noisy dataset that increases the accuracy of ML algorithms.

The main building block of the random forest algorithm is decision trees. The random forest provides the output based on different predictions made by each decision tree. The mean or average output from all the decision trees is taken into consideration to predict the outcome of the entire model. The more the number of trees, the more the accuracy of the random forest algorithm. Figure 2.8 shows an illustration of Random Forest.

![](img/bffdb4a72252285ac92f0fad78a7f104_33_0.png)

## Figure 2.8 Random forest.

Random forest is good at handling missing values as it can accomplish this automatically. It uses a rule approach instead of a distance-based approach which does not require scaling of the features. Moreover, it is very efficient at handling nonlinear parameters. It can also handle outliers pretty well and is less affected by noise which makes it a lot more stable. But, making a random forest is complex and the training time is very long.

COVID-19 is a relatively new disease in the medical field. So, detection of COVID-19 is not easy, and unreliable using one ML method as the dataset is not yet that vast. In this case, we can use a few types of ML algorithms for each decision tree. Then we can combine them using a random forest algorithm. This will provide the final output which will be more accurate compared to other individual methods.

- Naïve Bayes: The Naïve Bayes algorithm is based on the probability theory, Bayes theorem. To find the probability of an event occurring given the probability of another event that has already occurred is the main purpose of Bayes theorem. We can state Bayes theorem as:

```
Posterior = prior x likelihood / evidence
```

We can state that mathematically as the following equation:

```
P(a|x) = P(x|a)P(c)/P(a)
```

$P(a|X) = P(x_1|a)P(x_2|a)\cdots P(x_n|a)P(a)$

where:

- $P(c|x)$ is the posterior probability of class (c, target) given predictor (x, attributes)
- $P(x|c)$ is the likelihood which is the probability of predictor given class
- $P(c)$ is the prior probability of class
- $P(x)$ is the prior probability of predictor

Naïve Bayes is not a single algorithm. This is a group of algorithms that are basically based on Bayes theorem. It is assumed that all the predictors are independent. That means the presence of one certain feature in a class does not have any impact on another one.

Naïve Bayes is a lot faster than other algorithms and saves a lot of time. Solving a multi-class prediction problem is a highly suitable use case for Naïve Bayes. If the features are actually independent of each other, they can actually outperform other models and less training data is required. But there may be cases where the features are not independent of each other and one feature relies on another feature. In such cases, Naïve Bayes may underperform compared to other models. It works better on categorical input variables rather than numerical input variables. If the probability of an event can become zero anytime, which means the instance of the event is not present in the training dataset. In such cases, the accuracy of the outcome may suffer. Moreover, probability-based outputs should not be taken seriously.

In the medical field, Naïve Bayes can be used to find the probability of a disease occurring in a person. Depending on the different attributes and data of a person, we can assume the probability of whether a person will contract the disease or not.

- Artificial Neural Network (ANN): The concept of ANNs took birth from the thought of how biological neural networks work. Here, the term biological neural network refers to the human brain. In a human brain, the smallest unit or cells are called neurons. They are interconnected to one another assembling the entire structure of the brain. Similarly, an ANN has neurons that are interconnected in several layers. These neurons work together as one unit according to our need to classify data into various classes.

Let us compare biological neural networks and ANN. Figures 2.9 and 2.10 show both biological neural networks and ANN. The dendrites in a biological neural network are comparable to the inputs of the ANN. The cell nucleus works as the nodes, synapses are equivalent to the weights, and the axons work as output.

A single node of an ANN works by taking the individual inputs from the previous layer and multiplying it with some weight values and summing them up. Sometimes a bias value is also added to the summation. Then the value is
