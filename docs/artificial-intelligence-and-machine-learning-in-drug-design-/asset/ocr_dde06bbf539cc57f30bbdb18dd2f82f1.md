presupposes a linear decision boundary and feature independence, limiting its performance in non-linear instances and correlated feature relationships. It is intended primarily for binary classification, but it can be expanded to multiclass situations. Furthermore, extreme outliers and non-numerical data can have an impact on its performance. Understanding these advantages and disadvantages is critical when deciding whether logistic regression is appropriate for given tasks and datasets [67].

# 4.3.3 Naive Bayes

The naive Bayes (NB) algorithm is grounded in the Bayes theorem, which computes the posterior probability of each class based on the feature vectors and their prior probabilities. In this model, the joint distribution of feature vectors and class labels is considered. The model uses the posterior probability to make a decision, assuming that the features are mutually independent [76]. The NB approach calculates the posterior probability as follows:

```
argmax_y P(Y = y | X_1 = x_1, ..., X_n = x_n)
∝ argmax_y P(Y = y) ∏_{i=1}^n P(F_i = x_i | Y = y) =
```

The predicted class, denoted by Y, is determined by the maximum posterior probability, and P is the probability. Further mathematical information on naive Bayes can be found in the work [15, 76].

The NB machine learning algorithm is well known for its superior performance in multi-class prediction tasks. It is simple to use and very effective. It continues to be extensively used and has been utilized in biological informatics since 1961. Naive Bayes' interpretability, which enables us to understand how each feature contributed to the final prediction, is one of its significant benefits. It is essential to be aware, however, that Naive Bayes is based on the assumption that all input features are independent, which may not be the reality in actual datasets. When working with complex data, this assumption may limit its usefulness [15].

# 4.3.4 k-Nearest Neighbors

The k-nearest neighbors (k-NN) algorithm, introduced by Cover and Hart in 1967, belongs to the category of instance-based machine learning methods that retain all training samples [75]. When predicting for a test sample, k-NN directly examines the associations between the test data and instances in the training dataset to determine the result [65]. For a specific test dataset sample x̃_test, its k-nearest neighbors are identified by the data samples x̃_1, x̃_2, ..., x̃_k that have the k smallest distances (computed using a distance metric). The final outcome is obtained by:

```
y(x̃_test) = D([y(x̃_1), y(x̃_2), ..., y(x̃_k)])
```