
# Exercise 7.2

MOA’s Hoeffding Tree algorithm can use different prediction methods at the leaves. The default is an adaptive Naive Bayes method, but a majority class classifier can be used instead by specifying `-l` (`trees.HoeffdingTree -l MC`). You can set this up in MOA’s *Configure* interface (you need to scroll down).

a. What is the accuracy of the Hoeffding Tree when a majority class classifier is used at the leaves?

b. What is the accuracy of the OzaBag bagging classifier?

# Exercise 7.3

Now let us use an evolving data stream. The rate of movement of the centroids of the `RandomRBFGeneratorDrift` generator can be controlled using the `speedChange` parameter.

a. Use the Naive Bayes classifier on a `RandomRBFGeneratorDrift` stream of 1,000,000 instances with 0.001 change speed. Use again `BasicClassificationPerformanceEvaluator` for prequential evaluation. What is the accuracy that we obtain?

b. What is the accuracy of a Hoeffding Tree under the same conditions?

c. What is the corresponding accuracy of OzaBag?

# Exercise 7.4

The Hoeffding Adaptive Tree adapts to changes in the data stream by constructing tentative “alternative branches” as preparation for changes, and switching to them if they become more accurate. A change detector with theoretical guarantees (ADWIN) is used to check whether to substitute alternative subtrees.

a. What is the accuracy of `HoeffdingAdaptiveTree` in the above situation?

b. What is the accuracy for `OzaBagAdwin`, the ADWIN adaptive bagging technique?

c. Finally, what is the accuracy for `LeveragingBag` method?

# Exercise 7.5

Besides data streams, MOA can also process ARFF files. We will use the `covtypeNorm.arff` dataset, which can be downloaded from the MOA website. Run the following task, which uses the Naive Bayes classifier:

```
EvaluatePrequential
-s (ArffFileStream -f covtypeNorm.arff)
-e BasicClassificationPerformanceEvaluator
-i 1000000 -f 10000
```

You will have to copy and paste this into the *Configure* text box, because you cannot specify an `ArffFileStream` in MOA’s interactive interface. Also, the default location for files is the top level of the MOA installation folder—you will probably find the model files `modelNB.moa` and `modelHT.moa` that you made in the last session lab there—so you should either copy the ARFF file there or use its full pathname in the command.

a. What is the accuracy of Naive Bayes on this dataset?

b. What is the accuracy of a Hoeffding Tree on the same dataset?

c. Finally, what is the accuracy of Leveraging Bagging?

d. Which method is fastest on this data?

e. Which method is most accurate?

# 8 Regression

Regression is a learning task whose goal is to predict a numeric value, instead of a categorical attribute as in classification. Some of the techniques that are used in classification can be used in regression, but not all. Decision trees, the Perceptron and lazy learning can be used for regression, with modifications.

## 8.1 Introduction

Given a *numeric* attribute to be predicted, called the *outcome*, a regression algorithm builds a model that predicts for every unlabeled instance *x* a numeric prediction *y* for the outcome of *x*.

Examples of regression problems are predictions of quantities that cannot be reduced to a discrete label, such as prices in stock markets, product sales, time delays, or the number of visits to a website. It is possible to reduce regression to classification problems by discretizing the values of the outcome into intervals, or the other way around, to use regression algorithms to do classification, transforming the discrete class into a numerical variable. Of course, these transformations need not give optimal results.

The simplest regression algorithm is to return the mean value of the attribute that we want to predict. This is equivalent to the majority class method in classification, a learner that does not use the information in the rest of the attributes. A far more useful method in nonstreaming regression is *linear regression*.

Linear regression builds a linear model *f*, of the form

```
f(x) = w0 + w1*x1 + ... + wp*xp
```

that minimizes the residual sum of squares:

```
RSS(w) = Σ(yi - f(xi))^2
```

where the input is the set of *N* pairs (*x*[*i*]*, y*[*i*]). However, the exact solution is

```
w = (X^T X)^-1 X^T y
```

which is hard to compute incrementally, let alone in the streaming setting. Approximate solutions can be given using random projection sketches (see [73, 248] for example), but their use in practical data mining is still preliminary. So we look for other strategies that are more clearly incremental and adaptive.

## 8.2 Evaluation

To evaluate regression methods, we can use the same methodologies as in classification, such as holdout, prequential, and Interleaved test-then-train, but the misclassification rate measure is not applicable. The following measures are usually considered in regression:

*   **Mean square error (MSE):** This is the most common measure, and gives the error using the mean of the squares of the differences between the actual values and the predictions:

```
MSE = (1/N) * Σ(yi - ŷi)^2
```

*   **Root mean square error:** The square root of the mean square error:

```
RMSE = sqrt(MSE)
```

*   **Relative square error:** The ratio between the MSE of the regression method, and the MSE of the simplest regression method available, the mean regression algorithm:

```
RSE = MSE(model) / MSE(mean)
```

*   **Root relative square error:** The square root of the relative square error:

```
RRSE = sqrt(RSE)
```

*   **Mean absolute error:** This measure is similar to the MSE, but considers absolute values of the difference:

```
MAE = (1/N) * Σ|yi - ŷi|
```

*   **Relative absolute error:** Similar to the relative square error, but considers absolute values of the difference:

```
RAE = MAE(model) / MAE(mean)
```

It is easy to see that all these measures can be computed incrementally by maintaining a constant number of values in memory.

## 8.3 Perceptron Learning

The Perceptron [37] was presented in section 6.5 as an online classification method. However, it is just as naturally viewed as a regression method.

Given a data stream of pairs (*x*[*i*]*, y*[*i*]), where *x*[*i*] is an example and *y*[*i*] is its numeric outcome value, the goal of the perceptron is to minimize MSE on the examples. To do this, the strategy is again to move each weight in the weight vector *w* in the direction of the descending error gradient.

The update rule becomes in this case:

```
w <- w + η * (yi - ŷi) * xi
```

As in classification, weights can be updated at every single example, as in the weight above, or taken in mini-batches for a single update step per mini-batch. This allows us to fine-tune the trade-off between update time and adaptiveness.

## 8.4 Lazy Learning

Lazy learning is one of the simplest and most natural models for classification and regression—in particular the *k*-Nearest Neighbor algorithm. Given a distance function *d* among instances, the *k*-NN method in regression finds the *k* instances closest to the instance to predict, and averages their outcomes. As in classification, the average may be weighted according to the distance to each neighbor.

The performance of the method strongly depends on the distance function used. For dense instances with numeric attributes, the Euclidean distance could be appropriate. For textual data, the cosine similarity measure or the Jaccard coefficient could be more appropriate.

`IBLStreams`, due to Shaker and Hüllermeier [225], is an implementation of lazy learning for regression on streams. Besides the basic ideas from streaming *k*-NN, it includes heuristics for removing outlier points from the database, removing instances that are too close to some already in the database (hence, not that useful), and for adaptively choosing the size of the database and of the parameter *k*.

## 8.5 Decision Tree Learning
