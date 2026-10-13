
## 8.13 Proximal operators

$$
\mathbf{\theta}_{n} = \mathbf{\theta}_{n - 1} - \frac{\mu_{n}}{n}\sum\limits_{k = 1}^{n}\mathcal{L}_{k}^{\prime}(\mathbf{\theta}_{n - 1}).
$$

![Equation](images/B9780443292385000147/si476.png)(8.101)

*   Variants with different averaging scenarios (e.g., random selection instead of using all previously points) are also around. Such an averaging has a smoothing effect on the convergence of the algorithm. We have already seen this rationale in the context of the PEGASOS algorithm (Section [8.10.3](#Chp008_343-416_B9780443292385000147.xhtml#s0125)). The general trend of all the variants of the basic stochastic gradient scheme is to improve with respect to the involved constants, but the convergence rate still remains $\mathcal{O}(1/n)$.

*   In [50], the online learning rationale was used in the context of data sets of fixed size, $N$. Instead of using the gradient descent scheme in Eq. [(8.98)](#Chp008_343-416_B9780443292385000147.xhtml#deq186), the following version is proposed:

$$
\mathbf{\theta}^{(i)} = \mathbf{\theta}^{(i - 1)} - \frac{\mu_{i}}{N}\sum\limits_{k = 1}^{N}\mathbf{g}_{k}^{(i)},
$$

![Equation](images/B9780443292385000147/si478.png)(8.102)

*   where

$$
\mathbf{g}_{k}^{(i)} = \begin{cases} 
\mathcal{L}_{k}^{\prime}\left( \mathbf{\theta}^{(i - 1)} \right), & \text{if } k = i_{k}, \\ 
\mathbf{g}_{k}^{(i - 1)}, & \text{otherwise}. 
\end{cases}
$$

![Equation](images/B9780443292385000147/si479.png)(8.103)

*   The index $i_{k}$ is randomly chosen every time from $\{1, 2, \dots, N\}$. Thus, in each iteration only one gradient is computed and the rest are drawn from the memory. It turns out that for strongly convex smooth loss functions, the algorithm exhibits linear convergence to the solution of the empirical risk in Eq. [(8.56)](#Chp008_343-416_B9780443292385000147.xhtml#deq122). Of course, compared to the basic online schemes, an $\mathcal{O}(N)$ memory is required for keeping track of the gradient computations.

*   The literature on deriving performance bounds concerning online algorithms is very rich, both in studies and in ideas. For example, another line of research involves bounds for *arbitrary* online algorithms (see [1,19,69] and references therein).
