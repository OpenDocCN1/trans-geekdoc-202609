# CHAPTER 7 GLOBAL MODEL-AGNOSTIC METHODS

+   2. For the selected dataset X, get the predictions of the black box model.
3. Select an interpretable model type (linear model, decision tree, ...).
4. Train the interpretable model on the dataset X and its predictions.
5. Congratulations! You now have a surrogate model.
6. Measure how the surrogate model replicates the predictions of the black box model.
7. Interpret the surrogate model.

You may find approaches for surrogate models that have some extra steps or differ a little, but the general idea is usually as described here.

One way to measure how the surrogate model replicates the black box model is the R-squared measure:

```
$R^2 = 1 - \frac{SSE}{SST} = 1 - \frac{\sum_{i=1}^{n}(\hat{y}^{(i)} - \tilde{y}^{(i)})^2}{\sum_{i=1}^{n}(y^{(i)} - \tilde{y}^{(i)})^2}$
```

$\hat{y}^{(i)}$ is the prediction for the $i$-th instance of the surrogate model, $\tilde{y}^{(i)}$ the prediction of the black box model and $\tilde{y}$ the mean of the black box predictions. SSE stands for sum of squares and SST for sum of squares. The R-squared can be interpreted as the percentage of variance that is captured by the surrogate model. If R is close to 1 (low SSE), then the interpretable model approximates the behavior of the black box model well. If the interpretable model is very close, you not want to replace the complex model with the interpretable model. If the R-squared is close to 0 (= high SSE), then the interpretable model fails to explain the black box model.

Note that we have not talked about the model performance of the underlying black box model, how good or bad it performs in predicting the actual outcome. The performance of the black box model does not play a role in training the surrogate model. The interpretation of the surrogate model is still valid because it makes statements about the model and not about the real world. But of course the interpretation of the surrogate model becomes irrelevant if the black box model is bad, because the black box model itself is irrelevant.

We could build a surrogate model based on a subset of the original data or reweight the instances. In this way, we change the distribution of the surrogate model's input, which changes the focus of the interpretation (then it is no longer really global). If we weight the data locally by a specific instance of data (the instances to the selected instance, higher their weight), we get a local surrogate model that can explain the individual prediction of the instance. Read more about local models in the following chapter.

# 7.6.2 Example

To demonstrate the surrogate models, we consider a regression and a classification example.

First, we train a support vector machine to predict the daily number of rented bikes given weather and calendar information. The support vector machine is not very interpretable, so