
• [Advanced regression methods](#chap07.xhtml#h35)

## Objectives

This chapter introduces advanced machine learning techniques for algorithmic trading, with a focus on improving predictive accuracy and preventing overfitting. Readers will explore ensemble methods such as bagging and boosting and understand how they reduce variance and bias. They will implement random forests for volatility prediction, fine-tune `XGBoost` using `Scikit-Optimize`, and evaluate models using classification reports. In addition, the chapter covers `LASSO` and ridge regression, showing how to use `LASSO` for feature selection to reduce overfitting and improve model interpretability. Readers will also explore kernel methods for nonlinear relationships and online learning with `Scikit-multiflow` for real-time model adaptation. These techniques, including `XGBoost` and online learning, represent the state of the art in machine learning and provide readers with the tools to build adaptive and robust trading models for dynamic market conditions.

A case study on spread prediction demonstrates these advanced methods. First, we classify normal vs. abnormal price dynamics; then, we predict the spread's value within a volatility range.

## Understanding advanced machine learning

Modern machine learning for trading requires both predictive accuracy and adaptability. Traditional models that are trained once and applied indefinitely often fail in financial markets due to constant changes in trends, volatility, and market structure. To stay competitive, traders must use machine learning techniques that incorporate the latest advances in model ensembling, optimization, and real-time adaptation.

Ensemble methods, including bagging and boosting techniques like `XGBoost`, represent the cutting edge of predictive modeling. They improve accuracy by combining multiple models, iteratively correcting errors, and optimizing decision boundaries. These methods have become the industry standards for structured data tasks, including financial forecasting. `LASSO` and ridge regression introduce regularization, refining models by penalizing over-complexity and preventing over-fitting. Kernel methods extend traditional regression by capturing nonlinear relationships, allowing models to better reflect complex financial dependencies.

A key limitation of standard ML is its static nature: once trained, models remain fixed until retrained. Online learning overcomes this limitation by allowing models to be continuously updated with fresh data, making them highly effective for fast-moving markets. This real-time adaptation is critical for high-frequency trading, streaming data environments, and algorithmic strategies that must instantly adapt to new patterns.

Understanding these methods provides traders with the tools to build robust, adaptive, and high-performance models that go beyond traditional approaches. The following sections break down these techniques and their real-world applications in trading. To achieve greater predictive stability and accuracy, we turn to ensemble methods, which combine multiple models to improve performance and reduce errors.

## Introduction to ensembling methods

Ensemble methods are a powerful approach to improving model performance by combining multiple weak learners into a stronger, more reliable predictor. This technique leverages the principle that aggregated models generally outperform individual models in stability and accuracy. We introduced ensemble learning in [Chapter 5](#chap05.xhtml), Supervised Learning for Trading Systems, and earlier chapters; now, we will explore it in greater depth and apply it to trading strategies.

The core advantage of ensembling[1](#chap07.xhtml#footnote-093) is its ability to reduce errors and lower noise in predictions. By pooling the strengths and insights of different models, ensemble methods can effectively iron out the particularities and biases of individual predictors. This process of averaging or voting among models helps mitigate overfitting.

However, ensemble methods are not without their limitations. One key challenge is the potential correlation between predictors. If the individual models are too similar or correlated, the ensemble loses its diversity and, thus, some of its power. Another consideration is the number of predictors; too few may not provide sufficient diversity, while too many may lead to increased complexity and diminishing returns. We will discuss these points in detail in the following section, Statistical foundations of ensembling.

In the following sections, fight overfitting with bagging methods and Achieving high accuracy with boosting, we will explore two primary forms of ensembling, boosting and bagging, each with its unique approach to model combination and its strengths in the context of trading algorithms.

## Advanced ensembling method for classification

In this section, we look at the two cornerstone techniques of ensemble learning, bagging and boosting. We will explore the basic principles of these methods[2](#chap07.xhtml#footnote-092), highlighting their distinct advantages and how they differ from each other. As we unpack these methods, we will gain an understanding of their role in improving predictive accuracy and model robustness in various scenarios.

In the next section, we will explain the statistical foundations and motivations behind ensembling. This segment is optional and can be skipped if preferred.

### Statistical foundations of ensembling

In the context of ensemble learning, the theoretical motivation for error reduction when combining models can be understood through the bias-variance trade-off[3](#chap07.xhtml#footnote-091). The overall error of an ensemble can be decomposed into the following three components:

```
![](images/eq-12.jpg)
```

Let us define these three components:

* Bias is the tendency of a model to consistently make incorrect predictions due to overly simplistic assumptions in the learning algorithm. The simplicity of the model will lead to a high bias, which manifests itself as a systematic deviation from the true relationship in the data. The following graphs illustrate this:

```
![](images/fig-7-1.png)
```

The predictions illustrated in the linear relationship consistently deviate from accuracy (dotted line). Similarly, we demonstrate how bias impacts a machine learning classification algorithm.

In the following graph, the algorithm's overly simplistic boundary (frontier) between classes consistently results in poor classification outcomes:

```
![](images/fig-7-2.png)
```

* Variance describes how much the model's prediction errors fluctuate when applied to different sets of training data, highlighting the inconsistency of the model under varying data conditions.

* Irreducible error is the unavoidable error inherent in any model, caused by factors like unknown variables or inherent randomness in the data.

Now that we have grasped the fundamental terms let us explore how they interact and contribute to the overall error in a model.

Consider an ensemble of N independent models, each with a variance of and a bias of b. When these models are averaged, the bias of the ensemble remains b but the variance is reduced to `![](images/eq-31.jpg)` , assuming the models are independent and have equal variance.

This reduction in variance contributes significantly to the decrease in the total error of the ensemble, as the total error is a combination of bias squared, variance, and irreducible error.

Ensemble variance for an ensemble of models can be determined as follows:

```
![](images/eq-22.jpg)
```

This demonstrates how ensembling leads to a significant reduction in error by decreasing the variance component of the error.
