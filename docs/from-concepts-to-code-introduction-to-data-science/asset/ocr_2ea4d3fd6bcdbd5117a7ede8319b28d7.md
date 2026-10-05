Advanced Machine Learning Models

347

+   5. From the pairs $(\lambda_i, MSE)$, select the $\lambda_i$ with lowest value $MSE$. 
This yields the optimal value $\lambda^*$.

+   6. The final model is the version with regularization value $\lambda^*$

For a more accurate $\lambda^*$, a finer grid can be used in the first step after the MSEs are observed from the original course grid. Modern software packages support Lasso regression, as well the popular variants Ridge regression and elastic regularization. For more details on regularization, you might consult [4].

# 18.3 Advanced Machine Learning Models

Concurrent with strengthening the building blocks, I encourage you to explore and learn more classes of models. We studied regression models as they are prevalent, interpretable, and relatively simple in their architecture. For some data sets and use cases, other models will perform better. Two model classes which are extremely important *tree-based models* and *artificial neural networks*. A brief overview will be provided next, and I recommend other sources for details, as [4] and [49]. The latter provides an applied treatment with implementation in Python.

# 18.3.1 Tree-Based Models

Tree-based models are built up from the intuitive construct of a *decision tree*. Each tree forms a hierarchy, with a root at the top and branches emanating from the root and each node in the tree. For a pair of nodes connected by a branch, there is a parent-child relationship where the parent is higher in the tree. The terminating nodes at the bottom of the tree are the leaves. These leaves represent useful predictors, while the branches represent conditions on these predictors (e.g., if *age<20*, go left). A predictor is useful if it separates the observation target values into groups which increase *purity*, where purity is defined by a metric such as *entropy*. A 50/50 separation would have highest entropy (lowest purity).

![](bbox=[0.238, 0.693, 0.762, 0.803])