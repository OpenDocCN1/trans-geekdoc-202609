
## 2.2 TAXONOMY OF INTERPRETABILITY METHODS

- **Feature summary visualization:** Most of the feature summary statistics can also be visualized. Some feature summaries are actually only meaningful if they are visualized and a table would be a wrong choice. The partial dependence of a feature is such a case. Partial dependence plots are curves that show a feature and the average predicted outcome. The best way to present partial dependencies is to actually draw the curve instead of printing coordinates.

- **Model internals (e.g. learned weights):** The interpretation of intrinsically interpretable models falls into this category. Examples are the weights in linear models or the learned tree structure (the features and thresholds used for) of decision trees. The lines are blurred between model internals and feature summary statistic in, for example, linear models, because the weights are both model internals and summary statistics for the features at the same time. Another method that output models interpretation is useful for tabular data model-specific (see next criterion).

- **Data point:** This category includes all methods that return data points (already isnt or created) to make a model interpretable. One method is counterfactual explanations. To explain the prediction of a data instance, the method finds a similar data point by changing some of the features for which the predicted outcome changes in a relevant way (e.g. a flip in the predicted class). Another example is the identification of prototypes of predicted classes. To be useful, interpretation methods that output new data points require that the data points themselves can be interpreted. This works well for images and texts, but is less useful for data with hundreds of features.

- **Intrinsically interpretable model:** Solution to interpreting black box models is to approximate them (either globally or locally) with an interpretable model. The interpretable model itself is interpreted by looking at internal model parameters or feature summary statistics.

**Model-specific or model-agnostic:** Model-specific interpretation tools are limited to specific model classes. The interpretation of regression weights in a linear model is a model-specific interpretation, since – by definition – the interpretation of intrinsically interpretable models is always model-specific. Tools that only work for the interpretation of e.g. neural networks are model-specific. Model-agnostic tools can be used on any machine learning networks and are applied after the model has been trained (post hoc). These agnostic methods usually work by analyzing feature input and output pairs. By definition, these methods cannot have access to model internals such as weights or structural information.

**Local or global?** Does the interpretation method explain an individual prediction or the entire model behavior? Or is the scope somewhere between? Read more about the scope criterion in the next section.

## 2.3 Scope of INTERPRETABILITY

An algorithm trains a model that produces the predictions. Each step can be evaluated in terms of transparency or interpretability.

### 2.3.1 Algorithm Transparency

How does the algorithm create the model?

Algorithm transparency is about how the algorithm learns a model from the data and what kind of relationships it can learn. If you use convolutional neural networks to classify images, you can explain the algorithm edge detectors and filters on the lowest layers. This is an understanding of how the algorithm works, but not for the specific model that is learned in the end, and not for how individual predictions are made. Algorithm transparency only requires knowledge of the algorithm and not of the data or learned model. This focuses on model interpretability and not algorithm transparency. Algorithms such as the least squares for linear models are well studied and understood. They are characterized by a high transparency. Deep learning approaches (pushing a gradient through a network with millions of weights) are well understood and the inner workings are the focus of ongoing research. They are considered less transparent.

### 2.3.2 Global, Holistic Model Interpretability

How does the trained model make predictions?

You could describe a model as interpretable if you can comprehend the entire model at once (Lipton 2016). To explain the global model output, you need the trained model, knowledge of the algorithm and the data. This level of interpretability is about understanding how the model makes decisions, based on a holistic view of its features and each of the learned components such as weights, other parameters, and structures. Which features are important and what kind of interactions between them take place? Global model interpretability helps to understand the distribution of your target outcome based on the features. Global model interpretability is very difficult to achieve in practice. Any model that exceeds a handful of parameters or weights is unlikely to fit into the short-term memory of the average human. I argue that you cannot really imagine a linear model with 5 features, because it would mean drawing the estimated hyperplane in a 5-dimensional space. Any feature space with more than 3 dimensions is simply inconceivable for humans. Usually, when people try to comprehend a model, they consider only parts of it, such as the weights in linear models.

> Lipton, Zachary C. "The myths of model interpretability." arXiv preprint arXiv:1606.03490, (2016).

### 2.3.3 Global Model Interpretability on a Modular Level

How do parts of the model affect predictions?

A Naive Bayes model with many hundreds of features would be too big for me and you to keep in our working memory. And even if we manage to memorize all the weights, we would not be able to quickly make predictions for new data points. In addition, you need to have the joint distribution of all features in your head to estimate the importance of each feature and how the features affect the predictions on average. An impossible task. But you can easily understand a single weight. While global model interpretability is out of reach, there is a good chance of understanding at least some models on a modular level. Not all models are interpretable at a parameter level. For linear models, the interpretable parts are the weights, for trees it would be the splits (selected features cut-off points) and leaf node predictions. Linear models, for example, look as if they could be perfectly interpreted on a modular level but the interpretation of a single weight is interfered with all other features. The interpretation of a weight always comes with the footnote that the other features remain at the same value, which is not the case with many real applications. A linear model that predicts the value of a house, that takes into account both the size and the number of rooms, can have a negative weight for the room feature. It can happen because the number is already a highly correlated feature. In a neighborhood where people prefer larger houses, larger rooms could be more than a house with more rooms if both have the same size. The weights would only make sense in the context of the other features in the model. But the weights in a linear model can still be interpreted better than the weights of a deep neural network.

### 2.3.4 Local Interpretability for a Single Prediction

Why did the model make a certain prediction for an instance?

You can zoom in a single instance and examine what the model predicts for this input, and explain why. If you look at an individual prediction, the behavior of the otherwise complex model might behave more pleasantly. Locally, the prediction might depend linearly or monotonically on some features, rather than having a complex dependence on them. For example, the value of a house may depend nonarly on its size. But if you are looking only one particular 100 square meters house, there is a possibility for that dataset, your model prediction depends linearly on the size. You can find this out by simulating the predicted price changes when you increase or decrease the size by 10 meters. Local explanations can therefore be more accurate than global explanations. This book presents methods that can make individual predictions more interpretable in the section on model-agnostic methods.

### 2.3.5 Local Interpretability for a Group of Predictions

Why did the model make specific predictions for a group of instances?
