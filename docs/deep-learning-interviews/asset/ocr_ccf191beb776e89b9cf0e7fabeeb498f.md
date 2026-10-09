*You are provided with a pure Python code implementation of the Manhattan distance function (8.51):*

```
from scipy import spatial
x1 = [ 6 , 1 , 4 , 5]
x2 = [ 2 , 8 , 3 , -1]
cityblock = spatial.distance.cityblock(x1,x2)
print ("Manhattan:", cityblock)
```

![](bbox=[0.25, 0.28, 0.72, 0.31])

*In many cases, and for large vectors in particular, it is better to use a GPU for implementing numerical computations. PyTorch has full support for GPU's (and its my favourite DL library ...), use it to implement the Manhattan distance function on a GPU .*

# **PRB-266** ? **CH.PR B-8.90.**

*Your friend is training a logistic regression model for a binary classification problem using the L2 loss for optimization. Explain to him why this is a bad choice and which loss he should be using instead .*

# 8.3 Solutions

# 8.3.1 Cross Validation

On the significance of cross validation and stratification in particular, refer to “*A study of cross-validation and bootstrap for accuracy estimation and model selection*” [17] .

CV approaches

# **SOL-177** ✎ **CH.SOL-8.1.**

*The first approach is a leave-one-out CV (LOOCV) and the second is a K-fold cross-validation approach .*