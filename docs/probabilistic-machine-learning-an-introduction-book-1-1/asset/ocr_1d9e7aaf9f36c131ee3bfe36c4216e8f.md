![](bbox=[0.4375, 0.1074, 0.5817, 0.4252])

*Figure 3.24: A Gaussian mixture model represented as a graphical model.*

Fig. **3.24** shows a more interesting example, in which we represent a GMM (Sec. **3.7.1**) as a graphical model. We see that this encodes the joint distribution

$$p(\mathbf{y}_{1:N},\mathbf{z}_{1:N},\boldsymbol{\theta}) = p(\boldsymbol{\pi})\left[\prod_{k=1}^{K}p(\boldsymbol{\mu}_k)p(\boldsymbol{\Sigma}_k)\right]\left[\prod_{n=1}^{N}p(z_n\mid\boldsymbol{\pi})p(\mathbf{y}_n\mid z_n,\boldsymbol{\mu}_{1:K},\boldsymbol{\Sigma}_{1:K})\right] \tag{3.140}$$

We see that the latent variables $z_n$ as well as the unknown parameters, $\boldsymbol{\theta}=(\boldsymbol{\pi},\boldsymbol{\mu}_{1:K},\boldsymbol{\Sigma}_{1:K})$, are all shown as unshaded nodes.

# ### 3.9 Exercises

# **Exercise 3.1** [Gaussian vs jointly Gaussian]

Let $X\sim\mathcal{N}(0,1)$ and $Y=WX$, where $p(W=-1)=p(W=1)=0.5$. It is clear that $X$ and $Y$ are not independent, since $Y$ is a function of $X$.

+   a. Show $Y\sim\mathcal{N}(0,1)$.
+   
+   b. Show $\operatorname{Cov}[X,Y]=0$. Thus $X$ and $Y$ are uncorrelated but dependent, even though they are Gaussian.

**Hint:** use the definition of covariance

$$\operatorname{Cov}[X,Y]=\mathbb{E}[XY]-\mathbb{E}[X]\mathbb{E}[Y] \tag{3.141}$$

and the **rule of iterated expectation**

$$\mathbb{E}[XY]=\mathbb{E}\left[\mathbb{E}[XY\mid W]\right] \tag{3.142}$$