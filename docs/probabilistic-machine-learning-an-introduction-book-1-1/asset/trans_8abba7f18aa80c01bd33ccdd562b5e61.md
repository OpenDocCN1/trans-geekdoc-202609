
$$\frac{d}{dx} cx^n = c n x^{n-1}\tag{B.37}$$ $$\frac{d}{dx} \log(x) = 1/x\tag{B.38}$$ $$\frac{d}{dx} \exp(x) = \exp(x)\tag{B.39}$$ $$\frac{d}{dx}[f(x)+g(x)] = \frac{df(x)}{dx}+\frac{dg(x)}{dx}\tag{B.40}$$ $$\frac{d}{dx}[f(x)g(x)] = f(x)\frac{dg(x)}{dx}+g(x)\frac{df(x)}{dx}\tag{B.41}$$ $$\frac{d}{dx}f(u(x)) = \frac{du}{dx}\frac{df(u)}{du}\tag{B.42}$$

Eq. (B.42) 被称为 **微积分链式法则**。

### B.3.7.2 将向量映射为标量的函数

考虑一个可微函数 $f : \mathbb{R}^n \to \mathbb{R}$。这里有一些有用的恒等式：$^2$

$$\frac{\partial}{\partial \mathbf{x}} (\mathbf{a}^\top \mathbf{x}) = \mathbf{a}\tag{B.43}$$ $$\frac{\partial}{\partial \mathbf{x}} (\mathbf{b}^\top \mathbf{A} \mathbf{x}) = \mathbf{A}^\top \mathbf{b}\tag{B.44}$$ $$\frac{\partial}{\partial \mathbf{x}} (\mathbf{x}^\top \mathbf{A} \mathbf{x}) = (\mathbf{A} + \mathbf{A}^\top)\mathbf{x}\tag{B.45}$$

证明这些恒等式相当容易，只需展开二次型并应用标量微积分。

### B.3.7.3 将矩阵映射为标量的函数

考虑一个函数 $f : \mathbb{R}^{m\times n} \to \mathbb{R}$，它将矩阵映射为标量。我们使用以下自然布局来表示导数矩阵：

$$\frac{\partial f}{\partial \mathbf{X}} = \begin{pmatrix} \frac{\partial f}{\partial x_{11}} & \dots & \frac{\partial f}{\partial x_{1n}} \\ & \vdots & \\ \frac{\partial f}{\partial x_{m1}} & \dots & \frac{\partial f}{\partial x_{mn}} \end{pmatrix}\tag{B.46}$$

下面是一些有用的恒等式。

2. 部分恒等式取自 http://www.cs.nyu.edu/~roweis/notes/matrixid.pdf 中的列表。

### 涉及二次型的恒等式

可以证明以下结果。

$$\frac{\partial}{\partial X}(a^{\top} X b)= a b^{\top}\tag{B.47}$$ $$\frac{\partial}{\partial X}(a^{\top} X^{\top} b)= b a^{\top}\tag{B.48}$$

### 涉及矩阵迹的恒等式

可以证明以下结果。

$$\frac{\partial}{\partial X}\operatorname{tr}(A X B)= A^{\top} B^{\top}\tag{B.49}$$ $$\frac{\partial}{\partial X}\operatorname{tr}(X^{\top} A)= A\tag{B.50}$$ $$\frac{\partial}{\partial X}\operatorname{tr}(X^{-1} A)= -X^{-\top} A^{\top} X^{-\top}\tag{B.51}$$ $$\frac{\partial}{\partial X}\operatorname{tr}(X^{\top} A X)= (A + A^{\top}) X\tag{B.52}$$

### 涉及矩阵行列式的恒等式

可以证明以下结果。

$$\frac{\partial}{\partial X}\det(A X B)= \det(A X B) X^{-T}\tag{B.53}$$ $$\frac{\partial}{\partial X}\ln(\det(X))= X^{-T}\tag{B.54}$$

## B.4 凸性

在本节中，我们介绍凸性的概念，它在优化的理论和实践中起着基础作用，如我们在第 5 章所见，以及数学和统计学的其他几个领域。它建立在若干线性代数思想之上。更多细节可在各种教科书中找到，例如 [Dah10]。

### B.4.1 凸集

我们称 $\mathcal{S}$ 为凸集，如果对于任意 $x, x' \in \mathcal{S}$，我们有

$$\lambda x + (1-\lambda)x' \in \mathcal{S}, \quad \forall \lambda \in [0,1]\tag{B.55}$$

也就是说，如果我们从 $x$ 到 $x'$ 画一条线，线上的所有点都位于集合内部。见图 B.6 中凸集和非凸集的一些示例。

### B.4.2 凸函数

我们称 $f$ 为 **凸函数**，如果其 **上图**（函数上方点的集合，见图 B.7a 所示）构成一个凸集。等价地，函数 $f(\mathbf{x})$ 被称为凸的，如果它定义在凸集上，并且对于任意 $\mathbf{x}, \mathbf{y} \in \mathcal{S}$，以及任意 $0 \le \lambda \le 1$，我们有

$$f(\lambda \mathbf{x} + (1 - \lambda)\mathbf{y}) \le \lambda f(\mathbf{x}) + (1 - \lambda)f(\mathbf{y}) \tag{B.56}$$

见图 B.8(a) 中凸函数的一维示例。函数被称为 **严格凸** 如果不等式是严格的。函数 $f(\mathbf{x})$ 为 **凹** 如果 $-f(\mathbf{x})$ 是凸的，且为 **严格凹** 如果 $-f(\mathbf{x})$ 是严格凸的。见图 B.8(b) 中既不凸也不凹的函数的一维示例。

这里有一些一维凸函数的例子：

- $x^2$
- $e^{a x}$
- $-\log x$
- $x^a$, $a > 1$, $x > 0$
- $|x|^a$, $a \ge 1$
- $x \log x$, $x > 0$

### B.4.2.1 凸函数的刻画

直观上，凸函数形如碗状。形式上，可以证明以下重要结果：

**Theorem B.4.1.** *假设 $f : \mathbb{R}^n \to \mathbb{R}$ 在其定义域上二阶可微。则 $f$ 凸当且仅当 $\mathbf{H} = \nabla^2 f(\mathbf{x})$ 是正半定（Sec. C.1.5.3）对所有 $\mathbf{x} \in \text{dom}(f)$ 成立。此外，如果 $\mathbf{H}$ 正定，则 $f$ 严格凸。*

例如，考虑二次型

$$f(\mathbf{x}) = \mathbf{x}^\top \mathbf{A} \mathbf{x} \tag{B.57}$$

当 $\mathbf{A}$ 为正半定时它是凸的，当 $\mathbf{A}$ 为正定时它是严格凸的。如果 $\mathbf{A}$ 的特征值符号混合，则它既不凸也不凹。见图 B.9。

### B.4.2.2 强凸函数

我们称函数 $f$ 以参数 $m > 0$ 为 **强凸**，如果对 $f$ 定义域中所有 $\mathbf{x}, \mathbf{y}$ 都有：

$$(\nabla f(\mathbf{x}) - \nabla f(\mathbf{y}))^\top (\mathbf{x} - \mathbf{y}) \ge m \|\mathbf{x} - \mathbf{y}\|_2^2 \tag{B.58}$$

强凸函数也是严格凸的，但反之不成立。

如果函数 $f$ 二次连续可微，则它以参数 $m$ 强凸当且仅当对定义域中所有 $\mathbf{x}$ 有 $\nabla^2 f(\mathbf{x}) \succeq m \mathbf{I}$，其中 $\mathbf{I}$ 为单位矩阵，$\nabla^2 f$ 为 Hessian 矩阵，且不等式 $\succeq$ 表示 $\nabla^2 f(\mathbf{x}) - m \mathbf{I}$ 为正半定。这等价于要求 ∇² f(x) 的最小特征值对所有 x 至少为 m。如果定义域只是实数线，则 ∇² f(x) 只是二阶导数 f''(x)，因此条件变为 f''(x) ≥ m。如果 m = 0，则这意味着 Hessian 为正半定（或如果定义域是实数线，则意味着 f''(x) ≥ 0），这意味着函数是凸的，也许是严格凸的，但不是强凸的。

凸、严格凸和强凸之间的区别相当微妙。为了更好地理解这一点，考虑 f 二次连续可微且定义域为实数线的情况。然后我们可以如下刻画它们的区别：

- f 是凸的当且仅当 f''(x) ≥ 0 对所有 x 成立。
- f 是严格凸的如果 f''(x) > 0 对所有 x 成立（注意：这是充分的，但不是必要的）。
- f 是强凸的当且仅当 f''(x) ≥ m > 0 对所有 x 成立。

注意可以证明函数 f 以参数 m 强凸当且仅当函数

J(x) = f(x) - m/2 ||x||²   (B.59)

是凸的。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_786_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_786_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_786_2.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_786_3.png)

图 B.9：二维中的二次型 f(x) = x^T A x。 (a) A 为正定，因此 f 为凸。 (b) A 为负定，因此 f 为凹。 (c) A 为正半定但奇异，因此 f 为凸，但不严格。注意中间恒定高度的山谷。 (d) A 为不定，因此 f 既不凸也不凹。表面中间的驻点是鞍点。来自 [She94] 的图 5。

### B.4.2.3 保持凸性的运算

一般来说，判断一个函数是否凸在计算上可能很困难 [Ahm+13a]。幸运的是，有各种保持凸性的运算，可以让我们从更简单的部分推导出复杂的凸函数。许多此类规则在 [BV04] 中给出；这里我们只列出几个。

- 非负加权和：如果 $f_1,\dots,f_m$ 为凸函数且 $w_1,\dots,w_m \ge 0$，则 $f(\mathbf{x}) = \sum_{i=1}^m w_i f_i(\mathbf{x})$ 也是凸的。
- 与仿射映射的复合：假设 $f : \mathbb{R}^n \to \mathbb{R}$ 为凸。设 $\phi(\mathbf{u}) = \mathbf{A}\mathbf{u} + \mathbf{b}$ 为仿射函数，其中 $\mathbf{u} \in \mathbb{R}^m$，$\mathbf{A} \in \mathbb{R}^{n\times m}$，且 $\mathbf{b} \in \mathbb{R}^n$。最后定义 $g(\mathbf{u}) = f(\phi(\mathbf{u}))$。则 $g$ 是 $\mathbf{u}$ 的凸函数。例如，考虑函数 $g(\mathbf{u}) = (u_1 - 2u_2)^4$。它是凸的，因为 $(u_1 - 2u_2) = \mathbf{A}\mathbf{u}$ 是 $\mathbf{u}$ 的仿射函数，且 $f(z) = z^4$ 为凸。
- 点wise 最大值：如果 $f_1,\dots,f_m$ 为凸函数，则它们的点wise 最大值 $f(\mathbf{x}) = \max(f_1(\mathbf{x}),\dots,f_m(\mathbf{x}))$ 也是凸的。例如，hinge loss $f(x) = \max(0,1 - x)$ 为凸。相同的结论对点wise 最小值不成立。

### B.4.3 Jensen 不等式

**Jensen's inequality** 断言，对于任意凸函数 $f$，我们有

$f\left(\sum_{i=1}^n \lambda_i \mathbf{x}_i\right) \le \sum_{i=1}^n \lambda_i f(\mathbf{x}_i)$
(B.60)

其中 $\lambda_i \ge 0$ 且 $\sum_{i=1}^n \lambda_i = 1$。这对于 $n = 2$ 显然成立（由凸性定义），并且可以通过归纳法对 $n > 2$ 证明。

例如，如果 $f(z) = \log(z)$，它是一个凹函数，我们有

$\log(\mathbb{E}_z g(z)) \ge \mathbb{E}_z \log(g(z))$
(B.61)

作为应用，假设 $g(z) = p(z, x)$ 是概率模型的似然，其中 $x$ 为观测值，$z$ 为隐变量。则 $\log(\mathbb{E}_z g(z)) = \log p(x)$ 是观测数据的对数似然。我们通常希望最大化它，但计算可能很困难。幸运的是，$\mathbb{E}_z \log(g(z)) = \mathbb{E}_z \log p(x, z)$ 通常更容易计算，因此我们可以转而最大化这个下界。这就是 EM 算法用于 MLE 学习的基础，如第 5.7.2 节所述。

### B.4.4 次梯度

如果 $f(x)$ 在 $x = a$ 可微，则它在 $a$ 连续。然而，逆命题不成立。例如，图 B.2b 显示了绝对值函数 $f(x) = |x|$；它在 $x = 0$ 处也是连续的，但在该处不可微，因为在该点的斜率取决于是从左侧（即式 (B.20) 中 $h < 0$）还是从右侧（即 $h > 0$）趋近 $x = 0$。为处理此类情况，我们可以推广导数的概念，如下所述。

对于多变量凸函数 $f : \mathbb{R}^n \to \mathbb{R}$，我们称 $\mathbf{g} \in \mathbb{R}^n$ 为 $f$ 在 $\mathbf{x} \in \mathrm{dom}(f)$ 处的 **次梯度**，如果对所有向量 $\mathbf{z} \in \mathrm{dom}(f)$，
$f(\mathbf{z}) \ge f(\mathbf{x}) + \mathbf{g}^\top (\mathbf{z} - \mathbf{x})$ (B.62)

注意次梯度即使在 $f$ 在某点不可微时也可能存在，如图 B.10 所示。
函数 $f$ 在 $\mathbf{x}$ 处称为 **次可微**，如果在 $\mathbf{x}$ 处至少存在一个次梯度。这样的次梯度集合称为 $f$ 在 $\mathbf{x}$ 处的 **次微分**，记为 $\partial f(\mathbf{x})$。
