In a nonparallel plane regressor, two nonparallel functions pertaining to the \(\epsilon\)-insensitive down and up-bounds of the unknown regressor are formulated. Similar to \(\epsilon\)-SVR, TSVR finds two \(\epsilon\)-insensitive functions (up-bound and down-bound regressors) to solve the convex optimization problem having size smaller than the conventional \(\epsilon\)-SVR, thus significantly reducing the computation time.

The mathematical formulation of TSVR is

```
\min \frac{1}{2} \sum_{i=1}^n (y_i - e\epsilon_1 - (x_i w_1 + eb_1))^T (y_i - e\epsilon_1 - (x_i w_1 + eb_1))
+ C_1 e^T \sum_{i=1}^n \xi_i, \quad \text{s.t. } y_i - (x_i w_1 + eb_1) \ge e\epsilon_1 - \xi_i,
(4.14)

\min \frac{1}{2} \sum_{i=1}^n (y_i - e\epsilon_2 - (x_i w_2 + eb_2))^T (y_i - e\epsilon_2 - (x_i w_2 + eb_2))
+ C_2 e^T \sum_{i=1}^n \eta_i, \quad \text{s.t. } (x_i w_2 + eb_2) - y_i \ge e\epsilon_2 - \eta_i,
(4.15)
```

where C_1, C_2 > 0 and \epsilon_1, \epsilon_2 \ge 0 are the TSVR hyperparameters, and \xi_i, \eta_i are the slack variables introduced as a soft margin to the error \epsilon in the optimization problem. The dual optimization problem formulation of TSVR is given by introducing the Lagrangian function [15]

```
L(w_1, b_1, \epsilon_i, \alpha_i, \beta_i) = \frac{1}{2} \sum_{i=1}^n (y_i - e\epsilon_1 - (x_i w_1 + eb_1))^T
(y_i - e\epsilon_1 - (x_i w_1 + eb_1)) + C_1 e^T \sum_{i=1}^n \xi_i
- \sum_{i=1}^n \alpha_i (y_i - e\epsilon_1 - (x_i w_1 + eb_1)) - \sum_{i=1}^n \beta_i \xi_i, \quad (4.16)
```

where \alpha_i, \beta_i (i = 1, 2, ..., n) are the Lagrangian multipliers. Let X = (x_1, x_2, ..., x_n) denote the set of input vectors, Y = (y_1, y_2, ..., y_n) be the set of output vectors, where y_i \in \mathbb{R}, and \alpha, \gamma are the Lagrangian multipliers. The KKT conditions for the Lagrangian function utilized in TSVR optimization can be obtained by partially differentiating the function L with respect to w_1, b_1, \epsilon, \alpha, \text{ and } \beta: