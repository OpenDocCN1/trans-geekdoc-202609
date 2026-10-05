At last, we have formulated the hard-margin SVM optimization problem! Using the notation $w$ and $b$, the objective of hard-margin SVMs is

```
$$\min_{w,b} \frac{1}{2}\|w\|^2_2$
$\text{s.t.} \quad y_i(w^T x_i - b) \geq 1 \quad \forall i$\quad (6.5)$
```

# Soft-Margin SVMs

The hard-margin SVM optimization problem has a unique solution only if the data is linearly separable, but it has no solution otherwise. This is because the constraints are impossible to satisfy if we can't draw a hyperplane that separates the +1s from the -1s. In addition, hard-margin SVMs are very sensitive to outliers – for example, if our data is class-distributed Gaussian such that the two Gaussians are far apart, if we witness an outlier from class +1 that crosses into the typical region for class -1, then hard-margin SVM will be forced to compromise on a more generalized fit in order to accommodate this point. Our goal is to come up with a classifier that is not sensitive to outliers and can work even in the presence of data that is not linearly separable. To this end, we will talk Soft-Margin SVMs.

A soft-margin SVM modifies the constraints from the hard-margin SVM by allowing some points to violate the margin. Formally, it introduces slack variables $\xi_i$, for each training point, the constraints:

```
$y_i(w^T x_i - b) \geq 1 - \xi_i$\n$\xi_i \geq 0$
```

which is a less-strict, softer version of the hard-margin SVM constraints because it says that each point $x_i$, need only be a "distance" of $1-\xi_i$ of the separating hyperplane instead of a hard "distance" of 1.

(By the Greek, the Greek letter $\xi$ is spelled "xi" and pronounced "zai". $\xi_i$ is pronounced "zai-eye\). These constraints would be fruitless if we didn't bound the values of the $\xi_i$'s, because by setting them to large values, we are essentially saying that any point may violate the margin by an arbitrarily large distance...which makes our choice of w meaningless. We modify the objective function to:

```
$$\min_{w,b} \frac{1}{2}\|w\|^2 + C \sum_{i=1}^n \xi_i$
```

Where $C$ is a hyperparameter tuned through cross-validation. the soft-margin SVM optimization problem is

```
$$\min_{w,b} \frac{1}{2}\|w\|^2 + C \sum_{i=1}^n \xi_i$\n$\text{s.t.} \quad y_i(w^T x_i - b) \geq 1 \quad \forall i$\n$\xi_i \geq 0 \quad \forall i$\quad (6.6)$
```

The table below compares the effects of having a large $C$ versus a small $C$. As $C$ goes to infinity, the penalty for having non-zero $\xi_i$ goes to infinity, and thus forces the $\xi_i$'s to be zero, which is exactly the setting of the hard-margin SVM.