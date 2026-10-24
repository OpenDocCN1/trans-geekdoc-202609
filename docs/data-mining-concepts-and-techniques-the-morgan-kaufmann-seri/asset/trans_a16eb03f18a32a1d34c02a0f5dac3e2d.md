

## A.4.3 互信息

在信息论中，两个随机变量的*互信息*衡量的是在已知观察到另一个随机变量的前提下，我们对某个随机变量所获得的信息量。给定两个随机变量 \( X \) 和 \( Y \)，随机变量 \( X \) 和 \( Y \) 的互信息 \( I(X; Y) \) 总结如下：

\( I(X; Y) = \mathbb{E}_{(x,y) \sim p_{XY}} [\log \frac{p_{XY}(x, y)}{p_X(x) p_Y(y)} ] \
= \begin{cases} \sum_{(x,y)} p_{XY}(x, y) \log \frac{p_{XY}(x,y)}{p_X(x)p_Y(x)}, & \quad X, Y \text{ are discrete r.v.} \\ \int_{(x,y) \sim p_{XY}} p_{XY}(x, y) \log \frac{p_{XY}(x,y)}{p_X(x)p_Y(x)} dx dy, & \quad X, Y \text{ are continuous r.v.} \end{cases} \) (A.74)

其中 \( p_{XY} \) 是联合随机变量 \( (X, Y) \) 的联合分布，\( p_X \) 是随机变量 \( X \) 的边缘分布，\( p_Y \) 是随机变量 \( Y \) 的边缘分布。

### 互信息与KL散度的关系

从KL散度的角度来看，两个随机变量 \( X \) 和 \( Y \) 的互信息 \( I(X; Y) \) 等价于联合分布 \( p_{XY} \) 与其边缘分布乘积 \( p_X \otimes p_Y \) 之间的KL散度。互信息与KL散度的关系总结如下：

\( I(X; Y) = D_{KL}(p_{XY} || p_X \otimes p_Y). \) (A.75)

### 互信息与熵的关系

从熵的角度来看，两个随机变量的互信息衡量的是通过观察另一个随机变量，我们在某个随机变量中损失了多少不确定性。互信息与熵的关系总结如下：

\( I(X; Y) = H(X) - H(X|Y) = H(Y) - H(Y|X) = H(X) + H(Y) - H(X, Y), \) (A.76)

其中最后一个等式通过应用熵的链式法则得出。

### 条件互信息

给定三个随机变量 \( X \)、\( Y \) 和 \( Z \)，给定随机变量 \( Z \) 时随机变量 \( X \) 和 \( Y \) 的条件互信息总结如下：

\( I(X; Y|Z) = \mathbb{E}_{(x,y,z) \sim p_{XYZ}} [\log \frac{p_{X,Y|Z}(x, y|z)}{p_{X|Z}(x|z) p_{Y|Z}(y, z)}] = H(X|Z) - H(X|Y, Z). \) (A.77)

## 互信息的性质。

- 互信息非负，即 \( I(X; Y) \ge 0, \forall X, Y \)。
- 互信息具有对称性，即 \( I(X; Y) = I(Y; X) \)。
- 一个随机变量与其自身的互信息即为该随机变量的熵，即 \( I(X; X) = H(X) \)。
- 两个独立随机变量的互信息为0，即若 \( X \) 与 \( Y \) 独立，则 \( I(X; Y) = 0 \)。
- 互信息遵循链式法则，即 \( I(X; Y, Z) = I(X; Y) + I(X; Z|Y) \)，其中 \( I(X; Y, Z) \) 是 \( X \) 与联合随机变量 \( (Y, Z) \) 的互信息。
- 数据处理不等式。假设随机变量 \( Y \) 是通过对随机变量 \( X \) 应用某个函数 \( f \) 得到的（即 \( Y = f(X) \)），且随机变量 \( Z \) 是通过处理随机变量 \( Y \) 得到的（例如，对随机变量 \( Y \) 应用某个函数 \( g \) 以得到 \( Z = g(Y) \)）。数据处理不等式保证 \( X \) 与 \( Z \) 之间的互信息永远不会大于 \( X \) 与 \( Y \) 之间的互信息。在数学上，给定三个随机变量的马尔可夫链 \( X \rightarrow Y \rightarrow Z \)，有

\( I(X; Z) \le I(X; Y), \)

其中等号当且仅当 \( I(X; Y|Z) = 0 \) 时成立。

- 两个随机变量的*信息变分*（是一种度量）可以通过它们的互信息和联合熵推导出来，即 \( d(X, Y) = H(X, Y) - I(X; Y) \)。

## A.4.4 离散傅里叶变换（DFT）和快速傅里叶变换（FFT）

除非另有说明，本节中我们使用序列表示离散时间序列，并使用 \( N \) 表示有限离散时间序列的长度或周期性离散时间序列的周期长度。

### 有限序列

长度为 \( N \) 的*有限序列* \( x[n] \) 为以下形式的序列³：

\( x[n] = \begin{cases} \text{some number}, & 0 \le n \le N - 1 \\ 0, & \text{otherwise.} \end{cases} \)

### 有限序列与周期序列的关系

直观地，任何有限序列 \( x[n] \) 都与一个对应的周期序列 \( \tilde{x}[n] \) 相关联，即

\( \tilde{x}[n] = \sum_{t=-\infty}^{+\infty} x[n - tN] = x[(n \text{ mod. } N)], \)

其中 mod. 为取模运算。

同样，有限序列 \( x[n] \) 总可以从其对应的周期序列 \( \tilde{x}[n] \) 中提取出来，即

\( x[n] = \begin{cases} \tilde{x}[n], & n \in \{0, \dots, N - 1\} \\ 0, & \text{otherwise.} \end{cases} \)

## 周期序列的离散傅里叶级数（DFS）。

给定周期为 \( N \) 的周期序列 \(\tilde{x}[n]\)，周期序列 \(\tilde{x}[n]\) 的DFS \(\tilde{X}[k]\)（\(k \in \{0, \dots, N-1\}\)）的分析方程和合成方程总结如下⁴：

分析方程：\(\tilde{X}[k] = \sum_{n=0}^{N-1} e^{-i(2\pi/N)kn} \tilde{x}[n]\)

合成方程：\(\tilde{x}[n] = \sum_{k=0}^{N-1} e^{i(2\pi/N)kn} \tilde{X}[k]\)。

## 有限序列的DFT。

由于有限序列 \(x[n]\) 是周期序列 \(\tilde{x}[n]\) 的一个周期，为了保持时频域的对偶性，有限序列 \(x[n]\) 的DFT \(X[k]\) 对应于其对应周期序列 \(\tilde{x}[n]\) 的DFS \(\tilde{X}[k]\) 的一个周期。因此，有限序列 \(x[n]\) 的DFT \(X[k]\) 的分析方程和合成方程总结如下：

分析方程：\(X[k] = \sum_{n=0}^{N-1} e^{-i(2\pi/N)kn} x[n]\)

合成方程：\(x[n] = \sum_{k=0}^{N-1} e^{i(2\pi/N)kn} X[k]\)。

值得注意的是，矩阵 \(\mathbf{W}\)（其中 \(\mathbf{W}[i, j] = e^{-i(2\pi/N)ij}\)）称为*DFT矩阵*。

## DFT的性质。

- 线性。给定两个有限序列 \(x_1[n], x_2[n]\) 及其对应的DFT \(X_1[k], X_2[k]\)，若 \(x_3[n] = ax_1[n] + bx_2[n]\)，则 \(x_3[n]\) 的DFT 为

\(X_3[k] = aX_1[k] + bX_2[k]\)。

- 给定有限序列 \(x[n]\) 及其DFT \(X[k]\)，若在时间窗口中进行长度为 \(m\) 的循环移位并得到新的有限序列 \(x_1[n] = x((n - m) \text{ mod. } N))\)，则新的有限序列 \(x_1[k]\) 的DFT 为

\(X_1[k] = e^{-i(2\pi/N)km} X[k]\)。

- 向量 \(\mathbf{u}_k = [e^{-i(2\pi/N)k0}, e^{-i(2\pi/N)k1}, \dots, e^{-i(2\pi/N)k(N-1)}]\) 在 \(N\) 维复向量集合上构成一组正交基，即 \(\mathbf{u}_k^T \mathbf{u}_k^* = N\)。

- 帕塞瓦尔定理。给定两个序列 \(x_1[n]\) 和 \(x_2[n]\) 及其对应的DFT \(X_1[k]\) 和 \(X_2[k]\)，有

\(\sum_{n=0}^{N-1} x_1[n]x_2^*[n] = \frac{1}{N} \sum_{k=0}^{N-1} X_1[k]X_2^*[k]\),

其中 \(x_2^*[n]\) 是序列 \(x_2[n]\) 的共轭转置，\(X_2^*[k]\) 是 \(X_2[k]\) 的共轭转置。

- 对偶性。给定序列 \(x[n]\) 及其DFT \(X[k]\)，则 \(X[k]\) 的DFT 为 \(Nx[(-k \text{ mod. } N)]\)

- 对于有限序列 \(x[n]\) 及其DFT \(X[k]\)，若所有值均为实数，则有

\(X[k] = X^*[(-k \text{ mod. } N)],\) (A.87)

这称为*偶对称*。这里，\(X^*[k]\) 是 \(X[k]\) 的共轭转置；若所有值均为虚数，则有

\(X[k] = -X^*[(-k \text{ mod. } N)],\) (A.88)

这称为*奇对称*。

- 给定三个有限序列 \(x_1[n]\)、\(x_2[n]\) 和 \(x_3[n]\) 及其对应的DFT \(X_1[k]\)、\(X_2[k]\) 和 \(X_3[k]\)，若 \(X_3[k] = X_1[k]X_2[k]\)，则有

\(x_3[n] = \sum_{m=0}^{N-1} x_2[m]x_1[((n-m) \text{ mod. } N)].\) (A.89)

### FFT

FFT 是一组高效计算有限序列DFT的算法，其理论基础涵盖从算术到数论等多个领域。FFT 在数学、工程和音乐等众多实际场景中得到广泛应用。FFT 的关键原理是将长度为 \( N \) 的序列的DFT计算分解为若干个更小子序列的计算。一些代表性的FFT算法包括质因数算法（PFA）、Cooley-Tukey 算法、Goertzel 算法和 Winograd 算法。关于FFT算法的详细内容，请参阅参考文献注释。

## A.5 参考文献注释

概率密度函数（PDF）和显著性检验在许多统计学教材中有所介绍（Larsen and Marx [LM05] 和 Casella and Berger [CB21]）。关于 MLE 和 MAP，许多机器学习教材有所涵盖（Bishop [Bis06b] 和 James, Witten, Hastie, and Tibshirani [JWHT]）。交叉验证由 Bishop [Bis06b] 描述，而 Jackknife 由 Barber, Candes, Ramdas, and Tibshirani [BCRT21] 介绍。GD、SGD、GD 的变体、坐标下降法和牛顿法在许多入门和进阶教材中有所介绍，例如 Goodfellow, Bengio, and Courville [GBC16] 和 Boyd, Boyd, and Vandenberghe [BBV04]。Dennis and Moré 对准牛顿方法提供了详细的综述 [DM77]。关于二次规划（QP），由 Boyd, Boyd, and Vandenberghe [BBV04] 系统介绍。QP 的解法多种多样，例如主动集法（Murty and Yu [MY88]）、内点法（Wright [Wri97]）等。关于线性代数的基本概念、理论和应用，由 Strang [Str93, Str19] 和 Leon, Bica, and Hohn [LBH06] 全面介绍。

密度估计旨在近似底层概率密度函数，一直是统计学教材中的重要主题（Silverman [Sil18] 和 Devroye and Lugosi [DL12]）。基于核技巧的密度估计在相关研究工作中得到广泛探讨（Botev, Grotowski,

