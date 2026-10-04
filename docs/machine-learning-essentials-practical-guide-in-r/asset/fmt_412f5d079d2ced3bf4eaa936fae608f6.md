
In real life data, the separation boundary is generally nonlinear. Technically, the SVM algorithm perform a non-linear classification using what is called the [kernel trick](https://en.wikipedia.org/wiki/Support_vector_machine). The most commonly used kernel transformations are *polynomial kernel* and *radial kernel*.

Note that, there is also an extension of the SVM for regression, called support vector regression.

In this chapter, we'll describe how to build SVM classifier using the *caret* R package.

## 29.2 Loading required R packages

* `tidyverse` for easy data manipulation and visualization
* `caret` for easy machine learning workflow

```
```

## 29.3 Example of data set

Data set: `PimaIndiansDiabetes2` [in `mlbench` package], introduced in Chapter [21](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX), for predicting the probability of being diabetes positive based on multiple clinical variables.

We'll randomly split the data into training set (80% for building a predictive model) and test set (20% for evaluating the model). Make sure to set seed for reproducibility.

```
```

## 29.4 SVM linear classifier

In the following example variables are normalized to make their scale comparable. This is automatically done before building the SVM classifier by setting the option `preProcess = c("center","scale")`.

```
```

```
## [1] neg pos neg pos pos neg
## Levels: neg pos
```

```
```

```
## [1] 0.782
```

Note that, there is a tuning parameter `C`, also known as *Cost*, that determines the possible misclassifications. It essentially imposes a penalty to the model for making an error: the higher the value of `C`, the less likely it is that the SVM algorithm will misclassify a point.

By default `caret` builds the SVM linear classifier using `C = 1`. You can check this by typing `model` in R console.

It's possible to automatically compute SVM for different values of `C` and to choose the optimal one that maximize the model cross-validation accuracy.

The following R code compute SVM for a grid values of `C` and choose automatically the final model for predictions:

```
```

![](Image00026.jpg)

```
```

```
##       C
## 12 1.16
```

```
```

```
## [1] 0.782
```

## 29.5 SVM classifier using Non-Linear Kernel

To build a non-linear SVM classifier, we can use either polynomial kernel or radial kernel function. Again, the `caret` package can be used to easily computes the polynomial and the radial SVM non-linear models.

The package automatically choose the optimal values for the model tuning parameters, where optimal is defined as values that maximize the model accuracy.

* **Computing SVM using radial basis kernel**:

```
```

```
##   sigma    C
## 1 0.136 0.25
```

```
```

```
## [1] 0.795
```

* **Computing SVM using polynomial basis kernel**:

```
```

```
##   degree scale C
## 8      1  0.01 2
```

```
```

```
## [1] 0.795
```

In our examples, it can be seen that the SVM classifier using non-linear kernel gives a better result compared to the linear model.

## 29.6 Discussion

This chapter describes how to use support vector machine for classification tasks. Other alternatives exist, such as logistic regression (Chapter [22](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX)).

You need to assess the performance of different methods on your data in order to choose the best one.

# 30 Classification Model Evaluation

## 30.1 Introduction

After building a predictive classification model, you need to **evaluate the performance of the model**, that is how good the model is in predicting the outcome of new observations test data that have been not used to train the model.

In other words you need to estimate the model prediction *accuracy* and prediction errors using a new test data set. Because we know the actual outcome of observations in the test data set, the performance of the predictive model can be assessed by comparing the predicted outcome values against the known outcome values.

This chapter describes the commonly used metrics and methods for assessing the performance of predictive classification models, including:

* **Average classification accuracy**, representing the proportion of correctly classified observations.
* **Confusion matrix**, which is 2x2 table showing four parameters, including the number of true positives, true negatives, false negatives and false positives.
* **Precision, Recall and Specificity**, which are three major performance metrics describing a predictive classification model
* **ROC curve**, which is a graphical summary of the overall performance of the model, showing the proportion of true positives and false positives at all possible values of probability cutoff. The **Area Under the Curve** (**AUC**) summarizes the overall performance of the classifier.

We'll provide practical examples in R to compute these above metrics, as well as, to create the ROC plot.

## 30.2 Loading required R packages

* `tidyverse` for easy data manipulation and visualization
* `caret` for easy machine learning workflow

```
```

## 30.3 Building a classification model

To keep things simple, we'll perform a binary classification, where the outcome variable can have only two possible values: negative vs positive.

We'll compute an example of linear discriminant analysis model using the `PimaIndiansDiabetes2` [`mlbench` package], introduced in Chapter [21](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX), for predicting the probability of diabetes test positivity based on clinical variables.

1. Split the data into training (80%, used to build the model) and test set (20%, used to evaluate the model performance):

```
```

2. Fit the LDA model on the training set and make predictions on the test data:

```
```

## 30.4 Overall classification accuracy

The overall **classification accuracy** rate corresponds to the proportion of observations that have been correctly classified. Determining the raw classification accuracy is the first step in assessing the performance of a model.

Inversely, the **classification error rate** is defined as the proportion of observations that have been misclassified. `Error rate = 1 - accuracy`

The raw classification accuracy and error can be easily computed by comparing the observed classes in the test data against the predicted classes by the model:

```
```

```
## [1] 0.808
```

```
```

```
## [1] 0.192
```

From the output above, the linear discriminant analysis correctly predicted the individual outcome in 81% of the cases. This is by far better than random guessing. The misclassification error rate can be calculated as 100 - 81% = 19%.

In our example, a binary classifier can make two types of errors:

* it can incorrectly assign an individual who is diabetes-positive to the diabetes-negative category
* it can incorrectly assign an individual who is diabetes-negative to the diabetes-positive category.

The proportion of theses two types of errors can be determined by creating a **confusion matrix**, which compare the predicted outcome values against the known outcome values.

## 30.5 Confusion matrix

The R function `table()` can be used to produce a **confusion matrix** in order to determine how many observations were correctly or incorrectly classified. It compares the observed and the predicted outcome values and shows the number of correct and incorrect predictions categorized by type of outcome.

```
```

```
##                 predicted.classes
## observed.classes neg pos
##              neg  48   4
##              pos  11  15
```

```
```

```
##                 predicted.classes
## observed.classes   neg   pos
##              neg 0.615 0.051
##              pos 0.141 0.192
```
