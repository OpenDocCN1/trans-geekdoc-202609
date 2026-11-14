
## 28.2.5.1 Hybrid generative/discriminative training

Unfortunately the classification accuracy of generative models of the form \(p(\boldsymbol{x}, y)\) can be much worse than discriminative (conditional) models of the form \(p(y|\boldsymbol{x})\), since the latter are directly optimized to predict the labels given the features, and don’t “waste” capacity on modeling irrelevant details of the inputs. (For a more in-depth discussion of generative vs discriminative classifiers, see e.g., [Mur22, Sec 9.4].)

Fortunately it is possible to train generative models in a discriminative fashion, which can close the performance gap with conditional models, while maintaining the advantages of generative models. In particular, we can optimize the following hybrid objective, proposed in [BT04; Rot+18]:

```
\(\mathcal{L}(\boldsymbol{\theta}) = -\lambda \sum_{n=1}^N \log p(\boldsymbol{x}_n, y_n|\boldsymbol{\theta}) - (1 - \lambda) \sum_{n=1}^N \log p(y_n|\boldsymbol{x}_n, \boldsymbol{\theta})\underbrace{}_{\mathcal{L}_{gen}(\boldsymbol{\theta})} \quad \underbrace{}_{\mathcal{L}_{dis}(\boldsymbol{\theta})}\) (28.25)
```

where \(0 \le \lambda \le 1\) controls the tradeoff between generative and discriminative modeling.

If we have unlabeled data, we can modify the generative loss as shown below:

```
\(\mathcal{L}_{gen}(\boldsymbol{\theta}) = \kappa \sum_{n=1}^{N^l} \log p(\boldsymbol{x}_n^l, y_n^l|\boldsymbol{\theta}) + (1 - \kappa) \sum_{n=1}^{N^u} \log p(\boldsymbol{x}_n^u|\boldsymbol{\theta})\) (28.26)
```

Here we have introduced an extra trade-off parameter \(0 \le \kappa \le 1\) to prevent the unlabeled data from overwhelming the labeled data (if \(N_u \gg N_l\)), as proposed in [Nig+00].

An alternative to changing the objective function is to change the model itself, so that we parameterize the joint using \(p(\boldsymbol{x}, y) = p(y|\boldsymbol{x}, \boldsymbol{\theta})p(\boldsymbol{x}|\tilde{\boldsymbol{\theta}})\), and then define different kinds of joint priors \(p(\boldsymbol{\theta}, \tilde{\boldsymbol{\theta}})\); see [LBM06; BL07a] for details.

## 28.2.5.2 Optimization issues

To optimize the loss, we need to reparameterize the model into unconstrained form. For the class prior, we can use \(\pi_{1:C} = \text{softmax}(\tilde{\pi}_{1:C})\), and optimize wrt the logits \(\tilde{\pi}_{1:C}\). Similarly for the mixture weights \(\alpha_{c,1:K}\). The means \(\boldsymbol{\mu}_{ck}\) are already unconstrained. For the covariance matrices, we will use a diagonal plus low-rank representation, to reduce the number of parameters:

```
\(\boldsymbol{\Sigma}_{c,k} = \text{diag}(\boldsymbol{d}_{c,k}) + \mathbf{S}_{c,k}\mathbf{S}_{c,k}^\mathsf{T}\) (28.27)
```

where \(\mathbf{S}_{c,k}\) is an unconstrained \(D \times R\) matrix, where \(R \ll D\) is the rank of the approximation. (For numerical stability, we usually add \(\epsilon \mathbf{I}\) to the above expression, to ensure \(\boldsymbol{\Sigma}_{c,k}\) is positive definite for all parameter settings.) To ensure positivity of the diagonal term, we can use the softplus transform, \(d_{c,k} = \log(1 + \exp(d_{c,k}))\), and optimize wrt the \(\tilde{d}_{c,k}\) terms.

## 28.2.5.3 Numerical issues

To compute the class conditional log likelihood, \(\ell_c = \log p(\boldsymbol{x}|y=c)\), we can use the log-sum-exp trick to avoid numerical underflow. Define \(\hat{\alpha}_{ck} = \log \alpha_{ck}\) and \(\ell_{ck} = \log \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_{ck}, \boldsymbol{\Sigma}_{ck})\). Then we have

```
\(\ell_c = \log p(x|y=c) = \log \sum_k e^{\tilde{\alpha}_{ck}+\ell_{ck}}\tag{28.28}\)
\(= e^M \log \sum_k e^{\tilde{\alpha}_{ck}+\ell_{ck}-M} \stackrel{\Delta}{=} \text{logsumexp}(\{\tilde{\alpha}_{ck} + \ell_{ck}\}_k)\tag{28.29}\)
```

where \(M = \max_k \tilde{\alpha}_{ck} + \ell_{ck}\).
We can use a similar method to compute the posterior over classes. We have

```
\(p(y=c|x) = \frac{\pi_c e^{l_c}}{Z} = \frac{\pi_c e^{l_c-L}}{e^{-L} Z} = \frac{\pi_c e^{\tilde{l}_c}}{\tilde{Z}}\tag{28.30}\)
```

where \(L = \max_c l_c\), \(\tilde{l}_c = l_c - L\), and \(\tilde{Z} = \sum_c \pi_c e^{\tilde{l}_c}\). This lets us combine the class prior probability \(\pi_c\) with the scaled class conditional log likelihood \(\tilde{l}_c\) to get the class posterior in a stable way. (We can also compute the log normalization constant, \(\log p(x) = \log Z = \log(\tilde{Z}) + L\).)
To compute a single Gaussian log density, \(\ell_{ck} = \log \mathcal{N}(x|\mu_{ck}, \Sigma_{ck})\), we need to evaluate \(\log \det(\Sigma_{ck})\) and \(\Sigma_{ck}^{-1}\). To make this efficient, we can use the matrix determinant lemma to compute

```
\(\det(\mathbf{A} + \mathbf{S}\mathbf{S}^T) = \det(\mathbf{I} + \mathbf{S}^T \mathbf{A}^{-1} \mathbf{S}) \det(\mathbf{A})\tag{28.31}\)
```

where \(\mathbf{A} = \text{diag}(d) + \epsilon \mathbf{I}\), and the matrix inversion lemma to compute

```
\((\mathbf{A} + \mathbf{S}\mathbf{S}^T)^{-1} = \mathbf{A}^{-1} - \mathbf{A}^{-1}\mathbf{S}(\mathbf{I} + \mathbf{S}^T \mathbf{A}^{-1} \mathbf{S})^{-1} \mathbf{S}^T \mathbf{A}^{-1}\tag{28.32}\)
```

(See also the discussion of mixture of factor analyzers in Section 28.3.3.)

## 28.3 Factor analysis

In this section, we discuss a simple latent factor model in which the prior \(p(z)\) is Gaussian, and the likelihood \(p(x|z)\) is also Gaussian, using a linear decoder for the mean. This family includes many important special cases, such as PCA, as we discuss below. We also briefly discuss some simple extensions.

### 28.3.1 Factor analysis: the basics

Factor analysis corresponds to the following linear-Gaussian latent variable generative model:

```
\(p(z) = \mathcal{N}(z|\mu_0, \Sigma_0)\tag{28.33}\)
\(p(x|z, \theta) = \mathcal{N}(x|\mathbf{W}z + \mu, \Psi)\tag{28.34}\)
```

where \(\mathbf{W}\) is a \(D \times L\) matrix, known as the **factor loading matrix**, and \(\Psi\) is a diagonal \(D \times D\) covariance matrix.

### 28.3.1.1 FA as a Gaussian with low-rank plus diagonal covariance

FA can be thought of as a low-rank version of a Gaussian distribution. To see this, note that the induced marginal distribution \(p(\mathbf{x}|\boldsymbol{\theta})\) is a Gaussian (see Equation (2.129) for the derivation):

\(p(\mathbf{x}|\boldsymbol{\theta}) = \int \mathcal{N}(\mathbf{x}|\mathbf{W}\mathbf{z} + \boldsymbol{\mu}, \boldsymbol{\Psi})\mathcal{N}(\mathbf{z}|\boldsymbol{\mu}_0, \boldsymbol{\Sigma}_0)d\mathbf{z}\)
\(= \mathcal{N}(\mathbf{x}|\mathbf{W}\boldsymbol{\mu}_0 + \boldsymbol{\mu}, \boldsymbol{\Psi} + \mathbf{W}\boldsymbol{\Sigma}_0\mathbf{W}^T)\)

The first and second moments can be derived as follows:

\(\mathbb{E}[\mathbf{x}] = \mathbf{W}\boldsymbol{\mu}_0 + \boldsymbol{\mu}\)
\(\text{Cov}[\mathbf{x}] = \mathbf{W}\text{Cov}[\mathbf{z}]\mathbf{W}^T + \boldsymbol{\Psi} = \mathbf{W}\boldsymbol{\Sigma}_0\mathbf{W}^T + \boldsymbol{\Psi}\)

From this, we see that we can set \(\boldsymbol{\mu}_0 = \mathbf{0}\) without loss of generality, since we can always absorb \(\mathbf{W}\boldsymbol{\mu}_0\) into \(\boldsymbol{\mu}\). Similarly, we can set \(\boldsymbol{\Sigma}_0 = \mathbf{I}\) without loss of generality, since we can always absorb a correlated prior by using a new weight matrix, \(\tilde{\mathbf{W}} = \mathbf{W}\boldsymbol{\Sigma}_0^{-\frac{1}{2}}\), since then

\(\text{Cov}[\mathbf{x}] = \mathbf{W}\boldsymbol{\Sigma}_0\mathbf{W}^T + \boldsymbol{\Psi} = \tilde{\mathbf{W}}\tilde{\mathbf{W}}^T + \boldsymbol{\Psi}\)

Finally, we see that we should restrict \(\boldsymbol{\Psi}\) to be diagonal, otherwise we could set \(\tilde{\mathbf{W}} = \mathbf{0}\), thus ignoring the latent factors, while still being able to model any covariance. After these simplifications we have the final model:

\(p(\mathbf{z}) = \mathcal{N}(\mathbf{z}|\mathbf{0}, \mathbf{I})\)
\(p(\mathbf{x}|\mathbf{z}) = \mathcal{N}(\mathbf{x}|\mathbf{W}\mathbf{z} + \boldsymbol{\mu}, \boldsymbol{\Psi})\)

from which we get

\(p(\mathbf{x}) = \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \mathbf{W}\mathbf{W}^T + \boldsymbol{\Psi})\)

For example, suppose where \(L=1, D=2\) and \(\boldsymbol{\Psi} = \sigma^2\mathbf{I}\). We illustrate the generative process in this case in Figure 28.6. We can think of this as taking an isotropic Gaussian “spray can”, representing the likelihood \(p(\mathbf{x}|\mathbf{z})\), and “sliding it along” the 1d line defined by \(\mathbf{w}z + \boldsymbol{\mu}\) as we vary the 1d latent prior \(z\). This induces an elongated (and hence correlated) Gaussian in 2d. That is, the induced distribution has the form \(p(\mathbf{x}) = \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \mathbf{w}\mathbf{w}^T + \sigma^2\mathbf{I})\).

In general, FA approximates the covariance matrix of the visible vector using a low-rank decomposition:

\(\mathbf{C} = \text{Cov}[\mathbf{x}] = \mathbf{W}\mathbf{W}^T + \boldsymbol{\Psi}\)

This only uses \(O(LD)\) parameters, which allows a flexible compromise between a full covariance Gaussian, with \(O(D^2)\) parameters, and a diagonal covariance, with \(O(D)\) parameters.
