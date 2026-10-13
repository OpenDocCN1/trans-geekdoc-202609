
回顾公式 [(14.28)](#Chp014_717-754_B9780443292385000202.xhtml)，已知：(a) 一个函数 `f(x)`；(b) 一个期望分布 $p(\mathbf{x}) = \frac{1}{Z}\phi(\mathbf{x})$；(c) 一个建议分布 `q(x)`。我们有

$$
\mathbb{E}\left\lbrack f(\mathbf{x}) \right\rbrack := \mu_{f} \approx \sum\limits_{i = 1}^{N}W(\mathbf{x}_{i})f(\mathbf{x}_{i}) := \widehat{\mu},
$$ (17.1)

其中 `x[i]` 是从 `q(x)` 中抽取的样本。回顾一下，估计值

$$
\widehat{Z} = \frac{1}{N}\sum\limits_{i = 1}^{N}w(\mathbf{x}_{i})
$$ (17.2)

对应于真实归一化常数 `Z` 的无偏估计量，其中 `w(x[i])` 是未归一化权重，$w(\mathbf{x}_{i}) = \frac{\phi(\mathbf{x}_{i})}{q(\mathbf{x}_{i})}$。注意，公式 [(17.1)](#Chp017_855-884_B9780443292385000238.xhtml#deq1) 中的近似等价地意味着对期望分布的以下近似：

![Equation](images/B9780443292385000238/fx001.jpg) (17.3)

换句话说，即使是连续的 PDF 也可以用一组离散点及其分配的权重来近似。我们称该分布由粒子 `x[i]`、$i = 1, 2, \dots, N$ 及其相应的归一化权重 `W^((i)) := W(x[i])` 定义的*离散随机测度*来近似。该近似随机测度记为 $\chi = \{\mathbf{x}_{i}, W^{(i)}\}_{i=1}^{N}$。
