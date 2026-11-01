
频率（`ℬℱ[*i*]`）和速度（`ℬ𝒱[*i*]`）、脉冲率（`ℬ*R*[*i*]`）和响度（`ℬ*A*[*i*]`）为量子种群内部的每个量子解初始化（第3–4行）。

现在，为了生成活动聚类点，对种群应用了选择过程，选择过程由量子态 `Q^(BAT)(t)` 引导以产生二进制解 `Bs(t)`。二进制解 `Bs(t)` = {`bs[1]^(t)`, `bs[2]^(t)`,…, `bs[N]^(t)`} 是通过在初始代 `t` = 1 中感知状态 `Q^(BAT)(t)` 产生的。

每个二进制解 `bc[i]^(t)` 如下生成。

```
$bs_{i,j}^{t} = \\left\\{ \\begin{matrix} {1,\\,\\, IfP\\\_ BAT\\_{ij}^{\\beta t} > P\\\_ BAT\\_{ij}^{\\alpha t}} \\\\ {0,Otherwise} \\\\ \\end{matrix} \\right.,\\,\\, st.i = \\left\\{ {1,2,\\ldots,P\\, size} \\right\\}\\,\\, and\\,\\, j = \\left\\{ {1,2,\\ldots,BLn} \\right\\}$
```

判定条件 `bs[i, j]^(t)` = 1 用于从种群 `P_BAT(t)` 中识别激活的聚类点（[图5.1](#bodymatter-005.xhtml#b_9783110670707-005_fig_001)）对于第 `t^(th)` 代，其中 `i` = {1,2,…,`Psize`} 且 `j` = {1,2,…,`BLn`}。认为激发态受到影响以从种群的每个解中形成活动聚类质心，并用 `𝒩[C][i]` 表示种群的每个解。激活的唯一聚类点的数量 `𝒩[C][i]` 被存储在 `ℬCP[i]` 中。

![图5.1：聚类质心表示方案.](graphic/converted/b_9783110670707-005_fig_001.png)
图5.1：聚类质心表示方案。

现在，从 `ℬCP[i]` 出发，每个解的适应度（`ℱ[T][i]`）借助聚类有效性指标即 `DB-Index` 进行评估。[[式 (5.12)](#bodymatter-005.xhtml#b_9783110670707-005_eq_012)]。（第5–10行）。

现在，从所有计算的适应度值（`𝒪_ℱ[T][i]`）中识别出最佳适应度值 `𝒪_ℱ[T]`，并连同相应的聚类点数 `𝒪_𝒩[C]` 一起保存。（第11行）。

使用旋转门（[式 (5.10)](#bodymatter-005.xhtml#b_9783110670707-005_eq_010)）策略创建了另一组种群 `P_BAT[new]^(α)` 和 `P_BAT[new]^(β)`。根据最佳适应度值，使用其先前的值或最近创建的值 `P_BAT[new]^(α)` 和 `P_BAT[new]^(β)` 来更新 `P_BAT^(α)` 和 `P_BAT^(β)` 的值。现在，如果最近创建的值无法产生更好的适应度值，则当前值集被拒绝，种群中保留旧值集，否则接受新值集。现在可以创建新的量子种群，因为它在解空间中产生多样性（第12行）。

应用了旋转门更新过程，该过程产生了最佳适应度值（`ℬℱ[T]`），相应的聚类点被保存在 `ℬCP` 中，而 `ℬnc` 保存了聚类点的总数（第13行）。

在主循环的每次执行期间，量子位置和速度由 [式 (5.13)](#bodymatter-005.xhtml#b_9783110670707-005_eq_021) 和 [(5.14)](#bodymatter-005.xhtml#b_9783110670707-005_eq_022) 更新（第16行）。

旋转门策略负责最佳量子解的改进（第17行）。

根据更新位置计算的适应度选择最佳解，并使用 [式 (5.15)](#bodymatter-005.xhtml#b_9783110670707-005_eq_015) 生成局部解。（第18–20行）。

接下来，估计新的量子解，并通过应用旋转门策略更新状态 `Q^(BAT)(t)[J]`、`P_BAT[J]^(α)` 和 `P_BAT[J]^(β)` 的每个值。（第21–22行）。

现在接受新解，并通过 [式 (5.16)](#bodymatter-005.xhtml#b_9783110670707-005_eq_016) 和 ([5.17](#bodymatter-005.xhtml#b_9783110670707-005_eq_017)) 增加每只蝙蝠的脉冲率并降低每只蝙蝠的响度。（第23–26行）。

最佳量子解被确定并保存（第27行）。

为了获得最佳解，主循环继续执行预定义次数（第14–29行）。

最后，确定了最佳量子解，并确定了其相关的适应度值的最优聚类数。（第30行）。

QIBA 的工作原理如下所述。

### 算法
Quantum Inspired Bat Algorithm for automatic clustering

输入参数：
最大迭代次数：`MI`
种群大小：`Psize`

输出参数：
最优聚类数：`𝒪_𝒩[C]`
最优适应度值：`𝒪_ℱ[T]`

```
1. A population P_BAT having Psize number of particles (bat) was initialized.
2. Quantum state Q^(BAT)(t) was created for each of the elements of P_BAT. And in order to encode P_BAT the information of the quantum state was used and produce P_BAT^(α) and P_BAT^(β).
3. The frequency (ℬℱ)[i] and velocity (ℬ𝒱[i]) were initialized for every solution of the population.
4. The loudness (ℬA[i]) and the pulse rates (ℬR[i]) were also initialized.
5. for i = 1 to Psize do
6. for j = 1 to BLn do
7. 𝒩[C][i] numbers of cluster points from P_BAT[i] were created by satisfying the condition P_BAT[ij]^(β) > P_BAT[ij]^(α) and the cluster points were stored in ℬCP[i].
8. Now, the fitness ℱ[T][i] was evaluated from ℬCP[i] by using the cluster validity index (DB-Index).
9. end for.
10. end for.
11. The best solution in terms of the best fitness value 𝒪_ℱ[T] was identified.
12. Now, the quantum state Q^(BAT)(t) was updated by using quantum rotation gate to generate new set of values of P_BAT^(α) and P_BAT^(β).
13. The steps 5 to 12 were continued until a predefined condition was satisfied in order to identify the best fitness value ℬℱ[T].
14. for I = 1 to MI do
15. for J = 1 to Psize do
16. The velocity and location of every particles in P_BAT[J] were modified by using the eqs. (5.13) and (5.14).
17. Each value of the state Q^(BAT)(t)[J], P_BAT[J]^(α) and P_BAT[J]^(β) were updated using the rotation gate strategy in order to achieve a better solution from the population.
18. if (Rand(0,1)>ℬR[ij]) then
19. The best solution was selected after calculating the fitness of all bats from their updated positions and a native solution was generated with the help of the eq. (5.15).
20. end if.
21. Now, new solution was evaluated.
22. Each value of the state Q^(BAT)(t)[J], P_BAT[J]^(α) and P_BAT[J]^(β) were updated by using the rotation gate strategy in order to achieve a better solution from the population.
23. if (Rand(0,1)<ℬA[i]&ℬℱ[T][new]<ℬℱ[T][Best]) then
24. New solution was accepted.
25. ℬR[i] was increased and ℬA[i] was decreased by using the eqs. (5.16) and (5.17).
26. end if.
27. The best solution was chosen.
28. end for.
29. end for
30. Finally, the algorithm produced and reported the optimal number of cluster points 𝒪_𝒩[C] with its associated fitness value 𝒪_ℱ[T].
```

## 5.8 实验与结果分析
