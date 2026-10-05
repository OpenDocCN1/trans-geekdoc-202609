When we used a linear regression model, we assumed that the errors were normally distributed

When we used a linear regression model, this assumed a linear relationship between the predictors and target variable

To illustrate a real-world modeling assumption, I will draw from my first job as a credit derivatives researcher. To study different structures, we built financial models that took inputs such as the probability of default for various types of bonds. From a careful testings, we learned that a small change to the default assumptions could produce a large change in predictions. In fact, a small change could be the difference between a lucrative investment and financial distress.

In measuring the impact on the output, we will need to decide exactly what should be measured. This might mean running the model on some important cases, such as interest rate forecasts for predetermined scenarios. It might mean running the model on the entire test set. The decision will depend on what is important to stakeholders and the business case.

Once the analyst has identified what should be changed (e.g., a seed, a variable's distribution, an assumed value), and what output should be measured, we can design the tests. Running the tests will produce output that might be supplemented with metrics, visualizations, and alerts. For example, an alert might be triggered if any test causes a change of 10% or more for any metric. The results can be reported to the appropriate stakeholders.

Table 17.3 sensitivity testing on m given some model changes. The base case column shows predictions from the original model. The chg seed and median imput columns show predictions when a different seed and a different impute method were used, respectively. Note that the changes to predicted output were very small, which provides evidence of model stability. Accordingly, the changes to the RMSE statistics will also be small.

TABLE 17.3: Sensitivity Testing: Out-of-Sample Predictions

| index | base case | chg seed | median imput |
|---|---|---|--|
| 0 | 0.20 | 0.21 | 0.20 |
| 1 | -0.10 | -0.10 | -0.11 |
| 2 | 0.70 | 0.70 | 0.71 |
| 3 | 0.45 | 0.44 | 0.45 |
| 4 | 0.15 | 0.14 | 0.14 |