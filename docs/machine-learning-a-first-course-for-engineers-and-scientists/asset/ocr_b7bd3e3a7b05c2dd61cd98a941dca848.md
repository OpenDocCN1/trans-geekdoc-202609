![](bbox=[0.14325, 0.07934999999999999, 0.85675, 0.43955])

Figure 5.2: Comparison of some common loss functions for classification, plotted as a function of the margin.

# # Multiclass classification

So far we have only discussed the binary classification problem with $M = 2$. The cross-entropy (equivalently, negative log-likelihood) is straightforward to generalize to the multiclass problem, that is $M > 2$, as we did in Chapter 3 for logistic regression. This is a useful property of the likelihood-based loss, as it allows us to treat both binary and multiclass classification in the coherent framework.

Generalizing the other loss functions discussed above requires a generalization of the margin to the multiclass problem. This is possible but we do not elaborate on it in this book. Instead we mean a pragmatic approach which is to reformulate the margin as several binary problems. This reformulation can be done using a one-versus-all or one-versus-one scheme.

The one-versus-rest (or one-versus-all or binary relevance) idea is to train $M$ binary classifiers. Each classifier in this scheme is trained for predicting one class against all the classes. To make a prediction for a test point, all $M$ classifiers are used, and the class, which is predicted with the largest margin is then the predicted class. This approach is a pragmatic solution, which may turn out to work for some problems.

The one-versus-one idea is to train classifiers for each pair of classes. If there are $M$ classes in total, there are $rac{1}{2}M(M-1)$ pairs. To make a prediction each classifier predicts of its two classes, and the class which obtains most "votes" is chosen as the final prediction. The predicted margins can be used to break a tie if it happens. Compared to one-versus-rest, the one-versus-one approach has the disadvantage of involving $rac{1}{2}M(M-1)$ classifiers, instead of $M$. On the other hand each of these classifiers is trained on smaller datasets (only the data points that belong to either of the classes) compared to one-versus-rest which uses the entire training dataset for all $M$ classes