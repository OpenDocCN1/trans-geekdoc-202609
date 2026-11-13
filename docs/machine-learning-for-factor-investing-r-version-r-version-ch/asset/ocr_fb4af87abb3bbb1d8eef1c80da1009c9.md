where the first condition leads to

\(\mathbf{w}^* = \sum_{i=1}^I \lambda_i y_i \mathbf{x}_i.\)

This solution is indeed a linear form of the features, but only some points are taken into account. They are those for which the inequalities (8.1) are equalities.

Naturally, this problem becomes infeasible whenever the condition cannot be satisfied, that is, when a simple line cannot perfectly separate the labels, no matter the choice of coefficients. This is the most common configuration and datasets are then called logically *not linearly separable*. This complicates the process but it is possible to resort to a trick. The idea is to introduce some flexibility in (8.1) by adding correction variables that allow the conditions to be met:

\(\begin{aligned} \sum_{k=1}^K w_k x_{i,k} + b \ge +1 - \xi_i & \quad \text{when } y_i = +1 \\ \sum_{k=1}^K w_k x_{i,k} + b \le -1 + \xi_i & \quad \text{when } y_i = -1, \end{aligned} \quad (8.4)\)

where the novelties, the \(\xi_i\) are positive so-called ‘slack’ variables that make the conditions feasible. They are illustrated in Figure 8.2. In this new configuration, there is no simple linear model that can perfectly discriminate between the two classes.

![](bbox=[0.235, 0.439, 0.786, 0.672])

**FIGURE 8.2:** Diagram of binary classification with SVM - linearly inseparable data.

The optimization program then becomes

\(\underset{\mathbf{w},b,\xi}{\text{argmin}} \frac{1}{2}||\mathbf{w}||^2 + C \sum_{i=1}^I \xi_i \quad \text{s.t.} \quad y_i \sum_{k=1}^K w_k \phi(x_{i,k}) + b \ge 1 - \xi_i \quad \text{and} \quad \xi_i \ge 0, \quad \forall i \} , \quad (8.5)\)

where the parameter \(C > 0\) tunes the cost of mis-classification: as \(C\) increases, errors become more penalizing.

In addition, the program can be generalized to nonlinear models, via the kernel \(\phi\) which is applied to the input points \(x_{i,k}\). Nonlinear kernels can help cope with patterns that are more complex than straight lines (see Figure 8.3). Common kernels can be polynomial, radial