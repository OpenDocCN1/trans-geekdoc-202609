
# 8 Logistic Regression — Handling Imbalanced Data

204
different data, we could also end up with a regression line that predicts negative probabilities, which also does not make sense.

If we are willing to give up the linearity requirement, the problems mentioned above can be avoided. We could use a non-linear prediction line as shown in Figure 8.2 (the magenta curve). A non-linear prediction line can bend for greater income values downwards and thus avoiding exceeding 1. For small income values, the prediction line can bend upwards and thus falling below 0. When incomes exceed 250, the curve approaches 1, for very small incomes but never falls below 0.

![](img/f240d449191f5add983daf6c380e4fe3_220_0.png)

# 8.2 Comparing Linear and Logistic Function

Since the magenta curve looks like a step of a staircase, first horizontal, then (almost) vertical, and finally horizontal again, these types of curves are often called step functions. The scientific term is Sigmoid functions. Examples include⁴

- The Logistic function⁶
- The Hyperbolic Tangent function
- The Arc Tangent function

> ⁴A mitigation could be to define all probabilities greater than 100% as 100% and negative probabilities as 0%. However, this would lead to a kinked prediction line and is also not a good solution for other reasons.

> ⁵See Wikipedia contributors (2023d).

> ⁶Confusingly the Logistic function is sometimes also called the Sigmoid function.

# 8.3 The Idea Behind Logistic Regression

You can probably guess from the name, the Logistic function is used for Logistic Regression.

The equation below shows the prediction equation for a Logistic Regression with one predictor variable $x_i$ (income in our example) and $P^{rob}$ the probability for an event occurring (e.g., yacht ownership: 'yes'):-

```
$P^{rob} = \frac{1}{1+e^{(\beta_1+\beta_2x_i)}}$ (8.2)
```

In Equation (8.2), the parameter $\beta_2$ shifts the related curve horizontally, and the parameter $\beta_1$ determines the steepness of the step in the step-function graph. An Optimizer can be used to calibrate $\beta_1$ and $\beta_2$ to ensure the best prediction quality for the training data.

Note that Logistic Regression does not use the mean squared error (MSE) for the error function. Instead, an error on a function called Logistic Loss is used. For now, remember that Logistic Regression does not minimize the MSE and uses a different function instead.

In Figure 8.2, the magenta curve shows the Logistic prediction function with optimized $\beta$. When you apply the technique outlined above to create a decision boundary (magenta dashed decision boundary) you can see that every income greater than 110 (right of the magenta dashed decision boundary) is predicted as yacht ownership 'yes', and any income smaller than 110 (left of the magenta dashed decision boundary) is predicted as yacht ownership 'no'.

The position of the decision boundary for the Logistic Regression is slightly different from that for the linear regression — 110 vs. 158. However, the predictions are the same, and the yacht ownership of all friends is predicted correctly, except for Jack.

A big drawback of linear regression is that it is not well suited for classifying to outliers. This can be demonstrated with an example:

The 11th friend, Nina, arrives late (her Porsche had a flat tire). That is the reason that her data was initially considered. Nina's yearly income is $2.5 million, and she owns a yacht. This is what we would expect from our previous estimate. Therefore, adding the observation for Nina should keep the predictions approximately the same.

As you will see, Nina's high income combined with her yacht ownership (as expected) keep the predictions from the Logistic Regression very much the same. However, Nina's exceptionally high income (outlier) combined with her yacht ownership will change the predictions from the linear regression so much that they become useless.

To demonstrate this, let us add Nina's observation to the training data and

![](img/f240d449191f5add983daf6c380e4fe3_222_0.png)

### FIGURE 8.3 The Impact of an Outlier on Linear and Logistic Prediction Functions

see what happens. Given Nina's income ($2.5 million) and the fact that she owns a yacht (Yacht = 1), we get a new observation with an x-axis value of 2,500 to the right and a y-value of 1 because Nina owns a yacht. Adding the observation for Nina to the training data changes both the logistic and the linear prediction function (see Figure 8.2).

- The new curve for the *Logistic-Regression* (magenta) shifts a little to the right when adding the observation for Nina but the shift is minimal. The decision boundary is now at 122 instead of 110. Therefore, the predictions from the *Logistic-Regression*'s decision boundary have mostly stayed the same: Six of our friends with income greater than 1 are predicted correctly as yacht owners, including Nina's prediction. Five friends with an income of less than 122 are predicted as not owning a yacht, which is correct for four of our friends but not for Jack (the outlier).

- The new regression line — to better approximate the new data point is much flatter than the original (see the blue solid line). Consequently, the decision boundary for the linear regression is now at an income of negative 83 (blue dashed line). This changes the predictions of the new linear prediction function dramatically compared to when the observation for Nina (the outlier) was not considered. All 11 observations are predicted as yacht owners because all 11 observations have an income greater than negative

# 8.3 The Idea Behind Logistic Regression 207

83. This overly simplistic prediction leaves four outliers with wrong predictions (compared to one with the Logistic Regression).

Linear regression is unsuitable for predicting categorical variables, because it is sensitive to outliers.

The question remains is:

# What is the advantage of the Logistic function compared to Sigmoid (step) functions?

To answer this question, we must distinguish between odds and probabilities. You probably have heard about odds already in connection with sports betting.

# Probabilities vs. Odds

Both probabilities and odds measure the chance of a success (e.g., getting heads in a coin flip or rolling with a die). A probability measures the ratio between the expected number of successes occurring in relation to the total number of possible. For example, the probability of a head (success) in a coin flip is $\frac{1}{2}=\#Successes$, because we expect heads when we flip the coin twice. The probability of rolling a six with a die is $\frac{1}{6}=\#Successes$.

```
$P^{prob} = \frac{\#Successes}{\#Successes + #NoSuccesses} (8.3)
```

In contrast, odds measure the ratio between the number of successes occurring in relation to the number of no-successes occurring. One could also say odds are the number of events with "something happening" in relation to the number of events with "nothing happening".

For example, the odds in a coin flip for heads are $\frac{\#Successes}{\#NoSuccesses}=1$. The odds for rolling a six with a die are $\frac{\#Successes}{\#NoSuccesses}$. We would say that the odds for heads are 1 to 1, often expressed as 1:1 and that the odds of rolling a six with a die are 1 to 5. You can calculate odds as:

```
$Odds^{odds} = \frac{\#Successes}{\#NoSuccesses} (8.4)
```

To derive how to convert probabilities to odds, we start with dividing numerator and denominator in (8.4) by $\#Successes$;

```
$P^{prob} = \frac{\#Successes}{\#Successes + #NoSuccesses} (8.3)
```

In contrast, odds measure the ratio between the number of successes occurring in relation to the number of no-successes occurring. One could also say odds are the number of events with "something happening" in relation to the number of events with "nothing happening".

For example, the odds in a coin flip for heads are $\frac{\#Successes}{\#NoSuccesses}=1$. The odds for rolling a six with a die are $\frac{\#Successes}{\#NoSuccesses}$. We would say that the odds for heads are 1 to 1, often expressed as 1:1 and that the odds of rolling a six with a die are 1 to 5. You can calculate odds as:

```
$Odds^{odds} = \frac{\#Successes}{\#NoSuccesses} (8.4)
```

To derive how to convert probabilities to odds, we start with dividing numerator and denominator in (8.4) by $\#Successes$;

```
$P^{prob} = \frac{\#Successes}{\#Successes + #NoSuccesses} (8.3)
```

To derive how to convert probabilities to odds, we start with dividing numerator and denominator in (8.4) by $\#Successes$;

```
$P^{prob} = \frac{\#Successes}{\#Successes + #NoSuccesses} (8.3)
```

# 8 Logistic Regression — Handling Imbalanced Data

224
Now that you know odds, we can show you what makes the Logistic function so. We start with the Logistic function from (8.2):

```
$p_{rob,yes,i} = \frac{1}{1+e^{(\beta_1+\beta_2x_i)}}$
```

and take the reciprocal on both sides:

```
$\frac{1}{p_{rob,yes,i}} = 1 + e^{-(\beta_1+\beta_2)}$
```

Then we subtract 1 from both sides:

```
$\frac{1}{p_{rob,yes,i}} - 1 = e^{-(\beta_1+\beta_2)}$
```

When we consider that $-1 = \frac{p_{rob,yes,i}}$ and substitute $-1$ accordingly, we get (after simplification):

```
$\frac{1 - p_{rob,yes,i}}{p_{rob,yes,i}} = e^{-(\beta_1+\beta_2)}$
```

According to Equation (8.6) in the yellow box above, $\frac{p_{rob,yes,i}}{1 - p_{rob,yes,i}} = O^{odds}_{yes,i}$. If we substitute accordingly, we get:

```
$O^{odds}_{yes,i} = e^{\beta_1 x_i + \beta_2}$ (8.7)
```

Equation (8.7) is the prediction equation for *odds* rather than *probabilities* in (8.2).

But there is another benefit from all the transformations. We can show this when we take the logarithm on both sides of Equation (8.8), resulting in Equation (8.8):

```
$ln(O^{odds}_{yes,(n_i)}) = \beta_1 x_i + \beta_2$ (8.8)
```

The right-hand side of Equation (8.8) now shows a typical linear regression equation with one predictor variable. This allows us to interpret the coefficients, in our case $\beta_1$, in a familiar way: We can say if $x$ increases by one unit, the log odds on the left-hand side of Equation (8.8) increase by $\beta_1$ units.
