# Soft Computing and Machine Learning with Python

+   - Support Vector Machine
- Quadratic Classifiers
- K-Means Clustering
- Boosting
- Decision Tree
- Random Forest
- Neural networks
- Bayesian Networks

**Linear Classifiers:** In machine learning, the goal of classification is to group items that have similar feature values, into groups. Timothy et al (Timothy Jason Shepard, 1998) stated that a linear classifier achieves this by making a classification decision based on the value of the linear combination of the features. If the input vector to the classifier is a real vector $\vec{x}$

```
$y = f(\vec{w} \cdot \vec{x}) = f\left(\sum_{j} w_j x_j\right)$
```

$\vec{w}$ is a real vector of weights and $f$ is a function that converts the dot product of the two vectors into the desired output. The weight vector $\vec{w}$ is learned from a set of labelled training samples. Often $f$ is a simple function that maps all values above a certain threshold to the first class and all values to the second class. A more complex $f$ might give the probability that an item belongs to a certain class.

For a two-class classification problem, one can visualize the operation of a linear classifier as splitting a high-dimensional input space with a hyperplane: all points on one side of the hyperplane are classified as “yes”, while the others are classified as “no”. A linear classifier is often used in situations where the speed of classification is an issue, since it is often the fastest classifier, especially when $\vec{x}$ is sparse. However, decision trees can be faster. Also, linear classifiers often work very well when the number of dimensions in $\vec{x}$ is large, as in document classification, where each element is typically the number of words in a document (so document-term matrix). In such cases, the classifier should be well-regularized.

+   **Support Vector Machine:** A Support Vector Machine as stated by Luis et al (Luis Gonz, 2005) (SVM) performs classification by constructing an Ndimensional hyper plane that optimally