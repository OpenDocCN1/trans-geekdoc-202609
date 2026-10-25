# Figure 3. Negative consequences of opaque models

![](bbox=[0.215, 0.162, 0.755, 0.428])

# 3. INTERPRETABILITY TECHNIQUES

# 3.1. Methods for Making Machine Learning Models Interpretable

There are various methods that provide valuable tools for improving model interpretability, with each having unique strengths. The three popular techniques that makes the ML models interpretable includes local interpretable model-agnostic explanations (LIME), Shapley additive explanations (SHAP), and feature importance analysis (Figure 4). These techniques, helps us to gain valuable insights into complex machine learning models, enabling them to make informed decisions and build trust in AI-driven systems (Du et al. 2019; Wu et al., 2023; ElShawi et al., 2021; Pudjihartono et al., 2022; Altmann et al., 2010; Jie et al., 2018).

# 3.1.1. Local Interpretable Model-Agnostic Explanations (LIME)

LIME is a model-agnostic method designed to explain individual model predictions. It operates by training a simple interpretable model, such as linear regression, on a local neighbourhood of data points around the prediction of interest. The interpretable model approximates the behaviour of the complex black-box model within the vicinity of the specific data point. LIME provides quantitative explanations in the form of feature weights and contributions. These values indicate how much each feature influenced the prediction for the specific instance, helping users understand which aspects of the input data were most critical in the decision. Thus, LIME bridges the gap between complex black-box models and human understanding by providing insights into individual predictions. By offering quantitative and feature-level explanations, LIME empowers individuals to trust and make use of AI-driven systems in contexts where interpretability is paramount (Wu et al., 2023; ElShawi et al., 2021).