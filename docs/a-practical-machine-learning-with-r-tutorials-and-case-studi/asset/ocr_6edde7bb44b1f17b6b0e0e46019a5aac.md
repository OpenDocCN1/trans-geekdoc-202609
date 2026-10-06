# Dummy Variables and One-Hot Encoding

A *dummy variable* is a dummy because it fills in for the presence of a category. For example, the 1 of the dummy variable *Waterfront_yes* indicates a numerical value that a waterfront is present and 0 that a waterfront is not present.

In the waterfront case, creating the dummy variable seems straightforward. However, in the case of red and white wines, one might create two dummy variables *WineColor_white* and *WineColor_red* with a value of 1 for white (0 otherwise) and red, respectively. Creating a variable for each of a categorical variable is called *one-hot encoding*.

One-hot encoding can be advantageous for some machine learning models (e.g., Random Forest) because it allows for a more straightforward interpretation of the variables. In OLS regressions one-hot encoding leads to a situation that it mathematically impossible to calculate the eta (dummy trap).

The dummy trap occurs when using one-hot encoding for OLS because one dummy variable is redundant. For example, in the case of red and white wines, when we have that *WineColor_white* = 1, follows that *WineColor_red* = 0 (an observation (wine) can be either or red). This redundancy is also reflected in an algebraic property: if we use the values for *WineColor_white*, we can calculate the values for *WineColor_red* = 1 - *WineColor_white*. If we can calculate one from one or more predictor variables, these are perfectly correlated. The absence of perfect correlation is one of the conditions to be fulfilled for OLS regression.

Consequently

The multivariate *model design* for the housing analysis does not differ from the univariate *model design* in Section 5.4.2. From the package *lm*, we use the model *linear_reg*() with mode "Regression".

Please substitute the ... in the code block below and execute the code. If everything is correct, *R* will print information about the *model design:*

```
ModelDesignHouses=linear_reg(|>
set_mode("...") |>
print(ModelDesignHouses)
```

Next, you will use a pipe to add the recipe and the *model design* to a workflow and fit the workflow model to the training data.

Please substitute the ... in the code block below and execute the code. If everything is correct, *R* will print information about the fitted workflow model. The printout includes the optimal values for the $eta: