
## 继续顶点

### 15.6 引理.
*If* $\mathcal{M} \neq \emptyset$, then $\mathcal{M}$ 确实有顶点。更精确地说，$\mathcal{M}$ 中权值最小的每个向量都是一个顶点。

**证明** 如果 $0 \in \mathcal{M}$，那么它当然是一个顶点。现在设 $wt(\mathbf{x}) = r > 0$ 且假设 $r$ 是 $\mathcal{M}$ 中元素的最小权值。不失一般性 $x_1 \cdot x_2 \cdots x_r \neq 0$。如果 $\mathbf{x}$ 不是顶点，则存在 $(d_1,\ldots,d_r) \neq 0$ 使得 $\sum_{i=1}^r d_i \mathbf{c}_i = 0$。

设 $\mathbf{x}(\lambda) = \mathbf{x} + \lambda \cdot (d_1, d_2, \ldots, d_r, 0, \ldots, 0)$。则 $\mathbf{x}(\lambda)$ 仍满足定义 15.1 中的等式。如果 $\lambda$ 足够小，则 $\mathbf{x}(\lambda)$ 仍是 $\mathcal{M}$ 的成员。我们可以选取 $\lambda$ 使得 $\mathbf{x}(\lambda)$ 的权值小于 $r$，矛盾。

三种情况出现：

- 如果 $\mathcal{M}$ 为空，则我们问题的条件永远无法满足。
- 如果 $\mathcal{M}$ 有界，则称其为 **凸多面体**。我们稍后会看到，在这种情况下问题具有最小值，且该最小值在其中一个顶点取得。
- 最后，可能出现 $\mathcal{M}$ 无界的情况。此时目标函数 $Q$ 要么取得任意小的取值，要么 $Q$ 仍取得其最小值。

### 15.7 定义.
$\mathbf{x} \in \mathcal{M}$ 是 **极小点** 当且仅当 $Q(\mathbf{x}) \leq Q(\mathbf{y})$ 对所有 $\mathbf{y} \in \mathcal{M}$ 成立。

极小点的集合是凸的。事实上它是 $\mathcal{M}$ 与一个超平面的交集。

### 15.8 定理.
*If* $\mathcal{M}$ 是凸多面体（有界、非空），则 $\mathcal{M}$ 中的每一点都是顶点的凸组合。

**证明** 设 $\mathbf{x} \in \mathcal{M}$，$wt(\mathbf{x}) = r$ 且 $Z$ 为 $\mathbf{x}$ 的支撑集。如果 $r = 0$，则没有问题。设 $r > 0$。如果由 $Z$ 索引的列是独立的，则 $\mathbf{x}$ 本身就是一个顶点。于是假设存在 $A$ 的列的非平凡线性组合，系数为 $d_1,\ldots,d_n$，在 $Z$ 外消失。如前所述，考虑 $\mathbf{x}(\lambda) = \mathbf{x} + \lambda \cdot (d_1,\ldots,d_n)$。则 $\mathbf{x}(\lambda) \in \mathcal{M}$ 当且仅当 $\mathbf{x}(\lambda) \geq 0$，当且仅当 $\lambda_1 \leq \lambda \leq \lambda_2$，其中 $\lambda_1 < 0$ 是最小的负值，$\lambda_2 > 0$ 是最大的正值。显然 $\mathbf{x}(\lambda_1)$ 和 $\mathbf{x}(\lambda_2)$ 的权值都小于 $r$。由归纳法它们都是顶点的凸组合。由此可知 $\mathbf{x}$ 也是如此。

## 15.9 定理.
*If Q has a minimum in M, then this minimum is attained in a vertex.*

**证明** 只有当 M 无界时才有困难。设 x0 是一个不是顶点的极小点，x1, x2, …, xp 是 M 的顶点。技巧是考虑每个 x_i, i = 0, 1, …, p 的坐标之和 C_i。设 C 为这些数的最大值。如果 C = 0，则 0 是唯一的顶点和极小点。于是假设 C > 0。考虑标准形式的一个新的线性规划：增加一个新的不定元 x_{n+1}，不改变旧条件，增加 A 的一行对应条件 x1 + x2 + … + x_{n+1} = 2C，不改变 Q。相应的可行点空间 M~ 因最后一个条件而必定是有界的。向前 n 个坐标的投影将 M~ 映射到 M 的相应有界部分，同时保持目标函数 Q。特别地，x~0（x0 带有最后一个坐标使得坐标之和为 2C）是极小点。我们区分 M~ 中两类顶点。x~i, i = 1, 2, …, p 是最后一个坐标 > 0 的那些。剩余的顶点 x~i, i = p+1, …, r 最后一个坐标为零。将 x~0 = sum_j alpha_j x~j 表示为顶点的凸组合。最后一个坐标表明必须存在 j ≤ p 使得 alpha_j > 0。由此可知 x~j 是 M~ 的极小点，且顶点 x_j 是原线性规划的极小点。

## 15.10 定义.
*Let x be a vertex (we know wt(x) ≤ m). A basis of x is a set of m independent columns of A containing the support of x. Observe that the basis is uniquely determined if x is nondegenerate.*

## 顶点交换

设 x0 是一个顶点，其坐标为 x_k^{(0)}，Z 为 x0 的一个基的指标集。我们有 sum_{k∈Z} x_k^{(0)} c_k = b。A 的每个列向量都可以用该基表示。因此必定存在常数 α_{ki} 使得

$$c_i = \sum_{k∈Z} α_{ki}·c_k,\quad i=1,2,…,n.\tag{15.1}$$

如果 j ∈ Z，则当然 α_{kj}=δ_{kj}。假设存在 α_{\hat{k}j}>0，其中 \hat{k}∈Z，j∉Z。对每个 δ≥0，考虑具有以下坐标的 x(δ)：

$$x_k(δ)=\begin{cases}x_k^{(0)}-δ·α_{kj}&\text{if }k∈Z\\δ&\text{if }k=j\\0&\text{otherwise.}\end{cases}\tag{15.2}$$

则 $A \cdot \mathbf{x}(\delta) = \mathbf{b} - \delta \cdot \mathbf{c}_j + \delta \cdot \mathbf{c}_j = \mathbf{b}$。置

$\delta_1 = Min_{k,\alpha_{kj}>0}\left(x_k^{(0)}/\alpha_{kj}\right). \tag{15.3}$

如果 $\mathbf{x}_0$ 是退化的，则可能出现 $\delta_1 = 0$。在非退化情形下，$\delta_1 > 0$。下一个顶点是 $\mathbf{x}_1 = \mathbf{x}(\delta_1)$（见定义 15.2）。首先很明显我们有一个可行点，这是由 $\delta_1$ 的选取决定的。$\mathbf{x}_1$ 真的是顶点吗？当然 $wt(\mathbf{x}_1) \le m$，因为与 $\mathbf{x}_0$ 相比我们只有一个新的非零坐标，但 $\mathbf{x}_0$ 的至少一个非零坐标 $l$ 在 $\mathbf{x}_1$ 中变为零。

指标集为 $Z' = Z - \{l\} \cup \{j\}$ 的列构成 $\mathbf{x}_1$ 的一个基。事实上基数是正确的。每个向量都可以用 $\mathbf{c}_k$，其中 $k \in Z$ 表示（因为 $Z$ 是基）。由于 $\mathbf{c}_l$ 可以用 $\mathbf{c}_j$ 和 $\mathbf{c}_k$，$k \in Z \setminus \{l\}$ 表示，故我们得到一个生成集，从而是一个基。

如果 $\mathbf{x}_0$ 是退化的且 $j$ 选取得当（$\delta_1 = 0$），则 $\mathbf{x}_1 = \mathbf{x}_0$ 但具有新的基。现在用由 $Z'$ 给出的新基按类比于式 15.1 表示 $A$ 的列：

$\mathbf{c}_i = \sum_{k \in Z'} \alpha'_{ki} \cdot \mathbf{c}_k,\; i = 1,2,\dots,n.$

比较两个表达式，新的结构常数由旧的得到：

$\alpha'_{jl} = 1/\alpha_{ij}$  
$\alpha'_{ji} = \alpha_{li}/\alpha_{ij}$  
$\alpha'_{kl} = -\alpha_{kj}/\alpha_{ij}\quad (k \in Z,\;k \ne l)$  
$\alpha'_{ki} = \alpha_{ki} - \dfrac{\alpha_{li}\alpha_{kj}}{\alpha_{ij}}\quad (k \in Z,\;k \ne l). \tag{15.4}$

设 $\mathbf{x} \in \mathcal{M}$。由定义 $\sum_{i=1}^n x_i \cdot \mathbf{c}_i = \mathbf{b}$。对顶点 $\mathbf{x}_0$ 也有同样的关系。比较：$\displaystyle \sum_{k \in Z} x_k^{(0)}\mathbf{c}_k = \mathbf{b} = \sum_{i=1}^n x_i \sum_{k \in Z} \alpha_{ki}\mathbf{c}_k.$ 比较系数并注意到，对 $k,i \in Z$，系数 $\alpha_{ki}$ 只有在 $k=i$ 时才非零，我们得到 $\displaystyle x_k = x_k^{(0)} - \sum_{i \notin Z} \alpha_{ki}x_i \quad (k \in Z). \tag{15.5}$

## 单纯形算法

思想是进行一系列顶点交换，使目标函数 $Q$ 递减。于是再次设一个顶点 $\mathbf{x}_0$，其基由 $Z$ 索引；相应的目标函数值为 $Q_0 = \sum_{k \in Z} p_k \cdot x_k^{(0)}$。置

$$t_i = \sum_{k \in Z} \alpha_{ki} p_k.$$

对任意点 $\mathbf{x} \in \mathcal{M}$，我们有 $Q(\mathbf{x}) = \sum_{k \in Z} p_k x_k + \sum_{i \notin Z} p_i x_i = \sum_{k \in Z} p_k x_k^{(0)} + \sum_{i \notin Z} (p_i - \sum_{k \in Z} p_k \alpha_{ki}) x_i$，故

$$Q(\mathbf{x}) = Q_0 - \sum_{i \notin Z} (t_i - p_i) x_i.$$

注意以下事实：

- 1. 如果 $\mathbf{x}_0$ 是非退化的，$\hat{k} \in Z$，$j \notin Z$，$t_j > p_j$，$\alpha_{\hat{k}j} > 0$，则顶点交换给出一个目标函数值更小的顶点 $\mathbf{x}_1$：$Q_1 < Q_0$（我们有 $x_i^{(1)} = 0$ 若 $i \notin Z$，$i \neq j$，且 $x_j^{(1)} = \delta_1 > 0$。于是 $Q_1 = Q_0 - \delta_1 (t_j - p_j) < Q_0$）。
- 2. 如果对某个 $j \notin Z$ 有 $t_j > p_j$，$\alpha_{kj} \le 0$ 对所有 $k \in Z$ 成立，则线性规划取得任意小的值（$\mathbf{x}(\delta) \in \mathcal{M}$ 始终成立且 $Q(\mathbf{x}(\delta)) = Q_0 - \delta (t_j - p_j)$）。
- 3. 如果 $t_j \le p_j$ 对所有 $j \notin Z$ 成立，则 $\mathbf{x}_0$ 是极小点（$Q(\mathbf{x}) = Q_0 - \sum_{j \notin Z} (t_j - p_j) x_j \ge Q_0$）。

现在可以描述 **单纯形算法**。对顶点 $\mathbf{x}$ 和由 $Z$ 给出的基属于一个矩形数组：列由 $i \notin Z$ 索引，行由 $k \in Z$ 索引，行 $k$ 列 $i$ 的元素是 $\alpha_{ki}$。有一底行，其元素为 $d_i = t_i - p_i = \sum_{k \in Z} \alpha_{ki} p_k - p_i$，有一右列包含 $\mathbf{x}$ 关于 $Z$ 的系数。将目标函数值写在左下角单元。需要执行以下步骤：

- 1. 如果 $d_i \le 0$ 对所有 $i$ 成立，则达到最小值。
- 2. 选择 $d_j > 0$。
- 3. 如果所有 $\alpha_{kj} \le 0$，则线性规划取得任意小的值：不存在最小值。
