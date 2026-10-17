
*   `M[ik]` 为手段目标组合集合，每个手段目标处于指定性能水平 `ℓ`，`M[ik]` 中的每个组合均会导致目标 `i` 在性能水平 `k` 达成。

    *   对每个 `m ∈ M[ik]`，`J[ikm]` 为一组手段目标，均为目标 `i` 的子目标，且各自处于某性能水平，它们共同导致目标 `i` 在水平 `k` 达成。

    *   `z[ikm]` 为二元变量，`z[ikm] = 1` 表示 `J[ikm]` 中的每个手段目标 “j” 均处于相关性能水平 `ℓ`；`z[ikm] = 0` 表示否则。

    *   `1a: z[ikm] – x[jℓ] ≤ 0 ∀ m ∈ M[ik], (j,ℓ) ∈ J[ikm]`

    *   `1b: Σ[(j,ℓ)∈Jikm] x[jℓ] - z[ikm] ≤ (|J[ikm]| - 1) ∀ m ∈ M[ik]`

*   目标 “i” 在水平 “k” 达成，仅当 `M[ik]` 中至少有一个组合得以实现：

    `2: x[ik] - Σ[m ∈ Mik] z[ikm] ≤ 0 ∀ i ∈ I, k ∈ K[i]`

*   每个目标 “i” 恰好达成其允许水平 `k ∈ K[i]` 中的一个：

    `3: Σ[k∈Ki] x[ik] = 1 ∀ i ∈ I`

### 资源冲突

*   `q[rjℓ]` 为手段目标 “j” 在水平 “ℓ” 达成所需的可消耗资源 “r” 的最小量，`q[r••]` 为资源 “r” 的总可用量：

*   `4: Σ[j∈IMO] Σ[ℓ∈Ki] q[rjℓ]x[jℓ] ≤ q[r••] ∀ r ∈ R`

### 内在冲突

*   `P` 为具有内在冲突的目标对集合 `(i[1], i[2])`，其中 `i[1] ∈ I` 且 `i[2] ∈ I`，若 `i[1] ∈ I` 达成水平 `k[1]`，则 `i[2] ∈ I` 不能达成水平 `k[2]`。

*   `5: x[i1,k1] + x[i2,k2] ≤ 1 ∀ (i[1],k[1], i[2], k[2]) ∈ P`

### 用于生成备选方案的整数规划问题（*MPP*）

```
IP[GenAlt]: Max {Σ[i∈IFO] Σ[k∈Ki] w[i]v[ik]x[ik] | (1) – (5), & binary restriction on all variables}
```

### A2：生成备选方案过程子阶段

1.  构建并求解问题 `P[GenAlt]`。

2.  给定问题 `P[GenAlt]` 的初始最优解，若存在其他备选最优解则生成它们。

3.  使用 *What-If* 分析和/或敏感性分析，生成问题 `P[GenAlt]` 的其他备选“近似最优”解。

### A3：说明性示例

本节给出一个说明性示例，应用生成并评估备选方案的过程，以满足三类约束。图 A1 显示了某信息安全决策问题的手段-目的目标网络（本例中为层级结构）。

![图 A1 手段-目的目标网络](img/figa1_B.jpg)

图 A1 手段-目的目标网络

每个目标均有三种可能的性能水平（即 *High*（高，3）、*Medium*（中，2）、*Low*（低，1）。需注意，每个目标仅能达成 1 个定性性能水平。表 A1 显示了表示这些事实的约束条件，其中代表各手段目标（*MO*）水平的变量名以 “M” 开头，代表各基本目标（*FO*）水平的变量名以 “F” 开头，且每个变量均为二元变量（即 0 或 1）。

#### 表 A1 每个目标选择一种性能水平的约束

| **类型** | **目标** | **约束** | **说明** |
| --- | --- | --- | --- |
| 手段 | `MO_11` | `M111 + M112 + M113 = 1` | 确保手段目标 `MO_11` 仅选择 1 个水平（即 *High*（`M113 = 1`）、*Medium*（`M112 = 1`）或 *Low*（`M111 = 1`））。其他手段目标同理。 |
| 手段 | `MO_12` | `M121 + M122 + M123 = 1` | |
| 手段 | `MO_21` | `M211 + M212 + M213 = 1` | |
| 手段 | `MO_22` | `M221 + M222 + M223 = 1` | |
| 手段 | `MO_31` | `M311 + M312 + M313 = 1` | |
| 手段 | `MO_32` | `M321 + M322 + M323 = 1` | |
| 基本 | `FO_1` | `F11 + F12 + F13 = 1` | 确保基本目标 `FO_1` 仅选择 1 个水平（即 *High*（`F13 = 1`）、*Medium*（`F12 = 1`）或 *Low*（`F11 = 1`））。其他基本目标同理。 |
| 基本 | `FO_2` | `F21 + F22 + F23 = 1` | |
| 基本 | `FO_3` | `F31 + F32 + F33 = 1` | |

表 A2–A4b 展示了各种其他类型的约束：*绩效水平达成的父子约束*（表 A2）、*内在冲突*（表 A3）以及财务*资源冲突*（表 A4a 和 A4b）。表 A5a 显示了每个基本目标（FO）的权重以及达成每个 FO 每个绩效水平所关联的价值。每个基本目标的最高水平（即第 3 级）的价值设为 100，其较低水平的价值相对于最高水平的价值。诸如层次分析法（如 Saaty (1980)、Bryson (1995)、Osei-Bryson (2006)）等方法可用于推导每个 FO 的相对权重，以及每个 FO 其较低绩效水平相对于其最高绩效水平的相对价值。在表 A5b 中，每个变量的系数是其加权价值。

#### 表 A2 父子约束

| 若 MO_11 和 MO_12 均为*第 3 级*，则 FO_1 为*第 3 级*；若 MO_11 和 MO_12 均为*第 1 级*，则 FO_1 为*第 1 级*； | M113 + M123 – F13 <= 1 F13 – M113 <= 0 F13 – M123 <= 0 M111 + M121 – F11 <= 1 F11 – M111 <= 0 F11 – M121 <= 0 |
| --- | --- |
| 若 MO_21 和 MO_22 均为*第 3 级*，则 FO_2 为*第 3 级*；若 MO_21 和 MO_22 均为*第 1 级*，则 FO_2 为*第 1 级*； | M213 + M223 – F23 <= 1 F23 – M213 <= 0 F23 – M223 <= 0 M211 + M221 – F21 <= 1 F21 – M211 <= 0 F21 – M221 <= 0 |
| 若 MO_31 和 MO_32 均为*第 3 级*，则 FO_3 为*第 3 级*；若 MO_31 和 MO_32 均为*第 1 级*，则 FO_3 为*第 1 级*； | M313 + M323 – F33 <= 1 F33 – M313 <= 0 F33 – M323 <= 0 M311 + M321 – F31 <= 1 F31 – M311 <= 0 F31 – M321 <= 0 |

#### 表 A3 内在冲突约束

| *保密性*（FO_1）和*可用性*（FO_3）不能同时为第 3 级 | F13 + F33 <= 1 |
| --- | --- |

#### 表 A4a 目标水平达成成本

| **基本** | **手段** | **水平** | **成本** |
| --- | --- | --- | --- |
| *保密性(C)* | MO_11 | 3 | 110 |
| | | 2 | 80 |
| | | 1 | 60 |
| | MO_12 | 3 | 85 |
| | | 2 | 75 |
| | | 1 | 55 |
| *完整性(I)* | MO_21 | 3 | 85 |
| | | 2 | 75 |
| | | 1 | 65 |
| | MO_22 | 3 | 80 |
| | | 2 | 70 |
| | | 1 | 60 |
| *可用性(A)* | MO_31 | 3 | 105 |
| | | 2 | 90 |
| | | 1 | 65 |
| | MO_32 | 3 | 110 |
| | | 2 | 85 |
| | | 1 | 70 |

#### 表 A4b 财务资源约束

```
110M113 + 80M112 + 60M111 + 85M123 + 75M122 + 55M121 + 85M213 + 75M212 + 65M211 + 80M223 + 70M222 + 60M221 + 105M313 + 90M312 + 65M311 + 110M323 + 85M322 + 70M321
```

#### 表 A5a 权重与达成水平价值

| **基本目标** | **权重** | **水平** | **价值** |
| --- | --- | --- | --- |
| *保密性* (C) | 0.37 | 3 | 100.00 |
| | | 2 | 85.00 |
| | | 1 | 65.00 |
| *完整性* (I) | 0.30 | 3 | 100.00 |
| | | 2 | 88.00 |
| | | 1 | 75.00 |
| *可用性* (A) | 0.33 | 3 | 100.00 |
| | | 2 | 76.00 |
| | | 1 | 55.00 |

#### 表 A5b IP 问题的目标函数

```
37.00F13 + 31.45F12 + 24.05F11 + 30.00F23 + 26.40F22 + 22.500F21 + 33.00F33 + 25.08F32 + 18.15F31
```

在表 A6 中，我们展示了在三种场景下求解 IP 问题的结果：*无*（即无额外约束）、*保密性*必须处于其最高绩效水平（即设定 FO_1 为第 3 级），以及*完整性*必须处于其最高绩效水平（即设定 FO_2 为第 3 级）。对于每种场景，均提供了*基本目标*和*手段目标*的绩效水平。由于每个 MO 所对应的*达成过程*此前均已确定，因此*生成备选方案的程序*产生的结果可用于确定与给定*手段目标*绩效水平集合相对应的相关*达成过程*的绩效水平。

#### 表 A6 生成备选方案的描述

| **限制条件** | **价值** | **基本** | | **手段** | |
| --- | --- | --- | --- | --- | --- |
| | | **目标** | **水平** | **目标** | **水平** |
| 无 | 90.85 | FO_1 | 2 | MO_11 | 2 |
| | | | | MO_12 | 1 |
| | | FO_2 | 2 | MO_21 | 1 |
| | | | | MO_22 | 3 |
| | | FO_3 | 3 | MO_31 | 3 |
| | | | | MO_32 | 3 |
| 设定 FO_1 为第 3 级 | 88.48 | FO_1 | 3 | MO_11 | 3 |
| | | | | MO_12 | 3 |
| | | FO_2 | 2 | MO_21 | 3 |
| | | | | MO_22 | 1 |
| | | FO_3 | 2 | MO_31 | 2 |
| | | | | MO_32 | 1 |
| 设定 FO_2 为第 3 级 | 87.05 | FO_1 | 1 | MO_11 | 1 |
| | | | | MO_12 | 1 |
| | | FO_2 | 3 | MO_21 | 3 |
| | | | | MO_22 | 3 |
| | | FO_3 | 3 | MO_31 | 3 |
| | | | | MO_32 | 3 |

## 致谢

本章包含的材料此前曾发表于 Osei-Bryson, K. M. (2018). An Integrated Framework for The Value Focused Thinking Methodology. *Proceedings of the 51st Hawaii International Conference on System Sciences*. 1473–1481.

## 参考文献

*   Barclay, C., & Osei-Bryson, K. M. (2010). Project performance development framework: An approach for developing performance criteria & measures for information systems (IS) projects. *International Journal of Production Economics*, *124*(1), 272–292.

*   Barclay, C. (2014). Overview of the Value-focused Thinking methodology. In K.-M. Osei-Bryson & O. Ngwenyama, (Eds) *Advances in Research Methods for Information Systems Research* (pp. 183–196). US: Springer.

*   Barrett-Maitland, N., Barclay, C., & Osei-Bryson, K. M. (2016). Security in social networking services: A value-focused thinking exploration in understanding users’ privacy and security concerns. *Information Technology for Development*, *22*(3), 464–486.

*   Basili, V., Caldiera, G., & Rombach, H. (1994). The goal question metric approach. *Encyclopedia of Software Engineering*, 528–532.

*   Boylan, G. L., Tollefson, M. E. S., Kwinn, L. C. M. J., & Guckert, R. R. (2006). Using value‐focused thinking to select a simulation tool for the acquisition of infantry soldier systems. *Systems Engineering*, *9*(3), 199–212.

*   Bryson, N. (1995). A goal programming method for generating priority vectors. *Journal of the Operational Research Society*, *46*(5), 641–648.

*   Bryson, N. (1996). Group decision-making and the analytic hierarchy process: Exploring the consensus-relevant information content. *Computers & Operations Research*, *23*, 27–35.

*   Chang, J. C. J., Torkzadeh, G., & Dhillon, G. (2004). Re-examining the measurement models of success for Internet commerce. *Information & Management*, *41*(5), 577–584.

*   Chen, J. Q., & Lee, S. M. (2003). An exploratory cognitive DSS for strategic decision making. *Decision Support Systems*, *36*(2), 147–160.

*   Courtney, J. (2001). Decision making and knowledge management in inquiring organizations: Toward a new decision-making paradigm for DSS. *Decision Support Systems*, *31*, 17–38.

*   Doran, G. (1981). There’s a S.M.A.R.T. way to write management goals and objectives. *Management Review*, *70*(1), 35–36.

*   Dhillon, G., & Torkzadeh, G. (2006). Value‐focused assessment of information system security in organizations. *Information Systems Journal*, *16*(3), 293–331.

*   Dhillon, G., Bardacino, J., & Hackney, R. (2002). Value Focused Assessment of Individual Privacy Concerns for Internet Commerce. *ICIS 2002 Proceedings*. Paper 67. [`aisel.aisnet.org/icis2002/67`](http://aisel.aisnet.org)
