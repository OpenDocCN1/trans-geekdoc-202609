# Nonlinear SVM Classification

Although linear SVM classifiers are efficient and work surprisingly well in many cases, many datasets are not even close to being linearly separable. One approach to handling nonlinear datasets is to add more features, such as polynomial features (as you did in Chapter 4); in some cases this can result in a linearly separable dataset. Consider the left plot in Figure 5-5: it represents a simple dataset with one feature $x_1$. This dataset is not linearly separable, as you can see. If you add a second feature $x_2 = (x_1)^2$, the resulting 2D dataset is perfectly linearly separable.

![](bbox=[0.148, 0.263, 0.852, 0.463])

Figure 5-5. Adding features to make a dataset linearly separable

To implement this using Scikit-Learn, you can create a Pipeline containing a PolynomialFeatures transformer (discussed in "Polynomial Regression" on page 130), followed by a StandardScaler and a LinearSVC. Let's test this on the moons dataset: this is a toy for binary classification in which the data points are shared as interleaving half circles (see Figure 5-6). You can generate this dataset using the `make_moons()` function:

```
from sklearn.datasets import make_moons
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import PolynomialFeatures

polynomial_svm_clf = Pipeline([
    ('poly_features'
```