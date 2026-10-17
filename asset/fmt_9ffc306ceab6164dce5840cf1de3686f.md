
注意，由于问题的特殊形式，这些映射的定义域可以限制在 $f_i$ 和 $g_j$ 的像上。由于集合值映射定义在函数 $f_1, \dots, f_k, g_1, \dots, g_m$ 的图像向量上，单射假设确保每个图像向量都有唯一的原像向量，使得集合值映射在每个向量函数的图像上都是良好定义的。在进一步假设目标不会同时消失的情况下，我们可以形式化地给出概念性约束向量优化问题 (4.8) 的表述：

$$\min_{\mathcal{K}_{f_1}(f_1(x))\dots\mathcal{K}_{f_k}(f_k(x))} \begin{cases} f_1(x) \vdots \ f_k(x) \end{cases} \\ \text{受约束 } g_1(x) \in -\mathcal{K}_{g_1}(g_1(x)) \vdots \ g_m(x) \in -\mathcal{K}_{g_m}(g_m(x)) \ x \in \hat{S}.$$

问题 (4.8) 的复杂度现在隐藏在可变序结构中。

### 4.4 参考文献

更具理论意义。集合的强最小元素给出了一个非常强的最优性术语。许多集合没有强最小元素，因此，这种已知的最优性概念在实践中往往并不适用。

## 4.2 节

本节的结果已由 Jahn [74, 第 4.2 节] 开发。Jahn 和 Khan [76] 针对目标映射和约束使用可变顺序结构的具体向量优化问题建立了最优性条件。这种方法没有使用表示泛函。由于顺序是可变的，拉朗日乘数不是常数，而是变量的函数。

## 4.3 节

第 4.3 节的结果已由 Jahn 和 Khan [76, 第 4 节] 发表。结构优化中可以发现消失约束的问题 [1, 示例 1]。Achtziger 和 Kanzow 是第一个研究该类问题的最优条件和约束限定的人。具有切换约束的数学规划问题，例如 Mehlitz [105] 及其参考文献。条件目标出现在 Eichfelder [33, 第 1.3.1 节] 研究的医学数据图像注册中。Wacker [137]（也参见 Wacker 和 Deinzer [138]）是第一个通过加权方法研究此类问题的人，其中非负权重在迭代过程中可能会变化。由于目标的权重可能为零，基于医学技术中的这些具体应用，Eichfelder [32, 33] 开发了向量优化中的可变顺序结构理论。可变顺序结构是研究问题 (4.8) 的工具。

如果集合 $G_1, \dots, G_m$ 由不等式描述，那么 (4.8) 中的条件约束可以转换为具有消失约束数学规划 (MPVC) 的约束，这与平衡约束数学规划 (MPEC) 密切相关（细节请参见 Achtziger 和 Kanzow [1]）。在本节中，我们不假设集合 $G_1, \dots, G_m$ 具有特殊结构。这是可能的，因为我们使用了可变顺序结构。

# 第 5 章

# 集合优化的应用

**摘要** —— 表示 $-C$ 或 $-\mathcal{K}$ 的泛函是集合优化中的重要工具。在优化领域，人们研究具有集合值目标映射的优化问题。但在这里，我们在更通用的框架下研究这些问题，即我们研究一个集合族中的最小集合。与上一章一样，我们研究由凸锥 $C$ 给出的固定顺序结构问题，以及由合适的集合值映射 $\mathcal{K}$ 引入的可变顺序结构问题。在两种情况下，主要主题都是最小集合的刻画。

### 5.1 固定顺序结构

第一步，需要一个用于比较非空集合的序关系。实践中可以使用不同的序关系（例如，比较 Jahn 和 Ha [75]）。为了简单起见，我们限制使用 Young 在 1931 年引入的 [143] 为人知的集合小于序关系。

**定义 5.1** 设 $C$ 为实线性空间 $Y$ 中的一个凸锥。对于非空子集 $A, B \subseteq Y$，集合小于序关系 $\preceq_C$ 定义为：

$A \preceq_s B \iff (\forall b \in B \exists a \in A : a \preceq b) (\forall a \in A \exists b \in B : a \preceq b)$ (5.1)

$\preceq_C$ 表示由凸锥 $C$ 导出的偏序。

众所周知，定义 5.1 中的等价式 $(5.1)$ 可以写为：

$A \preceq_s B \iff B \subseteq A + C \text{ 且 } A \subseteq B - C$

（比较备注 1.1）。图 5.1 展示了这两个包含关系。如果给出表示 $-C$ 的泛函，这些包含关系可以被简单刻画。

## 5 集合优化的应用

82

![](img/e4a2e491dbba0d9f71abf293f149cd5b_92_0.png)

**命题 5.1** ([73, 命题 2.1]) 设 $C$ 为实线性空间 $Y$ 中的凸锥，$\psi$ 为表示 $a-C$ 的泛函。那么对于任意非空集合 $A, B \subseteq Y$，我们有：

$B \subseteq A+C \quad \Longrightarrow \quad \sup_{b\in B, a\in A} \psi(a-b) \leq 0$

$\quad\quadLongrightarrow \quad \inf_{b\in B, a\in A} \psi(a-b) \leq 0 \text{（若此最小值存在）}$

以及

$A \subseteq B-C \quad \Longrightarrow \quad \sup_{a\in A, b\in B} \psi(a-b) \leq 0$

$\quad\quadLongrightarrow \quad \inf_{a\in A, b\in B} \psi(a-b) \leq 0 \text{（若此最小值存在）}$

**证明** 对于任意非空集合 $A, B \subseteq Y$：

$B \subseteq A+C \quad \Longrightarrow \quad \forall b\in B \ \exists a\in A : \quad b \in \{a\}+C$

（OCR 文本在此处碎片化，遵循上述提供的逻辑流）。

### 5.1 固定顺序结构

93

应用命题 5.1，了解在什么情况下 sup min 是定义良好且有上界的是有意义的。

**命题 5.2** ([73, 命题 2.2]) 设 $C$ 为实范数空间 $(Y, \|\cdot\|)$ 中的凸锥，并 $\psi$ 为表示 $-C$ 的泛函。设 $A \subseteq Y$ 为非空紧集，$B \subseteq Y$ 为非空集，设 $\psi$ 在 $A-B$ 上有界。那么 $\sup_{b \in B} \min_{a \in A} \psi(a-b)$ 是定义良好的。

*证明* 由于 $\psi(-b)$ 是弱半连续的且集合 $A$ 是紧的，至少存在一个最小值 $a_b \in A$ 使得 $\psi(a_b-b) = \min_{a \in A} \psi(a-b)$。

## 5 在集优化中的应用

![](img/e4a2e491dbba0d9f71abf293f149cd5b_94_0.png)

图 5.2 $\mathbb{R}^2$ 中简单集的族 $\mathcal{F}$ 以及连同偏序 $\mathbb{R}^2_+$

我们现在将注意力转向集优化问题。根据实线性空间 $Y$ 中的集小于序关系，我们考虑 $Y$ 的非空子集的一个族 $\mathcal{F}$，并研究 $\mathcal{F}$ 的最小集。

**定义 5.2** 设 $C$ 为实线性空间 $Y$ 中的一个凸锥，设 $\mathcal{F}$ 为 $Y$ 的非空子集的一个族。称 $\tilde{A} \in \mathcal{F}$ 为 $\mathcal{F}$ 的*最小集*，当且仅当：

$A \preceq_s A, A \in \mathcal{F} \Longrightarrow \tilde{A} \preceq_s A.$

**示例 5.2** 设 $Y := \mathbb{R}^2$ 且 $C := \mathbb{R}^2_+$。设 $\mathcal{F} := \{A_1, \dots, A_5\}$ 为图 5.2 所示的集族。在这种情况下，我们仅有集不等式 $A_2 \preceq_s A_1, A_3 \preceq_s A_1, A_4 \preceq_s A_5$，那么显然 $A_2, A_3$ 和 $A_4$ 是 $\mathcal{F}$ 的唯一最小集。

**备注 5.2** 对于后续的研究，我们分别为一个集合中所有最小元素和极大元素构成的集引入了缩写。这里，我们使用了定义 4.1 给出的最小性概念的扩展。设 $C$ 为实线性空间 $Y$ 中的凸锥，并给定 $\emptyset \neq A \subseteq Y$。设 $\preceq_c$ 表示由 $C$ 导出的预序。集

$\min(A) := \{ \tilde{a} \in A \mid a \preceq_c \tilde{a}, a \in A \Longrightarrow \tilde{a} \preceq_c a \}$

表示 $A$ 的最小元素集，集

$\max(A) := \{ \tilde{a} \in A \mid \tilde{a} \preceq_c a, a \in A \Longrightarrow a \preceq_c \tilde{a} \}$

被称为 $A$ 的极大元素集。当然，如果凸锥 $C$ 是尖的，那么

$\min(A) = \{ a \in A \mid a \preceq_c A, a \in A \Longrightarrow a = \bar{a} \}$ （如定义 4.1 所示）且

$\max(A) = \{a\in A \mid \bar{a} \leq c, a \in A \Longrightarrow a = \bar{a}\}$

通过以下命题，我们研究如下问题：对于某个 $A \in \mathcal{F}$，两个不等式 $A \lesssim_s \tilde{A}$ 和 $\tilde{A} \lesssim_s A$ 成立，定义 5.2 意味着什么？

**命题 5.4 ([73])** 设 $C$ 为实线性空间 $Y$ 中的凸锥，设 $\mathcal{F}$ 为 $Y$ 的非空子集的族，其最小元素集和极大元素集非空。对于每个 $A \in \mathcal{F}$，满足方程

$A + C = \min(A) + C$ 和 $A - C = \max(A) - C$，则对于某个 $A \in \mathcal{F}$，$\tilde{A}$ 是 $\mathcal{F}$ 的最小集当且仅当对于所有 $A \in \mathcal{F}$ 都有 $A \lesssim_s \tilde{A}$。

**证明** 对于某个 $A \in \mathcal{F}$ 和任意的 $A \in \mathcal{F}$，根据定义，$A \lesssim_s \tilde{A}$ 和 $\tilde{A} \lesssim_s A$ 成立当且仅当 $\tilde{A}+C \subseteq A+C, A-C \subseteq \tilde{A}-C$。根据 Jahn [71, 引理 2.4]，这等价于 $\tilde{A}+C \subseteq A+C, A-C \subseteq \tilde{A}-C, A+C \subseteq \tilde{A}+C, \tilde{A}-C \subseteq A-C$，再次等价于 $\tilde{A}+C = A+C, \tilde{A}-C = A-C$。根据等式 (5.2)，可以写为 $\min(A)+C = \min(A)+C, \max(A)-C = \max(A)-C$。第一个等式意味着 $\min(A) \subseteq \min(\tilde{A})+C$，这意味着对于 $\tilde{a} \in \min(\tilde{A})$，存在 $a \in \min(A), c \in C$ 使得 $\tilde{a} = a+c$。任意选取 $\tilde{a} \in \min(\tilde{A})$。对于某个 $a \in \min(A)$ 和某个 $c \in C$，我们有 $\tilde{a} = a+c$。由于 (5.3) 中的第一个等式也意味着 $\min(A) \subseteq \min(\tilde{A})+C$，存在 $\hat{a} \in \min(\tilde{A})$ 和 $\hat{c} \in C$ 使得 $\tilde{a} = a+\hat{c}$。因此，我们得到 $\tilde{a} = a+c = \hat{a}+\hat{c}$。

## 5.1 固定序结构

图 5.3 等式 (5.2) 的说明 [73](img/e4a2e491dbba0d9f71abf293f149cd5b_96.png) 由于 $\bar{a}, \hat{a} \in \min(\hat{A})$，我们得到 $\hat{c} + c = 0$，即 $c = -\hat{a}$。由于 $C$ 是尖的，我们得到 $c \in C \cap (-C) = \{0\}$。因此，我们有 $\hat{a} = a$，从而 $\min(\hat{A}) \subseteq \mathbb{R}^2$。通过命名，我们也得到 $\min(A) \subseteq \min(A)$，并且有 $\min(A) = \min(A)$。等式 $\max(A) = \max(A)$ 可以类比证明。断言的 $\rightarrow$ 部分从最小性的定义得出。断言的 $\leftarrow$ 部分是等式 (5.3) 的简单结论。注意，集等式 (5.2) 是向量优化中一个著名的假设，也可以对某些非凸集成立（见图 5.3）。对于 $Y := \mathbb{R}^2, C := \mathbb{R}^2$ 且如图 5.3 所示，我们有 $A + C = \min(A) + C$ 和 $A - C = \max(A) - C$。但集等式 (5.2) 通常并不成立；例如，如果我们选择 $Y := \mathbb{R}^2, C := \mathbb{R}^2, A = \{(y_1, y_2) \in \mathbb{R}^2 \mid y_1^2 + y_2^2 < 1 \cup (-1, 0)\}$（见图 5.4），我们有 $\min(A) + C = (-1, 0)$，并且得到 $\min(A) + C = \{(y_1, y_2) \in \mathbb{R}^2 \mid y_1 \geq -1, y_2 \geq 0\} \neq A + C$，即 (5.2) 中的第一个等式不满足。为了在不使用集关系的情况下制定适当的最优条件，我们将命题 5.4 与命题 5.1 结合。

**推论 5 ([73, 推论 5])** 设 $C$ 为实线性空间 $Y$ 中的凸锥，设 $\mathcal{F}$ 为 $Y$ 的非空子集的族，其最小元素集和极大元素集非空且满足等式 (5.2)。

### 5.2 变序结构

图 5.4 由 (5.4) 定义的集 $A$ 和 $A + \mathbb{R}^2_+$![](img/e4a2e491dbba0d9f71abf293f149cd5b_97.png) 此外，让等式 $\sup_{a \in A} \psi(a-b) = \max_{a \in A} \psi(a-b)$ 和 $\inf_{b \in B} \psi(a-b) = \max_{b \in B} \psi(a-b)$ 对于所有 $A, B \in \mathcal{F}$ 满足。对于某个 $\tilde{A} \in \mathcal{F}$，$\tilde{A}$ 是 $\mathcal{F}$ 的最小集当且仅当对于所有 $A \in \mathcal{F}$ 都有 $\min(A) = \min(\tilde{A})$ 且 $\max(A) = \max(\tilde{A})$。

**证明** 根据命题 5.1，不等式 $A \preceq_s \tilde{A}$（对于所有 $A, \tilde{A} \in \mathcal{F}$）可以重写为 $\max \left\{\max_{a \in A} \psi(a-\tilde{a}), \max_{a \in \tilde{A}} \psi(\tilde{a}-a)\right\} \le 0$。

### 5.2 变序结构

```
$A \prec_{s,K} B \Longleftrightarrow \max \left\{ \sup_{b\in B\ a\in A} \psi(a-b, a), \sup_{a\in A\ b\in B} \psi(a-b, b) \right\} \leq 0$
```

如果产生的项存在。

显而易见，如果线性空间 $Y$ 是赋范的，集合 $A$ 和 $B$ 是弱紧凑的，且泛函 $\psi$ 是弱下半连续的，那么这些项就是存在的（参见 [72, Theorem 2.3]）。

我们研究了具有变序结构的集合优化问题。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

**定义 5.4** 假设假设 2.2 ，令 $\mathcal{F}$ 为 $Y$ 的非空子集族。如果集合 $\tilde{A} \in \mathcal{F}$ 被称为 $\mathcal{F}$ 的*最小集*，则当仅当

```
$A \prec_{s,K} \tilde{A}, \tilde{A} \in \mathcal{F} \Longimplies \tilde{A} \prec_{s,K} A$.
```

可以使用命题 5.6 中的等价性来刻画最小集。

**定理 5.1** [[74, Theorem 5.1]] 满足假设 2.2，并令 $\psi$ 为一个 $-K$-凸表示泛函。那么我们有：

$\tilde{A} \in \mathcal{F}$ 是 $\mathcal{F}$ 的最小集
