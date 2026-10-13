
### 公式推导

$$
\mathbf{\theta}_{k}(n) = \mathbf{\theta}_{k}(n - 1) + \mu_{k}(n)\left\lbrack \mathbf{x}_{k}(n)e_{k}(n) + \lambda\sum\limits_{m \in \mathcal{N}_{k \smallsetminus k}}\left( \mathbf{\theta}_{m}(n - 1) - \mathbf{\theta}_{k}(n - 1) \right) \right\rbrack,
$$

(5.93)

其中

$$
e_{k}(n) := y_{k}(n) - \mathbf{\theta}_{k}^{(T)}(n - 1)\mathbf{x}_{k}(n)
$$

且 $\lambda > 0$。

观察公式 [(5.93)](#Chp005_177-248_B9780443292385000111.xhtml#deq210) 中递归的形式；右侧括号内的项是一个正则化项，其目标是在节点 $k$ 的邻域内强制估计值相等。已有几种替代公式 [(5.93)](#Chp005_177-248_B9780443292385000111.xhtml#deq210) 被提出。例如，文献 [49] 在公式 [(5.93)](#Chp005_177-248_B9780443292385000111.xhtml#deq210) 右侧的共识求和中采用了不同的步长。文献 [99] 提供了以下公式：

$$
\mathbf{\theta}_{k}(n) = \mathbf{\theta}_{k}(n - 1) + \mu_{k}(n)\left\lbrack \mathbf{x}_{k}(n)e_{k}(n) + \sum\limits_{m \in \mathcal{N}_{k \smallsetminus k}}b_{m,k}\left( \mathbf{\theta}_{m}(n - 1) - \mathbf{\theta}_{k}(n - 1) \right) \right\rbrack,
$$

(5.94)
