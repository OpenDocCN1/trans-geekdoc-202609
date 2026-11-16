SVM is to learn a decision function to predict the label of an example. The optimization formulation of SVM is:

```
min \frac{||w||^2}{2} + G \sum \xi_i,
s.t. wx_i + b \ge 1 - \xi_i, i=1,\cdots,n,
wx_i + b \le -1 + \xi_i, i=n+1,\cdots,n+m
(31)
```

where, $\xi_i$ is the slack variables and G controls the fraction on misclassified training examples. This is a quadratic programming problem, use Lagrange multiplier method and meet the KKT conditions, can get the optimal classification function for the above problems:

```
f(x) = \text{sgn}\{w \cdot x + b^*\} = \text{sgn}\{\sum_{i=1}^n a_i^* y_i (x_i \cdot x) + b^*\}
(32)
```

where, $a_i^*$ and $b^*$ are to the parameters to determine the optimal classification surface. $(x \cdot x)$ is the dot product of two vectors.

For the nonlinear problem SVM can turn it into a high dimensional space by the nonlinear function mapping to solve the optimal classification surface. Therefore, the original problem becomes linearly separable. As can be seen from Equation (32) if we know dot product operation of the characteristics space the optimal classification surface can be obtained by simple calculation. According to the theory of Mercer, for any $\Phi(x) \neq 0$ if:

```
\left\{ \begin{array}{l} \int \phi^2(x) \mathrm{d}x < \infty \\ \iint K(x_i, x_j) \phi(x_i) \phi(x_j) \mathrm{d}x_i \mathrm{d}x_j > C \end{array} \right.
(33)
```

The arbitrary symmetric function $K(x,x)$ will be the dot product of a certain transformation space. Equation (32) will be corresponding to:

```
f(x) = \text{sgn}\{\sum_{i=1}^n a_i^* y_i K(x \cdot x) + b^*\}
(34)
```

This is SVM. There are a number of categories of the kernel function K (x, x):

+   - The linear kernel function $K(x_i, x_j) = (x \cdot x_i)$ ;
+   - The polynomial kernel function $K(x, x_i) = (s(x \cdot x_i) + c)^d$ , where s, c and d are parameters;
+   - The radial basis kernel function, $K(x, x_i) = \exp\{-\gamma |x - x_i|^2\}$, where $\gamma$ is the parameter;
+   - The Sigmoid kernel function $K(x, x_i) = \tanh(s(x \cdot x_i) + c)$, where s and c are parameters.