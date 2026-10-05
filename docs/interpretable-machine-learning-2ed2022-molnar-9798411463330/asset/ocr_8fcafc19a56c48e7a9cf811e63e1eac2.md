# 8.2 Local Surrogate (LIME)

Local surrogate models are interpretable models that are used to explain individual predictions of black box machine learning models. Local interpretable model-agnostic explanations (LIME) is a paper in which the authors propose a concrete implementation of local surrogate models. Surrogate models are trained to approximate the predictions of the underlying black box. Instead of training a global surrogate model, LIME focuses on training local surrogate models to explain individual predictions.

The idea is quite intuitive. First, forget about the training data and imagine you only have the black box model where you can input data points and get the predictions of the model. You can probe the box as often as you want. Your goal is to understand why the machine learning model made a certain prediction. LIME tests what happens to the predictions when you variations of your data into the machine learning model. LIME generates a new dataset consisting of perturbed samples and the corresponding predictions of the black box model. On this new dataset LIME interprets an interpretable model, which is weighted by the proximity of the sampled instances to the instance of interest. The interpretable model can be anything from interpretable chapter for example Lasso or a decision tree. The learned model should be a good approximation of the machine learning predictions locally, but it does not have to be a good global approximation. This kind of accuracy is also called local fidelity.

Mathematically, local surrogate models with interpretability constraint can be expressed as:

> explanation(x) = \min_{g\in G} L(f, g, \pi_x) + \Omega(g)

The explanation for instance x is the model g (e.g. linear regression model) that minimizes L (e.g. mean squared error), which measures how close the explanation is to the prediction of the original model f (e.g. an xgboost model), while the model complexity \Omega(g) is kept low (e.g. prefer features). G is the family of possible explanations, for all possible linear regression models. The proximity measure \pi_x defines the neighborhood around instance x that we consider for the explanation. In practice, LIME only optimizes the loss part. The user has to determine the complexity, by selecting the maximum number of features that the linear regression model may use.

The recipe for training local surrogate models:

+   * Select your instance of interest which you want to have an explanation of its black box prediction.
* Perturb your dataset and get the black box predictions for these new points.
* Weight the new samples according to their proximity to the instance of interest.
* Train a weighted, interpretable model on the dataset with the variations.

> 3Ribeiro, Marco Tulio, Sameer Singh, and Carlos Guestrin. “Why should I trust you?: Explaining the predictions of any classifier.” Proceedings of the 22nd ACM SIGKDD international conference on knowledge and data mining. ACM (2016).