when the samples $X_1, \dots, X_Y$ pass through the network. The aim is to keep this low so that $z_m$ is zero or close to zero for most inputs and has non-negative values for subset of inputs. This means, the neuron only reacts, or "fires", to a small number of inputs, which it identifies with subset common features. The error function includes a penalty term for all hidden neurons, which is large if $p_m$ differs from the predefined sparsity proportion $p$, small, if $p_m$ is close to zero, and zero if they are equal.

More specifically, the sparsity penalty term

```
$$\Omega_s = \sum_{l=1}^{L-1} \sum_{m=1}^{M_l} D_{KL}(p_m^{(l)} || p \log p + (1-p) \log \frac{1}{1-p})$})$
```

is added to the error function with a suitable weight $eta$. Suitable values for both $eta$ and $p$ can be chosen by monitoring the convergence and reconstruction behaviour, or via a validation set.

However, when adding this, the latent variables might become small, while the weights in the subsequent layer become large, counteracting the effect. In order to avoid another penalty, the $L_2$ regularization term on the weights is added as:

```
$$\Omega_w = \frac{1}{2} \sum_{l=1}^{L} \sum_{i=1}^{M_l} \ (w_{ij}^{(l)})^2$
```

where $M_0 = M_L = D$. As before, this is weighted by a suitable parameter $\lambda$. This term penalizes growth in the weights.

Another variation is the *contractive autoencoder*. Let the encoder function by $\phi(x) = (\phi_1(x), \dots, \phi_{M_L}(x))^T$. Its Jacobian matrix (the matrix of partial derivatives) is

```
$J_{\phi}(\mathbf{x}) = \begin{pmatrix} \frac{\partial \phi_1}{\partial x_1} & \dots & \frac{\partial \phi_1}{\partial x_D} \ \vdots & \ddots & \vdots \ \frac{\partial \phi_{M_L}}{\partial x_1} & \dots & \frac{\partial \phi_{M_L}}{\partial x_D} \end{pmatrix}$
```

If we have $M_{L/2} = D$, then the Jacobian matrix is square, the modulus of its determinant is the factor by which volumes in $\mathbb{R}^D$ under the transformation $\phi$ shrink or expand. The aim is to control this volume change favouring reductions in volume, therefore the name contractive autoencoder. However, generally $M_{L/2} \neq D$. In fact, a much smaller number than $D$ is desired. The *Frobenius norm* is a measure of change under these circumstances.

For a general, real $a \times b$ matrix $\mathbf{A}$ with $A_{ij}$, the Frobenius norm is defined as

```
$|\mathbf{A}||_F = \sqrt{\tr}(\mathbf{A}^T\mathbf{A})} = \sqrt{\sum_{i=1}^{a} \sum_{j=1}^{b} A_{ij}^2}$
```