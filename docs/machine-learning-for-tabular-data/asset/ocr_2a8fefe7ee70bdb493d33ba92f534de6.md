# Predicting Airbnb prices in New York City

model.save_model(xgb_save_model_path)

For Keras, we don't need an explicit statement to save the model because the model is saved automatically with the model-saving callback.

The following listing shows the code to load the model in XGBoost.

# Listing 3.4 Model-loading statements for XGBoost

```
loaded_saved_model = xgb.XGBClassifier()
loaded_saved_model.load_model(xgb_save_model_path)
```

> Defines a new XGBoost classifier object

> Loads the new XGBoost classifier object with the model you saved with the save_model statement

The statement to load a model for Keras is

```
saved_model = load_model(save_model_path)
```

One additional difference between XGBoost and Keras is that if you try to load a saved XGBoost classifier model (like the one we trained for the Airbnb NYC problem) and run a prediction, you will get an error if you are not on a current version of XGBoost. The XGBoost model training notebook includes the following statement to ensure that the XGBoost is at the latest:

```
!pip install --upgrade XGBoost
```

In this section, we have compared the simplicity of the XGBoost and Keras code for data preparation, model definition, model training, and model saving. Next, we will discuss the conclusions we can draw from this comparison.

# 3.1.6 Conclusions

One of the best pieces of advice for data science projects is to take the simplest approach. Apply Occam's razor to a data science project to make the task easier. If there is more than one way to solve a problem, pick the simplest approach. If linear regression will solve the problem, then why use support vector machines? If a conventional coding approach will solve the problem, then why use machine learning at all? If you take the simplest approach, you will likely get initial results faster, complete development of the whole solution faster, and an easier time maintaining the system it has been deployed.

To answer the question of how classic machine learning and deep learning in terms of simplicity, we compared solutions each approach to a concrete problem: the Airbnb NYC price prediction problem. By answering this question, we can apply the dictum “keep it simple” to tabular data problems.