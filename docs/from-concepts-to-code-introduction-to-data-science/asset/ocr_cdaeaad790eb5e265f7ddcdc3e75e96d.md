![](bbox=[0.278, 0.145, 0.722, 0.403])

mean zero. There should not be patterns in the data. The presence of a
trend line or curve would be problematic, as this would suggest one or more
missing predictors. The residual plot here is problematic, as the residuals do
not cluster around the zero line, and there is a negatively sloping set of points.
The sloping points are a result of the target maximum value of five.
At this stage, an analyst may spend a fair bit of time doing the mentioned
error analysis. Creating, filtering and sorting the data in
different ways will provide insights. Defects in the data may be discovered and
fixed, such as with incorrect predictor or target values. When updates need to
be made to the data, it is best to make the changes in code and save the adjusted
to separate files. This will make the changes transparent and repeatable,
nit will be possible to undo the changes if necessary. For further model
improvement, there may be additional predictors that can be engineered and
included. It may also be possible to collect more data, and focus should be
given where the model is weak.

# ### 13.3.6 Comparing Models

It will be important to try different models and compare their performance.
Graphical methods and metrics are valuable for making these comparisons.
Since we have used all of the provided predictors in building the model, let's
build a second model that includes a subset of the predictors. We will select the
predictor subset and then repeat the earlier steps. This code snippet selects
the first three predictors from the training data:

```
x_train_subset = x_train[:3]
```