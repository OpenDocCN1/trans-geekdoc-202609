
# Scikit-learn: Machine Learning in Python 275

The important object is the cross-validation iterator, which provides pairs of train and test indices to split input data, for example K-fold, leave one out, stratified cross-validation.

**Model selection:** Scikit-learn can evaluate an estimator’s performance or select parameters using cross-validation, optionally distributing the computation to several cores. This is accomplished by wrapping an estimator in a GridSearchCV object, where the “CV” stands for “cross-validated”. During the call to fit, it selects the parameters on a specified grid, maximizing a score (the score method of the underlying estimator). predict, score, or transform are then delegated to the tuned estimator. This object can therefore be used transparently as any other estimator. Cross validation may be more efficient for certain estimators by exploiting specific properties, such as warm restarts or regularization paths (Friedman et al., 2010). This is supported through special objects, such as the Lasso. Finally, a Pipeline object can combine several transformers and an estimator to create a better estimator to, for example, apply dimension reduction before fitting. It behaves as a standard estimator, and GridSearchCV therefore tunes the parameters of all steps.

# HIGH-LEVEL YET EFFICIENT: SOME TRADEoffs

While scikit-learn focuses on ease of use, and is mostly written in a high level language, has been taken to maximize computational efficiency. In Table 1, we compare computation time for a few algorithms implemented in the major machine learning toolkits accessible in Python. We use the Madelon data set (Guyon et al., 2004), 4400 instances and 500 attributes, The data set is large, but small enough for most algorithms to run.

**SVM:** While all of the packages compared libsvm in the background, the performance of scikitlearn can be explained by two factors. First, our bindings avoid memory copies and have up to 40% less overhead than the original libsvm Python bindings. Second, we patch libsvm to improve efficiency on dense data, use a smaller memory footprint, and use better memory alignment and pipeling capabilities of modern processors. This patched version also provides unique features, such as setting weights for individual samples.

**LARS:** Iteratively refining the residuals instead of recomputing them gives performance gains of 2–10 times over the reference R implementation Hastie and Efron, 2004). Pymvpa uses this implementation via the Rpy R bindings and pays a heavy price to memory copies.

**Elastic Net:** We benchmark the scikit-learn coordinate descent implementations of Elastic Net. It achieves the same order of performance as the highly optimized Fortran version glmnet (Friedman et al., 2010) on medium-scale problems, but performance on very large problems is limited since we do not use the KKT conditions to define an active set.

**kNN:** The k-nearest neighbors classifier implementation constructs a ball tree (Omohundo, 1989) of the samples, but uses a more efficient brute force search in large dimensions.

**PCA:** For medium to large data sets, scikit-learn provides an implementation of a truncated PCA based on random projections (Rokhlin et al., 2009).

**k-means:** scikit-learn's k-means algorithm is implemented in pure Python. Its performance is limited by the fact that numpy's array operations take multiple passes over data.

# CONCLUSION

Scikit-learn exposes a wide variety of machine learning algorithms, both supervised and unsupervised, using a consistent, task-oriented interface, thus enabling easy comparison of methods for a given application. Since it relies on the scientific Python ecosystem, it can easily be integrated into applications outside the traditional range of statistical data analysis. Importantly, the algorithms, implemented in a high-level language, can be used as building blocks for approaches specific to a use case, for example, in medical imaging (Michel et al., 2011). Future work includes online learning, to scale to large data sets.

# Scikit-learn: Machine Learning in Python

# REFERENCES

- 1. D. Albanese, G. Merler, S. and Jurman, and R. Visintainer. MLPy: high-performance python package for predictive modeling. In NIPS, MLOSS Workshop, 2008.
- 2. C.C. Chang and C.J. Lin. LISVM: a library for support vector machines. http://www.csie.ntu.tw/cj/libsvm, 2001.
- 3. P.F. Dubois, Engineering. Python Batteries Included, volume 9 of Computing in Science & Engineering. IEEE/AIP, May 2007.
- 4. R.E. Fan, W. Chang, C.J. Hsieh, X.R. Wang, and C.J. Lin. LIBLINEAR: a library for large linear classification. The Journal of Machine Learning Research, 9:1871–1874, 2008.
- 5. J. Friedman, T. Hastie, and R. Tibshirani. Regularization paths for generalized linear models via coordinate descent. Journal of Statistical Software, 33(1):1, 2010.
- 6. I Guyon, S. R. Gunn, A. Ben-Hur, and D. Gror. Result analysis of the NIPS 2003 feature selection challenge, 2004.
- 7. M. Hanke, Y.O. Halchenko, P.B. Sederberg, S.J. Hanson, J.V. Hoxby, and S. Pollmann. MyPVA: A Python tool for multivariate analysis.
- 8. T. Hastie and E. Efron. Elastic Net. r-project/lars.
- 9. P. Michel, A. Behr, and F. Gehl. A supervised approach for fMRI. Neuroinformatics, 2011.
- 10. S. Omohindi. balltree construction. ICSI Technical Report TR-89-03.
- 11. V. Rokhlin. A randomized algorithm for principal component analysis. SIAM Journal on Matrix Analysis and Applications, 31(3):1100–1124, 2009.
- 12. S. Schaul, J. Widmer, and T. Schmiduber. PyBrain. Journal of Machine Learning Research, 11:743–746, 2010.
- 13. S. Sonnenburg, G. Ratsch, and C. Zen. SHUN machine learning toolbox. Journal of Machine Learning Research, 11:1799–1802, 2010.
- 14. S. Van der Walt, S.C Colbert, and G. Varoaux. The NumPy array: A structure for efficient numerical computation. Computing in Science and Engineering, 11, 2011.
- 15. T. Zito, N. Wilbert, L. Wiskott, and P. Berkes. Modular toolkit for data processing (MDP): A Python processing framework. Frontiers in Neuroinformatics, 2, 2008.
