# # 15.2 Principal component analysis and autoencoders

```
## [3,] 0.5215295 0.5679119 -0.10533870 0.2574949
## [4,] 0.5445359 0.5335619 -0.08833864 0.2281793
## [5,] 0.5672644 0.5339749 -0.06092424 0.2320938
## [6,] 0.5871306 0.6420126 -0.44566482 0.3075399
```

These 4 factors can then be used as orthogonal features in any ML engine. The fact that the features are uncorrelated is undoubtedly an asset. But the price of this convenience is high: the features are no longer immediately interpretable. De-correlating the predictors adds yet another layer of “blackbox-ing” in the algorithm.

PCA can also be used to estimate factor models. In Equation (15.3), it suffices to replace **Z** with returns, **X** with valued values and **P** with factor loadings (see, e.g., Connor and Korajczyk (1988) for an early reference). More recently, Lettau and Pelger (2020a) and Lettau and Pelger (2020b) propose a thorough analysis of PCA estimation techniques. They notably argue that first moments of returns are important and should be included in the objective function, alongside the optimization on the second moments.

We end this subsection with a technical note. Usually, PCA is performed on the covariance matrix of returns. Sometimes, it may be preferable to decompose the **correlation** matrix. The result may adjust substantially if the variables have very different variances (which is not really the case in the equity space). If the investment universe encompasses several asset classes, then a correlation-based PCA will reduce the importance of the most volatile class. In this case, it is as if all returns are scaled by their respective volatilities.

# ## 15.2.3 Autoencoders

In a PCA, the coding from **X** to **Z** is straightfoward, linear and works both ways:

```
\(\mathbf{Z} = \mathbf{XP}\) and \(\mathbf{X} = \mathbf{YP}'\),
```

so that we recover **X** from **Z**. This can be written differently:

```
\(\mathbf{X}\longrightarrow^{\text{encode via }\mathbf{P}}\mathbf{Z}\longrightarrow^{\text{decode via }\mathbf{P}}\mathbf{X}\) (15.5)
```

If we take the truncated version and seek a smaller output (with only \(K'\) columns), this gives:

```
\(\mathbf{X}, (I \times K)\longrightarrow^{\text{encode via }\mathbf{P}_K}\tilde{\mathbf{X}}, (I \times K')\longrightarrow^{\text{decode via }\mathbf{P}_K}\check{\mathbf{X}}, (I \times K),\) (15.6)
```

where \(\mathbf{P}_K\) is the restriction of \(\mathbf{P}\) to the \(K'\) columns that correspond to the factors with the largest variances. The dimensions of matrices are indicated inside the brackets. In this case, the recoding cannot recover **P** exactly but only an approximation, which we write \(\check{\mathbf{X}}\). This approximation is coded with less information, hence this new data \(\tilde{\mathbf{X}}\) is compressed and provides a parsimonious representation of the original sample **X**.

An autoencodeur generalizes this concept to **nonlinear** coding functions. Simple linear autoencoders are linked to latent factor models (see Proposition 1 in Gu et al. (2020a) for the case of single layer autoencoders.) The scheme is the following

```
\(\mathbf{X}, (I \times K)\longrightarrow^{\text{encode via }N}\tilde{\mathbf{X}} = N(\mathbf{X}), (I \times K')\longrightarrow^{\text{decode via }N}\check{\mathbf{X}} = N'(\tilde{\mathbf{X}}), (I \times K),\) (15.7)
```