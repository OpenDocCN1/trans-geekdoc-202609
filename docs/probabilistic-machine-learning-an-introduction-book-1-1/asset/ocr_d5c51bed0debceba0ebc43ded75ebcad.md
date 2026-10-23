# 20.2.1  Generative model

Factor analysis corresponds to the following linear-Gaussian latent variable generative model:

$$p(\mathbf{z}) = \mathcal{N}(\mathbf{z}\mid\boldsymbol{\mu}_0,\boldsymbol{\Sigma}_0) \tag{20.32}$$

$$p(\mathbf{x}\mid\mathbf{z},\theta) = \mathcal{N}(\mathbf{x}\mid\mathbf{Wz}+\boldsymbol{\mu},\boldsymbol{\Psi}) \tag{20.33}$$

where $\mathbf{W}$ is a $D \times L$ matrix, known as the **factor loading matrix**, and $\boldsymbol{\Psi}$ is a diagonal $D \times D$ covariance matrix.

FA can be thought of as a low-rank version of a Gaussian distribution. To see this, note that the induced marginal distribution $p(\mathbf{x}\mid\theta)$ is a Gaussian (see Eq. (3.105) for the derivation):

$$p(\mathbf{x}\mid\theta)=\int \mathcal{N}(\mathbf{x}\mid\mathbf{Wz}+\boldsymbol{\mu},\boldsymbol{\Psi})\mathcal{N}(\mathbf{z}\mid\boldsymbol{\mu}_0,\boldsymbol{\Sigma}_0)d\mathbf{z} \tag{20.34}$$

$$\qquad\qquad=\mathcal{N}(\mathbf{x}\mid\mathbf{W}\boldsymbol{\mu}_0+\boldsymbol{\mu},\boldsymbol{\Psi}+\mathbf{W}\boldsymbol{\Sigma}_0\mathbf{W}^{\mathsf{T}}) \tag{20.35}$$

Hence $\mathbb{E}[\mathbf{x}]=\mathbf{W}\boldsymbol{\mu}_0+\boldsymbol{\mu}$ and $\operatorname{Cov}[\mathbf{x}]=\mathbf{W}\operatorname{Cov}[\mathbf{z}]\mathbf{W}^{\mathsf{T}}+\boldsymbol{\Psi}=\mathbf{W}\boldsymbol{\Sigma}_0\mathbf{W}^{\mathsf{T}}+\boldsymbol{\Psi}$. From this, we see that we can set $\boldsymbol{\mu}_0=0$ without loss of generality, since we can always absorb $\mathbf{W}\boldsymbol{\mu}_0$ into $\boldsymbol{\mu}$. Similarly, we can set $\boldsymbol{\Sigma}_0=\mathbf{I}$ without loss of generality, since we can always absorb a correlated prior by using a new weight matrix, $\widetilde{\mathbf{W}}=\mathbf{W}\boldsymbol{\Sigma}_0^{-\frac{1}{2}}$. After these simplifications we have

$$p(\mathbf{z})=\mathcal{N}(\mathbf{z}\mid\mathbf{0},\mathbf{I}) \tag{20.36}$$
$$p(\mathbf{x}\mid\mathbf{z})=\mathcal{N}(\mathbf{x}\mid\mathbf{Wz}+\boldsymbol{\mu},\boldsymbol{\Psi}) \tag{20.37}$$
$$p(\mathbf{x})=\mathcal{N}(\mathbf{x}\mid\boldsymbol{\mu},\mathbf{W}\mathbf{W}^{\mathsf{T}}+\boldsymbol{\Psi}) \tag{20.38}$$

For example, suppose where $L=1$, $D=2$ and $\boldsymbol{\Psi}=\sigma^2\mathbf{I}$. We illustrate the generative process in this case in Fig. 20.9. We can think of this as taking an isotropic Gaussian “spray can”, representing the likelihood $p(\mathbf{x}\mid\mathbf{z})$, and “sliding it along” the 1d line defined by $\mathbf{wz}+\boldsymbol{\mu}$ as we vary the 1d latent prior $z$. This induces an elongated (and hence correlated) Gaussian in 2d. That is, the induced distribution has the form $p(\mathbf{x})=\mathcal{N}(\mathbf{x}\mid\boldsymbol{\mu},\mathbf{w}\mathbf{w}^{\mathsf{T}}+\sigma^2\mathbf{I})$.

In general, FA approximates the covariance matrix of the visible vector using a low-rank decomposition:

$$\mathbf{C}=\operatorname{Cov}[\mathbf{x}]=\mathbf{W}\mathbf{W}^{\mathsf{T}}+\boldsymbol{\Psi} \tag{20.39}$$

This only uses $O(LD)$ parameters, which allows a flexible compromise between a full covariance Gaussian, with $O(D^2)$ parameters, and a diagonal covariance, with $O(D)$ parameters.

From Eq. (20.39), we see that we should restrict $\boldsymbol{\Psi}$ to be diagonal, otherwise we could set $\mathbf{W}=0$, thus ignoring the latent factors, while still being able to model any covariance. The marginal variance of each visible variable is given by $\mathbb{V}[x_d]=\sum_{k=1}^{L}w_{dk}^2+\psi_d$, where the first term is the variance due to the common factors, and the second $\psi_d$ term is called the **uniqueness**, and is the variance term that is specific to that dimension.

We can estimate the parameters of an FA model using EM (see Sec. 20.2.3). Once we have fit the model, we can compute probabilistic latent embeddings using $p(\mathbf{z}\mid\mathbf{x})$. Using Bayes rule for Gaussians we have

$$p(\mathbf{z}\mid\mathbf{x})=\mathcal{N}(\mathbf{z}\mid\mathbf{W}^{\mathsf{T}}\mathbf{C}^{-1}(\mathbf{x}-\boldsymbol{\mu}),\mathbf{I}-\mathbf{W}^{\mathsf{T}}\mathbf{C}^{-1}\mathbf{W}) \tag{20.40}$$

where $\mathbf{C}$ is defined in Eq. (20.39).