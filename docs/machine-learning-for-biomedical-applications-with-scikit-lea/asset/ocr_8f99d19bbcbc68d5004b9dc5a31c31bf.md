# Machine Learning for Biomedical Applications

![](bbox=[0.143, 0.085, 0.832, 0.269])

**Figure 4.8** Nonlinear support vector classifiers. Left: linear SVC with polynomial feature transformation. Right: kernel SVC with radial basis function (Gaussian) kernel.

# 4.2.3 Polynomial support vector classifier

Some datasets cannot be separated using a linear decision boundary. For example, if we wish to distinguish patients with mild and severe heart failure based on EF and QRS, nonlinear classification will work better, as shown in Fig. 4.8.

Similarly to the regression (Sect. 3.3.1), a linear classifier can be turned into a non-linear classifier by the application of a nonlinear feature transformation $\phi$. The decision boundary will become

> $h(x) = w^T\Phi(x) + b,$

and or soft margin objectives can be applied exactly the same way as before. In scikit-learn we can implement this as a pipeline of the nonlinear feature transformation, in this case of a third degree, followed by linear SVC:

```
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import PolynomialFeatures
from sklearn.preprocessing import StandardScaler
from sklearn.svm import LinearSVC
model = Pipeline(
    ("poly_features",PolynomialFeatures(degree=3)),
    ("scaler",StandardScaler()),
    ("svc",LinearSVC()))
)
```

The fitted polynomial support vector classifier is shown in Fig. 4.8, left.

# 4.2.4 Kernel support vector classifier

Alternatively we can create a nonlinear support vector classifier by using a kernel trick. We have already introduced the kernel trick in the context of ridge regression in Sect. 3.3.2. We will first replace the parameter vector $\bf w$ with its dual representation