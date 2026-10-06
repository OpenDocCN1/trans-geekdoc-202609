# 11.3 Categorizing package Interpretation Methods

+   - The ranger package (Wright and Ziegler (2017)) to create a Random Forest.
- The parallel package (R Core Team (2022)) to perform parallel processing.
- The DALEX package (Bieleck (2018)) to use various techniques, including SHAP values, to interpret machine learning results.
- The DALEXTRA package (Makymyniuk et al. (2020)) extends the DALEX package. Extra functionality provided by DALEXTRA includes working directly with tidymodels.
- The vip package (Greenwell and Boehke (2020)) to generate Variable Importance Plots.
- The LIME package (Hvitfeldt et al. (2022)) to use the LIME approach to interpret machine learning models.

# 11.3 Categorizing Interpretation Methods

In what follows, we will introduce several interpretation methodologies. Not every methodology can be applied to all models. To help you decide which methodology to use for which interpretation task, we categorize them by tasks in this section.

For example, some methods are only appropriate for explaining a prediction result for a specific observation (local interpretation methods). In contrast, others are only appropriate to help us understand a model in general and how it makes predictions overall (global interpretation methods).

Going back to the previous example of lenders making a loan decision, we have to decide if to analyze why a specific applicant (observation) is not approved for a loan (local interpretation methods) or how, in general, the model predicts loan risk related to one particular predictor variable (global interpretation methods).

# Local vs. Global Interpretation

**Local Interpretation:** To analyze the prediction of a specific observation and to interpret the impact of predictor variables on that specific observation, we use local interpretation methodologies.

**Global Interpretation:** To analyze the predictions of a machine learning model in general and to interpret the impact of predictor variables regardless of specific observations, we use global interpretation methodologies.