# CHAPTER 7 An-to-end example using XGBoost

that fairly distributes each feature's "credit" or "importance" in a model's prediction for a specific data instance. In other cases, SHAP values allocate the contribution of each feature to the model's output using a simple additive formula.

Shapley values consider the contribution of a feature across all possible combinations of features, which can be thought of as "games" in the model. "games" involve training the model on different feature sets. SHAP approximate Shapley values using a resampling strategy to avoid computing all possible games for the model and feature sets. By using SHAP values, we gain insights into how each feature influences the model's predictions on specific instances. This information is valuable for model debugging, feature engineering, and enhancing machine learning models' overall interpretability and trustworthiness.

We implemented SHAP values in listing 7.19 to gain insights into our previously built XGBoost model. In code, we retrieve the trained XGBoost model from a pipeline. In particular, we get its booster, the core component of the XGBoost model responsible for implementing the gradient boosting algorithm. We transformed the training data twice: first because we could not use the pipeline to feed the data into the booster. Hence, we preprocess it and extract its feature names for reference. Second, we transform the data into a DMatrix structure as the XGBoost documentation provides for efficient processing that is required for feeding the booster. At this point, we compute the SHAP values by a predict command with the parameter `pred_contribs` to set. Another simple predict command provides us with the predictions from the model to be used for comparison.

# Listing 7.19 SHAP values as an XGBoost output

```
from XGBoost import DMatrix

boster = model_pipeline['xgb'].get_booster()
\Xt = model_pipeline['processing'].transform(X)
feature_names = (
model_pipeline['processing']
    .feature_names_out())
)\Xd = DMatrix(Xt)

shap_values = booster.predict(Xd, pred_contribs=True)
preds = booster.predict(Xd)
```

Retrieves the trained XGBoost booster object from the pipeline's trained XGBoost model

Transforms the input data X using the processing pipeline

Gets the transformed features after the processing pipeline's transformations

Creates a DMatrix from the transformed input data

Gets the raw predicted values for the input data

Calculates SHAP values using the booster's predict function with the `pred_contribs=True` argument