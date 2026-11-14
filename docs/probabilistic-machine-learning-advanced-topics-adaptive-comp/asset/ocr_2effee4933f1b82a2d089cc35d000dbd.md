![](bbox=[0.38, 0.09, 0.63, 0.31])

Figure 5.10: Illustration of the rate-distortion tradeoff. See text for details. From Figure 1 of [Ale+18]. Used with kind permission of Alex Alemi.

For discrete data, all probabilities are bounded above by 1, and hence $H \ge 0$ and $D \ge 0$. In addition, the rate is always non-negative, $R \ge 0$, since it is the average of a KL divergence. (This is true for either discrete or continuous encodings \(\mathbf{z}\).) Consequently, we can plot the set of achievable values of $R$ and $D$ as shown in Figure 5.10. This is known as a **rate distortion curve**.

The bottom horizontal line corresponds to the zero distortion setting, $D = 0$, in which we can perfectly encode and decode our data. This can be achieved by using the trivial encoder where $e(\mathbf{z}|\mathbf{x}) = \delta(\mathbf{z} - \mathbf{x})$. Shannon's source coding theorem tells us that the minimum number of bits we need to use to encode data in this setting is the entropy of the data, so $R \ge H$ when $D = 0$. If we use a suboptimal marginal distribution \(m(\mathbf{z})\) for coding, we will increase the rate without affecting the distortion.

The left vertical line corresponds to the zero rate setting, $R = 0$, in which the latent code is independent of \(\mathbf{z}\). In this case, the decoder \(d(\mathbf{x}|\mathbf{z})\) is independent of \(\mathbf{z}\). However, we can still learn a joint probability model \(p(\mathbf{x})\) which does not use latent variables, e.g., this could be an autoregressive model. The minimal distortion such a model could achieve is again the entropy of the data, \(D \ge H\).

The black diagonal line illustrates solutions that satisfy \(D = H - R\), where the upper and lower bounds are tight. In practice, we cannot achieve points on the diagonal, since that requires the bounds to be tight, and therefore assumes our models \(e(\mathbf{z}|\mathbf{x})\) and \(d(\mathbf{x}|\mathbf{z})\) are perfect. This is called the “non-parametric limit”. In the finite data setting, we will always incur additional error, so the RD plot will trace a curve which is shifted up, as shown in Figure 5.10.

We can generate different solutions along this curve by minimizing the following objective:

```
$J = D + \beta R = \int d\mathbf{x} \ p(\mathbf{x}) \int d\mathbf{z} \ e(\mathbf{z}|\mathbf{x}) \left[ - \log d(\mathbf{x}|\mathbf{z}) + \beta \log \frac{e(\mathbf{z}|\mathbf{x})}{m(\mathbf{z})} \right]$ (5.160)
```

If we set \(\beta = 1\), and define \(q(\mathbf{z}|\mathbf{x}) = e(\mathbf{z}|\mathbf{x})\), \(p(\mathbf{x}|\mathbf{z}) = d(\mathbf{x}|\mathbf{z})\), and \(p(\mathbf{z}) = m(\mathbf{z})\), this exactly matches the VAE objective in Section 21.2. To see this, note that the ELBO from Section 10.1.1.2 can be written as

```
$\mathbb{L} = -(D + R) = \mathbb{E}_{p(\mathbf{x})} \left[ \mathbb{E}_{e(\mathbf{z}|\mathbf{x})} [\log d(\mathbf{x}|\mathbf{z})] - \mathbb{E}_{e(\mathbf{z}|\mathbf{x})} \left[ \log \frac{e(\mathbf{z}|\mathbf{x})}{m(\mathbf{z})} \right] \right]$ (5.161)
```