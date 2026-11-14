| Model | p(z) | p(x|z) | Section |
| :--- | :--- | :--- | :--- |
| FA/PCA | N(z|0, I) | N(x|Wz, Ψ) | Section 28.3.1 |
| GMM | Σc Cat(c|π)N(z|μc, Σc) | N(x|Wz, Ψ) | Section 28.2.4 |
| MixFA | Cat(c|π)N(z|0, I) | N(x|Wz + μc, Ψc) | Section 28.3.3-5 |
| NMF | Πk Ga(zk|αk, βk) | Πd Poi(xd|exp(wdTz)) | Section 28.4.1 |
| Simplex FA (mPCA) | Dir(z|α) | Πd Cat(xd|Wdz) | Section 28.4.2 |
| LDA | Dir(z|α) | Πd Cat(xd|Wz) | Section 28.5 |
| ICA | Πd Laplace(zd|λ) | Πd δ(xd - wdTz) | Section 28.6 |
| Sparse coding | Πk Laplace(zk|λ) | Πd N(xd|wdTz, σ2) | Section 28.6.5 |

Table 28.1: Some popular “shallow” latent factor models. Abbreviations: FA = factor analysis, PCA = principal components analysis, GMM = Gaussian mixture model, NMF = non-negative matrix factorization, mPCA = multinomial PCA, LDA = latent Dirichlet allocation, ICA = independent components analysis. k = 1 : L ranges over latent dimensions, d = 1 : D ranges over observed dimensions. (For ICA, we have the constraint that L = D.)

prior on this latent variable is p(z = k) = πk, and the conditional is p(x|z = k) = pk(x) = p(x|θk). That is, we define the following joint model:

```
p(z|θ) = Cat(z|π) (28.4)
p(x|z = k, θ) = p(x|θk) (28.5)
```

The “generative story” for the data is that we first sample a specific component z, and then we generate the observations x using the parameters chosen according to the value of z. By marginalizing out z, we recover Equation (28.3):

```
p(x|θ) = Σk=1^K p(z = k|θ)p(x|z = k, θ) = Σk=1^K πk p(x|θk) (28.6)
```

We can create different kinds of mixture model by varying the base distribution pk, as we illustrate below.

# 28.2.1 Gaussian mixture models (GMMs)

A Gaussian mixture model or GMM, also called a mixture of Gaussians (MoG), is defined as follows:

```
p(x) = Σk=1^K πk N(x|μk, Σk) (28.7)
```

In Figure 28.1 we show the density defined by a mixture of 3 Gaussians in 2d. Each mixture component is represented by a different set of elliptical contours. If we let the number of mixture components grow sufficiently large, a GMM can approximate any smooth distribution over RD.

GMMs are often used for unsupervised clustering of real-valued data samples xn ∈ RD. This works in two stages. First we fit the model, usually by computing the MLE θ̂ = argmax log p(D|θ),