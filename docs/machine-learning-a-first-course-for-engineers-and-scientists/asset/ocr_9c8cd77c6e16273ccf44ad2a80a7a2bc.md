# 7 Ensemble methods: Bagging and boosting

# 7.4 Gradient boosting

It has been seen in practice that AdaBoost performs well when there is little noise in the data. However, as the data becomes noisier, due to outliers (mislabeled data) or high uncertainty in the input-output relationship, the performance of the method can deteriorate. This is not an artifact of the boosting idea, but rather of the exponential loss used in the construction of AdaBoost. As discussed in Section 5.2, see Figure 5.2. To mitigate this and construct more robust boosting algorithms we can consider choosing some other (most robust) loss function. However, this will be at the expense of a more computationally intensive trained procedure.

To lay the foundation for more general boosting algorithms we will start by presenting a slightly different view on boosting. In the discussion above we have described boosting as learning a *sequence of weak classifiers*, each classifier tries to correct the mistakes made by the previous ones. This is an intuitive interpretation, but from a mathematical perspective, perhaps more useful is that boosting is a way to train an additive model. The fundamental task of supervised learning is to approximate some unknown function, mapping inputs to outputs, based on observed data. A very useful—and common—way of constructing a function approximator is using an additive model of the form,

```
f^B(X) = \sum_{b=1}^B a^{(b)}f^{(b)}(X) \quad (7.14)
```

where $a^{(b)}$ are real-valued coefficients and $f^{(b)}(X)$ are some "basis functions". For a regression problem, $f^{(b)}(X)$ can be used directly as the model's prediction. For a classification problem it can be thresholded by a sign function to obtain a hard classification, or transformed into a probability by passing through a logistic function.

Comparing (7.14) with (7.4) is clear that AdaBoost follows this additive form, where the learners (ensemble members) are the basis functions and their confidence scores are the coefficients. However, we have seen in fact other examples of additive models as well. To put boosting algorithms in a broader context provide a couple of examples:

If the basis functions $f^{(b)}(X)$ are a fixed priori, then the only learners are the coefficients $a^{(b)}$. The model (7.14) is then nothing than a linear regression, or generalized linear. For instance, transformations of the input. In Chapter 8 we will discuss more systematic ways of constructing (fixed) basis functions for additive models.

A more flexible model can be obtained if we allow the basis functions to be learnable. This is also important. In Chapter 6 we introduced the neural network model, and by outputting the expression for a two-layer regression network it can be seen that its an additive model.

> Time to reflect 7.3: If we write a two-layer regression neural network in the form of an additive model, what does $a^{(b)}$, and $f^{(b)}(X)$ correspond to?

An important consequence of this interpretation of boosting as an additive model, is that the individual ensemble members not necessarily have to correspond to "weak learners" for the specific problem study. For a classification problem, each ensemble member does need to correspond to a classifier to solve (some modified version of) the original problem. What is important is that the sum over all ensemble members in (7.14) results in a useful model! We will see an example of this below, where we discuss how regression is used to solve classification problems in the context of gradient boosting. This is also the reason for why we use $f$ instead of $y$ in the notation. Even for

^4Similarly, we can use link functions to turn the additive model $f^B(X)$ into a likelihood that is suitable for the properties of the data under study, using generalized linear models (Section 3.4).