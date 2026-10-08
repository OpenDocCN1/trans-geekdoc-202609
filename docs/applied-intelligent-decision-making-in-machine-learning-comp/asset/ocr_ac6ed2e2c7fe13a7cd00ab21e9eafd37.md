# Decoding Common Machine Learning Methods

Classification models are employed if the outcome variable is categorical, and regression models are used if continuous. Practical machine learning applications predominantly use supervised classification. The agricultural application datasets used in this chapter (soybean, aphids, and weed species) have a categorical output variable. Therefore, common supervised ML algorithms, such as LDA and kNN, were considered, methods developed and based on their algorithms, and discussed.

# 2.3.7 Linear Discriminant Analysis

The LDA is a popular technique for dimensionality reduction and supervised classification was originally developed to address the two-class problem (Fisher, 1936). It provides two regions separated by a line which aids in the classification of data and the regions, and the separation line is defined by the linear discriminant score function. This method was later generalized for multiclass problems (Rao, 1948). A linear discriminant score function is employed by the LDA method to predict the class labels following the test data instance. The discriminant score function is derived from Bayes theorem, which determines the class labels based on the probability of each class and the probability of the test data belonging to the class (2.14).

```
$P(\pi|\vec{x})=\frac{P(\pi,\vec{x})}{P(\vec{x})}$
```

where $P(\pi|\vec{x})$ is the probability of test data instance $\vec{x}$ belonging to $\pi$ class, $P(\pi,\vec{x})$ is the joint probability of $\pi$ and $\vec{x}$, and $P(\vec{x})$ is the prior probability of $\vec{x}$. The linear discriminant score function of Bayes theorem is expressed in the form of $y=ax+b$, where $a$ and $b$ are the parameters obtained from the training data and $x$ is the test data instance. A detailed derivation of linear score function from Bayes theorem can be found elsewhere (Konishi, 2014; Naik and Kiran, 2019). The linear discriminant score function for the class $i$ ($L_i$) is given as:

```
$L_i=-\frac{1}{2}\vec{\mu}_i^T\Sigma^{-1}\vec{\mu}_i+\vec{x}^T\Sigma^{-1}\vec{x}+log p_i$
```

where $\vec{\mu}_i$ is the mean vector of each class in the training dataset, $\Sigma$ is the covariance matrix of each class in the training dataset, $\vec{x}$ is the test data instance, and $p_i$ is the prior probability of each class $i$. Some of the major assumptions of performing LDA are: (i) the training and test data are normally distributed, and (ii) the covariance matrix of each class is equal. However, in reality, the covariance matrix of classes is not equal, therefore to account for the variances in the dataset, a pooled covariance matrix ($\hat{S}_p$) is considered instead.

```
$\hat{S}_p=\frac{\sum_{i=1}^m(n_i-1)\Sigma_i}{\sum_{i=1}^m(n_i-1)}$
```