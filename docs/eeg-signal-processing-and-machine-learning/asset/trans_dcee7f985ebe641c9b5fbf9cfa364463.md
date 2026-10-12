

## 8.6 时频域连接（续）

### 公式 (8.31)
![equation](images/c8-disp-0031.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.2em"/><msub><mi mathvariant="bold">X</mi><mi>k</mi></msub><mfenced open="(" close=")"><mrow><mi mathvariant="normal">τ</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><msubsup><mo>∫</mo><mrow><mo form="postfix">−</mo><mo>∞</mo></mrow><mo>∞</mo></msubsup><msub><mi mathvariant="bold">x</mi><mi>k</mi></msub><mfenced open="(" close=")"><mi>t</mi></mfenced><mfrac><mrow><mo>∂</mo><mi>f</mi><mo>∂</mo></mrow><msqrt><mrow><mn>2</mn><mi mathvariant="normal">π</mi></mrow></msqrt></mfrac><msup><mi>e</mi><mrow><mo form="prefix">−</mo><mfrac><mrow><msup><mfenced open="(" close=")"><mrow><mi mathvariant="normal">τ</mi><mo>−</mo><mi>t</mi></mrow></mfenced><mn>2</mn></msup><msup><mi>f</mi><mn>2</mn></msup></mrow><mn>2</mn></mfrac></mrow></msup><msup><mi>e</mi><mrow><mo form="prefix">−</mo><mi>i</mi><mn>2</mn><mi mathvariant="normal">π</mi><mtext mathvariant="italic">ft</mtext></mrow></msup><mi mathvariant="italic">dt</mi></math>

这与短时频率变换非常相似，在短时频率变换中，信号最初由高斯形状窗加窗。然而，该高斯窗的方差与频率的倒数成正比。因此，无需定义方差。信号的互谱定义为：

### 公式 (8.32)
![equation](images/c8-disp-0032.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.2em"/><msubsup><mi>C</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><mfrac><mrow><msubsup><mi>S</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced></mrow><msqrt><mrow><msubsup><mi>S</mi><mi mathvariant="italic">kk</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><msubsup><mi>S</mi><mi mathvariant="italic">ll</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced></mrow></msqrt></mfrac></math>

其中

### 公式 (8.33)
![equation](images/c8-disp-0033.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.2em"/><msubsup><mi>S</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><mfenced open="⟨" close="⟩"><mrow><msub><mi>X</mi><mi>k</mi></msub><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><msubsup><mi>X</mi><mi>l</mi><mo>*</mo></msubsup><mo stretchy="true">(</mo><mi>t</mi><mo>,</mo><mi>f</mi><mo stretchy="true">)</mo></mrow></mfenced></math>

其中 `⟨⟩` 表示样本期望，为复值。S-相干性的虚部（`ImSCoh`）与信号 `x[k](t)` 和 `x[l](t)` 在各频率 `f` 处的相位差有关，例如，若 `ImSCoh` 为正，则 `x[k](t)` 和 `x[l](t)` 存在相互作用，且 `x[k](t)` 超前于 `x[l](t)`。随后，互谱值被用于估计组合权重：

### 公式 (8.34)
![equation](images/c8-disp-0034.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msubsup><mi>a</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mo>=</mo><mfrac><mrow><mfenced open="" close=")"><mo mathvariant="italic">max</mo><mo>(</mo><mo>Im</mo><mo stretchy="true" form="prefix">(</mo><msubsup><mi>C</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>,</mo><mn>0</mn></mfenced></mrow><mrow><msub><mo>∑</mo><mrow><mi>l</mi><mo>∈</mo><msub><mi>N</mi><mi>k</mi></msub></mrow></msub><mo mathvariant="italic">max</mo><mfenced open="(" close=")"><mrow><mo>Im</mo><mo stretchy="true" form="prefix">(</mo><msubsup><mi>C</mi><mi mathvariant="italic">kl</mi><mfenced open="(" close=")"><mi mathvariant="italic">ST</mi></mfenced></msubsup><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>,</mo><mn>0</mn></mrow></mfenced></mrow></mfrac></math>

[图 8.3](#c08.xhtml#c8-fig-0003) 展示了一个模拟场景下的算法性能，该场景包含六个含噪测量。在该模拟中，区域 1 将其信号传输至区域 2，另一消息分别经由区域 5、4 和 3 传输。最后一个区域包含一个独立源，无任何泄漏或向其他区域的传输。信噪比（SNR）为 10 dB，结果为三次试验的平均值。

## 8.7 被试间 EEG 连接

### 8.7.1 目的

此处的目的是估计两个或多个被试在执行合作或竞争任务期间的大脑连接。从多个被试大脑同时记录 EEG 称为 *EEG 超扫描*。人际身体运动同步现象已被广泛观察到。例如，人们常有这样的体验：与朋友同行时，自己的脚步会无意识地与朋友的脚步同步。相反，在合作或竞争表现中，一个人的动作是对另一人（或他人）动作的反应。这可以在团队合作或比赛中一名选手对阵另一名选手的情况下加以考察。此类身体运动相干性机制及其与隐性社会交互的关系仍不清晰。

### 8.7.2 技术相关性

最近，一项在同时记录两名参与者 EEG 的情况下测量其指尖运动的研究被引入 [[44]](#c08.xhtml#c8-bib-0044)。特别是，其目的是评估两名或多名参与者之间的身体运动同步性和隐性社会交互，并评估其大脑区域内部及之间的潜在动力学和有效连接。多个大脑的并发活动可以被估计，不同大脑区域之间的因果连接（超连接）可以被指示。

在被试执行合作或竞争任务时，研究不同被试的并发和同步大脑活动，对于调查许多范式至关重要，在这些范式中，个体间同步交互的知识具有价值。无论是正常被试还是患有各种脑异常（如 AD、精神疲劳、药物输注期间）的患者，其专注、预测、合作、跟随、竞争、学习以及从事长期枯燥任务的能力，均可通过被试间合作或竞争时的同步 EEG 记录得到有效研究。

最近，基于单被试 EEG 记录建立的大脑连接测量方法，已被扩展并应用于同步多脑记录 [[45](#c08.xhtml#c8-bib-0045)–[50](#c08.xhtml#c8-bib-0050)]。记录的数据以不同方式进行处理。在一种基于时频域的方法中，利用 EEG 节律在常规频带（delta、theta、alpha 和 beta）中的幅度变化以及同步性。这些方法旨在估计来自多个大脑的记录 EEG 之间的相干性或同步性。

