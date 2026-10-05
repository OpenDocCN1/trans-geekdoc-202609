# 2.3 SCOPE OF INTERPRETABILITY

# 2.3.3 Global Model Interpretability on a Modular Level

How do parts of the model affect predictions?

A Naive Bayes model with many hundreds of features would be too big for me and you to keep in our working memory. And even if we manage to memorize all the weights, we would not be able to quickly make predictions for new data points. In addition, you need to have the joint distribution of all features in your head to estimate the importance of each feature and how the features affect the predictions on average. An impossible task. But you can easily understand a single weight. While global model interpretability is out of reach, there is a good chance of understanding at least some models on a modular level. Not all models are interpretable at a parameter level. For linear models, the interpretable parts are the weights, for trees it would be the splits (selected features cut-off points) and leaf node predictions. Linear models, for example, look as if they could be perfectly interpreted on a modular level but the interpretation of a single weight is interfered with all other features. The interpretation of a weight always comes with the footnote that the other input features remain at the same value, which is not the case with many real applications. A linear model that predicts the value of a house, that takes into account both the size and the number of rooms, can have a negative weight for the room feature. It can happen because the number is already a highly correlated feature. In a neighborhood where people prefer larger houses, larger rooms could be more than a house with more rooms if both have the same size. The weights would only make sense in the context of the other features in the model. But the weights in a linear model can still be interpreted better than the weights of a deep neural network.

# 2.3.4 Local Interpretability for a Single Prediction

Why did the model make a certain prediction for an instance?

You can zoom in a single instance and examine what the model predicts for this input, and explain why. If you look at an individual prediction, the behavior of the otherwise complex model might behave more pleasantly. Locally, the prediction might depend linearly or monotonically on some features, rather than having a complex dependence on them. For example, the value of a house may depend nonlinearly on its size. But if you are looking only one particular 100 square meters house, there is a possibility for that dataset, your model prediction depends linearly on the size. You can find this out by simulating the predicted price changes when you increase or decrease the size by 10 meters. Local explanations can therefore be more accurate than global explanations. This book presents methods that can make individual predictions more interpretable in the section on model-agnostic methods.

# 2.3.5 Local Interpretability for a Group of Predictions

Why did the model make specific predictions for a group of instances?