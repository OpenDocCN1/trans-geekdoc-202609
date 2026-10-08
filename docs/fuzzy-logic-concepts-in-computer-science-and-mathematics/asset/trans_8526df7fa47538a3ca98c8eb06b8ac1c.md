
## 5.2 预备知识

**定义 5.2.1.** 直觉模糊阈值超图（IFTHG）记作 $\mathbb{H}_G = (U, E; s_1, s_2)$，其中：

- 1. $U = \{u_1, u_2, \dots, u_n\}$ 是直觉模糊顶点的有限集合，
- 2. $E = \{E_1, E_2, \dots, E_m\}$ 是 $U$ 的清晰子集族，
- 3. $E_j = \{ (\mu_j^j(u_i), \nu_j^j(u_i)) \mid 0 \le \mu_j^j(u_i) + \nu_j^j(u_i) \le 1 \}, j = 1, 2, \dots, m$
- 4. $E_j \neq \varnothing, j = 1, 2, \dots, m$
- 5. $\bigcup_{j=1}^m E_j = U$
- 6. 若存在 $s_1$ 和 $s_2 > 0$，使得 $\sum_{u_i \in V} \mu_j^j(u_i) \le s_1$ 且 $\sum_{u_i \in V}(1 - \nu_j^j(u_i)) \le s_2$，则 $\mathbb{H}_G$ 中不相邻顶点的所有不同组合构成的独立集 $V \subseteq U$。

其中 $E_j$ 的超边是直觉模糊顶点的清晰集合，$\mu_i(u_i)$ 和 $\nu_i(u_i)$ 分别表示顶点 $u_i$ 对超边 $e_j$ 的隶属度和非隶属度。

**定义 5.2.2.** 设 $\mathbb{H}_G = (U, E; s_1, s_2)$ 为一个 IFTHG。若存在独立集 $V \subseteq U$，则 $\mathbb{H}_G$ 的高度记为 $H_u(\mathbb{H}_G) = \{ \max(\min(\mu_i)), \max(\max(\nu_i)) \}$，满足对所有 $i = 1, 2, \dots, m$ 和 $j = 1, 2, \dots, n$，有 $\sum_{u_i \in V} \mu_i^j(u_i) \le s_1$ 且 $\sum_{u_i \in V}(1 - \nu_i^j(u_i)) \le s_2$，其中 $\mu_i^j$ 和 $\nu_i^j$ 分别是第 $i$ 个顶点在第 $j$ 个超边中的隶属值和非隶属值。

**定义 5.2.3.** 设 $\mathbb{H}_G = (U, E; s_1, s_2)$ 为一个 IFTHG，且存在独立集 $V \subseteq U$。若 $e_j \times e_k \in E$ 且 $0 < \alpha, \beta < 1$，则定义 $(\alpha, \beta)$-水平为 $(e_j \times e_k)^{\alpha, \beta} = \{ u_i \mid u_i \in U \mid \min((\mu_i^j)^\alpha(u_i)) \ge \alpha, \max((\nu_i^k)^\beta(u_i)) \le \beta \}$，满足 $\sum_{u_i \in V} \mu_j^j(u_i) \le s_1$ 且 $\sum_{u_i \in V}(1 - \nu_j^j(u_i)) \le s_2$。

**定义 5.2.4.** 设 $\mathbb{H}_G = (U, E; s_1, s_2)$ 为一个 IFTHG，存在独立集 $V \subseteq U$ 使得 $\mathbb{H}_G^{(y_i, z_i)} = (U^{(y_i, z_i)}, E^{(y_i, z_i)})$ 为 $\mathbb{H}_G$ 的 $(y_i, z_i)$-水平。满足以下条件的一列实数 $\{ y_1, y_2, \dots, y_n; z_1, z_2, \dots, z_n \}$，其中 $0 \le y_i \le H_u(\mathbb{H}_G)$ 且 $0 \le z_i \le H_v(\mathbb{H}_G)$：

- 1. 若 $y_1 < \alpha < 1$ 且 $0 < \beta < z_1 \Rightarrow E^{\alpha, \beta} = \varnothing$；
- 2. 若 $y_{i+1} \le \alpha \le y_i; z_i \le \beta \le z_{i+1} \Rightarrow E^{\alpha, \beta} = E^{(y_i, z_i)}$；以及
- 3. $E^{(y_i, z_i)} \subset E^{(y_{i+1}, z_{i+1})}$

满足 $\sum_{u_i \in V} \mu_i^j(u_i) \le s_1$ 且 $\sum_{u_i \in V}(1 - \nu_i^j(u_i)) \le s_2$ 的数列被称为 $\mathbb{H}_G$ 的*基本序列*，记为 $F(\mathbb{H}_G)$。

**定义 5.2.5.** 设 $\mathbb{H}_G = (U, E; s_1, s_2)$ 为一个 IFTHG，且存在独立集 $V \subseteq U$。则 $\mathbb{H}_G$ 的*核集*记为 $C(\mathbb{H}_G)$，其中 $0 < (y_i, z_i) \le H_u(\mathbb{H}_G)$，定义为 $C(\mathbb{H}_G) = \{\mathbb{H}_{G}^{(y_1, z_1)}, \mathbb{H}_{G}^{(y_2, z_2)}, \dots, \mathbb{H}_{G}^{(y_n, z_n)}\}$。对应的 $(y_n, z_n)$-水平超图集合为 $\mathbb{H}_{G}^{(y_1, z_1)} \subset \mathbb{H}_{G}^{(y_2, z_2)} \subset \dots \subset \mathbb{H}_{G}^{(y_n, z_n)}$，满足 $\sum_{u_i \in V} \mu_y(u_i) \leq s_1$ 且 $\sum_{u_i \in V}(1 - \nu_y(u_i)) \leq s_2$，称为 $\mathbb{H}_G$ 的诱导基本序列，记为 $I(\mathbb{H}_G)$。$(y_r, z_r)$-水平被称为 $\mathbb{H}_G$ 的支撑水平，而 $\mathbb{H}_{G}^{(y_r, z_n)}$ 被称为 $\mathbb{H}_G$ 的支撑。

**定义 5.2.6.** 设 $\mathbb{H}_G = (U, \mathcal{E}, s_1, s_2)$ 和 $\mathbb{H}_G^{\prime} = (U^{\prime}, \mathcal{E}^{\prime}, s_1^{\prime}, s_2^{\prime})$ 为 IFTHG，且存在独立集 $V \subseteq U$ 使得 $\mathbb{H}_G$ 是 $\mathbb{H}_G^{\prime}$ 的一个*部分 IFTHG*：

$$u^{\prime} = \begin{cases} \min(\supp(\mu_y)) \text{ 且 } \sum_{u_j \in V^{\prime}} \mu_y(u_j) \leq s_1 \mid \mu_y \in \mathcal{E}^{\prime} \\ \max(\supp(\nu_y)) \text{ 且 } \sum_{u_j \in V^{\prime}} (1 - \nu_y(u_i)) \leq s_2 \mid \nu_y \in \mathcal{E}^{\prime} \end{cases}$$

由 $\mathcal{E}^{\prime}$ 生成的部分 IFTHG 表示为 $\mathbb{H}_G \subseteq \mathbb{H}_G^{\prime}$。若 $\mathbb{H}_G \subseteq \mathbb{H}_G^{\prime}$ 且 $\mathbb{H}_G \neq \mathbb{H}_G^{\prime}$，则记作 $\mathbb{H}_G \subset \mathbb{H}_G^{\prime}$。

**定义 5.2.7.** 设 $\mathbb{H}_G = (U, \mathcal{E}, s_1, s_2)$ 为一个 IFTHG，存在独立集 $V \subseteq U$ 使得 $C(\mathbb{H}_G) = \{\mathbb{H}_G^{(y_1, z_1)}, \mathbb{H}_G^{(y_2, z_2)}, \dots, \mathbb{H}_G^{(y_n, z_n)}\}$，满足 $\sum_{u_i \in V} \mu_y(u_i) \leq s_1$ 且 $\sum_{u_i \in V}(1 - \nu_y(u_i)) \leq s_2$。若 $C(\mathbb{H}_G)$ 有序，则称 $\mathbb{H}_G$ 为*有序的*。即 $\mathbb{H}_G^{(y_1, z_1)} \subset \mathbb{H}_G^{(y_2, z_2)} \subset \dots \subset \mathbb{H}_G^{(y_n, z_n)}$，满足 $\sum_{u_i \in V} \mu_y(u_i) \leq s_1$ 且 $\sum_{u_i \in V}(1 - \nu_y(u_i)) \leq s_2$。若 $\{\mathbb{H}_G^{(y_j, z_j)} \mid j = 1, 2, \dots, n\}$ 是简单有序的，即它是有序的，并且若 $\mathcal{E} \in \mathbb{H}_G^{(y_{j+1}, z_{j+1})} \setminus \mathbb{H}_G^{(y_j, z_j)}$，则 $\mathcal{E} \not\subseteq \mathbb{H}_G^{(y_j, z_j)}$，则称该 IFTHG 为*简单有序的*。

## 5.3 符号

- $\mathbb{H}_G = (U, \mathcal{E}; s_1, s_2)$：具有超边集 $\mathcal{E}$、顶点集 $U$ 以及阈值 $s_1$、$s_2$ 的 IFTHG。
- $\mathcal{H}_t(\mathbb{H}_G)$：IFTHG 的高度。
- $\mathcal{F}_t(\mathbb{H}_G)$：IFTHG 的基本序列。
- $C(\mathbb{H}_G)$：IFTHG 的核集。
- $I(\mathbb{H}_G)$：IFTHG 的诱导基本序列。
- $\mathbb{H}_G^{(y_j, z_j)}$：$\mathbb{H}_G$ 的 $(y_j, z_j)$-水平。
- $(y_j, z_j)$：超边的隶属值和非隶属值。
- $T_G(\mathbb{H}_G)$：IFTHG 的最小直觉模糊横截集（IFT）。

## 5.4 主要结果

**定义 5.4.1.** 设 IFTHG $\mathbb{H}_G = (U, \mathcal{E}; s_1, s_2)$。IFTHG 的 IFT $T$ 是 $U$ 的一个直觉模糊子集，满足 $T^{\langle e_j, e_k \rangle} \cap A^{\langle e_j, e_k \rangle} \neq \varnothing$ 对所有 $A \in \mathcal{E}$ 成立，其中 $e_j = \bigwedge (u_{ij})$ 且 $e_k = \bigvee(v_{ij})$，满足 $\sum_{u_i \in V} \mu_{ij}(u_i) \leq s_1$ 且 $\sum_{u_i \in V} (1 - \nu_{ij}(u_i)) \leq s_2$，$\forall 1 \leq i \leq m, 1 \leq j \leq n$。此外，$\mu_{ij}$ 和 $\nu_{ij}$ 分别是第 $j$ 个超边中第 $i$ 个顶点的隶属值和非隶属值。

**定义 5.4.2.** IFTHG 的最小 IFT $T$ 是 $\mathbb{H}_G$ 的一个横截集，满足若 $T_1 \subset T$，则 $T_1$ 不是 $\mathbb{H}_G$ 的 IFT。

**注：** IFTHG 的所有最小 IFT 的集合表示为 $\mathcal{T}\sigma(\mathbb{H}_G)$。总有 $\mathcal{T}\sigma(\mathbb{H}_G) \neq \varnothing$。

**例 5.4.3.** 考虑一个具有 $U = \{u_1, u_2, u_3, u_4, u_5, u_6\}$，$\mathcal{E} = \{\mathcal{E}_1, \mathcal{E}_2, \mathcal{E}_3, \mathcal{E}_4\}$ 的 IFTHG $\mathbb{H}_G$。

![](img/e9de70cd491e84262133af63cb33d500_81_0.png)

**图 5.1** 直觉模糊阈值超图 $\mathbb{H}_G$。

利用图 5.1，我们可以构造一个具有 $\mathcal{E} = \{\mathcal{E}_1, \mathcal{E}_2, \mathcal{E}_3, \mathcal{E}_4\}$ 的 IFTHG $\mathbb{H}_G$，其对应的关联矩阵如下所示：

| | $\mathcal{E}_1$ | $\mathcal{E}_2$ | $\mathcal{E}_3$ | $\mathcal{E}_4$ |
| :--- | :---: | :---: | :---: | :---: |
| $u_1$ | $\langle 0.3, 0.5\rangle$ | $\langle 0, 1\rangle$ | $\langle 0, 1\rangle$ | $\langle 0, 1\rangle$ |
| $u_2$ | $\langle 0, 1\rangle$ | $\langle 0.3, 0.4\rangle$ | $\langle 0, 1\rangle$ | $\langle 0, 1\rangle$ |
| $u_3$ | $\langle 0, 1\rangle$ | $\langle 0, 1\rangle$ | $\langle 0.2, 0.6\rangle$ | $\langle 0.2, 0.6\rangle$ |
| $u_4$ | $\langle 0, 1\rangle$ | $\langle 0.3, 0.5\rangle$ | $\langle 0, 1\rangle$ | $\langle 0.3, 0.6\rangle$ |
| $u_5$ | $\langle 0, 1\rangle$ | $\langle 0.4, 0.5\rangle$ | $\langle 0, 1\rangle$ | $\langle 0, 1\rangle$ |
| $u_6$ | $\langle 0.4, 0.6\rangle$ | $\langle 0.4, 0.6\rangle$ | $\langle 0.4, 0.6\rangle$ | $\langle 0.4, 0.6\rangle$ |

该 IFTHG 的最小 IFT 表示如下：

| | $T_1$ | $T_2$ |
| :--- | :---: | :---: |
| $u_1$ | $(0, 1)$ | $(0, 1)$ |
| $u_2$ | $(0, 1)$ | $(0, 1)$ |
| $u_3$ | $(0.2, 0.6)$ | $(0, 1)$ |
| $u_4$ | $(0, 1)$ | $(0.3, 0.5)$ |
| $u_5$ | $(0, 1)$ | $(0, 1)$ |
| $u_6$ | $(0.4, 0.6)$ | $(0.4, 0.6)$ |

对应的 IFTHG 如图 5.2 所示。

![](img/e9de70cd491e84262133af63cb33d500_82_0.png)

**定义 5.4.4.** 若 $T$ 是一个以 $(v_i, z_j)$ 为 $\mathbb{H}_{G}^{(v_i, z_j)}$ 最小 IFT 的直觉模糊集，且对所有 $(v_{i}, z_{j}) \in(0,1)$ 满足 $\sum_{u_{i} \in V} \mu_{y}(u_{i}) \leq s_{1}$ 和 $\sum_{u_{i} \in V}(1 - \nu_{i}(u_{i})) \leq s_{2}$ 以及 $\forall 1 \leq i \leq m, 1 \leq j \leq n$，则称 $T$ 为 IFTHG 的局部最小 IFT。包含 IFTHG 局部最小 IFT 的集合记为 $\mathcal{T} \times^{\prime}(\mathbb{H}_{G})$。

**定理 5.4.5.** 若 $T$ 是 IFTHG $\mathbb{H}_{G}=(U, \mathcal{E}, s_{1}, s_{2})$ 的一个 IFT，则 $\mathscr{A}_{T}\left(T_{e}\right) \supseteq \mathscr{A}_{T}\left(e_{j}\right)$ 对所有 $e_{j} \in \mathcal{E}$ 成立。并且，若 $T$ 是 IFTHG 的最小 IFT，则 $\mathscr{A}_{T}(T)=\left\{\max \left(\min \left(\mu_{y}\right)\right), \max \left(\max \left(\nu_{y}\right)\right) \mid \mu_{y}, \nu_{y} \in \mathcal{E}\right\}=\mathscr{A}_{T}\left(\mathbb{H}_{G}\right)$。

**定理 5.4.6.** 每个 IFTHG 都有一个非空的 IFT。

**注：** IFTHG 的每个 IFT 都包含一个最小 IFT。（即）$\mathcal{T}^{X}\left(\mathbb{H}_{G}\right) \subseteq T\left(\mathbb{H}_{G}\right)$。
