

# Scikit-learn: Python 中的机器学习 275

重要的对象是交叉验证迭代器，它提供训练和测试索引对以划分输入数据，例如 K折交叉（K-fold）、留一（leave one out）、分层交叉验证。

**模型选择：** Scikit-learn 可以使用交叉验证评估估计器的性能或选择参数，并可选地将计算分布到多个核心。这是通过将估计器封装在 `GridSearchCV` 对象中实现的，其中“CV”代表“交叉验证”（cross-validated）。在调用 `fit` 时，它会在指定的网格上选择参数，使得分最大化（底层估计器的 `score` 方法）。随后，`predict`、`score` 或 `transform` 将委托给调优后的估计器。因此，该对象可以透明地作为任何其他估计器使用。通过利用特定属性（如热重启或正则化路径），交叉验证对于某些估计器可能更高效（Friedman et al., 2010）。这通过特殊对象（如 Lasso）得到。最后，`Pipeline` 对象可以将多个转换器和一个估计器结合以创建一个更好的估计器，例如在拟合之前应用降维。它的行为类似于标准估计器，因此 `GridSearchCV` 会调优所有步骤的参数。

# 高级且高效：一些权衡

虽然 scikit-learn 专注于易用性，且大部分用高层语言编写，但它为了最大化计算效率进行了优化。在表 1 中，我们比较了 Python 中可用的主流机器学习工具包中实现的几种算法的计算时间。我们使用了 Madelon 数据集（Guyon et al., 2004），包含 4400 个实例和 500 个属性。该数据集很大，但足够让大多数算法运行。

**SVM：** 虽然所比较的所有包在后台都使用了 `libsvm`，但 scikit-learn 的性能可以用两个因素解释。首先，我们的绑定避免了内存拷贝，开销比原始的 `libsvm` Python 绑定少达 40%。其次，我们修补了 `libsvm` 以提高在密集数据上的效率，使用了更小的内存占用，并利用了现代处理器更好的内存对齐和流水线。。修补版本还提供了独特的功能，例如为单个样本设置权重。

**LARS：** 通过迭代精炼残差而不是重新计算它们，相比参考的 R 实现获得了 2-10 倍的性能（Hastie and Efron, 2004）。Pymvpa 通过 Rpy 绑定使用此实现，但为内存拷贝付出了沉重代价。

**Elastic Net：** 我们对 scikit-learn 的坐标下降 Elastic Net 实现进行了基准测试。在中等规模问题上，它的性能与高度优化的 Fortran 版本 `glmnet`（Friedman et al., 2010）同一数量，但在大型问题上性能受到限制，因为我们没有使用 KKT 条件来定义活动集。

**kNN：** k 最近邻分类器的实现构建了样本的球树（Omohundo, 1989），但在高维空间中使用更高效的暴力搜索。

**PCA：** 对于中、大型数据集，scikit-learn 提供了一种基于随机投影的截断 PCA 实现（Rokhlin et al., 2009）。

**k-means：** scikit-learn 的 k-means 算法是用纯 Python 实现的。其性能受限于 numpy 数组操作会对数据进行多次遍历的事实。

# 结论

Scikit-learn 使用一致的、面向任务的接口暴露了广泛的机器学习算法（包括监督和无监督学习），从而能够针对特定应用轻松地比较各种方法。由于它依赖于科学 Python 生态系统，它可以轻松集成到传统统计数据分析范围之外的应用中。重要的是，这些用高层语言实现的算法可以作为特定用例方案的构建块，例如在医学影像中（Michel et al., 2011）。未来的工作包括在线学习，以扩展到大数据集。

# Scikit-learn: Python 中的机器学习

# 参考文献

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

