
## 6 Polynomial Regression — Overfitting/Tuning Explained

Thanks to `tidymodels` package, it is fairly easy to repeat the analysis for a Degree-10 Polynomial Model by only modifying the recipe. Instead of using `step_mutate()` to generate new predictor variables with various powers of Sqft, we now use `step_poly()` to generate 10 new variables for the different powers of Sqft:

```r
RecipeHousesPoly10=recipe(Price ~, data=DataTrain) |
  step_poly(Sqft, degree=10, options=list(raw=TRUE))
```

By default `options=list(raw=FALSE)` the command transforms the calculated polynomials to orthogonal polynomials, which allows for better interpretation of the regression parameters (βs). Since the *Polynomial Regression* model we use here is too complex to allow any interpretation of its parameters and orthogonal polynomials exceed the scope of this book, we will work with the original polynomials in what follows `options=list(raw=TRUE)`. The predictions are the same regardless of whether you use original or *orthogonal polynomials*.

If we graph the resulting prediction function of the *Degree-10 Polynomial Model* (magenta line in Figure 6.3), you can see the complete disaster of extreme overfitting.

The *Degree-10 Polynomial Model* represented by the magenta line estimates the 20 training observations (red dots) almost perfectly but totally fails to predict the testing data (small dots).

For example, the *Degree-10 Polynomial Model* predicts extremely high prices for houses with small square footage, predicts negative housing prices for houses with square footage in the ranges of 1,000 – 1,200 sqft and 2,700 – 3,700 sqft, and predicts extremely high prices for houses with 3,900 – 4,400 sqft.

From Figure 6.3, it is obvious to see why *overfitting* occurred. However, in almost all real-world cases we will not be able to generate a graph like Figure 6.3. Therefore, comparing performance between training and testing data is the only way to identify *overfitting*.

> ^4For more details about Orthogonal Polynomial Regression see Narula (1979).

![](img/f240d449191f5add983daf6c380e4fe3_161_0.png)

## Overfitting Summary

Overfitting occurs when a non-linear (flexible) model adjusts almost perfectly to a small number of training observations, but the adjustment is so specific that the model fails when predicting test data.

Overfitting is sometimes compared to human learning behavior, whereby somebody learns by heart rather than understanding the underlying theory.

If — after the completion of model development — a comparison of training and testing data reveals overfitting, the model development needs to start from scratch.

The new model development includes generating new sets of training and testing data (change of the value in set.seed()). Otherwise, we risk extending the overfitting from training to the testing data. 

## 6.5 Tuning the Complexity of a Polynomial Model

In the previous section, overfitting occurred in the Degree-5 Polynomial Model and to an extreme degree in the Degree-10 Polynomial Model. The linear model (blue line in Figures 6.2 and 6.3) seemed to be superior to the Degree-5 and Degree-10 Polynomial Model.

However, this does not mean a linear model is always the best choice. For example, when the underlying pattern that generated the data is non-linear, a linear regression model is sub-par to fit the non-linear pattern.

This raises the question:

How can we choose the right degree for a Polynomial Model?

### 6.5.1 Hyper-Parameters vs. Model Parameters

The appropriate degree for a Polynomial Model cannot be found with the Optimizer $\beta$-parameters (model parameters) because in order to run the Optimizer, we have to choose the model first — including the polynomial degree. Therefore parameters like the polynomial degree, that needs to be determined before the model calibration, are called hyper-parameters rather than model parameters.

![](img/f240d449191f5add983daf6c380e4fe3_162_0.png)

- 1. Hyper-parameters are parameters that change the design of a machine learning model or the data pre-processing in a recipe. For example, the hyper-parameter $k$ in a $k$-Nearest Neighbors model design or the degree of a Polynomial Model in a recipe.
- 2. Hyper-parameters often control the degree of non-linearity, and thus the flexibility of the prediction function. Therefore, we often face a trade-off between model flexibility and the risk of overfitting.
- 3. Hyper-parameters cannot be determined with an Optimizer based on training data. Therefore, we must utilize a trial-error process to find suitable hyper-parameters. This process is called hyper-parameter tuning.
- 4. We cannot utilize the testing data for hyper-parameter tuning because this can extend overfitting into the testing data!

Finding the best hyper-values is not specific to Polynomial Models only; we ran into this challenge in Chapter 4 when deciding on the parameter $k$ (the number of neighbors to consider) for k-Nearest Neighbors. Later, in Chapter 9, when covering Neural Network models, we have to decide how many neurons to consider when building a Neural Network. The number of neurons in a Neural Network is also considered a hyper-parameter. In fact, most machine learning models require finding best hyper-parameters at the model design stage. This process is called hyper-parameter tuning.

## 6.5 Tuning the Complexity of a Polynomial Model

### 6.5.2 Creating the Tuning Workflow

In order to evaluate the performance of several different degrees for the Polynomial Model, we have to decide which degrees we would like to try out. This is an arbitrary decision.

Nevertheless, the tidym package can provide some guidance. For most hyper-parameters a related command exists that returns a recommended hyper-value range. The name of the command is often the same as the name of the hyper-parameter. For example, you can use the command degree() to find a recommended range for the hyper-parameter degree:

```r
degree()
```

```
# Polynomial Degree (quantitative)
## Range: [1, 3]
```

The command returns a recommended range for the hyper-parameter degree from 1 – 3. We will extend this range and evaluate polynomial degrees from 1 – 10.

For purposes, the tidymodel package expects a data frame with the values for each hyper-parameter in the columns. The column names must be the same as the name of the respective hyper-parameter. Since we tune only one hyper-parameter in this case, the data frame ParGridHouses contains only one column named degree with values from 1 – 10.

```r
ParGridHouses=data.frame(degree=c(1:10))
print(ParGridHouses)
```

