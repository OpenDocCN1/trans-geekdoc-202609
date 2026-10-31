
(U*)：寻找长度为 m 的列向量 w 满足

$A^t\mathbf{w} \le \mathbf{p},\ \mathbf{w} \ge 0.$

**Maximize** $Q^*(\mathbf{w}) = \mathbf{w}\cdot\mathbf{b}$.

*然后 (U) 与 (U*) 在与前述定理相同的意义下是对偶问题。*

**PROOF** 我们可以简单地将其化为对偶的第一种形式。事实上，(U) 等价于

$A\mathbf{x} - \mathbf{y} = b,\ \mathbf{x},\mathbf{y} \ge 0,\ \mathbf{p}\cdot\mathbf{x}=Min.$

对应的对偶问题是 $(U^*)$。

需要提及对偶定理的一个推论：

## 15.13 定理（Farkas 择一性）。给定实矩阵 $A$ 和实向量 $\mathbf{b}$，以下方程中恰有一个有解：

- $A\mathbf{x} = \mathbf{b},\ \mathbf{x} \ge 0.$
- $\mathbf{y}^t A \ge 0,\ \mathbf{y}\cdot\mathbf{b} < 0.$

**PROOF** 考虑对偶定理的第一种形式，其中 $\mathbf{p}=0$。对应的原问题 $(G)$ 只有 $0$ 作为唯一可能的值。假设两个 Farkas 备选方案都有解。则 $(\mathbf{y}^t A)\mathbf{x} \ge 0$ 出于一个原因，而 $\mathbf{y}^t(A\mathbf{x}) = \mathbf{y}\cdot\mathbf{b} < 0$ 出于另一个原因，矛盾。剩下要证明至少有一个备选方案有解。假设第一个备选方案无解。对偶问题 certainly 有容许值 $(\mathbf{y}=0$ 给出一个)。根据对偶定理，对偶问题取任意大的值。用 $-\mathbf{y}$ 代替，这表明第二个备选方案有解。假设第二个备选方案无解：每当 $\mathbf{y}^t A \ge 0$，则 $\mathbf{y}\cdot\mathbf{b} \ge 0$。等价地，每当 $\mathbf{y}^t A \le 0$ 则 $\mathbf{y}\cdot\mathbf{b} \le 0$。这意味着 $G^*$ 有最大值。根据对偶定理 $(G)$ 有有限最小值。特别地，第一个 Farkas 备选方案有解。

已经可以看出一般情况下对偶问题是什么样子。我们想详细描述这一点。

## 一般的对偶问题

设原问题由以下给出

- 一个实 $(m,n)$ 矩阵 $A$，一个长度为 $n$ 的列向量 $\mathbf{p}$ 以及另一个长度为 $n$ 且 $\mathbf{b} \ge 0$ 的列向量。
- $A$ 的每一行 $\mathbf{z}_i$ 给出一个方程或不等式（$\mathbf{z}_i\mathbf{x} = b_i$ 或 $\mathbf{z}_i\mathbf{x} \ge b_i$ 或 $\mathbf{z}_i\mathbf{x} \le b_i$）。
- 目标函数为 $Q(\mathbf{x}) = \mathbf{x} \cdot \mathbf{p} = Min.$

则对偶问题如下：

- $A$ 的每一行 $\mathbf{z}_i$ 对应一个不定元 $w_i$。主要条件是 $A^t \cdot \mathbf{w} \le \mathbf{p}$。
- 如果原问题中 $A$ 的对应行给出方程，则 $w_i$ 无限制。如果原问题中 $\mathbf{z}_i\mathbf{x} \ge b_i$，则 $w_i \ge 0$；如果 $\mathbf{z}_i\mathbf{x} \le b_i$，则 $w_i \le 0$。
- 目标函数为 $Q^*(\mathbf{w}) = \mathbf{w} \cdot \mathbf{b} = Max.$

这些条件包括了一切，也包括变量的非负性条件。作为例子，考虑类型 $(G)$，我们写成 $x \ge 0$，$Ax = b$ 且目标函数为 $x \cdot p$。在一般术语中我们将使用一个 $(n+m, n)$ 矩阵，前 $n$ 行是 $I$，$A$ 在其下方。我们有下不等式作为前 $n$ 个条件，剩余 $m$ 行是等式。对偶问题有未知数 $y_1, \dots, y_n \ge 0$ 和无限制的 $w_1, \dots, w_m$。主要条件是 $y_i + (A^t w)_i \le p_i$ 对 $i = 1, \dots, n$。由于 $y_i \ge 0$，这等价于 $A^t w \le p$。目标函数是 $w \cdot b$。这就是我们的对偶问题 $(G^*)$。

## 备注

人们可能会认为原问题无解当且仅当对偶问题取遍所有值。然而，这并不能从对偶定理得出，事实上并非如此，下例所示。

最大化 $2x_1 - x_2$ 受条件限制

$x_1, x_2 \ge 0,\; x_1 - x_2 \le 1,\; -x_1 + x_2 \le -2.$

显然无解。考虑对偶问题。变量为 $w_1, w_2, w_3, w_4$，其中 $w_1, w_2 \ge 0$ 且 $w_3, w_4 \le 0$。不等式为

$w_1 + w_3 + w_4 \le -2$ and $w_2 - w_3 - w_4 \le 1.$

相加得到 $w_1 + w_2 \le -1$，矛盾。这表明对偶问题也没有解。

## 牛/羊例子的对偶

标准形式下的牛/羊例子为

$A = \begin{pmatrix}1 & 0 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 0 \\ 1 & 0.2 & 0 & 0 & 1 \\ 150 & 25 & 0 & 0 & 1\end{pmatrix},\; b = (50,200,72,10000)^t,\; p = (-250,-45,0,0,0,0)^t.$

其最小值为 $-17200$。

对偶问题有四个未知数和六个条件。未知数向量为 $\mathbf{w} = (w_1,w_2,w_3,w_4)^t$，条件为 $A^t\mathbf{w} \le \mathbf{p}$ 且目标函数 $\mathbf{b}\cdot\mathbf{w}$ 需最大化。最后四个不等式为 $w_i \le 0$。我们应改用 $z_i = -w_i \ge 0$。用两个新变量 $z_5,z_6$ 写出其余两个不等式：

$z_1 + z_3 + 150z_4 - z_5 = 250$  
$z_2 + 0.2z_3 + 25z_4 - z_6 = 45$

这具有标准形式，有六个变量和两个条件。矩阵为

$B = \begin{pmatrix}1 & 0 & 1 & 150 & -1 & 0 \\ 0 & 1 & 0.2 & 25 & 0 & -1\end{pmatrix},$

右端为 $(250,45)^t$，目标函数由向量 $(50,200,72,10000,0,0)$ 描述。

作为起始顶点我们可以选择 $\mathbf{w}_0 = (250,45,0,0,0,0)^t$。起始单纯形表为

3 4 5 6 w0
1 1 150 -1 0 250
2 0.2 25 0 -1 45
18 2500 -50 -200 21500

其余自动进行：

2 4 5 6 w1
1 -5 25 -1 5 25
3 5 125 0 -5 225
-90 250 -50 -110 17450

2 1 5 6 w2
4 -1/5 1/25 -1/25 1/5 1
3 -5 100
-80 -10 -40 -160 17200

## 互补松弛原理

这直接由定理 15.11 的证明得出。基本不等式为

$Q(\mathbf{x}) = \mathbf{p} \cdot \mathbf{x} \ge \mathbf{w}^t A \mathbf{x} = \mathbf{w} \cdot \mathbf{b} = Q^*(\mathbf{w}).$

何时等号成立？唯一使用的不等式是 $(\mathbf{p} - A^t \mathbf{w}) \cdot \mathbf{x} \ge 0$。为了使 $Q(\mathbf{x}) = Q^*(\mathbf{w})$，必须在 $x_i > 0$ 时有 $p_i = (A^t \mathbf{w})_i$。

## 15.14 命题（互补松弛）

考虑对偶问题 $(G)$ 和 $(G)^*$。设 $\mathbf{x} \in \mathcal{M}$，$\mathbf{w} \in \mathcal{M}^*$。则以下等价：

- $Q(\mathbf{x}) = Q^*(\mathbf{w})$。
- *每当 $x_i > 0$，我们必须有 $p_i = \mathbf{c}_i \cdot \mathbf{w}$。*

在对偶的对称形式中：

## 15.15 推论。

容许点 $\mathbf{x} \in \mathcal{M}(U)$ 是线性规划 $(U)$ 的最小解当且仅当存在 $\mathbf{w} \in \mathcal{M}(U^*)$ 使得满足以下条件：

- $x_k(\mathbf{c}_k \cdot \mathbf{w} - p_k) = 0$，$k = 1,2,\dots q$。
- $w_i(\mathbf{z}_i \cdot \mathbf{x} - b_i) = 0$，$i = 1,2,\dots,m$。

这里 $\mathbf{c}_k$ 是第 $k$ 列，$\mathbf{z}_i$ 是 $A$ 的第 $i$ 行。

我们将使用线性规划来推导码和正交数组的显式界。

## 15.2 傅里叶变换

我们的目标是对不一定是线性的码和正交数组给出界。一个工具是傅里叶变换：在条目集合上施加循环群的结构：

## 15.16 定义。

设 $E = \mathbb{Z}/v\mathbb{Z}$，$V = (\mathbb{Z}/v\mathbb{Z})^n$，$g = |V| = v^n$。记 $L^2(V)$ 为复值函数 $f : V \longrightarrow \mathbb{C}$ 的集合，其内积（双线性形式）$\langle , \rangle$ 定义为

$\langle f, g \rangle = \frac{1}{g} \sum_{x \in V} f(x) \cdot g(x)$。

这里 $x = (x_1, x_2, \dots, x_n) \in V$。

## 15.17 定义。

对每个元素 $z = (z_1, z_2, \dots, z_n) \in V$，考虑 $L^2(V)$ 中的函数 $\phi_z$ 定义为

$$\phi_z(x) = \zeta^{x \cdot z}.$$

$\phi_z$ 被称为群 $V$ 的 **特征**。这里 $\zeta$ 是一个固定的本原复 $v$ 次单位根，$x \cdot z$ 表示标准点积。

特征构成了 $g$ 维复向量空间 $L^2(V)$ 的标准正交基。

## 15.18 定义。

设 $f \in L^2(V)$。将 $f$ 用特征表示为

$$f = \sum_{z \in V} \hat f(z) \phi_z.$$

复数 $\hat f(z)$ 被称为 $f$ 的 **傅里叶系数**。$f$ 的 **傅里叶变换** 是函数 $\hat f$，其在 $z$ 处的值为 $\hat f(z)$。

由于特征的正交归一性，傅里叶系数由下式给出

$$\hat f(z) = \langle f, \phi_z \rangle = \frac{1}{g} \sum_{x \in V} f(x) \zeta^{-x \cdot z}. \tag{15.6}$$

我们主要感兴趣的对象，码或正交数组，由字母 $E$ 中的条目构成的 $n$ 元组组成。因此它们可以与它们的特征函数等同：

## 15.19 定义。

设 $\mathcal{A}$ 是一个具有 $n$ 列且条目在 $v$ 集合 $E$ 中的数组。特征函数 $f(x) = \chi_{\mathcal{A}}(x)$ 计数 $x \in E^n$ 以何种重数作为 $\mathcal{A}$ 的一行出现。我们通过将 $\mathcal{A}$ 与其特征函数等同并应用定义 15.18 来定义 $\mathcal{A}$ 的傅里叶变换 $\hat{\mathcal{A}}(z)$。

我们将证明傅里叶系数与数组的强度之间存在密切联系。如果 $\mathcal{A}$ 的强度为 $t$，则 $\hat{\mathcal{A}}(z) = 0$ 对每个 $0 \neq z \in G$ 且权 $wt(z) \le t$ 成立。这由正交数组的定义和单位根幂之和为零的事实得出。反之亦真，因为条件 $\hat{\mathcal{A}}(z) = 0$ 对所有 $0 \neq z \in G$ 定义了 $L^2(G)$ 的一维子空间，常值函数。

## 15.20 定理。

以下对每个数组 $\mathcal{A} \subseteq G = E^n$ 和每个坐标位置的子集 $D$ 等价：

- $\hat{\mathcal{A}}(z) = 0$ 对所有 $0 \neq z \in V$ 且 $\operatorname{supp}(z) \subseteq D$ 成立。
- $\mathcal{A}$ 在 $D$ 上的投影是均匀分布的。

特别地，$\mathcal{A}$ 的强度为 $t$ 当且仅当关于所有非零向量 $z$ 且权至多为 $t$ 的傅里叶系数消失。
