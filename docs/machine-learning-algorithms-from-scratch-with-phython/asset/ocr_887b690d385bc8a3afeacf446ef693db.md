# # Chapter 7

# # Simple Linear Regression

Linear regression is a prediction method that is more than 200 years old. Simple linear regression is a great first machine learning algorithm to implement as it requires you to estimate properties from your training dataset, but is simple enough for beginners to understand. In this tutorial, you will discover how to implement the simple linear regression algorithm from scratch in Python.

After completing this tutorial you will know:

+   - How to estimate statistical quantities from training data.
+   - How to estimate linear regression coefficients from data.
+   - How to make predictions using linear regression for new data.

Let's get started.

# ## 7.1 Description

This section is divided into two parts: a description of the simple linear regression technique and a description of the dataset to which we will later apply it.

# ### 7.1.1 Simple Linear Regression

Linear regression assumes a linear or straight line relationship between the input variables (X) and the single output variable (y). More specifically, that output (y) can be calculated from a linear combination of the input variables (X). When there is a single input variable, the method is referred to as a simple linear regression.

In simple linear regression we can use statistics on the training data to estimate the coefficients required by the model to make predictions on new data. The line for a simple linear regression model can be written as:

```
y = b0 + b1 × x
(7.1)
```

Where b0 and b1 are the coefficients we must estimate from the training data. Once the coefficients are known, we can use this equation to estimate output values for y given new input