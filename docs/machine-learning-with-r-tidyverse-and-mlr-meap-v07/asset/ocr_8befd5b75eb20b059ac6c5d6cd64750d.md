In this section, I'll summarize the general machine learning concepts we covered throughout the book, referencing the relevant sections of the book as we go. These concepts include:

+   - Types of machine learning algorithms
+   - The bias-variance trade-off
+   - Model validation
+   - Hyperparameter tuning
+   - Missing value imputation
+   - Feature engineering and feature selection
+   - Ensemble techniques
+   - Regularization

My hope is that now you've completed the book, these concepts will fit more concretely into your bigger picture of machine learning.



Machine learning tasks can be divided into supervised and unsupervised tasks, based on whether the algorithm has access to labeled data. In other words, whether we have access to the ground truth when training the model, or not.

Algorithms that learn patterns in the data that can be used to predict the ground truth are said to be supervised. Supervised machine learning algorithms can be further split, based on the kind of output variable they predict. Supervised learning algorithms that predict categorical variables (or classes) are said to be classification algorithms, while those that predict continuous variables are said to be regression algorithms.

> NOTE Some algorithms, like k-nearest neighbors, random forest, and XGBoost can be used for both classification and regression.

Unsupervised algorithms learn patterns in the data, without any form of ground truth. We can split these algorithms up based on what their purpose is. Unsupervised learning algorithms that can compress the information in a high-dimensional dataset into a lower dimensional representation are called dimension reduction algorithms. Unsupervised learning algorithms that find groups of cases that are more similar to each other than cases in other clusters, are called clustering algorithms.

We first encountered these definitions in section 1.2, all the way back in chapter 1. I've reproduced figure 1.5 here in figure 20.1, that summarizes the differences between supervised and unsupervised learning.