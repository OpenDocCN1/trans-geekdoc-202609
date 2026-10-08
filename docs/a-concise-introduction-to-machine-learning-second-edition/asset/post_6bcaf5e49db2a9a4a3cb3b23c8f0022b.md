
For the extractive autoencoder, the penalty term

```
$$\Omega_F = \frac{1}{2} \sum_{n=1}^N ||J_{\theta}(\mathbf{x}_n)||^2 = \frac{1}{2} \sum_{n=1}^N \text{tr}(J_{\theta}(\mathbf{x}_n)^T J_{\theta}(\mathbf{x}_n)) = \sum_{n=1}^N \sum_{m=1}^M \frac{M_{L/2,m}}{2} (\frac{\partial\phi_m}{\partial\mathbf{x}_d})^2$
```

is added to the error function, multiplied by a weight $\lambda$.

Once trained, the autoencoders produce latent variables $\chi^{(L/2)}$ deterministically from which the output is calculated in a deterministic way. The *variational autoencoder* takes a different approach. The assumption is that the data $\mathbf{x}_1,\dots,\mathbf{x}_N$ are sampled from some distribution $p(\mathbf{x})$,

```
$p(\mathbf{x}) = \int p(\mathbf{x}|\chi^{(L/2)}) p(\chi^{(L/2)}) dx\chi^{(L/2)}$
```

Further, it is assumed that $p(\chi^{(L/2)})$ follows a normal distribution with mean $\chi$ and variance $\sigma^2 I$, where I is the $D \times D$ identity matrix. The prior probability distribution of it is the standard multivariate normal distribution. The overall probability $p(\mathbf{x})$ can be estimated by sampling many variables $\chi_1^{(L/2)},\dots,\chi_K^{(L/2)}$ and then calculating

```
$p(\mathbf{x}) = \frac{1}{K} \prod_{k=1}^K p(\mathbf{x}|\chi_k^{(L/2)}) = \frac{1}{K} \prod_{k=1}^K (2\pi\sigma^2)^{-D/2} \exp\left(-\frac{1}{2\sigma^2} ||\mathbf{x} - \chi_k^{(L/2)}||^2\right)$
```

The complete likelihood is estimated as

```
$L = \prod_{n=1}^N \prod_{k=1}^K (2\pi\sigma^2)^{-D/2} \exp\left(-\frac{1}{2\sigma^2} ||\mathbf{x}_n - \chi_k^{(L/2)}||^2\right)$
```

Maximizing $L$ is equivalent to minimizing the negative logarithm. However, this does not result in a convenient sum of squares as before because of the sum resulting from the $p(\mathbf{x})$. Another computational difficulty is that $K$ need to be large (in high dimensions) to obtain a good estimate. In addition, sampling is not a continuous operation and thus differentiable. So error backpropagation cannot be applied.

Variational autoencoders address these problems in the following way. The first step is to reduce $K$ to one $p_{\phi}(\mathbf{x})$, such that only values of $\chi^{(L/2)}$ are sampled which are samples of $\mathbf{x}$. For this other words, the encoder is used. To make this clear in notation the encoder gives an estimate $p_{\phi}(\chi^{(L/2)}|\mathbf{x})$ as a normal multivariate distribution. The function $\phi$ does not return $\chi^{(L/2)}$, but a mean and variance for the distribution of it

```
$$\mu(\mathbf{x}), \Sigma(\mathbf{x}) = \phi(\mathbf{x})$$


To keep the number of variables manageable, $\Sigma(\mathbf{x})$ is restricted to diagonal, that is, $\Sigma(\mathbf{x}) = \text{diag}(\sigma_1^2,\dots,\sigma_{M_{L/2}}^2)$. Hence, $\phi$ calculates $2M_{L/2}$ latent variables.

In order to use backpropagation, the sampling is moved to the input neurons, where a vector $\boldsymbol{\eta}=(\eta_1,\dots\eta_{M_{L/2}})^T$ is sampled from the standard normal distribution in $M_{L/2}$ dimensions. With this,

```
$z^{(L/2)} = \mu(\mathbf{x}) + \mathbf{\Sigma}^{1/2}(\mathbf{x}) = \begin{pmatrix} \mu_1(\mathbf{x}) + \sigma_1(\mathbf{x})\eta_1 \\ \vdots \\ \mu_{M_{L/2}}(\mathbf{x}) + \sigma_{M_{L/2}}(\mathbf{x})\eta_{M_{L/2}} \end{pmatrix}$
```

The schematics are

![](img/c6c76bf52016db7e78a5e30d4766ef81_320_0.png)

For clarity the input neurons are shaded. As before, the dotted lines indicate that any combination of hidden neurons, layers and transfer functions is possible, making use of the capacity of neural networks to model any function.

The error function is the sum over all training data $\mathbf{x}_n$ of $-\log p(\mathbf{x}_n)$ and the KL divergence $p_0^{(L/2)}|\mathbf{x}_n)$ and $p(z^{(L/2)}|\mathbf{x}_n)$. One term of this is given by

```
$E_n = - \log p(\mathbf{x}_n) + D_{KL}(p_0^{(L/2)}|\mathbf{x}_n) || p(z^{(L/2)}|\mathbf{x}_n)) = \int p_0(z^{(L/2)}|\mathbf{x}_n) [ - \log p(\mathbf{x}_n) - \log \frac{p(z^{(L/2)}|\mathbf{x}_n)}{p_0(z^{(L/2)}|\mathbf{x}_n)}] dz^{(L/2)}$
```

By Bayes' rule

```
$p(z^{(L/2)}|\mathbf{x}_n) = \frac{p(\mathbf{x}_n|z^{(L/2)})p(z^{(L/2)})}{p(\mathbf{x}_n)}$
```

this simplifies to

```
$E_n = \int p_{\phi}(\mathbf{z}^{(L/2)}|\mathbf{x}_n) \left[-\log \frac{p(\mathbf{z}^{(L/2)})}{p_{\phi}(\mathbf{z}^{(L/2)}|\mathbf{x}_n)} - \log p(\mathbf{x}_n|\mathbf{z}^{(L/2)})\right] d\mathbf{z}^{(L/2)} = \int p_{\phi}(\mathbf{z}^{(L/2)}|\mathbf{x}_n) [D_{KL}(p_{\phi}(\mathbf{z}^{(L/2)}|\mathbf{x}_n) || p_0(\mathbf{z}^{(L/2)}))] d\mathbf{z}^{(L/2)}$
```

The first term is the KL divergence between $p_{\phi}(\mathbf{z}^{(L/2)}|\mathbf{x}_n)$ and the prior $p_0(\mathbf{z}^{(L/2)})$, which simplifies to

$E_n = D_{KL}(p_{\phi}(\mathbf{z}^{(L/2)}|\mathbf{x}_n) || p_0(\mathbf{z}^{(L/2)})) - \log p(\mathbf{x}_n|\mathbf{z}^{(L/2)})$.

## 9.4 Autoencoder Example

We apply a sparse autoencoder to the MNIST dataset as gathered by LeCun et al. (1998) and compare this method to the techniques we already encountered. For this data, D = 784, and the components of x are individual pixel values.

The simplest autoencoder has two layers. Schematically, it is represented as

![](img/c6c76bf52016db7e78a5e30d4766ef81_322_0.png)

In this case, the encoder and decoder functions are

$\phi(\mathbf{x}) = h^{(1)}(\mathbf{W}^{(1)}\mathbf{x} + \mathbf{b}^{(1)})$ and $\psi(\mathbf{z}) = h^{(2)}(\mathbf{W}^{(2)}\mathbf{z} + \mathbf{b}^{(2)})$.

If $\mathbf{W}^{(2)}=\mathbf{W}^{(1)T}$, then the weights are tied. However, in this example we do not enforce this, let them be independent from each other.

Both $h^{(1)}$ and $h^{(2)}$ are chosen to be the logistic sigmoid elementwise. Since the output of logistic sigmoid is $[0, 1]$ and autoencoders reconstruct the pixel values of the input images needed to be scaled between zero and one as a pre-processing step.

Listing 9.2 is a minimal implementation with no regularization of this network. Of course, the native implementations of MATLAB and Python are preferable, especially for efficiency and regularization. However, it is also good practice to experiment with different algorithms directly. Listing 9.3 applies to a range of digits in the MNIST dataset.

Valuable insight can be gained from visualizing the activations and latent variables are separated spatially. This is easily possible for $M=1, 2$ or $3$. In the following, we show one technique that this can be done for larger $M$. The activations in the output layer are given by

```
$\mathbf{z} + \mathbf{b} = z_1\mathbf{w}_1^{(2)} + \dots + z_M\mathbf{w}_M^{(2)} + \mathbf{b},$
```
