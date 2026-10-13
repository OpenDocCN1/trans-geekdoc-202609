
$$
\var\left\lbrack \widehat{Z} \right\rbrack = \frac{Z^{2}}{N}\left( \int\frac{p^{2}(\mathbf{x})}{q(\mathbf{x})}d\mathbf{x} - 1 \right).
$$

![Equation](images/B9780443292385000238/si24.png)

### 17.3
Show that using resampling in importance sampling, as the number of particles tends to infinity, the approximating, by the respective discrete random measure, distribution, $\overline{p}$![Equation](images/B9780443292385000238/si267.png), tends to the true (desired) one, $p$.

**Hint**: Consider the one-dimensional case.

### 17.4
Show that in sequential importance sampling, the proposal distribution that minimizes the variance of the weights at time $n$, conditioned on $\mathbf{x}_{1:n-1}$![Equation](images/B9780443292385000238/si73.png), is given by

$$q_{n}^{\text{opt}}(\mathbf{x}_{n}|\mathbf{x}_{1:n-1}) = p_{n}(\mathbf{x}_{n}|\mathbf{x}_{1:n-1}).$$

![Equation](images/B9780443292385000238/si268.png)

### 17.5
In a sequential importance sampling task, let

$$p_{n}(\mathbf{x}_{1:n}) = \prod\limits_{k = 1}^{n}\mathcal{N}(x_{k}|0,1),\quad \phi_{n}(\mathbf{x}_{1:n}) = \prod\limits_{k = 1}^{n}\exp\left( - \frac{x_{k}^{2}}{2} \right),$$

![Equation](images/B9780443292385000238/si269.png)

and let the proposal distribution be

$$q_{n}(\mathbf{x}_{1:n}) = \prod\limits_{k = 1}^{n}\mathcal{N}(x_{k}|0,\sigma^{2}).$$

![Equation](images/B9780443292385000238/si270.png)
