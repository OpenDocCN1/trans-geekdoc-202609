# # 5 Robustness of Penalty Estimators

# ## 5.1 Introduction

The loss functions $L_1, L_2$, Huber, and log-cosh described in Chapters 2 and 3 provide reasonable models for prediction but they can be improved through a procedure called *regularization*. In this procedure, a penalty is added to a loss function so that parameter values can be fine-tuned to produce a better model. Using a penalty function with a loss function provides a range of models to choose from and the goal becomes one of finding optimal model that produces the lowest prediction error. In effect, we seek a model that does not overfit or underfit a given training set, but rather one that strikes a balance between the two. Penalty functions can also be used to reduce model complexity. In this chapter, we explore the basic properties and characteristics of a variety of different penalty functions that can be used to regularize regression models. In the next chapter, the issues of overfitting and underfitting are explored in detail along with the procedures that use penalty functions to control model complexity.

# ## 5.2 Penalty Functions

Penalty functions (see Saleh et al. 2019, 2022; James et al. 2023) and their effective use are very important in machine learning, especially for linear and logistic regression models and, to some extent, neural networks. Unfortunately, they are not used as often as they should be because many of their key benefits are not well-understood. While the primary benefit stems from their use in regularization, they have a number of other advantages. For example, they can be used to mitigate the effects of collinearity, reduce parameter variance, identify important features, or simply keep the values of the parameters under control. These and other capabilities will be covered in this chapter. In the context of outliers, we will delve into whether or not penalty functions can help reduce the impact of outliers. In this section, we describe the origins of penalty functions, how they are derived, their functional form, and their main properties.

# ## 5.2.1 Multicollinearity

The original motivation for penalty functions was the problem of multicollinearity. To understand this concept, consider the closed-form least squares (LS) solution in matrix form given by

$$ \hat{\beta}^{LS} = (X^T X)^{-1} X^T y, $$
(5.2.1)