![](bbox=[0.147, 0.085, 0.852, 0.513])

Figure 8-11. Kernel PCA and the reconstruction pre-image error

You may be wondering how to perform this reconstruction. One is to train a supervised regression model, with the projected instances as the training set and the original instances as the targets. Scikit-Learn do this automatically if you set fit_inverse_transform=True, as shown in the following code:

```
rbf_pca = KernelPCA(n_components = 2, kernel="rbf", gamma=0.0433,
X_reduced = rbf_pca.fit_transform(X)
X_preimage = rbf_pca.inverse_transform(X_reduced)
```

> By default, fit_inverse_transform=False and KernelPCA has no inverse_transform() method. This method only gets created when you set fit_inverse_transform=True.

+   7 Scikit-Learn uses the algorithm based on Kernel Ridge Regression described in Gokhan H. Bakır, Jason Weston, and Bernhard Scholkopf, "Learning to Find Pre-images" (Tübingen, Germany: Max Planck Institute for Biological Cybernetics, 2004).