11.9 When and When Not to Use Interpretation 335

# ## The Intercept from the linear OLS model is: 5.463 5.463 5.463

we can show that the Intercept, together with the quantitative impacts from Helga's predictor variables values, add up to the prediction of the linear OLS model (.predOLS);

| 5.46 | 2.38 | 1.51 | -1.53 | 7.82 |
|---|---|---|---|--|
| Intercept | ContrEduc | ContrTenure | ContrFem | predOLS |

# 11.9 When and When Not to Use Interpretation

We should always use interpretation algorithms to better understand why our model predicts certain outcomes and quantify the impact of individual and cumulative predictions. It is also a good practice to use interpretation methodologies to check if the results are similar.

For choosing an appropriate interpretation methodology, it is important to consider which type of questions we can answer with which methodology. Below is a list that gives some points:^{23}

+   - Ceterisis Plots:
    - Can be used to quantify the impact of variable change for a specific observation.
    - Model-agnostic and local.

+   - Partial Dependence Plots:
    - Can be used to quantify the impact of variable change for a complete model, but they are not specific individual observations.
    - Model-agnostic and global.

+   - Variable Importance Plots (VIP)
    - Analyze the importance of variables but not the quantitative impact on the predictions.
    - VIPs are well suited for deciding which predictor variables stay in a model and which ones should be dropped.
    - Model-specific (model-agnostic versions also exist) and local.

+   - SHAP Values
    - Quantify the impact of predictor variable values on a specific prediction.
    - Model-agnostic and global.

+   - LIME.

> ^23 See Molinar (2020) for a detailed overview of interpretation methodologies.