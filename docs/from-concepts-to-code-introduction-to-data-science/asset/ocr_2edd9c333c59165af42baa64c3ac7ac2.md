286

Classification with Logistic Regression

increases the precision and decreases the recall. This makes sense, as a higher threshold makes it more stringent to predict a positive label. This reduces the number of false positives, which increases precision. At the same time, there are fewer predicted positives, and this increases the number of false negatives (cases which were actually positive but predicted as negative). The F1 scores for the lower and higher thresholds are 0.8028 and 0.7971, respectively, which suggests that the lower threshold is the better of the two.

A different model will likely produce different metrics. While the threshold may be changed to get better results, it is always preferable to build the best model possible, and then try different thresholds to tune it. The model and optimal threshold can be saved to predict outcomes on new data.

# 14.3 Chapter Summary

Logistic regression can be a useful supervised learning approach when the target variable is binary. It assumes that a linear combination of predictors is linearly related to the log of odds of an event. To estimate the parameters, we worked with the log-likelihood of the estimate and applied the gradient descent algorithm. Gradient descent works by iteratively moving the parameter estimates in a direction which is expected to be optimal. Many machine learning models variants of gradient descent, including deep neural networks.

We considered a dataset of tumors which were either benign or malignant. We used this case for logistic regression, and we fit the model using sklearn. We also verified the parameter estimates using gradient descent, and they matched our learning rate and number of iterations. We measured model performance using binary classification metrics. As the model outputs probabilities, the predicted label is determined by applying a threshold to the probabilities. We learned that varying the threshold will produce different performance metrics.

In this chapter and the previous chapter, we studied models that are useful when the data is labeled. Oftentimes, data is not labeled, and unsupervised methods will be valuable. In the next chapter, we will study an algorithm that is useful for exploring data groupings and detecting outliers without the benefit of labels.

# 14.4 Exercises

Exercises with solutions are marked with §. Solutions can be found in the book_materials folder of the repo at this location: