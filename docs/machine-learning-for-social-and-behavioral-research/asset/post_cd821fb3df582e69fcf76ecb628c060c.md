
## FIGURE 6.10. Partial dependence plot for math with rug marks

![](img/5047f0f064e22688ceb5d0cdfaf3e964_172_0.png)

An additional drawback of partial dependence plots is that when predictors are correlated, the average across other predictors can bias the visualized relationship between x and expected y. A method developed to overcome this issue and demonstrate unbiased function approximation in the presence of correlations among predictors is the accumulated local effects plot (ALE; Apley, 2016). In some data analysis scenarios, partial dependence and ALE plots can demonstrate discrepancies. To illustrate these differences, we simulated data where two predictors have a correlation of 0.88 and have effects on a continuous y variable. In this simulation, $x_1$ was simulated to have a linear effect on $y$, while $x_2$ was simulated to have a nonlinear relationship following a sine curve. Both the partial dependence and ALE plots are displayed in Figure 6.11.

FIGURE 6.11. Partial dependence plot in the left pane, while the accumulated local effects plot is displayed in the right pane for the simulated data.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_173_0.png)

Despite $x_1$ having a linear relationship, the nonlinear effect of $x_2$ is essentially absorbed into the partial dependence plot in the left panel. The ALE plot depicts a linear relationship within the highest density values of $x_1$. Given that many predictors are correlated in social and behavioral datasets, we would expect to see small biases to partial dependence plots in many analysis scenarios.

## 6.5.2 Local Interpretation

To visualize how an individual's prediction of the outcome can change when aspects of a predictor change, one can examine the *individual conditional expectation* (ICE) plot (Goldstein, Kapner, Bleich, & Pitkin, 2015). In contrast to the partial dependence plot, which depicts the average relationship between a predictor and the outcome, ICE plots identify heterogeneous relationships by plotting the relationship between predictor and outcome for each observation. This involves replacing an individual's value on $x$ with a grid of potential values while retaining the individual's values on the other predictors, and generating predictions of the outcome based on the grid of $x$ values.

An ICE plot was generated for the ECLS-K analysis for the reading variable and depicted in Figure 6.12. In this, we see little evidence for heterogeneity, most lines follow the general form of the aggregate (grey) line. However, based on our initial testing with simulated data, it seems as though this approach has difficulty picking up on heterogeneous effects, thus we use caution in their use.

A second method for examining the relationship between variables at the individual level is to use *local interpretable model-agnostic explanations* (LIME; Ribeiro, Singh, & Guestrin, 2016). > ²It would work just well to use a form of regularized logistic regression

## FIGURE 6.12. Individual conditional expectation plot for reading scores.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_174_0.png)

The general idea behind LIME is that although complex algorithms may be necessary to adequately model a dataset, at the local level (individual case), linear relationships abound, allowing one to better understand the predictions from a complex algorithm. Using the global surrogate model approach as a basis, a complex algorithm (e.g., random forests) is used to generate predictions and repeated a large number of times based on permuted values of the predictors. Although there are series of additional steps to this process, it results in a metric such as R² for how well the simpler model is able to capture the relationship for each individual, along with a feature importance weight for a subset of the most important predictors. This is implemented in the lime package, and we output the values for the first two observations using random forests on the ECLS-K data in Table 6.3. From the values in this table, we examine how a linear regression with five features can explain the predictions from random forests. For the first two cases, 87% of the variance was explained with a much simpler model, along with the weights for each predictor used in explaining the predictions. Across all of the observations, there was very little variation to the amount of variance explained, with R² values ranging from 0.86 to 0.89.

## Ensembles

**TABLE 6.3.** Results from Using LIME to Explain the Predictions from Random Forests with Linear Regression. Only the first two cases, using a maximum of five predictors are given.

| case | model_r2 | model_intercept | model_prediction | feature_value | feature_weight |
|---|---|---|---|---|---|
| 1 | read | 0.87 | 32.98 | 102.97 | 206.63 | 0.25 |
| 1 | knowledge | 0.87 | 32.98 | 102.97 | 38.15 | 0.27 |
| 1 | math | 0.87 | 32.98 | 102.97 | 1.56 | 1.01 |
| 1 | income | 0.87 | 32.98 | 102.97 | 128000.00 | 0.00 |
| 2 | read | 0.87 | 32.15 | 82.36 | 163.26 | 0.26 |
| 2 | knowledge | 0.87 | 32.15 | 82.36 | 18.73 | 0.27 |
| 2 | math | 0.87 | 32.15 | 82.36 | 19.65 | 0.12 |
| 2 | SES | 0.87 | 32.15 | 82.36 | 0.62 | 1.02 |
| 2 | income | 0.87 | 32.15 | 82.36 | 55800.00 | 0.00 |

## 6.6 Empirical Example

To explain the usage of bagging, random forests, and boosting, we apply all three algorithms to the NSDUH dataset, with all 43 predictors to predict suicidal thoughts (SUICTHNK). The original sample of 55,271, we subset the dataset into a training dataset with 1,000 observations, and a test dataset with 1,000 observations. These two new datasets were created so they have equal proportions of yes and no responses, with the original sample being heavily skewed. We assessed the use of five methods: logistic regression, bagging, random forests, gradient boosting, and extreme gradient boosting. Logistic regression serves as a baseline approach.

## Machine Learning for Social and Behavioral Research

The number of tuning parameters for each algorithm, we only present the results based on the highest AUC value for each approach. These are displayed in Table 6.4, as assessed using bootstrap samples and assessed on the test dataset.

**TABLE 6.14. AUC as Assessed Using Bootstrapping and Evaluation on the Test Sample.**

| Bootstrapping | Test |
|---|---|
| GLM | 0.78 | 0.79 |
| Bagging | 0.76 | 0.78 |
| RF | 0.79 | 0.79 |
| GBM | 0.81 | 0.80 |
| XGBoost | 0.81 | 0.80 |

The comparison of AUC can be facilitated through the use of ROC plots, which are depicted in Figure 6.13. To create this figure, we used the model developed on the training sample to create predicted probabilities.

FIGURE 6.13. ROC plots for NSDUH example across the five algorithms as evaluated on the test dataset.

![](img/5047f0f064e22688ceb5d0cdfaf3e964_176_0.png)
