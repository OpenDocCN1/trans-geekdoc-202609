# 19.5.2 Weighted ERM for covariate shift

In this section we reconsider the risk minimization objective in Equation (19.8), but leverage unlabeled data from the target distribution to estimate it. If we make the covariate shift assumption (i.e., $q(\boldsymbol{x}, \boldsymbol{y}) = q(\boldsymbol{x})p(\boldsymbol{y}|\boldsymbol{x})$), then we have

$R(f, q) = \int q(\boldsymbol{x})q(\boldsymbol{y}|\boldsymbol{x})\ell(\boldsymbol{y}, f(\boldsymbol{x}))dxdy$
$= \int q(\boldsymbol{x})p(\boldsymbol{y}|\boldsymbol{x})\ell(\boldsymbol{y}, f(\boldsymbol{x}))dxdy$
$= \int \frac{q(\boldsymbol{x})}{p(\boldsymbol{x})}p(\boldsymbol{x})p(\boldsymbol{y}|\boldsymbol{x})\ell(\boldsymbol{y}, f(\boldsymbol{x}))dxdy$
$\approx \frac{1}{N} \sum_{(\boldsymbol{x}_n, \boldsymbol{y}_n) \in \mathcal{D}_L^t} w_n \ell(\boldsymbol{y}_n, f(\boldsymbol{x}_n))$

where the weights are given by the ratio

$w_n = w(\boldsymbol{x}_n) = \frac{q(\boldsymbol{x}_n)}{p(\boldsymbol{x}_n)}$

Thus we can solve the covariate shift problem by using **weighted ERM** [Shi00a; SKM07].

However, this raises two questions. First, why do we need to use this technique, since a discriminative model $p(\boldsymbol{y}|\boldsymbol{x})$ should work for any input $\boldsymbol{x}$, regardless of which distribution it comes from? Second, given that we do need to use this method, in practice how should we estimate the weights $w_n = w(\boldsymbol{x}_n) = \frac{q(\boldsymbol{x}_n)}{p(\boldsymbol{x}_n)}$? We discuss these issues below.

# 19.5.2.1 Why is covariate shift a problem for discriminative models?

For a discriminative model of the form $p(\boldsymbol{y}|\boldsymbol{x})$, it might seem that such a change in $p(\boldsymbol{x})$ will not affect the predictions. If the predictor $p(\boldsymbol{y}|\boldsymbol{x})$ is the correct model for all parts of the input space $\boldsymbol{x}$, then this conclusion is warranted. However, most models will only be accurate in certain parts of the input space. This is illustrated in Figure 19.10b, where we show that a linear model fit to the source distribution may perform much worse on the target distribution than a model that weights target points more heavily during training.

# 19.5.2.2 How should we estimating the ERM weights?

One approach to estimating the ERM weights $w_n = w(\boldsymbol{x}_n) = \frac{q(\boldsymbol{x}_n)}{p(\boldsymbol{x}_n)}$ is to learn a density model for the source and target. However, density estimation is difficult for high dimensional features. An alternative approach is to try to approximate the density ratio, by fitting a binary classifier to distinguish the two distributions, as discussed in Section 2.7.5. In particular, suppose we have an equal number of samples from $p(\boldsymbol{x})$ and $q(\boldsymbol{x})$. Let us label the first set with $c = -1$ and the second set with $c = 1$. Then we have

$p(c = 1|\boldsymbol{x}) = \frac{q(\boldsymbol{x})}{q(\boldsymbol{x}) + p(\boldsymbol{x})}$