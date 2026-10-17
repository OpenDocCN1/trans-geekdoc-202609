
| *D* − `std` || 1.1424 || 1.0787 || 1.1133 || 1.0887 || 1.1053 |

| *I* − `mean` || 48.6890 || 47.3009 || 48.2036 || 47.4963 || 47.8111 |

| *I* − `std` || 2.0383 || 2.0673 || 2.0253 || 2.0554 || 2.0402 |

Table 11.19: 热喀斯特湖泊面积演化的预测至 2022 年。

| --- |
| Year || 2018 || 2019 || 2020 || 2021 || 2022 |
| --- |
| *C* − `mean` || 19.6453 || 19.5491 || 19.4576 || 19.3742 || 19.3070 |
| *C* − `std` || 0.6367 || 0.5969 || 0.5569 || 0.5215 || 0.4901 |
| *D* − `mean` || 19.6215 || 19.6897 || 19.6372 || 19.6780 || 19.6546 |
| *D* − `std` || 1.0913 || 1.0979 || 1.0885 || 1.0911 || 1.0867 |
| *I* − `mean` || 47.5081 || 47.6778 || 47.6040 || 47.6912 || 47.6729 |
| *I* − `std` || 2.0584 || 2.0421 || 2.0484 || 2.0405 || 2.0443 |

Figure 11.18 展示了区域 *C*, *D* 和 *I* 的预测集合。这里均值轨迹和标准差区域分别用 (`mean`) 和 (`std`) 标示。

![Figure 11.18: Forecast for 15 years.](img/fig11_18.jpg)

Figure 11.18: 15 年预测。

本文预测的湖泊面积演化以均值 (Table 11.17、Table 11.18、Table 11.19) 和 2 至 4.5% 的标准差为特征。此外，区域 *D* 和 *I* 的图表 (Fig. 11.17) 具有振荡过程，在 2018 年后达到恒定水平。

# 附录 A 最大熵估计 (MEE) 及其渐近效率

DOI: [10.1201/9781003306566-A](https://doi.org/10.1201/9781003306566-A)

## A.1 最大熵估计问题的陈述

考虑一个标量连续函数 `φ`(`x`, `θ`)，其参数为 `θ` = {`θ`[1],…,`θ`[*n*]}。假设该函数是具有输入 `x` 和输出 `y` 的对象模型的一个特征。设 `x`^((*r*)) = {`x`[1],…,`x`[*r*]} 和 `y`^((*r*)) = {`y`[1],…,`y`[*r*]} 为给定的测量值。注意后者是在随机误差 `ξ` = {`ξ`[1],…,`ξ`[*r*]} 下获得的，在一般情况下，不同时间瞬时不同。

因此，经过 `r` 次测量后，模型和观测由方程描述

$$
\begin{aligned}
\hat{\mathbf{y}} & {= \Gamma(\mathbf{x}^{(r)},\theta),} \\
\hat{\mathbf{v}} & {= \hat{\mathbf{y}} + \xi,} \\
\end{aligned}
$$

(A.1)

其中向量函数 `Γ`(`x`^((*r*)), `θ`) 的分量为 $\varphi(x\lbrack t\rbrack,\theta),\, t = \overline{1,r};$ $\hat{\mathbf{v}}$ 表示包含对象输出测量噪声的模型观测输出。

估计问题表述如下：*求最大化广义信息熵泛函的 PDFs `P*`(`θ`) 和 `Q*`(`ξ`) 的最大熵估计*

$$
\begin{aligned}
& {\mathcal{H}\lbrack P(\theta),Q(\xi)\rbrack = - {\int_{Q}P}(\theta)\ln P(\theta)d\theta -} \\
& \left. \quad - {\sum\limits_{t = 1}^{r}{\int_{\Xi_{t}}Q_{t}}}(\xi\lbrack t\rbrack)\ln Q_{t}(\xi\lbrack t\rbrack)\Rightarrow\max \right. \\
\end{aligned}
$$

(A.5)

*受以下条件约束*

* —由下式给出的 PDFs 的归一化条件

$$
\begin{array}{r}
{{\int_{\Theta}P}(\theta)d\theta = 1;\quad{\int_{\Xi_{t}}Q_{t}}(\xi\lbrack t\rbrack)d\xi\lbrack t\rbrack = 1,\, t = \overline{1,r}.} \\
\end{array}
$$

(A.6)

和

* —经验平衡条件

$$
\begin{aligned}
& {\Phi\lbrack P(\theta),Q(\xi)\rbrack = \mathbf{y}^{(r)},} \\
{\Phi\lbrack P(\theta),Q(\xi)\rbrack =} & \left\{ \Phi_{1}\lbrack P(\theta),Q(\xi)\rbrack,\ldots,\Phi_{r}\lbrack P(\theta),Q(\xi)\rbrack \right\} \\
{\Phi_{t}\lbrack P(\theta),Q(\xi)\rbrack = \int_{\Theta}} & {\varphi(x\lbrack t\rbrack,\theta)P(\theta)d\theta + \int_{\Xi_{t}}Q_{t}(\xi\lbrack t\rbrack)\xi\lbrack t\rbrack d\xi\lbrack t\rbrack,} \\
& {\text{\quad\quad}\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.7)

优化问题 (A.1–A.1) 是 Lyapunov 型 [77, 174]：此类问题具有积分泛函和积分约束。因此，模型参数和测量噪声的熵最优 PDF 具有形式

$$
\begin{aligned}
\left. P^{\*}(\theta\, \middle| \,\mathbf{y}^{(r)}\,\mathbf{x}^{(r)}) \right. & {\frac{\exp\left( {- {\sum\limits_{j = 1}^{r}\lambda_{j}}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)}{\mathcal{P}(\lambda(\mathbf{y}^{(r)}),\mathbf{x}^{(r)})},} \\
\left. Q_{t}^{\*}(\xi\lbrack t\rbrack\, \middle| \,\mathbf{y}^{(r)}\,\mathbf{x}^{(r)}) \right. & {\frac{\exp\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\xi\lbrack t\rbrack} \right)}{\mathcal{Q}_{t}(\lambda_{t}(\mathbf{y}^{(r)}),\mathbf{x}^{(r)})},\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.8)

其中

$$
\begin{aligned}
{\mathcal{P}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)}) = \int_{\Theta}} & {\exp\left( {- \sum_{j = 1}^{r}\lambda_{j}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta,} \\
{\mathcal{Q}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})} & {\int_{\Xi_{t}}\exp\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\xi\lbrack t\rbrack} \right)d\xi\lbrack t\rbrack,} \\
& {\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.9)

由于等式 (A.1) 和 (A.1)，熵最优 PDF 由拉格朗日乘子 `λ`[1],…, `λ`[*r*] 参数化，其代表经验平衡方程的解

$$
\begin{array}{r}
{\frac{\mathcal{G}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))}{\mathcal{P}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))} + \frac{\mathcal{E}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))}{\mathcal{Q}_{t}\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})} \right)} = y\lbrack t\rbrack,\quad t = \overline{1,r},} \\
\end{array}
$$

(A.10)

其中

$$
\begin{aligned}
{\mathcal{G}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)})) = \int_{\Theta}} & {\varphi(x\lbrack t\rbrack,\theta)\exp\left( {- \sum_{j = 1}^{r}\lambda_{j}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta,} \\
{\mathcal{E}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))} & {\int_{\Xi_{t}}\exp\left( {- \lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\xi\lbrack t\rbrack} \right)d\xi\lbrack t\rbrack,} \\
& {\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.11)

这些方程的解 `λ*`(`y`^((*r*))), `x`^((*r*))) 依赖于用于构建 PDF 最大熵估计的样本 (`y`^((*r*))), `x`^((*r*))。

## A.2 隐式函数 `θ`(`\widetilde{\mathbf{y}}^{(r)}`, `x^{(r)}`) 的存在性

根据平衡方程 (A.10), (A.1)，其第二项是每次测量 `t` 中噪声的均值。噪声及其特征通常被假定为与测量无关，即在表达式 (A.3) 中，

$$
\begin{array}{r}
{\Xi_{t} = \Xi = \lbrack\xi^{-},\xi^{+}\rbrack.} \\
\end{array}
$$

(A.12)

因此，噪声的均值由下式给出

$$
\begin{array}{r}
{\overline{\xi} = \frac{\mathcal{E}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))}{\mathcal{Q}_{t}\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})} \right)} \in \Xi.} \\
\end{array}
$$

(A.13)

平衡方程可以写成

$$
\begin{aligned}
& \left. \quad W_{t}(\lambda\, \middle| \,\widetilde{y}\lbrack t\rbrack,\mathbf{x}^{(r)}) = {\int_{\Theta}\left( {\varphi(x\lbrack t\rbrack,\theta) - \widetilde{y}\lbrack t\rbrack} \right)} \times \right. \\
& {\times \exp\left( {- {\sum\limits_{j = 1}^{r}\lambda_{j}}({\widetilde{\mathbf{y}}}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta = 0,} \\
& {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}t = \overline{1,r},} \\
\end{aligned}
$$

(A.14)

其中

$$
\begin{array}{r}
{\widetilde{y}\lbrack t\rbrack = y\lbrack t\rbrack - \overline{\xi},\text{\quad\quad}{\widetilde{\mathbf{y}}}^{(r)} = \left\{ \widetilde{y}\lbrack 1\rbrack,\ldots,\widetilde{y}\lbrack r\rbrack \right\}.} \\
\end{array}
$$

(A.15)

在向量形式中，方程 (A.2) 由下式描述

$$
\begin{array}{r}
\left. \mathbf{W}(\lambda\, \middle| \,,{\widetilde{\mathbf{y}}}^{(r)},\mathbf{x}^{(r)}) = \mathbf{0}. \right. \\
\end{array}
$$

(A.16)

方程 (A.16) 定义了一个隐式函数 `λ`(`\widetilde{\mathbf{y}}^{(r)}`, `x^{(r)}`)。该隐式函数的存在性和性质取决于雅可比矩阵的性质

$$
\begin{array}{r}
\left. J_{\lambda}(\lambda\, \middle| \,\mathbf{y}^{(r)},\mathbf{x}^{(r)}) = \left\lbrack \frac{\partial W_{t}}{\partial\lambda_{i}},\, \middle| \,(t,i) = \overline{1,r} \right\rbrack, \right. \\
\end{array}
$$

(A.17)

其元素为

$$
\begin{aligned}
& {\frac{\partial W_{t}}{\partial\lambda_{i}} = {\int_{Q}\left( {\varphi(x\lbrack t\rbrack,\theta) - \widetilde{y}\lbrack t\rbrack} \right)}\varphi(x\lbrack i\rbrack,\theta) \times} \\
& {\quad \times {\sum\limits_{j = 1}^{r}\exp}\left( {- {\sum\limits_{j = 1}^{r}\lambda_{j}}\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta.} \\
\end{aligned}
$$

(A.18)

## A.3 最大熵估计的渐近有效性

MEE 给出输入和输出数据数组的熵最优 PDFs（A.1），每个数组的大小为 *r*。为方便起见，考虑由指数拉格朗日乘子 *z* = exp ( − *λ*) 参数化的 PDFs。则等式 (A.1) 取形式
