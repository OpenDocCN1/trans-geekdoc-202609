# 58 | Machine learning with sklearn

```
$$\sum_{i=1} \alpha_i y^{(i)} = 0. \quad (3.28)$
```

From this optimization problem it turns out that the $\alpha_i$ of only a few examples, those that are lying on the margin, are the only ones which have $\alpha_i \neq 0$. The corresponding training examples are called support vectors. The actual optimization can be done with several algorithms. John Platt developed the sequential minimal optimization (SMO) algorithm which is very efficient for this optimization problem. Please note that the optimization problem is convex and can be solved efficiently without the danger of getting stuck in local minima.

Once we find the support vectors with $\alpha_S$, we can calculate $w$ from Egn 3.24 and $b$ from a similar equation. Then, if we are a new input vector to be classified, then it can be calculated with the hyperplane Egn 3.13

```
$y = \begin{cases} 1 & \text{if} \sum_{i \in S} \alpha_i y^{(i)} x > 0 \ -1 & \text{otherwise} \end{cases} \quad (3.29)$
```

Since this is only over the support vectors, which should be only a few data points from the training set, classification becomes very efficient after training.

# 3.6.2 Soft margin classifier

Thus far have only discussed the linear separable case, but how about the case when there are overlapping classes? It is possible to extend the optimization problem by allowing some points to be in the margin by penalizing these points somewhat. We therefore include slack variables $\xi_i$, that reduce the effective margin for each data point, and add a penalty to the optimization that penalizes the sum of these slack variables is large,

```
$$\min_{w,b} \frac{1}{2}\|w\|^2 + C \sum \xi_i, \quad (3.30)$
```

subject to the constraints

```
$y^{(i)}(w^T x + b) \geq 1 - \xi_i \quad (3.31)\n\xi_i \geq 0 \quad (3.32)$
```

. The constant $C$ is free parameter in this algorithm. Making this large means fewer points to be in the margin. This parameter must be tuned and it is advisable to try to vary this parameter in order to verify that the results do not dramatically affect an initial choice.

# 3.6.3 Non-linear support vector machines

We have treated the case of overlapping classes while assuming that the best we can do is a linear separation. However, what if the underlying problem is separable with a function that might be more complex? An example is shown in Fig. 3.10. Nonlinear separation and regression models are of course much more common in machine learning, and we will now look into the non-linear generalization of the SVM.