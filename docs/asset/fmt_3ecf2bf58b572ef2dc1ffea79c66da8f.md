
## 8.4.2 偏相干

(8.19)
![equation](img/c8-disp-0019.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msubsup><mi>ξ</mi><mi mathvariant="italic">ij</mi><mn>2</mn></msubsup><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced><mo>=</mo><mfrac><mrow><msubsup><mi>C</mi><mi mathvariant="italic">ij</mi><mn>2</mn></msubsup><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced><msup><mfenced open="|" close="|"><mrow><msub><mi>H</mi><mi mathvariant="italic">ij</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced></mrow></mfenced><mn>2</mn></msup></mrow><mrow><msub><mo>∑</mo><mi>f</mi></msub><munderover><mo>∑</mo><mrow><mi>m</mi><mo>=</mo><mn>1</mn></mrow><mi>k</mi></munderover><msup><mfenced open="|" close="|"><mrow><msub><mi>H</mi><mi mathvariant="italic">im</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced></mrow></mfenced><mn>2</mn></msup></mrow></mfrac><mspace width="0.2em"/></math>

其中 `Cij(ω)` 是偏相干，定义为：

(8.20)
![equation](img/c8-disp-0020.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>C</mi><mi mathvariant="italic">ij</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced><mo>=</mo><mfrac><mrow><msub><mi>M</mi><mi mathvariant="italic">ij</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced></mrow><msqrt><mrow><msub><mi>M</mi><mi mathvariant="italic">ii</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced><msub><mi>M</mi><mi mathvariant="italic">jj</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced></mrow></msqrt></mfrac></math>

而 `Mii(ω)` 和 `Mij(ω)` 分别是频谱和互频谱。此外，在植入电极信号的情况下，区分直接传输与间接传输至关重要。当信号之间存在相位差时，DTF 和 dDTF 都会显示传播。基于相位相干性，可以估计相似频率分量起始之间的延迟，从而揭示传播方向。然而，相位应在 2π 范围内变化（或模 2π），否则方向性可能会被误判。

偏相干分析已被用于确定大脑功能连接的图模型 [[31]](#c08.xhtml#c8-bib-0031)。研究表明，此类分析的结果可能会受到诸如频谱平滑程度、线路和干扰去除、矩阵求逆稳定化、侧瓣泄漏效应的抑制、不同时期和不同受试者结果的组合以及多重假设检验等因素的显著影响。

### 8.4.3 偏导向相干

另一种称为 PDC 的相干度相似度量也已被定义为 [[17]](#c08.xhtml#c8-bib-0017)，[[30]](#c08.xhtml#c8-bib-0030)：

(8.21)
![equation](img/c8-disp-0021.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>P</mi><mi mathvariant="italic">ij</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced><mo>=</mo><mfrac><mrow><msub><mi>A</mi><mi mathvariant="italic">ij</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced></mrow><msqrt><mrow><msubsup><mi mathvariant="bold">a</mi><mi>j</mi><mo>∗</mo></msubsup><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced><msub><mi mathvariant="bold">a</mi><mi>j</mi></msub><mfenced open="(" close=")"><mi mathvariant="normal">ω</mi></mfenced></mrow></msqrt></mfrac></math>

其中 `Aij(ω)` 是 `A(ω)` 的一个元素，`A(ω)` 是 MVAR 模型系数 `A(ω)` 的傅里叶变换，其中 `aj(ω)` 是 `A(ω)` 的第 `j` 列，星号表示向量埃尔米特算子。PDC 仅表示通道之间的直接流向 [[30]](#c08.xhtml#c8-bib-0030)。最后，广义 PDC 方法已被定义为 [[30]](#c08.xhtml#c8-bib-0030)：

## 8.5 利用结构方程建模对连接性进行建模

正如文献[33, 34]所述，连接性可以被建模，且节点信号之间的协方差可与实际测量值进行比较。

结构方程建模（SEM）旨在建立一个先验连接模型，并旨在解答：(i) 变量信噪比（SNR）水平对 SEM 获得的模式连接性估计准确性的影响，(ii) 皮层区域间连接性估计获得良好准确性所需的数据量，(iii) 不精确的解剖模型构建在多大程度上降低 SEM 性能，以及当皮层区域间的连接未被正确假设时，其是否仍能对连接模式进行良好估计，(iv) 应避免哪类错误。SEM 也已被用于对来自高分辨率（空间和时间双高分辨率）EEG 数据的此类活动进行建模。解剖学和生理学约束已被利用将一个欠定方程组转化为一个定解方程组。

SEM 由一组包含观测变量和定义变量间因果关系参数的线性结构方程组成[35]。变量可以是内生的（即在模型中独立于其他变量）或外生的（独立于模型本身）。考虑一组变量（表示为偏离其均值的偏差），具有 N 个观测值，对这些变量的 SEM 估计可表示为：

(8.23)

```
y = By + Γx + ξ
```

其中，`y` 是 `m×1` 因变量（内生变量）向量，`x` 是 `n×1` 自变量（外生变量）向量，`ξ` 是 `m×1` 方程误差向量（随机扰动），`B`（`m×m`）和 `Γ`（`m×n`）分别为内生变量和外生变量的系数矩阵。假设 `ξ` 与数据不相关，`B` 为零对角矩阵。若 `z` 为包含按以下顺序排列的所有 `p = m + n` 个外生和内生变量的向量：

(8.24)

```
z^T = [x1 ⋯ xn y1 ⋯ ym]
```

则观测协方差可表示为：

(8.25)

```
Σ_obs = (1/(N−1)) Z·Z^T
```

其中 `Z` 为 `z` 的 `N` 个观测值组成的矩阵。模型隐含的协方差矩阵可按如下方式获得：

(8.26)

```
Σ_mod = E[z z^T] = [ E[xx^T]  E[xy^T] ]
                    [ E[yx^T]  E[yy^T] ]
```

若 `E[xx^T] = Φ`，则

(8.27)

```
E[xy^T] = ((I − B)^(−1) ΓΦ)^T
```

(8.28)

```
E[yx^T] = (I − B)^(−1) ΓΦ
```

及

(8.29)
![equation](img/c8-disp-0029.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>E</mi><mfenced open="[" close="]"><mrow><mi mathvariant="bold">y</mi><msup><mi mathvariant="bold">y</mi><mi>T</mi></msup></mrow></mfenced><mo>=</mo><msup><mfenced open="(" close=")"><mrow><mi mathvariant="bold">I</mi><mo>−</mo><mi mathvariant="bold">B</mi></mrow></mfenced><mrow><mo form="prefix">−</mo><mn>1</mn></mrow></msup><mfenced open="(" close=")"><mrow><mi>ΓΦ</mi><msup><mi mathvariant="normal">Γ</mi><mi>T</mi></msup><mo>+</mo><mi mathvariant="normal">Ψ</mi></mrow></mfenced><msup><mfenced open="(" close=")"><msup><mfenced open="(" close=")"><mrow><mi mathvariant="bold">I</mi><mo>−</mo><mi mathvariant="bold">B</mi></mrow></mfenced><mrow><mo form="prefix">−</mo><mn>1</mn></mrow></msup></mfenced><mi>T</mi></msup></math>

其中 `Ψ = E[ξξ^T]`。在无约束条件下，由于变量数量（`B`、`Γ`、`Φ` 和 `Ψ`）大于方程数量 `(m + n)(m + n + 1)/2`，因此观测协方差与模型隐含协方差之间差异的最小化问题是欠定的。SEM 的意义在于，它基于一些先验的解剖学和生理学（以及可能的功能性）信息，消除了连接图中的某些连接。例如，在图 8.2 中，如果假设模型中不存在连接 `a[42]`，则可将其设为零。

因此，如果 `r` 是待估计的参数数量，我们将需要满足 `r ≤ (m + n)(m + n + 1)/2`。参数是通过最小化观测协方差和隐含协方差的函数来估计的。SEM 最广泛使用的目标函数是最大似然 (ML) 函数 [[33]](#c08.xhtml#c8-bib-0033)：

(8.30)
![equation](img/c8-disp-0030.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>F</mi><mi mathvariant="italic">ML</mi></msub><mo>=</mo><mo>log</mo><mfenced open="|" close="|"><msub><mi mathvariant="bold">Σ</mi><mi mathvariant="italic">mod</mi></msub></mfenced><mo>+</mo><mi>tr</mi><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">Σ</mi><mi mathvariant="italic">obs</mi></msub><mo>.</mo><msubsup><mi mathvariant="bold">Σ</mi><mi mathvariant="italic">mod</mi><mrow><mo form="prefix">−</mo><mn>1</mn></mrow></msubsup></mrow></mfenced><mo form="postfix">−</mo><mo>log</mo><mfenced open="|" close="|"><msub><mi mathvariant="bold">Σ</mi><mi mathvariant="italic">obs</mi></msub></mfenced><mo>−</mo><mi>p</mi></math>

其中 `p` 为观测变量的数量（内源性 + 外源性）。对于多元正态分布变量，ML 函数的最小值乘以 `N − 1`，近似服从自由度为 `(p[p + 1]/2) − t` 的 `χ²` 分布，其中 `t` 为待估计的参数数量，`p` 为观测到的内源性和外源性变量的总数。随后可使用 `χ²` 统计检验来推断所得结构方程模型的统计显著性。公开可用的软件 LISREL [[36]](#c08.xhtml#c8-bib-0036) 可用于实现脑连接的 SEM。

![图 8.2 模拟信号生成中施加的连接模式。链接上的数值代表连接强度。](img/c08f002.gif)

**图 8.2** 模拟信号生成中施加的连接模式。链接上的数值代表连接强度。

在 [[33]](#c08.xhtml#c8-bib-0033) 中，SEM 首次被应用于 EEG，并研究了噪声和数据长度对结果准确性及建模误差的影响。

在该实验中，作者研究了信噪比 (SNR) 对 SEM 获得的模式连接估计准确性的影响、达到皮层区域间连接估计可接受准确性所需的 EEG 数据量、不精确的解剖模型构建导致的 SEM 性能下降，以及应尽可能避免的误差类型。在该实验中，他们使用了四个大脑皮层区域之间连接的模拟模型。据称，该方法在不同实验条件下恢复了区域间的皮层连接。在下一个试验中，他们将 SEM 应用于人类简单手指敲击实验的数据，以突显该方法在执行简单运动任务期间绘制脑区皮层连接模式的能力。

在上述涉及分布式脑源的大多数脑连接测量方法中，应用真实的头模型是有利的。真实的头模型有助于准确定位（和追踪）参与连接测量的源。尽管求解逆问题（如 [5, 37]）和使用 fMRI [[38]](#c08.xhtml#c8-bib-0038) 已被提出用于此目的，但各有缺点。求解逆问题用于偶极子源的定位，无法充分追踪分布式源。相反，fMRI 揭示了作为事件相关活动和皮层激活结果的血管氧合信息。与事件起始或皮层活动（如运动相关活动）相比，它也有 2 到 5 秒的长时间滞后。

在 [[39]](#c08.xhtml#c8-bib-0039) 中，SEM 和 DTF 均被实现用于从 EEG 运动相关电位估计连接。应用 SEM 方法估计连接的结果显示了在运动开始前 alpha 频段获得的具有统计显著性的皮层连接模式。运动前 alpha 频段期间的连接模式主要涉及左顶区，其与左、右前运动皮层区、左感觉运动区以及双侧前额脑区功能连接。

较强的功能连接对应于左顶区与双侧大脑半球前运动区之间的链接。在运动准备和手指运动开始后，可以观察到连接模式的变化。特别是，功能连接链接的起源位于左侧感觉运动皮层区。从那里，建立了与左前额区和双侧前运动区的功能链接。一种功能链接将右顶区与右感觉运动区连接起来。在先前条件下非常活跃的左顶区，转而与左感觉运动区和右前运动皮层区相连。

如前所述，功能连接链接的起源位于左侧感觉运动皮层区 (SMl)。从那里，在左前额区和双侧前运动区（左和右）之间建立了功能链接 [[39]](#c08.xhtml#c8-bib-0039)。模型阶数、ROI 的数量和位置在应用算法前确定。

## 8.6 用于连接估计的 Stockwell 时频变换

在非常近期的实践中，提出了另一种用于脑连接估计的有效方法 [40–42]。Stockwell 时频变换 (S 变换) [[43]](#c08.xhtml#c8-bib-0043) 是识别连接网络中链接权重的有效方法。与自回归 (AR) 方法相比，该方法更准确，且对时频参数变化的敏感度更低。其定义如下：

### 8.6.1 公式 (8.31)

![equation](img/c8-disp-0031.png)
