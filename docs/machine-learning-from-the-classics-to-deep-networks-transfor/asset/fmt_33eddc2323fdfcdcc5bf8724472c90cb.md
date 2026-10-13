
## 2. Hint

Use the matrix inversion lemma from Appendix A, in terms of the Schur complement $\overline{\Sigma}$ of $\Sigma_x$ in $\Sigma$ and the fact that $\text{det}(\Sigma) = \text{det}(\Sigma_y)\text{det}(\overline{\Sigma})$.

## 3. Exercise 3.17

Assume a number $l$ of jointly Gaussian random variables $\{x_1, x_2, \dots, x_l\}$ and a nonsingular matrix $A \in \mathbb{R}^{l \times l}$. If $\mathbf{x} := [x_1, x_2, \dots, x_l]^T$, then show that the components of the vector $\mathbf{y}$, obtained by $\mathbf{y} = A\mathbf{x}$, are also jointly Gaussian random variables.

## 4. Consequence

A direct consequence of this result is that any linear combination of jointly Gaussian variables is also Gaussian.

## 5. Exercise 3.18

Let $\mathbf{x}$ be a vector of jointly Gaussian random variables of covariance matrix $\Sigma_x$. Consider the general linear regression model

$$
\mathbf{y} = \Theta\mathbf{x} + \boldsymbol{\eta},
$$

where $\Theta \in \mathbb{R}^{k \times l}$ is a parameter matrix and $\boldsymbol{\eta}$ is the noise vector which is considered to be Gaussian, with zero mean, and with covariance matrix $\Sigma_\eta$, independent of $\mathbf{x}$. Then show that $\mathbf{y}$ and $\mathbf{x}$ are jointly Gaussian, with the covariance matrix given by

$$
\Sigma = \begin{bmatrix}
\Theta\Sigma_x\Theta^T + \Sigma_\eta & \Theta\Sigma_x \\
\Sigma_x\Theta^T & \Sigma_x
\end{bmatrix}.
$$

## 6. Exercise 3.19

Show that a linear combination of Gaussian independent variables is also Gaussian.

## 7. Exercise 3.20

Show that if a sufficient statistic $T(\mathcal{X})$ for a parameter estimation problem exists, then $T(\mathcal{X})$ suffices to express the respective ML estimate.

## 8. Exercise 3.21

Show that if an efficient estimator exists, then it is also optimal in the ML sense.
