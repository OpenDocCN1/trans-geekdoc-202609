+   2. Sampling without replacement.

+   3. This may be mostly a result of bagging, since in boosting we would have expected miss-correctly classified observations to repeatedly appear in subsequent samples.

# ### 6.3.2 Approaches for Combining Predictors

> **SOL-141** CH.SOL- 6.7.
An Algebraic weighted average for class probabilities.

> **SOL-142** CH.SOL- 6.8.
This is true. $[\ \hat{3}\ ]$ provides a mathematical proof.

> **SOL-143** CH.SOL- 6.9.
This is true. For extension, see instance $[\ \underset{\sim}{\hat{8}}\ ]$.

> **SOL-144** CH.SOL- 6.10.
This is true. In a bagging approach, we first randomly draw (with replacement), $K$ examples where $K$ is the size of the original training corpus therefore leading to an imbalanced representation of the instances.

# ### 6.3.3 Monolithic and Heterogeneous Ensembling

> **SOL-145** CH.SOL- 6.11.

1. **True** Due to their lack of diversity, an ensemble of monolithic architectures tends to perform worse than an heterogeneous ensemble.
2. **True** This has be consistently demonstrated in $[\ \text{\underline{11}},\ \text{\underline{5}}\ ]$.