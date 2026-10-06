using Pandas. Calculate the accuracy of this classifier, the recall for each class, and the average recall. Discuss the performance of the classifier.

# 4.2. Support vector classifier

The Support Vector Classifier (SVC) is a large margin classifier that aims not only to find the decision boundary that correctly splits the samples but also results in the largest separation of the classes. In this section we will introduce the hard-margin and soft-margin support vector classifiers and the kernel trick for nonlinear classification.

# 4.2.1 Hard-margin support vector classifier

In classification problems where the two classes are linearly separated, there is no unique solution. The hard-margin classifier (Fig.4.6 left) will choose the decision boundary with the largest distance from the samples of both classes. The decision boundary is determined by **support vectors**, the samples that lie on the margins. In Fig. 4.6 the margins are shown by dashed lines and the support vectors by pink circles.

![](bbox=[0.166, 0.446, 0.833, 0.638])

**Figure 4.6** Hard-margin and soft-margin support vector classifiers.

The decision function is a multivariate linear function

```
$h(\mathbf{x}) = \mathbf{w}^T\mathbf{x} + b.$
```

This formulation is equivalent to the formulation in Eq. (4.1), except that the intercept is denoted by $b$ rather than $u_0$. The decision boundary is determined by

```
$h(\mathbf{x}) = 0,$
```

while margins are defined as

```
$h(\mathbf{x}) = \pm1.$
```