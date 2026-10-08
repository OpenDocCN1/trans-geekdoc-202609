L \|_U \in C^1(U, R^d) that

F(\theta) = (\nabla L)(\theta). (6.1)

Then we say that \Theta is the GD process for the objective function L with generalized gradient F, learning rates (\gamma_n)_{n \in N}, and initial value \xi (we say that \Theta is the GD process for the objective function L with learning rates (\gamma_n)_{n \in N} and initial value \xi if and only if it holds that \Theta : N_0 \to R^d is the function from N_0 to R^d which satisfies for all n \in N that

\Theta_0 = \xi and \Theta_n = \Theta_{n-1} - \gamma_n F(\Theta_{n-1}). (6.2)

+   *   **Exercice 6.1.1.** Let \xi = (\xi_1, \xi_2, \xi_3) \in R^3 satisfy \xi = (1, 2, 3), let L : R^3 \to R satisfy for all \theta = (\theta_1, \theta_2, \theta_3) \in R^3 that
    $$L(\theta) = 2(\theta_1)^2 + (\theta_2 + 1)^2 + (\theta_3 - 1)^2, (6.3)$$
    and let \Theta be the GD process for the objective function L with learning rates N \ni n \mapsto \frac{1}{2^n}, and initial value \xi (cf. Definition 6.1.1). Specify \Theta_1, \Theta_2, and \Theta_3 explicitly and prove that your results are correct!

+   *   **Exercice 6.1.2.** Let \xi = (\xi_1, \xi_2, \xi_3) \in R^3 satisfy \xi = (\xi_1, \xi_2, \xi_3) = (3, 4, 5), let L : R^3 \to R satisfy for all \theta = (\theta_1, \theta_2, \theta_3) \in R^3 that
    $$L(\theta) = (\theta_1)^2 + (\theta_2 - 1)^2 + 2(\theta_3 + 1)^2,$$
    and let \Theta be the GD process for the objective function L with learning rates N \ni n \mapsto 1/3 \in [0, \infty) and initial value \xi (cf. Definition 6.1.1). Specify \Theta_1, \Theta_2, and \Theta_3 explicitly and prove that your results are correct.

# **6.1.1 GD optimization in the training of ANNs**

In the next example we apply the GD optimization method in the context of the training of fully-connected feedforward ANNs in the vectorized description (see Section 1.1) with the loss function being the mean squared error loss function in Definition 5.4.2 (see Section 5.4.2).

**Example 6.1.2.** Let d, h, \mathfrak{d} \in N, l_1, l_2, \ldots, l_h \in N satisfy \mathfrak{d} = l_1(d+1)+ [\sum_{k=2}^{h} l_k(l_{k-1}+1)] + l_h+1, let u : R \to R be differentiable, let M \in N, x_1, x_2, \ldots, x_M \in R^d, y_1, y_2, \ldots, y_M \in R, let L : R^{\mathfrak{d}} \to [0, \infty) satisfy for all \theta \in R^{\mathfrak{d}} that
$$L(\theta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \left( \mathcal{N}^{\theta, d}_{\mathfrak{d}}_{w_{l_{a,i_1}}, w_{l_{a,i_2}}, \ldots, w_{l_{a,i_h}}, id\mathfrak{d}}(x_m) - y_m \right)^2 \right], (6.4)$$
let \xi \in R^{\mathfrak{d}}, let (\gamma_n)_{n \in N} \subseteq N, and let \Theta : N_0 \to R^{\mathfrak{d}} satisfy for all n \in N that
$$\Theta_0 = \xi \text{ and } \Theta_n = \Theta_{n-1} - \gamma_n(\nabla L)(\Theta_{n-1}) (6.5)$$
(cf. Definitions 1.1.3 and 1.2.1 and Corollary 5.3.6). Then \Theta is the GD process for the objective function L with learning rates (\gamma_n)_{n \in N} and initial value \xi.