
### 12.8.1 The exponential family and the maximum entropy method

Besides the computational advantages associated with the exponential family, there is another reason that justifies its high popularity. Assume that we are given a set of observations, $x_n \in \mathcal{A}_x \subseteq \mathbb{R}$, $n = 1, 2, \dots, N$, drawn from a distribution whose functional form is unknown. Our goal is to estimate the unknown PDF; however, we require that it will respect certain empirical expectations, which are computed from the available observations, that is,

$$
\widehat{\mu}_i := \frac{1}{N}\sum_{n=1}^{N}u_i(x_n), \quad i \in \mathcal{I},
$$

(12.89)
