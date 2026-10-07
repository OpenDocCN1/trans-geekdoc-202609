The problem was: since the logistic regression model is a linear classifier then it has to be a straight line, it cannot generate curve. So it cannot separate the Green-points and Red-points properly (notice the figure).

✎ It can't make some kind of curve to catch some green users that are in the green region. Right now we're in the red region as well as some Green-points in the red region. This clearly reflects the fact that our data is not linearly separable. Those users are not in the region.

The solution is to use a non-linear classifier, i.e. KNN, SVM or Naive-Bayes or Random-Forest. But we are not gonna do this, we'll use Kernel-PCA to keep this straight line as a prediction boundary of the Logistic regression linear classifier.

# 10.11 Kernel-PCA in Python: Part 2: Kernel-PCA with Logistic Regression

Since we're going to use kernel-PCA, this will apply kernel trick to map the data to a higher dimension and then apply PCA to extract new components that will be new dimensions that explain the most variants.

✎ It'll manage to get some new dimensions in which the data will be linearly separable by a linear classifier like logistic regression.

Now we are going to apply kernel PCA inside of this Logistic linear classifier to see how kernel-PCA will save the situation. We will observe how the kernel PCA managed to extract PCs from non linearly separable data.

✎ We need to apply PCA after the data preprocessing phase and just before fitting our classifier (building classification model) using logistic regression to our training-set.

✎ We'll use Kernel class from sklearn.decomposition.

Then we create an object of this kernelPCA class naming dcomposer_kr_PCA.
Parameters: We use n_components=2 because we have 2-independent variables.

✎ And we need to choose the kernel because Kernel-PCA will use a kernel trick to our data-set. We will choose kernel="rbf".
Here we have kernel parameter which is exactly similar to Kernel-SVM, we have the same options. Here we choose 'rbf' that represents Gaussian RBF kernel

```
from sklearn.decomposition import KernelPCA
dcomposer_kr_PCA = KernelPCA(n_components=2, kernel="rbf")
```

Gaussian RBF kernel

![](bbox=[0.193, 0.617, 0.773, 0.786])

✎ When we apply PCA to our data set, our data set will be mapped to a higher dimension where the kernel trick will already create some new dimensions in a feature space where the data is linearly separable. (You can revisit Kernel-SVM for more).

✎ And since we are in this new feature space where the data is linearly separable PCA will be applied to reduce the dimensionality by extracting the principal components.

```
# Kernel-PCA: Unsupervised
from sklearn.decomposition import KernelPCA
dcomposer_kr_PCA = KernelPCA(n_components=2, kernel="rbf")
X_train = dcomposer_kr_PCA.fit_transform(X_train)
X_test = dcomposer_kr_PCA.transform(X_test)
```