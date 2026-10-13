
$$
\min_{\theta}\text{MSE}(\theta) \leqslant \min_{\theta:\ \mathbb{E}[\theta] = \theta_{o}}\text{MSE}(\theta),
$$

其中，公式 (3.23) 中 MSE 对估计量 $\theta$ 的依赖关系被显式地标记出来。

令 $\hat{\theta}_{\text{MVU}}$ 表示任务 $\min_{\theta:\ \mathbb{E}[\theta] = \theta_{o}}\text{MSE}(\theta)$ 的一个解。根据公式 (3.22) 可以很容易地验证，$\hat{\theta}_{\text{MVU}}$ 是一个最小方差无偏估计量。这样的估计量被称为*最小方差无偏*（MVU）估计量，我们假设存在这样一个估计量。MVU 估计量并不总是存在（参见 [20]，问题 3.3）。此外，如果它存在，则是唯一的（问题 3.4）。受公式 (3.23) 的启发，我们下一个目标是寻找一个*有偏*估计量，希望它能产生更小的 MSE。令该估计量记为 $\hat{\theta}_{b}$。为了便于说明，并限制对 $\hat{\theta}_{b}$ 的搜索范围，我们在此考虑 $\hat{\theta}_{b}$ 为 $\hat{\theta}_{\text{MVU}}$ 的一个标量倍数，使得

$$
\hat{\theta}_{b} = (1 + \alpha)\hat{\theta}_{\text{MVU}},
$$

其中 $\alpha \in \mathbb{R}$ 是一个自由参数。注意 $\mathbb{E}[\hat{\theta}_{b}] = (1 + \alpha)\theta_{o}$。将公式 (3.24) 代入公式 (3.22) 并经过一些简单的代数运算后，我们得到
