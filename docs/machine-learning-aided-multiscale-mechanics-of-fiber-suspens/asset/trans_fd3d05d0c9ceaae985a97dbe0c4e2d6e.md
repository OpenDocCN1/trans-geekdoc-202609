
其中 \(\mathbb{I} \in (\mathbb{R}^3)^{\otimes 4}\) 表示四阶单位张量。算子 \(\mathbb{I}_{\mathbb{I}}(\boldsymbol{n})\) 编码了由层合板的周期性、各相间的完美粘结、动量平衡 (5.11) 以及本构方程 (5.19) 所施加的约束。取决于我们希望计算层合板的原始有效性质还是对偶有效性质，需要不同的算子 \(\mathbb{I}_{\mathbb{I}}(\boldsymbol{n})\)。对于原始有效性质的均质化，即 \(\bar{\mathbb{A}} = \bar{\mathbb{M}}\)，算子 \(\mathbb{I}_{\mathbb{I}}(\boldsymbol{n})\) 等于算子 \(\mathbb{I}_1^{\text{co}}(\boldsymbol{n})\)。对于对偶有效性质的均质化，即 \(\bar{\mathbb{A}} = \bar{\mathbb{K}}\)，算子 \(\mathbb{I}_{\mathbb{I}}(\boldsymbol{n})\) 等于算子 \(\mathbb{I}_2^{\text{co}}(\boldsymbol{n})\)。算子 \(\mathbb{I}_1^{\text{co}}\) 和 \(\mathbb{I}_2^{\text{co}}\) 通过其对二阶张量 \(\boldsymbol{X} \in \text{Sym}(3)\) 的作用来定义

\(\mathbb{I}_1^{\text{co}}(\boldsymbol{n})[\boldsymbol{X}] = 2(\boldsymbol{X}\boldsymbol{n}) \otimes_s \boldsymbol{n} - (\boldsymbol{n} \cdot \boldsymbol{X}\boldsymbol{n})\boldsymbol{n} \otimes \boldsymbol{n} \quad \text{(5.28)}\)

和

\(\mathbb{I}_2^{\text{co}}(\boldsymbol{n})[\boldsymbol{X}] = \boldsymbol{X} - \mathbb{I}_1^{\text{co}}(\boldsymbol{n})\boldsymbol{X}, \quad \text{(5.29)}\)

其中 \(\otimes_s\) 表示对称化 dyadic 乘积。算子 \(\mathbb{I}_1^{\text{co}}\) 和 \(\mathbb{I}_2^{\text{co}}\) 投影到子空间

\(\mathcal{E}^\text{co} = \{ \text{Sym}(3) \ni \boldsymbol{X} = \boldsymbol{d} \otimes \boldsymbol{n} + \boldsymbol{n} \otimes \boldsymbol{d} \mid \boldsymbol{d} \in \mathbb{R}^3 \} \quad \text{(5.30)}\)

和

\(\mathcal{S}^\text{co} = \{ \text{Sym}(3) \ni \boldsymbol{X} \mid \boldsymbol{X}\boldsymbol{n} = \boldsymbol{0} \}, \quad \text{(5.31)}\)

并源于字段 \([[\nabla^s w]] \in \mathcal{E}^\text{co}\) 的跳跃的事实

\([[\nabla^s w]] = [[\nabla w \boldsymbol{n}]] \otimes_s \boldsymbol{n}, \quad \text{(5.32)}\)

以及应力 \([[\boldsymbol{\sigma}]] \in \mathcal{S}^\text{co}\) 的跳跃存在于互正交子空间上（Milton, 2002, §9），因为有

\([[\boldsymbol{\sigma}\boldsymbol{n}]] = \boldsymbol{0}. \quad \text{(5.33)}\)

有趣的是，运动学无约束线性弹性固体和线性黏性流体的本构方程具有相同的结构，参见方程 (5.19)。此外，方程 (5.32) 和 (5.33) 对分层乳液来说按定义满足，因为各相之间没有滑移，且动量平衡 (5.11) 得到满足。因此，所考虑分层乳液的均质化问题与层合板的均质化问题具有相同的结构。结果，由运动学无约束材料 \(m_1, m_2 \in \mathcal{M}\) 组成的两相分层乳液的有效性质 \(\bar{\mathbb{A}} \in \mathbf{M}^+\) 可以用方程 (5.23) 计算。如果运动学场 \(w\) 是无散度的，使得不可压缩质量守恒 (5.14) 得到满足，则由方程 (5.32) 可得

\(\left[\left[\nabla^s w n\right]\right] \cdot n = 0.\) (5.34)

另外，如果材料 \(m_1, m_2 \in \mathcal{M}\) 是不可压缩的，则由方程 (5.21) 和 (5.33) 可得

\(\left[\left[\sigma n\right]\right] = \mathbf{0} \quad \Longleftrightarrow \quad \left[\left[\tau n\right]\right] = \left[\left[p\right]\right] n.\) (5.35)

因此，跳跃 \(\left[\left[\nabla^s w\right]\right] \in \mathcal{E}^{\text{ico}}\) 和 \(\left[\left[\sigma\right]\right] \in \mathcal{S}^{\text{ico}}\) 存在于互正交空间中

\(\mathcal{E}^{\text{ico}} = \{ \text{Sym}_0(3) \ni X = 2 d \otimes_s n - 2(d \cdot n)n \otimes n \mid d \in \mathbb{R}^3 \}\) (5.36)

和

\(\mathcal{S}^{\text{ico}} = \{ \text{Sym}_0(3) \ni X \mid X n = a n, \ a \in \mathbb{R} \}.\) (5.37)

两个算子 \(\Gamma_1^{\text{ico}}(n)\) 和 \(\Gamma_2^{\text{ico}}(n)\)，通过其对迹为零的二阶张量 \(X \in \text{Sym}_0(3)\) 的作用定义，

\(\Gamma_1^{\text{ico}}(n)[X] = 2(Xn) \otimes_s n - 2(n \cdot Xn)n \otimes n\) (5.38)

和

\(\Gamma_2^{\text{ico}}(n)[X] = X - \Gamma_1^{\text{ico}}(n)[X],\) (5.39)

分别投影到空间 $\mathcal{E}^{\text{ico}}$ 和 $\mathcal{S}^{\text{ico}}$。因此，可以使用 Milton (2002) 中详细介绍的方法来计算由不可压缩组分组成的分层材料的有效性质 \(\bar{\mathbb{A}} \in \text{M}_0^+\)。在此背景下，均质化方程 (5.23) 适用，前提是属性场 \(\mathbb{A} : Y \to \text{M}_0^+\)、参考属性 \(\mathbb{A}_0 \in \text{M}_0^+\) 和算子 \(\mathbb{\Gamma}_{\text{I}}(\boldsymbol{n}) \in (\mathbb{\Gamma}_1^{\text{ico}}(\boldsymbol{n}), \mathbb{\Gamma}_2^{\text{ico}}(\boldsymbol{n}))\) 根据张量 \(\bar{\mathbb{A}}\) 表示原始有效性质还是对偶有效性质来选择。总之，对于由线性材料 \(m_1, m_2 \in \mathcal{M}\) 组成的分层材料，有效材料性质 \((\bar{\mathbb{M}}, \bar{\mathbb{K}}) \in \{(\text{M}^+)^2, (\text{M}_0^+)^2\}\) 可以用均质化方程 (5.23) 计算。算子 \(\mathbb{\Gamma}_{\text{I}}(\boldsymbol{n})\) 的选择取决于各相是可压缩还是不可压缩，以及是寻求原始有效张量还是对偶有效张量。

## 5.2.3 涂层分层材料

由于我们有兴趣为刚性颗粒悬浮液构建 FDMN，因此 FDMN 的架构应能够处理无限黏性，即刚性，相。在本节中，我们利用均质化方程 (5.23) 研究在存在刚性相时反复分层材料的均质化。我们在下文定义并使用分层材料的 *rank*（级）术语，以更好地区分构建分层材料的可能方式。分层材料的级 \(R \in \text{N}_{\ge 0}\) 定义了使用分层方向 \(\boldsymbol{n}_r \in \mathcal{S}^2\) 构建材料所需的分层步骤数，使得索引 \(r\) 从 1 开始到 \(R\) 结束，即 \(r \in \{1, \dots, R\}\)。按定义，0 级分层材料只是一种单相材料，没有任何分层。另外，每个分层步骤中分层的材料不必相同。例如，设 2 级分层材料的第一层由材料 \(m_1\) 和 \(m_2\) 组成。那么，第二层可以由材料 \(m_1\) 和 \(m_2\)（以第一层的形式）以及第三种材料 \(m_3\) 组成。

![](img/283dee3537da34c9897f9777475c5d3d_132_0.png)

图 5.1：具有正交分层方向（a）和非正交分层方向（b）的三级涂层分层材料。核心材料显示为红色，涂层材料显示为灰色。我们通过层厚的选择暗示材料层之间的长度尺分离。图改编自 Storr et al. (2024a, Figure 1)。

在材料对比无限的情况下，一级两相分层材料不适合作为 DMN 的构建块，因为如果其中一相是奇异的，其有效性质总是奇异的。为了寻找能够处理刚性相的构建块，我们遵循 Milton (2002, §9) 详细介绍的术语和分析方法，研究一种特定类型的分层材料的有效性质。我们将这种特定类型的分层材料称为涂层分层材料（CLMs）。构建 CLM 时，一种材料 \(m_2\)（称为涂层）反复分层到另一种材料 \(m_1\)（称为核心）上。分层过程分为多个步骤，使得第 \(r\) 个分层步骤在方向 \(\boldsymbol{n}_r\) 上应用，且分层步骤的总数等于 CLM 的级 \(R\)。例如，图 5.1 描绘了两个三级 CLM，其中分层方向 \(\boldsymbol{n}_r \in \mathcal{N}_1\)
