
## 7.8 Classification trees

Classification trees are based on a simple yet powerful idea, and they are among the most popular techniques for classification. They are *multistage* systems, and classification of a pattern into a class is achieved *sequentially*. Through a series of tests, classes are *rejected* in a sequential fashion until a decision is finally reached in favor of one remaining class. Each one of the tests, whose outcome decides which classes are rejected, is of a *binary* “Yes” or “No” type and is applied to a *single* feature. Our goal is to present the main philosophy around a special type of trees known as *ordinary binary classification trees* (OBCTs). They belong to a more general class of methods that construct trees, both for classification and for regression, known as *classification and regression trees* (CARTs) [2,31]. Variants of the method have also been proposed [35].

The basic idea around OBCTs is to partition the feature space into (*hyper*)*rectangles*; that is, the space is partitioned via hyperplanes, which are parallel to the axes. This is illustrated in [Fig. 7.12](#Chp007_293-342_B9780443292385000135.xhtml#f0075). The partition of the space in (hyper)rectangles is performed via a series of “questions” of this form: is the value of the feature `x[i] < a`? This is also known as the *splitting criterion*. The sequence of questions can nicely be realized via the use of a tree. [Fig. 7.13](#Chp007_293-342_B9780443292385000135.xhtml#f0080) shows the tree corresponding to the case illustrated in [Fig. 7.12](#Chp007_293-342_B9780443292385000135.xhtml#f0075). Each node of the tree performs a test against an *individual* feature, and if it is not a leaf node, it is connected to two *descendant* nodes: one is associated with the answer “Yes” and the other with the answer “No.”

![Figure 7.12 Partition of the two-dimensional features space, corresponding to three classes, via a classification (OBCT) tree.](images/B9780443292385000135/gr012.jpg)

Figure 7.12 Partition of the two-dimensional features space, corresponding to three classes, via a classification (OBCT) tree.

![Figure 7.13 The classification tree that performs the space partitioning for the task indicated in Fig. 7.12.](images/B9780443292385000135/gr013.jpg)

Figure 7.13 The classification tree that performs the space partitioning for the task indicated in [Fig. 7.12](#Chp007_293-342_B9780443292385000135.xhtml#f0075).

## Remarks 7.5

*   If `J3` is used with other matrix combinations, as might be achieved by using `Σ[m]` in place of `Σ[b]`, the constraint of the rank being equal to `M - 1` is removed, and larger values for `m` can be obtained.
*   In a number of practical cases, `Σ[w]` may not be invertible. This is, for example, the case in the *small sample size* problems, where the dimensionality of the feature space, `l`, may be larger than the number of the training data, `N`. Such problems may be encountered in applications such as web document classification, gene expression profiling, and face recognition. There are different escape routes in this problem; see [38] for a discussion and related references.

## Fisher's Method and Dimensionality Reduction

*   In other words, there is no loss of information (as measured via the `J3` criterion) by reducing the dimension from `l` to `M - 1`. Note that in this case, Fisher's method produces `m = M - 1` discriminant (linear) functions. This complies with a general result in classification stating that the minimum number of discriminant functions needed for an `M`-classification problem is `M - 1` [38]. Recall that in Bayesian classification, we need `M` functions, `P(ω[i]|x)`, `i = 1, 2, …, M`; however, only `M - 1` of those are independent, because they must all add to one. Hence, Fisher's method provides the minimum number of linear discriminants required.
*   `m < M - 1`. If `A` is built having as columns the eigenvectors corresponding to the maximum `m` eigenvalues, then `J3y < J3x`.
*   However, the resulting value `J3y` is the maximum possible one.
