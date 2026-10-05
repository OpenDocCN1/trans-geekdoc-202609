# 478

# MACHINE LEARNING

The way we constructed tabTree2D table reflects the underlying decision:

+   - Case: $x > 0.5
  - Case: $y > -0.2
  - Case: $y \le -0.2$
- Case: $x \le 0.5
  - Case: $x > -0.1$
    * Case: $y > 0$
    * Case: $y \le 0$
    - Case: $x \le -0.1$
    * Case: $y > -0.8$
    * Case: $y \le -0.8$
      - Case: $y > -0.7$
      - Case: $y \le -0.7$

where in bold font, we have denoted the "leaf" nodes, i.e. those which have been depicted in Figure 24.1.

Let us further assume that we are in fact solving a regression problem, where we have two features $x_1,x_2$, both defined in $[-1,1]^2$, and one dependent variable $y$, i.e. the model for the data looks like:

$y = f(x_1, x_2). \quad (24.1)$

We can use the tree structure built in the previous paragraph to model $y$ as a function of $x_1,x_2$. The regression model is such that we approximate the true function in every domain by a constant $c_i$;

$\hat{y} = \hat{f}(x_1, x_2) = \sum_{i=1}^{7} c_i 1((x_1,x_2) \in \text{domain}_i). \quad (24.2)$

where $1()$ is the indicator function used to model the tree domains.

![](bbox=[0.164, 0.633, 0.835, 0.9])

**FIGURE 24.1** Example of the tree-based partitioning for a two-dimensional case