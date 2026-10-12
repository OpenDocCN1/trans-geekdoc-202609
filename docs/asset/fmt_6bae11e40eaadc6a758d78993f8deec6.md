
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.2em"/><msub><mi mathvariant="bold">X</mi><mi>k</mi></msub><mfenced open="(" close=")"><mrow><mi mathvariant="normal">τ</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><msubsup><mo>∫</mo><mrow><mo form="postfix">−</mo><mo>∞</mo></mrow><mo>∞</mo></msubsup><msub><mi mathvariant="bold">x</mi><mi>k</mi></msub><mfenced open="(" close=")"><mi>t</mi></mfenced><mfrac><mrow><mo>∂</mo><mi>f</mi><mo>∂</mo></mrow><msqrt><mrow><mn>2</mn><mi mathvariant="normal">π</mi></mrow></msqrt></mfrac><msup><mi>e</mi><mrow><mo form="prefix">−</mo><mfrac><mrow><msup><mfenced open="(" close=")"><mrow><mi mathvariant="normal">τ</mi><mo>−</mo><mi>t</mi></mrow></mfenced><mn>2</mn></msup><msup><mi>f</mi><mn>2</mn></msup></mrow><mn>2</mn></mfrac></mrow></msup><msup><mi>e</mi><mrow><mo form="prefix">−</mo><mi>i</mi><mn>2</mn><mi mathvariant="normal">π</mi><mtext mathvariant="italic">ft</mtext></mrow></msup><mi mathvariant="italic">dt</mi></math>

这与短时频率变换非常相似，在短时频率变换中，信号最初由高斯形状窗加窗。然而，该高斯窗的方差与频率的倒数成正比。因此，无需定义方差。信号的互谱定义为：

#### 公式 (8.32)

![equation](img/c8-disp-0032.png)

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.2em"/><msubsup><mi>C</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><mfrac><mrow><msubsup><mi>S</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced></mrow><msqrt><mrow><msubsup><mi>S</mi><mi mathvariant="italic">kk</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><msubsup><mi>S</mi><mi mathvariant="italic">ll</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced></mrow></msqrt></mfrac></math>

其中

#### 公式 (8.33)

![equation](img/c8-disp-0033.png)

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.2em"/><msubsup><mi>S</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><mfenced open="⟨" close="⟩"><mrow><msub><mi>X</mi><mi>k</mi></msub><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><msubsup><mi>X</mi><mi>l</mi><mo>*</mo></msubsup><mo stretchy="true">(</mo><mi>t</mi><mo>,</mo><mi>f</mi><mo stretchy="true">)</mo></mrow></mfenced></math>

其中 `⟨⟩` 表示样本期望，为复值。S-相干性的虚部（`ImSCoh`）与信号 `xk` 和 `xl` 在各频率 `f` 处的相位差有关，例如，若 `ImSCoh` 为正，则 `xk` 和 `xl` 存在相互作用，且 `xk` 超前于 `xl`。随后，互谱值被用于估计组合权重：

#### 公式 (8.34)

![equation](img/c8-disp-0034.png)

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msubsup><mi>a</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mo>=</mo><mfrac><mrow><mfenced open="" close=")"><mo mathvariant="italic">max</mo><mo>(</mo><mo>Im</mo><mo stretchy="true" form="prefix">(</mo><msubsup><mi>C</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>,</mo><mn>0</mn></mfenced></mrow><mrow><msub><mo>∑</mo><mrow><mi>l</mi><mo>∈</mo><msub><mi>N</mi><mi>k</mi></msub></mrow></msub><mo mathvariant="italic">max</mo><mfenced open="(" close=")"><mrow><mo>Im</mo><mo stretchy="true" form="prefix">(</mo><msubsup><mi>C</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>,</mo><mn>0</mn></mrow></mfenced></mrow></mfrac></math>

图 8.3 展示了一个模拟场景下的算法性能，该场景包含六个含噪测量。在该模拟中，区域 1 将其信号传输至区域 2，另一消息分别经由区域 5、4 和 3 传输。最后一个区域包含一个独立源，无任何泄漏或向其他区域的传输。信噪比（SNR）为 10 dB，结果为三次试验的平均值。

## 8.7 被试间 EEG 连接

### 8.7.1 目的

此处的目的是估计两个或多个被试在执行合作或竞争任务期间的大脑连接。从多个被试大脑同时记录 EEG 称为 `EEG 超扫描`。人际身体运动同步现象已被广泛观察到。例如，人们常有这样的体验：与朋友同行时，自己的脚步会无意识地与朋友的脚步同步。相反，在合作或竞争表现中，一个人的动作是对另一人（或他人）动作的反应。这可以在团队合作或比赛中一名选手对阵另一名选手的情况下加以考察。此类身体运动相干性机制及其与隐性社会交互的关系仍不清晰。

### 8.7.2 技术相关性

最近，一项在同时记录两名参与者 EEG 的情况下测量其指尖运动的研究被引入 [[44]](#c08.xhtml#c8-bib-0044)。特别是，其目的是评估两名或多名参与者之间的身体运动同步性和隐性社会交互，并评估其大脑区域内部及之间的潜在动力学和有效连接。多个大脑的并发活动可以被估计，不同大脑区域之间的因果连接（超连接）可以被指示。

在被试执行合作或竞争任务时，研究不同被试的并发和同步大脑活动，对于调查许多范式至关重要，在这些范式中，个体间同步交互的知识具有价值。无论是正常被试还是患有各种脑异常（如 AD、精神疲劳、药物输注期间）的患者，其专注、预测、合作、跟随、竞争、学习以及从事长期枯燥任务的能力，均可通过被试间合作或竞争时的同步 EEG 记录得到有效研究。

最近，基于单被试 EEG 记录建立的大脑连接测量方法，已被扩展并应用于同步多脑记录 [45–50]。记录的数据以不同方式进行处理。在一种基于时频域的方法中，利用 EEG 节律在常规频带（delta、theta、alpha 和 beta）中的幅度变化以及同步性。这些方法旨在估计来自多个大脑的记录 EEG 之间的相干性或同步性。

![Figure 8.3 The result of application of S‐transform to a set of simulated sources for connectivity estimation.](img/c08f003.gif)

**Figure 8.3** 将 S 变换应用于一组用于连接性估计的模拟源的结果。

第二种方法基于连接性或同步性度量，允许估计多个大脑中的并发活动以及不同大脑区域之间的连接（所谓的超连接）。建议在该方法中使用格兰杰因果性。MVAR 结合 DTF 等多种技术也可被使用。上述方法也可以结合使用，以提高系统的有效性。

作为一个很好的例子，研究表明 AD 与功能脑网络的改变密切相关，即不同脑区之间的功能连接性 [[51]](#c08.xhtml#c8-bib-0051)。已经对 AD、正常对照 (NC) 和轻度认知障碍 (MCI) 估计了叶内连接、叶间连接以及半球间连接。AD 的颞叶直接叶内连接显著少于 NC。颞叶内的这种直接连接可能会因 AD 而减弱。研究还表明，与 NC 相比，AD 中海马和海马旁区与其他区域的分离程度要大得多。然而，与 NC 相比，MCI 的颞叶在直接连接数量上并未显示出显著下降。AD 的额叶显示出比 NC 多得多的连接性。正如文献 [[51]](#c08.xhtml#c8-bib-0051) 及其参考文献所指出的，这被解释为认知资源的代偿性重新分配或调动。在顶叶内连接和枕叶内连接方面，AD、MCI 和 NC 之间没有显著差异。

就叶间连接性而言，一般来说，人脑的叶间连接数量往往少于叶内连接。此外，AD 的顶枕直接连接显著多于 NC。AD 顶叶与枕叶之间连接数量的增加此前已在文献 [[52]](#c08.xhtml#c8-bib-0052) 中报道。这也可能被解释为一种代偿效应。此外，与 NC 相比，MCI 也显示出顶叶和枕叶之间直接连接数量的增加，但这种增加不如 AD 显著。虽然额叶与枕叶之间直接连接数量在 AD 和 NC 之间差异不大，但对于 MCI 却显示出显著下降。此外，AD 导致颞枕连接和额顶连接减少，但顶颞连接性高于 NC。

最后，半球间连接性估计结果表明，AD 破坏了左右半球同一区域之间的强连接，而这种破坏在 MCI 中并不显著 [[51]](#c08.xhtml#c8-bib-0051)。

为了达到相同的目的，Escudero 等人 [[53]](#c08.xhtml#c8-bib-0053) 进行了另一项研究，旨在从 MEG 信号中区分 NC、AD 和 MCI。这将在第 15 章中讨论，该章探讨了神经退行性疾病在 EEG 中的表现。

## 8.8 用于皮层相互作用估计的状态空间模型

上述大多数用于从 EEG 或 MEG 估计大脑皮层连接性的方法都受到测量中噪声的影响。因此，如果能开发出一种合适的技术来改进预测/连接参数的估计，并使其对噪声更具鲁棒性，那将非常有用 [[54]](#c08.xhtml#c8-bib-0054)。

Nalatore 等人 [[55]](#c08.xhtml#c8-bib-0055) 开发了一种状态空间方法来估计用于侵入性脑电生理记录的 MVAR 模型，并表明显式建模噪声可改进连接性估计。Shumway 和 Stoffer [[56]](#c08.xhtml#c8-bib-0056) 引入了一种期望最大化方法，用于状态空间 MVAR 模型中的 ML 参数估计。

文献 [[57]](#c08.xhtml#c8-bib-0057) 开发了一种状态空间模型来估计 MVAR 参数。这种模型可以表示皮层动力学的 MVAR 模型，而观测方程则描述了将皮层信号与测量的 EEG 以及空间相关噪声的存在联系起来的物理关系。在该模型中，假设皮层信号源自已知的皮层区域，但每个区域内活动的空间分布未知。然后，通过期望最大化方法计算 MVAR 参数。该算法还可从测量的 EEG 中计算出空间活动分布分量和噪声的空间协方差矩阵 [[57]](#c08.xhtml#c8-bib-0057)。

状态空间方法并不能规避 EEG 和 MEG 关于噪声的局限性，但它利用 ML 准则从信号中求解 MVAR 参数。已知 ML 估计是渐近无偏的，随着数据长度增加，其方差趋近于 Cramer-Rao 下界。因此，在两阶段方法中，首先通过求解逆问题的一个变体来估计皮层源，接下来，将 MVAR 模型拟合到估计的皮层信号上 [[57]](#c08.xhtml#c8-bib-0057)。从数学上讲，该过程可表示如下：

考虑 `x_{n,j} = [x_{n,j}¹, ..., x_{n,j}^M]^T, n = 1, ..., N, j = 1, ..., J` 为第 *j* 次试验的一个 *M* × 1 状态向量，代表来自 *M* 个区域在时间 *n* 的皮层信号样本。用于表示皮层信号 **x**[*n*, *j*] 的 *P* 阶 MVAR 可描述为：

(8.35)

```
x_{n,j} = Σ_{p=1}^P A_p x_{n-p,j} + w_{n,j}
```

其中 **A**[*p*] 为预测系数矩阵。这可重写为：

(8.36)

```
x_{n,j} = A z_{n-1,j} + w_{n,j}
```

### 状态空间模型与连接性估计

其中 **A** = [**A** [1,] …, **A**[*P*]] 是一个 *M* × *MP* 的预测系数矩阵，而 **z**[*n*−1, *j*] = [**x**[*n*−1, *j*]^T^, …, **x**[*n*−*P*, *j*]^T^]^T^ 是一个包含过去 *P* 个状态向量的 *MP* × 1 向量。此处假设初始向量 **z**[0, *j*] 服从高斯分布，具有未知均值 *μ*[**0**] 和未知协方差矩阵 **Σ**[**0**]。观测值 **y**[*n*, *j*] 的动态状态空间模型表示为：

(8.37)

```
y[n, j] = CΛ x[n, j] + v[n, j]
```

这可以与公式 (8.36) 中的 MVAR 模型结合，形成状态空间方程 [[57]](#c08.xhtml#c8-bib-0057)：

(8.38)

```
{
x[n, j] = A z[n−1, j] + w[n, j]
y[n, j] = CΛ x[n, j] + v[n, j]
}
```
