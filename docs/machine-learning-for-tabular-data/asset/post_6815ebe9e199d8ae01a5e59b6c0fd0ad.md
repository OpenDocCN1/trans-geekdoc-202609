
# Ensembling the two solutions to the Tokyo Airbnb problem

## Scatterplot of Errors with Smoothed Trend Line and Diagonal Line

![](img/def89cc476fa39f4c54bd34e78d91674_477_0.png)

**Figure 12.2** Scatterplot of errors for XGBoost and fastai

## 12.5 Ensembling the two solutions to the Tokyo Airbnb problem

Now that we have established the performance of the XGBoost and fastai solutions to the Tokyo Airbnb problem in isolation, we will look at ensembling the two solutions to see whether a combination of the two approaches provides any improvements.

The following listing shows the loop where we ensemble the results of the two models.

Listing 12.4 Code to ensemble the two models

```
blend_list = [
  [1., 0.], [0., 1.], [0.25,0.75],
  [0.75,0.25], [.5, .5]
]
for a, b in blend_list:
  print(f"XGBoost weight={a}, DNN weight={b}")
  blended_oof_preds = (
    xgb_preds * a + dnn_oof_preds * b
)
r2 = r2_score(blended_oof_preds, y)
rmse = np.sqrt(mean_squared_error(blended_oof_preds, y))
mae = mean_absolute_error(blended_oof_preds, y)
```

# CHAPTER 12 Blending gradient boosting and deep learning

```python
print(f'blended result for R-squared: {r2:.3f}')
print(f'blended result for RMSE: {rmse:.3f}')
print(f'blended result for MAE: {mae:.3f}')
```

The code combines results for XGBoost and fastai according to the blending values in blend_list. Note that these blending values are not optimized to find the optimum—we are simply using a set of fixed values to get a general sense of the effect of blending. Also, note that we are evaluating the results using out-of-fold predictions. Nevertheless, by combining the predictions from XGBoost and fastai according to the proportions specified by blend_list, we can see the effect of ensembling the two approaches across a range of values.

The output of the blending code for a typical run is:

```
XGBoost weight=1.0, DNN weight=0.0
blended result for R-squared: 0.599
blended result for RMSE: 10783.027
blended result for MAE: 6531.102

XGBoost weight=0.75, DNN weight=0.25
blended result for R-squared: 0.619
blended result for RMSE: 10570.904
blended result for MAE: 6366.257

XGBoost weight=0.5, DNN weight=0.5
blended result for R-squared: 0.625
blended result for RMSE: 10527.024
blended result for MAE: 6384.576

XGBoost weight=0.25, DNN weight=0.75
blended result for R-squared: 0.618
blended result for RMSE: 10338.831
blended result for MAE: 6566.663

XGBoost weight=0.0, DNN weight=1.0
blended result for R-squared: 0.599
blended result for RMSE: 11419.374
blended result for MAE: 6959.540
```

These figures may be a bit hard to interpret, so let's see what they look like in the form of a chart. Figure 12.3 shows the results for R-squared, RMSE, and MAE for a range of blending between XGBoost and fastai. As 12.3 shows, we get the optimal results for R-squared when we use a 50/50 blend of the predictions from XGBoost and fastai. For measures like RMSE and MAE, we obtain a better result weighting XGBoost than fastai; however, if we use a 50/50 blend, we would obtain only worse scores. The worst results are when we use 100% prediction from fastai, as we would expect from the results we got from each model in isolation, but it is interesting to notice that using only XGBoost is always worse than blending with the other solution using 75/25 or 50/50.

## Overall comparison of gradient boosting and deep learning

![](img/def89cc476fa39f4c54bd34e78d91674_479_0.png)

**Figure 12.3** Results of blending XGBoost and fastai models

Ensembling the XGBoost and fastai models gets better results than using either model in isolation. As we will see in the next section, our observations from ensembling are consistent with results comparing machine learning approaches and deep learning on tabular data.

## 12.6 Overall comparison of gradient boosting and deep learning

In chapter 1, we introduced the controversy over whether deep learning is needed to solve problems involving tabular data. We cited academic papers that support both sides of the argument—those that advocate for deep learning approaches and those that maintain classical machine learning approaches, in particular gradient boosting, consistently outperform deep learning. One of the papers that we mentioned in chapter 1 is worth revisiting here: "Tabular Data: Deep Learning Is Not All You Need," by David Shwartz-Ziv and Amit Armon (https://arxiv.org/abs/2106.03253). In the Discussion and Conclusions of this paper, the authors make the following statement:

> In our analysis, the deep models were weaker on datasets that did not appear in their original papers, and they were weaker than XGBoost, the baseline model. Therefore we proposed using an ensemble of these deep models with XGBoost. This ensemble performed better on these datasets than any individual model.

Their observation is not a hard rule; in our experience we encountered situations where using a gradient boosting solution or a deep learning one alone resulted in the best performances. However, in many of the situations we faced, we can confirm that simply averaging solutions resulted in better predictions. We are strongly convinced that this happened because the two algorithms have two ways of optimizing predictions. Gradient boosting is based on decision trees, which are a form of analogy search because as an algorithm trees split your dataset into parts where the features tend to be similar in values between themselves and map to similar outputs. The gradient part of the algorithm intelligently combines multiple trees together for a better prediction, although it doesn't change the basic way in which decision trees behave. Deep learning, on the other hand, is purely on the principle of differentiation and nonlinear transformations, where the algorithm looks for the best weights to combine the transformed inputs.

These two different approaches result in quite different estimations whose errors tend to partially cancel each other out because they are strongly uncorrelated, in similar fashion to what actually happens in a random forest algorithm when we average the results of decision trees. This conclusion matches our experience comparing the results of gradient boosting and deep learning on the Tokyo Airbnb problem. The ensemble of the XGBoost model with the fastai model produced the best results, as shown in figure 12.3.

# Summary

- XGBoost solution to the Tokyo Airbnb problem shown in chapter 7 provides a baseline that we can use to assess the efficacy of deep learning to solve the same problem.
- Using XGBoost solution from chapter 7 as a starting point, we can create a deep learning solution for the Tokyo Airbnb problem. The fastai library provides a compact and relatively well-performing deep learning solution.
- By blending the predictions of the XGBoost and fastai models across a range of ratios, from 100% XGBoost to 100% fastai, we can see the effect of ensembling the models. We get the optimal results with a 50/50 ensemble of the two models.
- This result matches the recommendation from research focused on scrutinizing the claims of the efficacy of deep learning on tabular data.

# Appendix A
# Hyperparameters for classical machine learning models

Table A.1 Hyperparameters for linear models

| Hyperparameter | Description |
| --- | --- |
| C | Inversely related to regularization, smaller values correspond to stronger regularization. Search in the range `np.logspace(-4, 4, 10)`. |
| alpha | Constant that multiplies the regularization term, larger values correspond to stronger regularization. Search in the range `np.logspace(-2, 2, 10)`. |
| l_ratio | Blending L1 and L2 regularization in Elasticnet, pick from the values `[1, 5, 7, 9, 99]`. |

Table A.2 Hyperparameters for random forests and ERTs

| Hyperparameter | Description |
| --- | --- |
| max_features | Lower this parameter to increase bias and lower variance. Try such as `sqrt`, `log2`, and integer numbers representing 1/10th and 1/20th of the features. |
| min_samples_leaf | A way to regularize trees, usually set to 1; try growing it up to 30. |
