
# Measures of Machine Learning Models

- **Precision:** The proportion of true predictions out of all positive predictions made by the model. It is a measure of the model's ability to avoid false positives.

```
$Precision = \frac{TP}{TP + FP} \quad (6.25)$
```

- **Recall (Sensitivity):** The proportion of true predictions out of all active positive instances in the dataset. It is a measure of the model's ability to identify all positive instances.

```
$Recall = \frac{TP}{TP + FN} \quad (6.26)$
```

- **Confusion Matrix:** A table that summarises the performance of a classification model, showing the number of true positive (TP), true negative (TN), false positive (FP), and false negative (FN) predictions. It is used to calculate metrics such as accuracy, precision, recall, and specificity.

- **F1 Score:** The harmonic mean of precision and recall, providing a balanced measure of a model's performance. It is particularly useful when dealing with imbalanced datasets.

```
$F1 = 2 \frac{Precision \times Recall}{Precision + Recall} \quad (6.27)$
```

- **Receiver Operating Characteristic (ROC):** A graphical representation of the trade-off between true positive rate (sensitivity) and false positive rate (1-specificity) across different thresholds. It is used to evaluate the performance of binary classification models.

```
$TPR = \frac{TP}{TP + FN}; FPR = \frac{FP}{FP + TN} \quad (6.28)$
```

- **Area Under the Curve (AUC):** The area under the ROC curve, which provides a single value to summarise the model's performance. An AUC of 0.5 indicates a random classifier, while an AUC of 1.0 indicates a perfect classifier.

```
$AUC = \int_{0}^{1} TPR(FPR)dFPR \quad (6.29)$
```

These are only a few of the most common loss functions and evaluation metrics to provide insights into the model's performance to generalize to new data and make accurate predictions.

# 6.4.3 Public Health Loss Functions

“The public may be less interested in environmental quality than in economic prosperity.”
Dubos

In the field of public health the measures of cost mortality and morbidity are used to evaluate the outcome of health and well-being of a population.

The most common analyses methods:¹⁰

- Cost-utility, using quality-adjusted life years (QALYs)
- Cost-effectiveness, for specific outcomes, such as life expectancy or medical outcomes.

> ¹⁰Marja Hult et al., “Cost-Effectiveness Calculators for Health, Well-Being and Safety Promotion: A Systematic Review,” The European Journal of Public Health 31, no. 5 (May 2021): 997–1003, doi:10.1093/eurpub/ckab068.

As mentioned in the history of health metrics (Chapter 2), the cost-utility framework has been employed for calculating QALYs. Over time, this measure has been criticised for potentially discriminating against certain disabilities in the population by assigning costs that were perceived as either too high or too low, and for failing to capture the full spectrum of human health conditions.

Moreover, comprehensive tools that assess the impacts through cost-effectiveness measures to estimate the effectiveness of health interventions should also include a measure of disability. The measure of DALYs (Disability-Adjusted Life Years), developed in 1993, took major consideration of the disability status in evaluating the well-being of a population. It was further enhanced by incorporating a layer based on disability weights.

In summary, the measures for a cost-effectiveness intervention involve a careful calibration of following components: mortality, morbidity, and disability.

# 7 Techniques for Machine Learning Applications

Learning Objectives

- Apply feature engineering techniques to prepare data for modelling
- Evaluate and select the most appropriate machine learning model based on data characteristics
- Understand the fundamentals of key machine learning algorithms and their applications

Selecting the most suitable machine learning model involves understanding **the goals of the analysis**, the **nature of the data**, and the **statistical and machine learning methods** that suit the tasks. In Chapter 6, we learned about what machine learning models are, provided examples for building a model framework, and selected common metrics for model performance calibration and evaluation.

In this chapter, we focus on the strategies for selecting appropriate models by leveraging the strengths of different techniques, specifically for health metrics and for infectious diseases. We will explore various considerations involved in addressing potential biases, and discuss actions to prevent them.

# 7.1 Goals of the Analysis and Nature of Data

The identification of the **goal of the analysis** is fundamental. Whether it involves trend analysis, investigating the relationships between response and predictor variables, or strictly forecasting to predict future outcomes, the strategy for model selection varies accordingly.

Health Metrics Data:

- **Composite Measures:** Health metrics like DALYs are composite measures that include both mortality and morbidity data, often requiring sophisticated regression models capable of handling continuous variables and multiple predictors. By examining the components of DALYs (e.g., Years of Life Lost (YLLs) and Years Lived with Disability (YLDs)), we can identify the key drivers such as mortality rates, disease prevalence, and risk factors.
- **Regression Models:** Regression models, including **linear regression, Ridge regression, and Lasso regression**, are commonly used to handle these continuous variables and address challenges like correlation and multicollinearity with appropriate techniques such as regularisation.

# Infectious Disease Data:

- **Categorical and Continuous Data**: Infectious disease data can be categorical (e.g., disease presence or absence) or continuous (e.g., incidence rates). Classification models are suitable for categorical outcomes, while regression models are appropriate for continuous data.

- **Disease Dynamics**: Understanding the dynamics of infectious diseases, such as transmission rates, incubation periods, and immunity, informs the selection of models. Common models include compartmental models (e.g., SIR, SEIR) and agent-based models.

**Common considerations for health metrics and infectious diseases data type:**

- **Seasonality and Trends**: The data may exhibit seasonality or trends, necessitating the use of time series analysis models like ARIMA or seasonal decomposition to capture these patterns.

- **Simulation Models**: These models can predict the impact of interventions on DALYs and infectious diseases, estimating the effectiveness of different interventions and guiding policy decisions. Examples of these types of models are: **SIR models**, and **Agent-based models**. In addition, **confidence intervals** and **sensitivity analyses** help assess the uncertainty with these predictions.

- **Bayesian Models**: These models can estimate parameters and make predictions based on prior knowledge and observed data, incorporating uncertainty and variability.

- **Predictive modelling**: Such as **decision trees, support vector machines (SVM)**, and **Long Short-Term Memory (LSTM) neural networks**, can predict disease outbreaks, identify high-risk populations, and optimise resource allocation.

# 7.2 Statistical and Machine Learning Methods

The choice of model depends on the type of data, the relationships between variables, and the goals of the analysis. Once we have these factors well identified, we are a step forward in restricting the range of applicable models.

The next step involves conducting a thorough **explatory data analysis (EDA)**. This initial exploration helps to uncover the underlying structure of the data, the relationships between variables, and the response variable—which may also be referred to as the outcome—depends on predictors. This phase is critical as it informs the necessity of subsequent data adjustments and transformations.

The importance of data preparation and exploratory data analysis in machine learning is the building blocks in the preparation of machine learning digestible data. **Feature engineering** is a technique that involves creating new features from existing ones on domain knowledge or transformation of data to improve the model's ability to discern patterns. For example, creating features like **moving averages** or differences between consecutive days can reveal trends and cycles that are not immediately apparent from raw data.

Another example is the **standardisation** process, which is crucial when dealing with variables measured in different units. It involves rescaling the features so they have a mean of zero and a standard deviation of one. This process is particularly important when variables span
