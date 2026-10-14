
## Part 2
### Supervised learning

In the second part of the book, we will cover supervised learning algorithms. Supervised learning algorithms contain labeled examples as part of the training dataset and consist of two main classes, depending on the discrete or continuous nature of the quantity we are trying to predict: classification and regression. Supervised learning algorithms are widely used in machine learning, and we’ll be deriving some of the most exciting algorithms from scratch, to build our experience with fundamentals and motivate the design of new ML algorithms.

In chapter 5, we’ll focus on classification algorithms and derive several classic algorithms, including the perceptron, SVM, logistic regression, naive Bayes, and decision trees.

In chapter 6, we’ll study four intriguing regression algorithms: Bayesian linear regression, hierarchical Bayesian regression, KNN regression, and Gaussian process regression. We’ll derive all algorithms from the first principles and implement them using best practices.

In chapter 7, we’ll investigate a selected set of supervised learning algorithms, including Markov models, such as page rank algorithms and hidden Markov models; imbalanced learning strategies; active learning; Bayesian optimization for hyperparameter selection; and ensemble methods. We’ll conclude with ML research, focusing on supervised learning.

## Classification algorithms

![](img/325742126d3ff007c6c385f4ffb5c3be_93_0.png)

### This chapter covers

- Introducing classification
- The perceptron algorithm
- The SVM algorithm
- SGD logistic regression
- The Bernoulli naive Bayes algorithm
- The decision tree (CART) algorithm

In the previous chapter, we looked at the computer science fundamentals required to implement ML algorithms from scratch. In this chapter, we focus on supervised learning algorithms. Classification is a fundamental class of algorithms and is widely used in machine learning. We will derive from scratch and implement several selected classification algorithms to build our experience with fundamentals and motivate the design of new ML algorithms. The algorithms in this chapter were selected because they illustrate important algorithmic concepts and expose the reader to progressively more complex scenarios that can be implemented from scratch. These concepts have wide application, including email spam detection, document classification, and customer segmentation.

### 5.1 Introduction to classification

In supervised learning, we are given a dataset D = {(x₁, y₁), ..., (xₙ, yₙ)}, consisting of tuples of data x and labels y. The goal of a classification algorithm is to learn a mapping from inputs x to outputs y, where y is a discrete quantity (i.e., y ∈ {1, ..., K}). If K = 2, we have a binary classification problem, while for K > 2, we have multiclass classification.

A classifier h can be viewed as a mapping between a d-dimensional feature vector φ(x) and a k-dimensional label y (i.e., h: Rᵈ → Rᵏ). We often have several models to choose from; let’s call this set of classifier models H. Thus, for a given h ∈ H, we can obtain a prediction y = h(φ(x)). We are typically interested in predicting new or unseen data—in other words, our classifier h must be able to generalize to new data samples.

Finding the right classifier is known as model selection. We want to choose a model that has a sufficient number of parameters (degrees of freedom) to avoid underfitting or overfitting to training data, as shown in figure 5.1.

![](img/325742126d3ff007c6c385f4ffb5c3be_94_0.png)

Figure 5.1 Model selection to avoid overfitting or underfitting to training data

For model classes H = [1, 2, 3], training and test loss functions are both decreasing, which indicates that there’s more capacity to learn; as a result, these models underfit the data. For model classes H = [6, 7, 8], the training loss decreases while the test loss is starting to increase, which indicates that we are overfitting the data.

### 5.2 Perceptron

Let’s start with the most basic classification model: a linear classifier. We’ll be using the perceptron classifier on the iris dataset. We can define a linear classifier as shown in equation 5.1.

```
h(x; θ) = sign(θ₁x₁ + ⋯ + θ_d x_d + θ₀)
          = sign(θ · x + θ₀) = { +1  if θ · x + θ₀ ≥ 0
                                   -1  if θ · x + θ₀ < 0 }  (5.1)
```

Notice how the sign function of the inner product between the parameter θ and the feature input x maps to ±1 labels. Geometrically, θ·x + θ₀ = 0 describes a hyperplane in d-dimensional space uniquely determined by the normal vector θ. Any point that lies on the same side as the normal θ is labeled +1, while any point on the opposite side is labeled −1. As a result, θ·x + θ₀ = 0 represents the decision boundary. Figure 5.2 illustrates these concepts in 2 dimensions.

![](img/325742126d3ff007c6c385f4ffb5c3be_95_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_95_1.png)

Figure 5.2 Linear classifier and a decision boundary

How do we measure the performance of this classifier? One way is to count the number of mistakes it makes compared to ground truth labels y. We can count the number of mistakes as follows.

E_n(θ) = 1/n Σ_{i=1}^n [[y_i ≠ h(x_i;θ)]] = 1/n Σ_{i=1}^n [[y_i(θ·x_i + θ_0) ≤ 0]]  (5.2)

Here, [[•]] is an indicator function, which is equal to 1 when the expression inside is true and 0 otherwise. Notice in equation 5.2, a mistake occurs whenever the label y_i ∈ [+1,−1] disagrees with the prediction of the classifier h(x_i;θ) ∈ [+1,−1] (i.e., their product is negative).

Another way to measure the performance of a binary classifier is via a confusion matrix.

|          | Actual |      |
|----------|--------|------|
|          | y = 1  | y = 0|
| Predicted|        |      |
| ŷ = 1    | TP     | FP   |
| ŷ = 0    | FN     | TN   |

Figure 5.3 Confusion matrix for a binary classifier

In the ROC plot on the left of figure 5.4, TPR stands for true positive rate and can be computed as follows: TPR = TP / (TP + FN). We can also compute the false positive rate

![](img/325742126d3ff007c6c385f4ffb5c3be_96_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_96_1.png)

Figure 5.4 Receiver operating characteristic (ROC) plot (left) and precision-recall plot (right)

(FPR) as FPR = FP / (FP + TN). By varying our classification threshold, we get different points along the ROC curve. Perfect classification results in TPR = 1 and FPR = 0; in reality, the closer we are to the upper-left corner, the better the classifier will be. At the chance level, we get the diagonal TPR = FPR line. The quality of ROC curve is often summarized by a single number using the area under the curve or AUC. Higher AUC scores are better, with a maximum of AUC = 1.

In information retrieval, it is common to use a precision-recall plot, as shown on the right-hand side of figure 5.4. The precision is defined as Precision = TP / (TP + FP), and the recall is defined as Recall = TP / (TP + FN). A precision-recall curve is a plot of precision versus recall as we vary the classification threshold. The curve can be summarized by a single number using the mean precision by averaging over the recall values, which approximates the area under the curve. Additionally, for a fixed threshold, we can summarize performance in a single statistic, called the F1 score, which is the harmonic mean of precision and recall: F1 = 2PR / (P + R).

Perceptron is a mistake-driven algorithm: it starts with θ=0 and successively adjusts the parameter θ for each training example until there are no more classification mistakes, assuming the data is linearly separable. The perceptron update rule can be summarized as follows.

```
if y_i ≠ h(x_i; θ^(k)) then
θ^(k+1) = θ^(k) + y_i x_i
θ_0^(k+1) = θ_0^(k) + y_i
(5.3)
```

Here, index k denotes the number of times the parameter updates (aka the number of mistakes). You can think of a θ0 update as similar to a θ update but with x = 1. If the training examples are linearly separable, then the perceptron algorithm in equation 5.3 converges after a finite number of iterations. Notice that the order of input data points makes a difference in how parameter θ is learned; therefore, we can randomize (shuffle) the training dataset. In addition, we can introduce a learning rate to help with θ convergence—the properties of which we’ll discuss following the implementation. The perceptron algorithm can be summarized in the pseudo-code in figure 5.5.

The code consists of Perceptron class with two functions: fit and predict. In the fit function, we take the training data X and labels y, and upon encountering an error (in which case, the if statement condition is true), we update the learning rate and update theta, as derived previously. Finally, in the predict function, we make a prediction for test data based on the sign of the decision boundary.
