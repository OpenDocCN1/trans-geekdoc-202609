# 10.1 The Gaussian mixture model and discriminant analysis

# LDA

# QDA

![](bbox=[0.115, 0.103, 0.467, 0.283])

![](bbox=[0.532, 0.103, 0.884, 0.283])

(a) Decision boundaries for the music classification problem for an LDA classifier.

(b) Decision boundaries for the music classification problem for a QDA classifier.

**Figure 10.4:** We apply an LDA and QDA classifier to the music classification problem from Example 2.1 and plot the resulting decision boundaries. Note that the LDA classifier has linear decision boundaries, whereas the QDA classifier has decision boundaries with quadratic shapes.

![](bbox=[0.135, 0.396, 0.862, 0.506])

**Figure 10.5:** We consider the same situation as in Figure 10.1, for the fact that we have "lost" the output for most of the data points. The problem is not semi-supervised. The unlabeled data points $(x_i, y_i)_{i=1}^{n_u}$ are illustrated in the left panel as gray, where the $n_l=6$ labeled data points are red or blue. In the right panel we have learned a GMM using only the unlabeled data points, as if problem was solved without $n_l$ data points. Clearly the unlabeled data points have made the problem harder, compared to Figure 10.1. We will, however, continue this story in Figure 10.6 where we use this as an initialization to a semi-supervised procedure.

Intuitively, the unlabeled inputs can be used to find groups (or clusters) of values with properties that can be assumed to belong to the same class. Looking at Figure 10.5 again, by considering the unlabeled data points (gray) it is reasonable to assume that the two clusters of points correspond to the two classes (red and blue, respectively). As we will see, by including this information we can obtain better estimates of the class-conditional distributions $p(x|y)$ and thereby obtain a better classifier.

We will now turn to the technical details of how to learn the GMM in this semi-supervised setting. Similarly to above we use the maximum likelihood approach, meaning that we maximize the likelihood of the observed data. To the supervised case, however, the observed data contains both labeled and unlabeled instances, as that would be like to

```
$$\theta = \arg\max_{\theta} p(\{x_i, y_i\}_{i=1}^{n_l}, \{x_j\}_{j=1}^{n_u} | \theta)$
```

Unfortunately this problem has no closed-form solution for the GMM. We will discuss the reason for this intractability in more detail in Section 10.2, where we revisit the same problem in the fully unsupervised setting. Intuitively, we will conclude that it is not possible to compute the model parameters as in (10.3), because we do not know which the unlabeled data points belong to. Hence,