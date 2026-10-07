# Introduction to Multiple Regression 551

# 20.5 Using Software for Multiple Regression and Cross-Validation

Using software for multiple regression is similar to the bivariate regression approaches detailed in Section 17.6.6. Additional predictors are simply added to the Independent variable list in SPSS. In R, additional predictors are included in the regression equation in the lm function with a + between them; reg_out <- lm(data = dat, Y ~ X1 + X2); confidence intervals for the intercept and partial slope parameters can be obtained using the conf function in the {stats} package, which takes the output of regression as input: confint(reg_out).

Cross-validation involves several steps that can be done and quickly in R:

+   1. Identify a training set of data by randomly sampling a percentage of the cases and saving the sample case numbers. The sample function in [base] R a good tool to use. Having 126 cases and we want to sample 25% of them, train.index <- sample(seq(1:126), 32) will store a random sample of 32 integers from the set 1 to 126.
2. Assign those cases to a training set, test.set <- datcv(train.index), and complete the cases to a test set, test.set <- datcv(train.index).
3. Run the regression on all predictor variables, and see the results: model.cv <- lm(tc-, data = train.set). At this point, you can run step regression (Chapter 21) on these predictors using the step function in [stats], although that is not a necessary part of cross-validation. If you include this, be sure to store the results: model.cv <- step(model.cv, scope = lower(Y ~ 1), upper = lm(Y ~)), direction = "both"
The scope parameters specify the range of models under consideration, where Y ~ 1 indicates a model with an intercept, and Y ~ indicates a model with all predictors included.
4. Compute and store the Y values for the test cases (Section 19.3.3), using the model generated with the training cases: predictions.cv <- model$cv%predict(test.set).
5. Finally, compute R² for the predicted and observed values: cor(predictions.cv, test.set)$^2. Additional cross-validation methods in R are described by De Rooij and Weeda (2020).

In SPSS, cross-validation is not automated but it can be easily achieved by the following steps:

+   1. Select a random sample of cases using the Select Cases option from the Data pull-down menu, and then clicking the radio button for Random sample of case, choose a sample size.
2. Run the regression on the selected sample, which is the training set.
3. Use the Transform menu to compute a new variable, Y by typing in the Numeric Expression box the regression you obtained. Instead of clicking OK, click on the If... bar at the bottom of the Compute Variable window and select the radio button to Include if case satisfies condition, then type "filter_$=0" in the box (without the quote marks), then click Continue and OK. This will compute the predicted value of Y only for the cases that were not in the training set that was used to develop the equation.
4. Finally, select all cases and compute the square of the correlation between the observed and newly predicted values of Y; this will be R² for the test cases.