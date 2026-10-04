
# Explaining your model with SHAP

## 293

| Feature value | SHAP value (impact on model output) |
| :--- | :--- |
| numeric_availability_365 | Low |
| target_encoding_coordinates | -0.5 |
| numeric_number_of_bedrooms | 0.0 |
| numeric_number_of_beds | 0.5 |
| numeric_minimum_nights | |
| numeric_nearest_airport | | |
| numeric_calculated_host_listings_count | | |
| numeric_imperial_palace_distance | | |
| numeric_number_of_reviews | | |
| ordinal_encoding_type_of_accommodation | | |
| ordinal_encoding_neighbourhood_more_than_30 | | |
| onehot_encoding_room_type_Entire_home_apt | | |
| binary_has_shared_bath | | |
| numeric_nearest_subway | | |
| numeric_reviews_per_month | | |
| numeric_nearest_train_station | | |
| numeric_nearest_convenience_store | | |
| numeric_number_of_reviews_itm_ratio | | |
| numeric_nearest_bus_station | | |
| numeric_days_since_last_review | | |

Figure 7.17 SHAP violin plot

![](img/def89cc476fa39f4c54bd34e78d91674_315_0.png)

# CHAPTER 7 End-to-end example using XGBoost

In addition, the need for a narration explaining the model's predictions of the dataset is crucial under regulations such as those in the European Union. Transparency and interpretability are essential components of regulations striving at data protection and preserving privacy, as the General Data Protection Regulation in the EU does. According to these regulations, individuals have the right to make sense of the logic behind automated decision-making processes that significantly affect their lives. Providing a clear explanation for why a specific prediction has been made ensures transparency and accountability and promotes fairness: it gives individuals power to seek clarification, challenge unfair decisions, and ultimately safeguard their rights.

You can actually generate each of these narratives by simple prompts to create explanations on the fly or by using ChatGPT API and the model process batches of explanations that you can recall when questioned about the reason for a specific prediction. The recipe, however, is in the case of on-the-fly or batch processing approaches: you tell the LLM to explain by providing the list of features (detailed with their description or meaning, if available), the original value in the dataset, and the SHAP value relative to the feature. Of course, it is necessary to mention the resulting prediction. Gluing together such information for the LLM to process JSON (a dictionary of dictionaries) would be ideal. In 7.22, we offer a solution for preparing a JSON structure to facilitate the prompt request to ChatGPT to explain a specific example in the dataset, identified by its row index. The code generates a data structure that encompasses all the information required to construct a coherent narrative.

+ Listing 7.22 Building a JSON of SHAP explanations as part of a prompt

```python
def generate_prediction_explanation(
    index,
    X,
    feature_names,
    shapley_values,
    predictions
):
    explanation = {"prediction": predictions[index]}
    for feature, original_value, shap_value in zip(
        feature_names,
        X[index],
        shapley_values[index, :]
    ):
        explanation[feature] = {
            "original_value": original_value,
            "shapley_value": shapley_value
        }
    return explanation
```

- Instantiates the JSON data structure as a Python dictionary
- Includes the predicted value to explain in the JSON
- Iterates over the features, original value, and SHAP values of the examined row

index_to_explain = 5
explanation_json = generate_prediction_explanation(
    index_to_explain,
)

# Summary 295

```python
feature_names,
Xt,
shap_values,
preds
print(explanation_json)
```

In our example, we require a description of why the model predicted a particular value for row 5 of the dataset. The printed JSON can then be enclosed in a prompt such as:

```

```text
You are an expert data scientist, and you need to interpret the predictions of a regression model based on the SHAP values provided in a JSON file. You build the explanations as a narration of how the most important variables contribute to the prediction. Here is the JSON file:
{'prediction': 55225.176, 'onehot_encoding_room_type_Entire_home/apt': {'original_value': 1.0, 'shap_value': 0.03404991}, 'onehot_encoding_room_type_Hotel': {'original_value': 0.0, 'shap_value': 0.00020163489}, ...}
```

When you send this prompt to ChatGPT, you will receive a text object in bullet points categorized by types of variables. This text describes the influence of each individual variable or group of variables on the outcome. The following is an excerpt of the insights we derived for the specific instance with row 5:

- Room type—the “home/apt” room type has a positive effect on the predicted price, contributing a SHAP value of 0.034. This suggests that listings with the entire home/apartment as the room type tend to have higher prices.
- The other types ("Hotel room, "Private room," and "Shared room")—These have smaller positive or negligible contributions, indicating that their effect on the price is not as significant.
- Neighborhood—The feature `neighbourhood_more_than_30` has a positive SHAP value of 0.083, suggesting that being in a neighborhood more than 30 influences the price.
- Type of accommodation—The `type_of_accommodation` feature has a small negative effect with a SHAP value of -0.008.

The complete text touches on all the features and you can prompt the LLM to reduce them to the top impactful features.

# Summary

- Building a baseline model is an often-neglected phase in modeling tabular data problems. Still, it can provide valuable insights by inspecting how the model underfits or overfits the data and its internal coefficients. A baseline model should ideally be simple, meaning that linear and logistic regression are the best candidates for regression and classification.

- After you get insights from your baseline model, you can proceed to more complex models using XGBoost. Cues about underfitting, nonlinearities, interactions, targets, and the predictors’ characteristics should be considered when setting up the first tentative values for key hyperparameters.

- Optimizing your model using Optuna can save you lot of time if you set your search space to incorporate insights and hypotheses you have developed so far regarding how your model should handle the data and the problem. Once the optimization has been completed, further insights can be gained from observing hyperparameter importance and optimization path charts.

- Explaining your trained model can be easily done with XGBoost and LightGBM using the predict method with the parameter `pred_contribs` set to true. The SHAP values, which are effectively multipliers with respect to the prediction, obtained, you can use standard charts from the `shap` package, such as the importance plot or the violin plot.
