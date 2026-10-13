
$$
\mathcal{E}_{\text{appr}} + \mathcal{E}_{\text{est}} + \mathcal{E}_{\text{opt}} \sim \mathcal{E}_{\text{appr}} + \left( \frac{\ln N}{N} \right)^{a} + \rho,\quad a \in \left\lbrack \frac{1}{2},1 \right\rbrack,
$$

which verifies the fact that as $N \to \infty$ the estimation error decreases and provides a rule for the respective convergence rate. The excess error $\mathcal{E}$, besides the approximation component, on which we have no access to control (given the family of functions, $\mathcal{F}$), it depends on (a) the number of data and (b) the accuracy, $\rho$, associated with the algorithm used. How one can control these parameters depends on the type of learning task at hand.

*   **Small-scale tasks**: These types of tasks are constrained by the number of training points, $N$. In this case, one can reduce the optimization error, since computational load is not a problem, and achieve the minimum possible estimation error, as this is allowed by the number of available training points. In this case, one achieves the approximation–estimation tradeoff.

*   **Large-scale/big data tasks**: These types of tasks are constrained by the computational resources. Thus, a computationally cheap and less accurate algorithm may end up with lower excess error, since it has the luxury of exploiting more data, compared to a more accurate yet computationally more complex algorithm, given the maximum allowed computational load.

### Batch versus online learning

Our interest in this subsection lies in investigating whether there is a performance loss if in place of a batch algorithm an online one is used. There is a very subtle issue involved here, which turns out to be very important from a practical point of view. We will restrict our discussion to differentiable convex loss functions.

Two major factors associated with the performance of an algorithm (in a stationary environment) are its convergence rate and its accuracy after convergence. The general form of a batch algorithm in minimizing Eq. [(8.66)](#Chp008_343-416_B9780443292385000147.xhtml#deq140) is written as

$$
\boldsymbol{\theta}^{(i)} = \boldsymbol{\theta}^{(i - 1)} - \mu_{i}\Phi_{i}\nabla J_{N}\left( \boldsymbol{\theta}^{(i - 1)} \right) = \boldsymbol{\theta}^{(i - 1)} - \frac{\mu_{i}}{N}\Phi_{i}\sum\limits_{n = 1}^{N}\mathcal{L}^{\prime}\left( \boldsymbol{\theta}^{(i - 1)},y_{n},\mathbf{x}_{n} \right).
$$
