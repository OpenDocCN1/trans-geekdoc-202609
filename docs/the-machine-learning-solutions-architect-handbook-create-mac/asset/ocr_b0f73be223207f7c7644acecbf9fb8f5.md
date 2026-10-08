The basic idea behind the coalition game theory is to form different permutations of coalitions of players when playing a game, then observe the game results from the different permutations, and finally calculate the contribution of each player. For example, if there are three features (A, B, and C) in the training dataset, then there will be distinct coalitions (2^3). We train one model for each distinct coalition for a total of eight models. We use all models to generate predictions in the dataset, figure out the marginal contribution of each feature, and assign a Shapley value to feature to indicate the feature importance. For example, if the model that uses a coalition with only features A and B generates an output of 50, and the model that uses features A, B, and C generates an output of 60, then feature C has a marginal contribution of 10. This is just a generalization of the concept; the actual calculation and assignments are more involved.

SHAP can also be installed as a regular Python package. It can be used to explain tree ensemble models, natural language models (such as transformers), and deep learning models. It has the following explainers:

+   * TreeExplainer: An implementation for computing SHAP values for trees and ensemble of trees algorithms
* DeepExplainer: An implementation for computing SHAP values for deep learning models
* GradientExplainer: An implementation of the expected gradients to approximate SHAP values for deep learning models
* LinearExplainer: Used to explain linear models with independent features
* KernelExplainer: A model-agnostic method for estimating SHAP values for any model because it doesn't make assumptions about the model type

SHAP is widely considered the state-of-the-art model explainability algorithm, and it has been implemented in commercial offerings as SageMaker. It can be used to compute both global feature importance and local explainability for a single instance. It does have some shortcomings as well, as slow computation associated with KernelExplainer.

# Designing an ML platform for governance

ML technology systems are critical in the overall operations of ML governance processes and activities. First, these technology systems need to be designed and built to meet the internal and external policies and guidelines themselves. Second, technology can help with simplifying and automating ML governance activities. The following diagram shows the various ML governance touchpoints in an enterprise ML platform: