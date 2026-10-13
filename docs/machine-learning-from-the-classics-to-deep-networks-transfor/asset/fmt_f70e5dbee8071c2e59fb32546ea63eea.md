
### 7. 8.28

Consider the online version of PDMb in Eq. [(8.64)](#Chp008_343-416_B9780443292385000147.xhtml#deq138), that is,

$$
\mathbf{\theta}_{n} = \begin{cases} 
P_{C}\left( \mathbf{\theta}_{n - 1} - \mu_{n}\frac{J(\mathbf{\theta}_{n - 1})}{||J^{\prime}(\mathbf{\theta}_{n - 1})||^{2}}J^{\prime}(\mathbf{\theta}_{n - 1}) \right), & \text{if } J^{\prime}(\mathbf{\theta}_{n - 1}) \neq 0, \\
P_{C}(\mathbf{\theta}_{n - 1}), & \text{if } J^{\prime}(\mathbf{\theta}_{n - 1}) = 0,
\end{cases}
$$

(8.144)

1.  where we have assumed that `J[*] = 0`. If this is not the case, a shift can accommodate for the difference. Thus, we assume that we know the minimum. For example, this is the case for a number of tasks, such as the hinge loss function, assuming linearly separable classes, or the linear `ϵ`-insensitive loss function, for bounded noise. Assume that

$$
\mathcal{L}_{n}(\mathbf{\theta}) = \sum\limits_{k = n - q + 1}^{n}\frac{\omega_{k}d_{C_{k}}(\mathbf{\theta}_{n - 1})}{\sum_{k = n - q + 1}^{n}\omega_{k}d_{C_{k}}(\mathbf{\theta}_{n - 1})}d_{C_{k}}(\mathbf{\theta}).
$$

1.  Then derive the APSM algorithm of Eq. [(8.39)](#Chp008_343-416_B9780443292385000147.xhtml#deq74).

### 2. 8.29

Derive the regret bound for the subgradient algorithm in [(8.83)](#Chp008_343-416_B9780443292385000147.xhtml#deq164).
