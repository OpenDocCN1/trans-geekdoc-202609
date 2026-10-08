# Multi-Criteria Decision-Making with Machine Learning

![](bbox=[0.198, 0.09, 0.804, 0.363])

**FIGURE 3.4** The role of the kernel.

![](bbox=[0.248, 0.433, 0.778, 0.673])

**FIGURE 3.5** Linear regressions with the range of epsilon.

In SVR, the initial step involves transforming the input variable x into a m-dimensional feature space through a nonlinear mapping function. After this transformation, a linear model is developed within this higher-dimensional space. The construction of this linear model (Figure 3.5) adheres to Equation (3.1), which succinctly describes the association between the transformed input variables and the target variable within the enlarged feature space. This approach allows SVR to accommodate nonlinear relationships (Figure 3.6) in the data by leveraging the power of linear models in a higher-dimensional context:

```
$f(x,w) = \sum_{i=1}^{m} w_i \cdot g_i(x) + b \quad (3.1)$
```