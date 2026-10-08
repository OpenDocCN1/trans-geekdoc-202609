
其中

$$U^{Rank}(X_{i}) = \begin{cases} AET(X_{i}) + \max _{X \in \operatorname{SUC}(X_{i})} \left(CT_{i, j} + U^{Rank}(X_{j})\right) & \text{if } X_{i} \neq X_{\text{exit}} \\ AET\left(X_{\text{exit}}\right) & \text{if } X_{i} = X_{\text{exit}} \end{cases}$$

$$U^{Rank}(X_{i}) = \begin{cases} \max _{X_{j} \in \operatorname{PRE}(X_{i})} \left\{D^{Rank}(X_{j}) + AET(X_{j}) + CT_{i, j}\right\} & \text{if } X_{i} \neq X_{\text{entry}} \\ 0 & \text{if } X_{i} = X_{\text{entry}} \end{cases}$$

其中 $PRE(X_{i})$ 是任务 $X_{i}$ 的有限前驱集。$D^{Rank}(X_{i})$ 的正式定义是从 $X_{\text{entry}}$ 到 $X_{i}$ 的最大距离，并且避免了平均执行时间 AET($X_{i}$) 的干扰。

### b. 关键路径任务

它有一个关键路径长度 $\left|\mathrm{C}^{\mathrm{p}}\right|$，这是给定 DAG 中从 $X_{\text{entry}}$ 到 $X_{\text{exit}}$ 的最长路径的长度。$\left|\mathrm{C}^{\mathrm{p}}\right|$ 的值为 $X_{\text{entry}}^{Priority}(X_{\text{entry}})$。此阶段还识别了给定 $\mathrm{DAG}_{1}$ 的关键路径任务，表达如下：

它由 $CP_{\mathrm{SET}}$ 指定，并根据文献 [24] 计算如下：

```
Step 1: CP_SET = {X_entry}
Step 2: X = X_entry
Step 3: while X != X_exit then
        Find successors of X as X_j
        If T_j^Priority(X) = |C^P| then
            CP_SET = CP_SET U {X}
        Otherwise
            X = X_j
        End While.
Step 4: stop.
```

该算法有助于计算给定 DAG 关键路径上的所有任务。

### c. 关键路径 VM

它识别出在计算所有关键路径任务 $\mathrm{CP}_{\mathrm{SET}}$ 时执行时间最短的虚拟机，即在同一 VM 上执行 $\mathrm{CP}_{\mathrm{SET}}$，公式为：

$$CP^{VM} = \min_{X_i \in CP^{SET}} \{ \sum ECT(X_i) \text{ on VM} \}$$

# 一个示例

考虑与图 9.5 中所示相同的 DAG₁ [14, 26] 示例，以及表 9.1 中给出的任务 ECT [14] 值。DAG₁ [27] 由 10 个任务组成，具有单一入口任务和单一出口任务，并考虑了两台云服务器 CS₁ 和 CS₂。CS₁ 包含两个虚拟机 VM₁ 和 VM₂。同样，CS₂ 包含一个虚拟机 VM₃。给定 DAG₁ 的任务向下秩（$D^{Rank}$）的计算将从入口任务 $T_{entry}$ 开始，并沿给定 DAG₁ 向下移动。向下秩（$D^{Rank}$）计算 [24] 的详细信息如表 9.3 所示，任务优先级 $T^{Priority}$ 的计算如表 9.4 所示。

$|CP|$ 的值为 108，关键路径任务 $CP^{SET}$ 将是 $\{X_1, X_2, X_9, X_{10}\}$，并且这些任务在 VM₂ 上执行所需的最短执行时间为 54。因此，在调度给定 DAG₁ 的任务时，所有 $CP^{SET}$ 任务都分配在 VM₂ 上。

# 第二阶段：VM 选择

此阶段包括就绪队列（RQ），它由给定 DAG₁ 的入口任务初始化。任务从 RQ 中逐个移除，如果移除的任务 T 属于 $CP^{SET}$，则将其调度到 $CP^{VM}$ 中的虚拟机上；否则，将其调度到执行时间（EFT）最短的虚拟机上。$T_i$ 的所有后继任务 $T_j$ 将根据 $T^{Priority}$ 的值插入 RQ。在分配到虚拟机时必须始终保持前置约束，否则给予下一个低优先级任务机会。

# 一个示例

按照 COP 算法的顺序，给定图 9.5 中 DAG₁ 的任务顺序为 $X_1, X_2, X_3, X_7, X_4, X_5, X_6, X_8, \text{ and } X_{10}$。任务的 ECT 值在表 9.1 中给出。在这里，考虑两台云服务器 CS1 和 CS₂。CS₁ 包含两个虚拟机 VM₁ 和 VM₂。CS₂ 包含一个虚拟机 VM₃。为此，使用甘特图 [23] 来表示任务在 VM 上的分配，如图 9.7 所示。COP 算法为包含 10 个任务的给定 DAG₁ 生成了 86 个单位长度的调度时长。

# 表 9.3 DAG₁ 任务的向下秩计算。（续）

| Task($X_{i}$) | AET($X_{i}$) | Computation of $D_{Rank}^{*}(X_{i})$ |
| :--- | :--- | :--- |
| $X_{1}$ | $\begin{aligned} AET(X_{1}) &= \frac{14+16+19}{3} \\ &= 13 \end{aligned}$ | $X_{1}$ 是入口任务，其向下值为 0，即 $D_{Rank}^{*}(X_{1}) = 0$ |
| $X_{2}$ | $\begin{aligned} AET(X_{2}) &= \frac{13+19+18}{3} \\ &= 16.667 \end{aligned}$ | $X_{1}$ 是 $X_{2}$ 的唯一前驱任务。 <br>$\begin{aligned} D_{Rank}^{*}(X_{2}) &= \max_{X_{j} \in PRE(X_{2})} [D_{Rank}^{*}(X_{j}) + AET(X_{j}) + CT_{j}] \\ &= 0 + 13 + 18 = 31 \end{aligned}$ |
| $X_{3}$ | $\begin{aligned} AET(X_{3}) &= \frac{11+13+19}{3} \\ &= 14.334 \end{aligned}$ | $X_{1}$ 是 $X_{3}$ 的唯一前驱任务。 <br>$\begin{aligned} D_{Rank}^{*}(X_{3}) &= \max_{X_{j} \in PRE(X_{3})} [D_{Rank}^{*}(X_{j}) + AET(X_{j}) + CT_{j}] \\ &= 0 + 13 + 12 = 25 \end{aligned}$ |
| $X_{4}$ | $\begin{aligned} AET(X_{4}) &= \frac{13+8+17}{3} \\ &= 12.667 \end{aligned}$ | $X_{1}$ 是 $X_{4}$ 的唯一前驱任务。 <br>$\begin{aligned} D_{Rank}^{*}(X_{4}) &= \max_{X_{j} \in PRE(X_{4})} [D_{Rank}^{*}(X_{j}) + AET(X_{j}) + CT_{j}] \\ &= 0 + 13 + 9 = 22 \end{aligned}$ |
| $X_{5}$ | $\begin{aligned} AET(X_{5}) &= \frac{12+13+10}{3} \\ &= 11.667 \end{aligned}$ | $X_{1}$ 是 $X_{5}$ 的唯一前驱任务。 <br>$\begin{aligned} D_{Rank}^{*}(X_{5}) &= \max_{X_{j} \in PRE(X_{5})} [D_{Rank}^{*}(X_{j}) + AET(X_{j}) + CT_{j}] \\ &= 0 + 13 + 11 = 24 \end{aligned}$ |
| $X_{6}$ | $\begin{aligned} AET(X_{6}) &= \frac{13+16+9}{3} \\ &= 12.667 \end{aligned}$ | $X_{1}$ 是 $X_{6}$ 的唯一前驱任务。 <br>$\begin{aligned} D_{Rank}^{*}(X_{6}) &= \max_{X_{j} \in PRE(X_{6})} [D_{Rank}^{*}(X_{j}) + AET(X_{j}) + CT_{j}] \\ &= 0 + 13 + 14 = 27 \end{aligned}$ |

# 表 9.3 DAG 任务的向下秩计算。（续）

| Task($X$) | AET($X$) | Computation of $D^{Rank}(X)$ |
| :---: | :---: | :---: |
| $X_7$ | $AET(X_7) = \frac{7+13+11}{3} = 11$ | $X_6$ 是 $X_7$ 的唯一前驱任务。<br>$D^{Rank}(X_7) = \max_{X_j \in PRE(X_7)} [D^{Rank}(X_j) + AET(X_j) + CT_{j,7}] = 27 + 12.667 + 22.534 = 62.534$ |
| $X_8$ | $AET(X_8) = \frac{5+11+14}{3} = 10$ | $X_2, X_3$ 和 $X_6$ 是 $X_8$ 的三个前驱任务。<br>$D^{Rank}(X_8) = \max_{X_j \in PRE(X_8)} \{ [D^{Rank}(X_2) + AET(X_2) + CT_{2,8}], [D^{Rank}(X_3) + AET(X_3) + CT_{3,8}], [D^{Rank}(X_6) + AET(X_6) + CT_{6,8}] \} = 66.667$ |
| $X_9$ | $AET(X_9) = \frac{18+12+20}{3} = 16.67$ | $X_2, X_4$ 和 $X_5$ 是 $X_9$ 的三个前驱任务。<br>$D^{Rank}(X_9) = \max_{X_j \in PRE(X_9)} \{ [D^{Rank}(X_2) + AET(X_2) + CT_{2,9}], [D^{Rank}(X_4) + AET(X_4) + CT_{4,9}], [D^{Rank}(X_5) + AET(X_5) + CT_{5,9}] \} = 63.667$ |
| $X_{10}$ | $AET(X_{10}) = \frac{21+7+16}{3} = 14.67$ | $X_7, X_8$ 和 $X_9$ 是 $X_{10}$ 的三个前驱任务。<br>$D^{Rank}(X_{10}) = \max_{X_j \in PRE(X_{10})} \{ [D^{Rank}(X_8) + AET(X_8) + CT_{8,10}], [D^{Rank}(X_9) + AET(X_9) + CT_{9,10}] \} = 93.333$ |

# 表 9.4 DAG 1 中任务优先级 $T^{Priority}$ [20] 的计算。

| Task($X_i$) | $U^{Rank}(X_i)$ | $D^{Rank}(X_i)$ | $T^{Priority}(X_i) = U^{Rank}(X_i) + D^{Rank}(X_i)$ |
| :--- | :--- | :--- | :--- |
| $X_1$ | 108 | 0 | 108 |
| $X_2$ | 77 | 31 | 108 |
| $X_3$ | 80 | 25 | 105 |
| $X_4$ | 80 | 22 | 102 |
| $X_5$ | 69 | 24 | 93 |
| $X_6$ | 63.33 | 27 | 90.33 |
| $X_7$ | 42.66 | 62.33 | 105 |
| $X_8$ | 35.66 | 66.66 | 102.33 |
| $X_9$ | 44.33 | 63.66 | 108 |
| $X_{10}$ | 14.66 | 93.33 | 108 |

![](img/cbc35e0d02425baa6028b87d56263a7f_233_0.png)

图 9.7 任务分配的甘特图。

## 9.7.3 尽可能晚（ALAP）算法

ALAP [12] 是一种适用于异构和同构平台的调度算法。该算法有两个阶段：任务优先级排序和 VM 选择。

### 任务优先级排序阶段

任务优先级排序阶段计算为给定 $DAG_{1}$ 中任务 $X_{i}$ 的*关键路径* $C^{Path}$ 与*向上秩* $U^{Rank}$ 之间的差值。它可以表示为

$$T^{Priority}(X_{i}) = C^{Path} - U^{Rank}(X_{i})$$

