To obtain different classifiers, we simply choose different kernel functions and compute \(\alpha_i\). Three useful kernel functions are the linear kernel,

```
\(k(\mathbf{x}_i, \mathbf{x}) = \mathbf{x}_i^T \mathbf{x},\) \quad (11.5.26)
```

the polynomial kernel, with expansion up to the \(d\)th power, given by

```
\(k(\mathbf{x}_i, \mathbf{x}) = (1 + \mathbf{x}_i^T \mathbf{x})^d,\) \quad (11.5.27)
```

and the radial basis function (RBF) kernel or Gaussian kernel,

```
\(k(\mathbf{x}_i, \mathbf{x}) = \exp(-\gamma(||\mathbf{x}_i - \mathbf{x}||^2).\) \quad (11.5.28)
```

The latter one, the Gaussian kernel, is the most popular and produces a non- linear decision boundary that is quite adept at capturing the true nature of the two classes. As a result, SVM is a powerful alternative to logistic regression. The approach also has certain robustness properties that make a comparison with rank-based methods appropriate. The decision boundary is constructed from only a few data points that belong to the two classes. These key points inside and around the two margins surrounding the boundary are the only ones that have non-zero \(\hat{\alpha}_i\) and they are called support vectors\(^1\). They act to support the decision boundary, and hence their name. All other points are irrelevant to the construction of the boundary, since their \(\hat{\alpha}_i = 0\), which makes it robust, albeit in a different sense than rank-based methods.

The RBF kernel has the property of decreasing in value as a function of the distance from a support vector that may produce highly irregular decision boundaries (i.e. it is exponential and depends on the \(\gamma\) parameter). SVM has an added advantage over LLR and RLR in that it does not require specification of all the various polynomial expansions of the variables to create the needed features. It will figure that out for itself from the original variables and data using the RBK function. However, the user must adjust two tuning parameters, \(\gamma\) and \(C\), to obtain satisfactory results.

The above description is meant simply to give the reader a conceptual understanding of SVMs and its connection to logistic regression. Implementation details are quite complex and beyond the scope of this book but many software packages are available that provide this capability. Again, the basic idea is to use so-called kernel functions to increase the feature space of support vector classifiers. These classifiers use a small number of observations, or support vectors, to define the decision boundary. Since SVMs are considered to be a state- of-the-art method, we will use it for comparison purposes and refer the reader to James et al. (2013) for further details.

1 The term “vector” is derived from the simple fact that all \(\mathbf{x}_i\) can be viewed as vectors in \(p\)-space.