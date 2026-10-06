# 6 Polynomial Regression — Overfitting/Tuning Explained

Thanks to `tidymodels` package, it is fairly easy to repeat the analysis for a Degree-10 Polynomial Model by only modifying the recipe. Instead of using `step_mutate()` to generate new predictor variables with various powers of Sqft, we now use `step_poly()` to generate 10 new variables for the different powers of Sqft:

```
RecipeHousesPoly10=recipe(Price-, data=DataTrain) |
  step_poly(Sqft, degree=10,
  options=list(raw=TRUE)
```

By default `options=list(raw=FALSE)` the command transforms the calculated polynomials to orthogonal polynomials, which allows for better interpretation of the regression parameters (s). Since the *Polynomial Regression* model we use here too complex to allow any interpretation of its parameters and orthogonal polynomials exceed the scope of this book, we will work with the original polynomials in what follows `options=list(raw=TRUE)`. The predictions are the same regardless of whether you use original or *orthogonal polynomials*.

If we graph the resulting prediction function of the *Degree-10 Polynomial Model* (magenta line in Figure 6.3), you can see the complete disaster of extreme overfitting.

The *Degree-10 Polynomial Model* represented by the magenta line estimates the 20 training observations (red dots) almost perfectly but totally fails to predict the testing data (small dots).

For example, the *Degree-10 Polynomial Model* predicts extremely high prices for houses with small square footage, predicts negative housing prices for houses with square footage in the ranges of 1,000 – 1,200 sqft and 2,700 – 3,700 sqft, and predicts extremely high prices for houses with 3,900 – 4,400 sqft.

From Figure 6.3, it is obvious to see why *overfitting* occurred. However, in almost all real-world cases we will not be able to generate a graph like Figure 6.3. Therefore, comparing performance between training and testing data is the only way to identify *overfitting*.

> ^4For more details about Orthogonal Polynomial Regression see Narula (1979).