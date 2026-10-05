

值 `$q = {\sum\limits_{k = 1}^{s}i_{k}}$` 称为矩函数的阶。在矩函数类中，阶为 1 和 2 的矩函数占有特殊地位，即

### 均值

$$
\begin{array}{r} {m(t_{1}) = m_{1}(t_{1}) = \mathcal{M}\left\{ x(t_{1}) \right\};} \\ \end{array}
$$

(2.20)

### 相关函数

$$
\begin{array}{r} {R(t_{1},t_{2}) = m_{11}(t_{1},t_{2}) = \mathcal{M}\left\{ \lbrack x(t_{1}) - m(t_{1})\rbrack\lbrack x(t_{2}) - m(t_{2})\rbrack \right\}.} \\ \end{array}
$$

(2.21)

若 `t[1] = t[2] = t`，则 `R(t, t) = sigma^2` 为固定 `t` 时随机变量 `x(t)` 的方差。若 `R(t[1], t[2]) = 0`，则随机函数 `x(t)` 的取值 `x(t[1])` 和 `x(t[2])` 不相关。在随机变量 `x(t[1])` 和 `x(t[2])` 的二维联合概率分布为高斯且不相关条件成立的特殊情形下，随机变量 `x(t[1])` 和 `x(t[2])` 相互独立。

连续性是函数的重要性质。对于随机函数，该性质具有概率意义，可形式化为所有对 `x(t[1]), x(t[2])` 的分布。在集合 `mathcal{T}` 上引入距离 `rho(t[1],t[1])=|t[1]-t[2]|`。随机函数 `x(t), t in mathcal{T}`, 在点 `t^*` 处称为 *随机连续* 的，如果对所有 `epsilon > 0`，

$$
\begin{array}{r} \left. \mathbf{P}\left\{ \middle| x(t^{*}) - x(t) \middle| > \varepsilon \right\}\rightarrow 0\quad\text{as}\,\,\rho(t^{*},t)\rightarrow 0. \right. \\ \end{array}
$$

(2.22)

若条件 (2.22) 对所有值 `t in mathcal{T}` 成立，则相应函数 `x(t)` 在 `mathcal{T}` 上随机连续。

根据定义 (2.22)，随机连续性是一种“渐近”性质，仅需声明。更具构造性的定义应涉及某些定量值。事实上，*一致随机连续性* 构成了这种性质。随机函数在 `mathcal{T}` 上一致随机连续，如果对任意 `epsilon > 0`，存在 `delta > 0` 使得

$$
\begin{array}{r} {\mathbf{P}\left\{ \middle| x(t) - x(\widetilde{t}) \middle| > \varepsilon \right\} < \varepsilon} \\ \end{array}
$$

(2.23)

对满足不等式 `rho(t, tilde{t}) < epsilon` 的所有对 `(t, tilde{t})` 成立。

由于集合 `mathcal{T}` 是紧的，随机函数在 `mathcal{T}` 上的随机连续性蕴含其在 `mathcal{T}` 上的一致随机连续性。

考虑若干类随机函数（过程）。

## 1. 高斯随机函数

在许多应用中，具有高斯有限维概率分布的随机函数起着关键作用。就有限维分布而言，随机函数可由随机 `n` 维向量 `overset{rightarrow}{x} = { x(t_{1}),...,x(t_{n}) }.` 描述。随机向量 `overset{rightarrow}{x}` 服从高斯分布，如果其特征函数可表示为

$$
\begin{array}{r} {\Phi(\overset{rightarrow}{u}) = \mathcal{M}\left\{ \exp\left( {j\left\langle \overset{rightarrow}{u},\overset{rightarrow}{x} \right\rangle} \right) \right\} = \exp\left( {j\left\langle \overset{rightarrow}{u},\overset{rightarrow}{m} \right\rangle - \frac{1}{2}\left\langle G\,\overset{rightarrow}{u},\overset{rightarrow}{u} \right\rangle} \right).} \\ \end{array}
$$

(2.24)

这里 `overset{rightarrow}{m}` 表示向量 `overset{rightarrow}{x}` 对应元素的 `n` 维均值向量；`overset{rightarrow}{u}` 是定义在 `R^{(n)}` 上的 `n` 维实变量向量；`G` 表示非负定实对称矩阵（相关矩阵）；最后，`langle bullet, bullet rangle` 表示相应向量的标量积。

高斯随机函数的矩可通过展开其特征函数计算。若仅中心矩 (`m[1](t[1]) = 0`) 足够，则

$$
\begin{aligned} {\Phi(\overset{rightarrow}{u})} & {= \exp\left( {- \frac{1}{2}\left\langle G\,\overset{rightarrow}{u},\overset{rightarrow}{u} \right\rangle} \right) = 1 - \frac{1}{2}\left\langle G\,\overset{rightarrow}{u},\overset{rightarrow}{u} \right\rangle + \frac{1}{2^{2}2!}\left\langle G\,\overset{rightarrow}{u},\overset{rightarrow}{u} \right\rangle^{2} - \ldots} \\ & {+ {( - 1)}^{n}\frac{1}{2^{n}n!}\left\langle G\,\overset{rightarrow}{u},\overset{rightarrow}{u} \right\rangle^{n} + \ldots.} \\ \end{aligned}
$$

(2.25)

因此，奇数阶矩函数为

$$
\begin{array}{r} {m_{i_{1},\ldots,i_{s}}(t_{1},\ldots,t_{s}) = 0,\text{\\quad\\quad}{\sum\limits_{k = 1}^{s}i_{k}} = 2n + 1;} \\ \end{array}
$$

(2.26)

偶数阶矩函数形式为

$$
\begin{aligned} {m_{i_{1},\ldots,i_{s}}(t_{1},\ldots,t_{s})} & {= \frac{\partial^{2n}}{\partial t_{1}^{i_{1}}\cdots\partial_{s}^{i_{s}}}\left( {\frac{1}{2^{n}n!}\left\langle G\,\overset{rightarrow}{u},\overset{rightarrow}{u} \right\rangle} \right),} \\ {\sum\limits_{k = 1}^{s}i_{k}} & {= 2n.} \\ \end{aligned}
$$

(2.27)

高斯随机函数在不同（理论和应用导向）研究中具有极其重要的意义。事实上，在相当不苛刻的条件下，大量独立随机函数的小值之和可由高斯随机函数近似，而与项的概率论性质无关。这一重要结果——正态相关定理——是中心极限定理的推广 [[166](#refbib.xhtml#r166)]。

## 2. 具有独立增量的随机过程

具有独立增量的随机过程的研究始于布朗运动及其适当的数学模型维纳过程。后来，在具有独立增量的过程类中发展了广义的数学模型并进行了积分。

随机过程 `overset{rightarrow}{x}(t), t in mathcal{T},` 取值于 `R^{(n)}`，称为具有独立增量的过程，如果对任意 `n`，`t[0] <= t[1] <= ... <= t[n] = T`，随机向量 `overset{rightarrow}{x}(t_{0}),overset{rightarrow}{x}(t_{1}) - overset{rightarrow}{x}(t_{0}),...,overset{rightarrow}{x}(t_{n}) - overset{rightarrow}{x}(t_{n - 1})` 互为独立。

向量 `overset{rightarrow}{x}(t_{0})` 称为过程的初始状态（值），其概率分布称为过程的初始分布。定义具有独立增量的过程，只需定义初始分布 `P_{0}(mathcal{B}) = mathbf{P}\left\{ overset{rightarrow}{x}(t_{0}) in mathcal{B} \right\},` 以及向量 `Delta overset{rightarrow}{x}(t,h) = overset{rightarrow}{x}(t + h) - overset{rightarrow}{x}(t),` 的分布集合 `P(t,h,mathcal{B}) = mathbf{P}\left\{ Delta overset{rightarrow}{x}(t,h) in mathcal{B} \right\}`，其中 `t in mathcal{T}`，`h > 0`，且 `mathcal{B} in R^{(m)}` 为基本事件集。

如果分布 `P(t, h, mathcal{B})` 与 `t` 无关，即 `P(t, h, mathcal{B}) = P(h, mathcal{B})`，则相应的具有独立增量的过程称为 *齐次* 的。

