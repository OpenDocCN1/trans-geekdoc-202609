
$J_{m - 1}\mathbf{r}_{m - 1} = \begin{bmatrix} {r(m - 1),r(m - 2),\cdots,r(1)} \\ \\ \end{bmatrix}^{T}.$

![Equation](img/si278.png)

对公式 (4.60) 中的上分块应用附录 A.1 的矩阵求逆引理，我们得到

$\Sigma_{m}^{- 1} = \begin{bmatrix} \Sigma_{m - 1}^{- 1} & 0 \\ 0^{T} & 0 \\ \end{bmatrix} + \begin{bmatrix} {- \Sigma_{m - 1}^{- 1}J_{m - 1}\mathbf{r}_{m - 1}} \\ 1 \\ \end{bmatrix}\frac{1}{\alpha_{m - 1}^{b}}\begin{bmatrix} {- \mathbf{r}_{m - 1}^{H}J_{m - 1}\Sigma_{m - 1}^{- 1},1} \\ \end{bmatrix},$

![Equation](img/si279.png)(4.63)

其中对于这种情况，所谓的*舒尔补*是标量

$m$ 阶互相关向量 $\mathbf{p}_m$ 具有如下分区形式：

$$

\mathbf{p}_m = \begin{bmatrix} \mathbb{E}[u_n d_n^*] \\ \vdots \\ \mathbb{E}[u_{n-m+2} d_n^*] \\ \mathbb{E}[u_{n-m+1} d_n^*] \end{bmatrix} = \begin{bmatrix} \mathbf{p}_{m-1} \\ p_{m-1} \end{bmatrix}, \quad \text{where} \quad p_{m-1} := \mathbb{E}[u_{n-m+1} d_n^*].

$$

结合公式 (4.63) 和 (4.65)，可得出以下简洁的关系：

### 前向和后向 MSE 最优预测器

$$

\mathbf{w}_{m} := \Sigma_{m}^{-1}\mathbf{p}_{m} = \begin{bmatrix} \mathbf{w}_{m-1} \\ 0 \end{bmatrix} + \begin{bmatrix} -\mathbf{b}_{m-1} \\ 1 \end{bmatrix}k_{m-1}^{w},

$$

![Equation](img/si283.png)(4.66)

其中

$$

\mathbf{w}_{m-1} = \Sigma_{m-1}^{-1}\mathbf{p}_{m-1},\quad \mathbf{b}_{m-1} := \Sigma_{m-1}^{-1}J_{m-1}\mathbf{r}_{m-1}

$$

![Equation](img/si284.png)

和

$$

k_{m-1}^{w} := \frac{p_{m-1} - \mathbf{r}_{m-1}^{H}J_{m-1}\mathbf{w}_{m-1}}{\alpha_{m-1}^{b}}.

$$

![Equation](img/si285.png)(4.67)

公式 (4.66) 是一个阶递归，它将最优解 $\mathbf{w}_{m}$ 与 $\mathbf{w}_{m-1}$ 联系起来。为了获得一个完整的递归方案，所需要的只是一个用于更新 $\mathbf{b}_{m}$ 的递归。

**后向预测**：向量 `b[m] = Σ[m]^(−1) J[m] r[m]` 有一个有趣的物理解释：它是 `m` 阶的 MSE 最优后向预测器。也就是说，它是一个线性滤波器，给定 `u[n − m + 1]`、`u[n − m + 2]`、…、`u[n]` 的值，可最优地估计/预测 `u[n − m]` 的值。因此，为了设计 `m` 阶最优后向预测器，期望响应必须为

`d[n] = u[n − m]`

由相应的正规方程可得

```
b_m = Σ_m^(−1) [ E[u_n u_(n−m)*] ; E[u_(n−1) u_(n−m)*] ; ⋮ ; E[u_(n−m+1) u_(n−m)*] ] = Σ_m^(−1) J_m r_m
```

(4.68)

因此，MSE 最优后向预测器与 `b[m]` 重合，即

![Equation](img/fx015.jpg)

此外，将公式 (4.19) 适配到当前需求，相应的最小 MSE 等于

`J(b[m]) = r(0) − r[m]^(H) J[m] Σ[m]^(−1) J[m] r[m] = α[m]^(b)`

即，Eq. (4.64) 中的 Schur 补等于相应的最优 MSE！

**前向预测**：前向预测任务的目标是给定值 `u[n]`、`u[n-1]`、…、`u[n-m+1]`，预测值 `u[n+1]`。因此，MSE 最优的 `m` 阶前向预测器 `a[m]` 是通过选择期望响应 `d[n] = u[n+1]` 获得的，相应的正规方程变为：

```
a_m = Σ_m^{-1} [ E[u_n u_{n+1}^*] ; E[u_{n-1} u_{n+1}^*] ; ... ; E[u_{n-m+1} u_{n+1}^*] ] = Σ_m^{-1} [ r^*(1) ; r^*(2) ; ... ; r^*(m) ]
```

![Equation](img/si297.png)(4.69)

或

![Equation](img/fx016.jpg)(4.70)

由 Eq. (4.70) 可知（问题 4.16），回想 `J[m]J[m] = I[m]`，不难证明：

```
a[m] = J[m] b[m]^(*)  ⇒  b[m] = J[m] a[m]^(*)
```

![Equation](img/si299.png)(4.71)

并且，前向预测的最优均方误差 `J(a[m]) := α[m]^(f)` 等于后向预测的最优均方误差，即

`J(a[m]) = α[m]^(f) = α[m]^(b) = J(b[m])`。

![Equation](img/si301.png)

图 4.16 描绘了这两个预测任务。换句话说，最优前向预测器是后向预测器的共轭反序，因此

```
a_m := [a_m(0); ...; a_m(m-1)] = J_m b_m^* := [b_m^*(m-1); ...; b_m^*(0)].
```

![Equation](img/si302.png)

![图 4.16 后向预测器的冲激响应是前向预测器冲激响应的共轭反序。](img/gr016.jpg)

图 4.16 后向预测器的冲激响应是前向预测器冲激响应的共轭反序。

这一性质归因于所涉及过程的平稳性。因为统计特性仅取决于时间瞬间的差值，前向和后向预测并无太大区别；在两种情况下，给定一组样本 `u[n-m+1], ..., u[n]`，我们预测未来的*一个*样本（前向预测中的 `u[n+1]`）或过去的*一个*样本（后向预测中的 `u[n-m]`）。

在建立了公式 (4.71) 中 `a[m]` 和 `b[m]` 之间的关系后，我们已准备好补全公式 (4.66) 中缺失的步骤，即补全 `b[m]` 更新的阶递归步骤。由于公式 (4.66) 对任意期望响应 `d[n]` 均成立，因此它也适用于最优滤波器为前向预测器 `a[m]` 这一特殊情况；在这种情况下，`d[n] = u[n + 1]`。在公式 (4.66) 中用 `a[m]` (`a[m - 1]`) 替换 `w[m]` (`w[m - 1]`) 可得

```
\mathbf{a}_{m} = \begin{bmatrix} \mathbf{a}_{m - 1} \\ 0 \\ \end{bmatrix} + \begin{bmatrix} {- J_{m - 1}\mathbf{a}_{m - 1}^{\ast}} \\ 1 \\ \end{bmatrix}k_{m - 1},
```

![Equation](img/si308.png)(4.72)

其中已使用了公式 (4.71) 以及

```
k_{m - 1} = \frac{r^{\ast}(m) - \mathbf{r}_{m - 1}^{H}J_{m - 1}\mathbf{a}_{m - 1}}{\alpha_{m - 1}^{b}}.
```

![Equation](img/si309.png)(4.73)

将公式 (4.66)、(4.67)、(4.71)、(4.72) 和 (4.73) 结合起来，可得出以下称为 *Levinson* 算法的算法，用于求解正规方程。除了其优雅性外，该算法还有一些非常有趣的几何解释，我们稍后将进行讨论。

### 算法 4.1：Levinson 算法

**输入**

1. `r(0), r(1), ..., r(l)`

#### 算法步骤

##### 2. 计算互相关向量

$$p_k = \mathbb{E}[u[n-k]d^*[n]], \quad k = 0, 1, \dots, l-1$$

############ 初始化

1.  **设置初始参数**

    $$w_1 = \frac{p_0}{r(0)}, \quad a_1 = \frac{r^*(1)}{r(0)}, \quad \alpha_1^b = r(0) - \frac{|r(1)|^2}{r(0)}$$

2.  **计算初始增益系数**

    $$k_1^w = \frac{p_1 - r^*(1)w_1}{\alpha_1^b}, \quad k_1 = \frac{r^*(2) - r^*(1)a_1}{\alpha_1^b}$$

#### 迭代过程

**For** $m = 2, \dots, l$ **Do**

1.  **更新权重向量**

    $$\mathbf{w}_m = \begin{bmatrix} \mathbf{w}_{m-1} \\ 0 \end{bmatrix} + \begin{bmatrix} -J_{m-1}\mathbf{a}_{m-1}^* \\ 1 \end{bmatrix} k_{m-1}^w$$

#### 算法步骤

2.  $\mathbf{a}_m = \begin{bmatrix} \mathbf{a}_{m-1} \\ 0 \end{bmatrix} + \begin{bmatrix} -J_{m-1}\mathbf{a}_{m-1}^* \\ 1 \end{bmatrix}k_{m-1}$

3.  $\alpha_m^{(b)} = \alpha_{m-1}^{(b)}(1 - |k_{m-1}|^2)$; 当 $m < l$ 时

4.  $k_m^w = \frac{p_m - \mathbf{r}_m^H J_m \mathbf{w}_m}{\alpha_m^b}$; 当 $m < l$ 时

5.  $k_m = \frac{r^*(m+1) - \mathbf{r}_m^H J_m \mathbf{a}_m}{\alpha_m^b}$; 当 $m < l$ 时

*   **结束循环**

请注意，$\alpha_m^{(b)}$ 的更新是其在公式 (4.64) 和 (4.72) 中定义的直接结果（问题 4.17）。另请注意，$\alpha_m^{(b)} \ge 0$ 意味着 $|k_m| \le 1$。

#### 备注 4.3

*   每阶递归的复杂度为 $4m$ 次 MADS，因此对于包含 $l$ 个方程的系统，总计为 $2l^2$ 次 MADS。与采用通用方案所需的 $O(l^3)$ 次 MADS 相比，这种计算量的节省是巨大的。之前的计算高效算法是由 Levinson [26] 于 1947 年提出的。Durbin [12] 也独立提出了该算法的一种形式化表述；该算法有时被称为 *Levinson–Durbin* 算法。文献 [11] 中指出，Levinson 算法在其预测部分存在冗余，并由此发展出了 *split Levinson* 算法，其递归围绕对称向量量展开，从而实现了进一步的计算节省。

### 4.8.1 格-梯形结构

到目前为止，我们一直在处理线性时不变 FIR 滤波器的所谓*横向*实现；换句话说，输出被表示为脉冲响应与线性结构输入之间的卷积。Levinson 算法提供了一种计算高效的方案来获得 MSE 最优估计 `w*`。我们现在将注意力转向相应线性滤波器的一种等效实现，这是 Levinson 算法的直接结果。

定义与第 *m* 阶最优前向和后向预测器在时刻 *n* 相关的误差信号为

```
e[m]^(f)(n) := u[n] - a[m]^(H) um
```

其中 `um` 是第 *m* 阶滤波器的输入随机向量，且滤波器阶数已显式引入符号中。^(²⁴)

```
e[m]^(b)(n) := u[n - m] - b[m]^(H) um = u[n - m] - a[m]^(T) J[m] um
```

利用公式 (4.75)、公式 (4.72) 中的阶递归，以及由以下公式表示的 `um` 的分区

```
um = [u[m - 1]^(T)(n), u[n - m + 1]]^(T) = [u[n], u[m - 1]^(T)(n - 1)]^(T)
```

即公式 (4.74)，我们可以很容易地得到

#### 正交性与最优后向误差

##### 格子递推公式

前向预测误差的递推公式为：

$$ e_m^{(f)}(n) = e_{m-1}^{(f)}(n) - e_{m-1}^{(b)}(n-1) k_{m-1}^*, \quad m = 1, 2, \dots, l $$

后向预测误差的递推公式为：

$$ e_m^{(b)}(n) = e_{m-1}^{(b)}(n-1) - e_{m-1}^{(f)}(n) k_{m-1}, \quad m = 1, 2, \dots, l $$

初始条件为：

$$ e_0^{(f)}(n) = e_0^{(b)}(n) = u_n $$

反射系数初始值为：

$$ k_0 = \frac{r^*(1)}{r(0)} $$

这组递推公式被称为**格子递推**。

##### 最优后向误差的正交性

从随机信号的向量空间解释来看，显然后向预测误差 $ e_m^{(b)}(n) $ 位于由 $ u_{n-m}, \dots, u_n $ 张成的子空间中，即：

$$ e_m^{(b)}(n) \in \text{span}\{u(n-m), \dots, u(n)\} $$

此外，由于 `e[m]^(b)(n)` 是与 MSE 最优后向预测器相关的误差，因此 `e[m]^(b)(n) ⊥ span{u(n−m+1), …, u(n)}`。然而，后一个子空间正是 `e[m−k]^(b)(n), k = 1, 2, …, m` 所在的子空间。因此，对于 `m = 1, 2, …, l−1`，我们可以写出

```
[Equation: images/B978044329238500010X/fx017.jpg]
```

此外，显而易见的是

```
span{e[0]^(b)(n), e[1]^(b)(n), …, e[l−1]^(b)(n)} = span{u[n], u[n−1], …, u[n−l+1]}.
```

```
[Equation: images/B978044329238500010X/si341.png]
```

因此，归一化的“向量”

```
[Equation: images/B978044329238500010X/fx018.jpg]
```

在 `span{u[n], u[n−1], …, u[n−l+1]}` 中形成一组*标准正交*基（参见图 4.17）。事实上，公式 (4.77) 和 (4.78) 这一对方程构成了一个*施密特*正交化器 [47]。

![图 4.17 最优后向误差在相应的输入随机信号空间中形成一组正交基。](img/gr017.jpg)

图 4.17 最优后向误差在相应的输入随机信号空间中形成一组正交基。

现在让我们用这组新的正交向量来表示 `d̂[n]`，即 `d[n]` 在 `span{u[n], ..., u[n−l+1]}` 中的投影。

$$

\widehat{d}_n = \sum_{m=0}^{l-1} h_m e_m^b(n)

$$

![Equation](img/si344.png) (4.79)

其中系数 `h[m]` 由下式给出

$$

\begin{aligned}

h_m &= \langle \widehat{d}_n, \frac{e_m^b(n)}{\|e_m^b(n)\|^2} \rangle \\

&= \frac{\mathbb{E}[\widehat{d}_n e_m^{b*}(n)]}{\|e_m^b(n)\|^2} \\

&= \frac{\mathbb{E}[(d_n - e_n) e_m^{b*}(n)]}{\|e_m^b(n)\|^2} \\

&= \frac{\mathbb{E}[d_n e_m^{b*}(n)]}{\|e_m^b(n)\|^2},

\end{aligned}

$$

![Equation](img/si346.png) (4.80)

其中已考虑到误差 `e[n]` 与由后向误差张成的子空间之间的正交性。由公式 (4.67) 和 (4.80)，并考虑到所涉及量的各自定义，我们可直接得到

`h[m] = k[m]^(w*)`。

![Equation](img/si348.png)

也就是说，Levinson 算法中的系数 `k[m]`、`k[m]^(w)`、`m = 0, 1, …, l − 1` 是 `d̂[n]` 按正交基展开时的参数。将公式 (4.77)–(4.79) 结合起来，得到 图 4.18 的 *lattice-ladder*（格-梯形）结构，其输出是 `d[n]` 的 MSE 近似 `d̂[n]`。
