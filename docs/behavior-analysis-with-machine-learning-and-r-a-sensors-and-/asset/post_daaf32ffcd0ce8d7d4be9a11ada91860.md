
# CHAPTER 1. INTRODUCTION

# 31

![](img/91c149cc24c3e5af2971580c9dda9d8b_43_0.png)

Figure 1.14: Model complexity v.s. train and validation error.

starts to 'memorize' the train set instead of finding general patterns applicable to new unseen instances. If we were to choose a model, the best one would be the one in the middle. Even if it was not perfect on the train data, it will do better than the other models when evaluating it on new test data.

Overfitting is a common problem in machine learning. One way to know if a model is overfitting is if the error in the train set is low, but it is high on a new set (a test or validation set). Figure 1.14 illustrates this idea. Too-simple models will have a high error in both, the train and validation sets. As the complexity of the model increases, the error on both sets is reduced. At some point, the complexity of a model is too high so that it gets too specific on the train set and fails to perform well on a new independent set.

In this example, we saw how overfitting and overfitting can affect the generalization performance of a model in a classification setting but the same can occur in regression problems.

There are several methods to reduce overfitting but many are specific to each type of model. For example, with decision trees (covered in chapter 2), one way to reduce overfitting is to limit their depth or build ensembles of trees (chapter 3). Neural networks are also highly prone to overfitting since they can be very complex with millions of parameters and there are also several techniques to reduce the effect of overfitting (chapter 8).

## 1.9 Bias and Variance

So far, we have seen how we can train predictive models and evaluate how well they do on new data (test/validation sets). The main goal is to have predictive models that have a low error rate with new data. Understanding the source of the error can help us

![](img/91c149cc24c3e5af2971580c9dda9d8b_44_0.png)

Figure 1.15: Error due to bias and variance.

more informed decisions when building predictive models. The *test error*, also known as the *generalization error* of a predictive model can be decomposed into three components: a bias, a variance, and noise.

**Noise.** This component is related to the data and there is nothing we can do about it. For example, two instances having the same values in their features but with a different label.

**Bias.** The bias is how much the average prediction differs from the true value. Note the *average* keyword. This means that we make the assumption that an infinite (or very large) number of train sets can be generated, and for each predictive model is trained. Then we average the predictions of all those models and see how much that average differs from the true value.

**Variance.** The variance relates to how much the predictions change for a given data point when training a model using a different train set each time.

The following picture graphically illustrates different scenarios for high/low bias and variance. The center of the target represents the true value and the small red dots the predictions on a hypothetical *test set*.

Bias and variance are closely related to underfitting and overfitting. High variance is a sign

![](img/91c149cc24c3e5af2971580c9dda9d8b_45_0.png)
![](img/91c149cc24c3e5af2971580c9dda9d8b_45_1.png)
![](img/91c149cc24c3e5af2971580c9dda9d8b_45_2.png)

overfitting. That is, a model is so complex that it will fit a particular train set very well. Every time it is trained with a different train set, the *train error* will be low, but it will likely generate very different predictions for the same test points and a much higher *test error*. Figure 1.16 illustrates the relation between overfitting and high variance with a regression problem. Given a feature $x$, two models are trained to predict $y$: i) a *complex model* (top row), and ii) a *simpler model* (bottom row). Both models are fitted with two training sets (a and b) sampled from the same distribution. The complex model fits the train data perfectly but makes very different predictions (big $\Delta$) for the same test point when using a different train set. The simpler model does not fit the data well but has a smaller $\Delta$ and a lower error on the test point as well. Visually, the function (red curve) of the complex model also varies a lot across train sets whereas the shapes of the simpler model functions look very similar.

On the other hand, if a model is too simple, it will underfit causing *highly biased* results and not being able to capture the input-output relationships. This results in a high *train error* as well.

> A formal formulation of the error decomposition can be consulted in the book “The elements of statistical learning: data mining, inference, and prediction” (Hastie et al., 2009).

## 1.10 Summary

In this chapter, several introductory machine learning concepts and terminology were introduced.

- Behavior can be defined as “an activity”.
- Three main reasons why we may want to analyze behavior: react, understand, and document.
- Machine Learning consists of a set of algorithms that automatically find patterns from data.
- The three building blocks of machine learning are data, algorithms.
- The main types of machine learning are supervised, semi-supervised, partially-supervised, and unsupervised learning.
- In R, data is usually stored in data frames. Data frames have variables (columns) and instances (rows).
- A predictive model is a model that takes some input and produces an output. Classifiers and regressors are predictive models.
- A data analysis pipeline consists of collection, cleaning, preprocessing, and evaluation.
- Model evaluation can be performed with hold-out validation or k-fold cross-validation.
- Overfitting occurs when a model ‘memorizes’ the train set instead of finding patterns.
- The test error can be decomposed into noise, bias, and variance.

# WHERE ARE WE?

BIAS

"THEY PASSED THE POWER ON TO YOU. YOU WILL LEARN TO CONTROL THEM."

# 1 YEAR LATER

LET'S TRY A NEW SETTING TO MAKE SURE YOU ARE NOT OVERITTING.

WELL DONE. YOU ARE DECREASING THAT ABSOLUTE ERROR.

SORRY TO INTERRUPT THE TRAINING BUT I'VE JUST RECEIVED A REPORT OF A STRANGE OBJECT 300 KM FROM HERE.

```r
Define function.
simple.model.train <- function(data, centrality = mean){
  classes <- unique(data$class)
}
```

WE'LL TAKE CARE OF THAT.

TO BE CONTINUED.

behavior enriquegc.com

![](img/91c149cc24c3e5af2971580c9dda9d8b_48_0.png)

# CHAPTER 2 Predicting Behavior with Classification Models

In the previous chapter, the concept of classification was introduced along with a simple example (feline type classification). This chapter will cover more in depth concepts on classification methods and their application to behavior analysis tasks. Moreover, additional performance metrics will be introduced. This chapter begins with an introduction to k-nearest neighbors (k-NN) applied to indoor location using Wi-Fi signals is presented. This chapter also covers Decision Trees and Naive Bayes classifiers and how they can be used for activity recognition based on smartphone accelerometer data. After that, Dynamic Time Warping (DTW) (a method for aligning time series) is introduced, and an example of how it can be used for gesture recognition is presented.

## 2.1 k-nearest Neighbors

k-nearest neighbors (k-NN) is one of the simplest classification algorithms. The predicted class for a given query instance is the most common class of its k nearest neighbors. A query instance is just the instance we want to make predictions on. In its most basic, the algorithm consists of two steps:

-1. Compute the distance between the query instance and all training instances.
2. Return the most common class among the k nearest training instances.

This is a type of lazy-learning algorithm because all the computations take place at prediction time. There are no parameters to learn at training time! The training phase consists of
