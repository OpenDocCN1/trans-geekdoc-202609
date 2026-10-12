
(8.29)![equation](images/c8-disp-0029.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>E</mi><mfenced open="\[" close="\]"><mrow><mi mathvariant="bold">y</mi><msup><mi mathvariant="bold">y</mi><mi>T</mi></msup></mrow></mfenced><mo>=</mo><msup><mfenced open="(" close=")"><mrow><mi mathvariant="bold">I</mi><mo>&#8722;</mo><mi mathvariant="bold">B</mi></mrow></mfenced><mrow><mo form="prefix">&#8722;</mo><mn>1</mn></mrow></msup><mfenced open="(" close=")"><mrow><mi>&#915;&#934;</mi><msup><mi mathvariant="normal">&#915;</mi><mi>T</mi></msup><mo>+</mo><mi mathvariant="normal">&#936;</mi></mrow></mfenced><msup><mfenced open="(" close=")"><msup><mfenced open="(" close=")"><mrow><mi mathvariant="bold">I</mi><mo>&#8722;</mo><mi mathvariant="bold">B</mi></mrow></mfenced><mrow><mo form="prefix">&#8722;</mo><mn>1</mn></mrow></msup></mfenced><mi>T</mi></msup></math>

其中 Ψ = *E*[**ξξ**^(*T*)]。在无约束条件下，由于变量数量（**B**、**Γ**、**Φ** 和 **Ψ**）大于方程数量 (*m + n*)(*m + n* + 1)/2，因此观测协方差与模型隐含协方差之间差异的最小化问题是欠定的。SEM 的意义在于，它基于一些先验的解剖学和生理学（以及可能的功能性）信息，消除了连接图中的某些连接。例如，在 [图 8.2](#c08.xhtml#c8-fig-0002) 中，如果假设模型中不存在连接 a[42]，则可将其设为零。

因此，如果 *r* 是待估计的参数数量，我们将需要满足 *r* ≤ (*m + n*)(*m + n* + 1)/2。参数是通过最小化观测协方差和隐含协方差的函数来估计的。SEM 最广泛使用的目标函数是最大似然 (ML) 函数 [[33]](#c08.xhtml#c8-bib-0033)：

(8.30)![equation](images/c8-disp-0030.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>F</mi><mi mathvariant="italic">ML</mi></msub><mo>=</mo><mo>log</mo><mfenced open="|" close="|"><msub><mi mathvariant="bold">&#8721;</mi><mi mathvariant="italic">mod</mi></msub></mfenced><mo>+</mo><mi>tr</mi><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">&#8721;</mi><mi mathvariant="italic">obs</mi></msub><mo>.</mo><msubsup><mi mathvariant="bold">&#8721;</mi><mi mathvariant="italic">mod</mi><mrow><mo form="prefix">&#8722;</mo><mn>1</mn></mrow></msubsup></mrow></mfenced><mo form="postfix">&#8722;</mo><mo>log</mo><mfenced open="|" close="|"><msub><mi mathvariant="bold">&#8721;</mi><mi mathvariant="italic">obs</mi></msub></mfenced><mo>&#8722;</mo><mi>p</mi></math>

其中 *p* 为观测变量的数量（内源性 + 外源性）。对于多元正态分布变量，ML 函数的最小值乘以 *N* − 1，近似服从自由度为 (*p*[*p* + 1]/2) − *t* 的 **χ**^2 分布，其中 *t* 为待估计的参数数量，*p* 为观测到的内源性和外源性变量的总数。随后可使用 **χ**^2 统计检验来推断所得结构方程模型的统计显著性。公开可用的软件 LISREL [[36]](#c08.xhtml#c8-bib-0036) 可用于实现脑连接的 SEM。

![图 8.2 模拟信号生成中施加的连接模式。链接上的数值代表连接强度。](images/c08f002.gif)

[**图 8.2**](#c08.xhtml#R_c8-fig-0002) 模拟信号生成中施加的连接模式。链接上的数值代表连接强度。

在 [[33]](#c08.xhtml#c8-bib-0033) 中，SEM 首次被应用于 EEG，并研究了噪声和数据长度对结果准确性及建模误差的影响。

在该实验中，作者研究了信噪比 (SNR) 对 SEM 获得的模式连接估计准确性的影响、达到皮层区域间连接估计可接受准确性所需的 EEG 数据量、不精确的解剖模型构建导致的 SEM 性能下降，以及应尽可能避免的误差类型。在该实验中，他们使用了四个大脑皮层区域之间连接的模拟模型。据称，该方法在不同实验条件下恢复了区域间的皮层连接。在下一个试验中，他们将 SEM 应用于人类简单手指敲击实验的数据，以突显该方法在执行简单运动任务期间绘制脑区皮层连接模式的能力。

在上述涉及分布式脑源的大多数脑连接测量方法中，应用真实的头模型是有利的。真实的头模型有助于准确定位（和追踪）参与连接测量的源。尽管求解逆问题（如 [[5](#c08.xhtml#c8-bib-0005), [37](#c08.xhtml#c8-bib-0037)]）和使用 fMRI [[38]](#c08.xhtml#c8-bib-0038) 已被提出用于此目的，但各有缺点。求解逆问题用于偶极子源的定位，无法充分追踪分布式源。相反，fMRI 揭示了作为事件相关活动和皮层激活结果的血管氧合信息。与事件起始或皮层活动（如运动相关活动）相比，它也有 2 到 5 秒的长时间滞后。

在 [[39]](#c08.xhtml#c8-bib-0039) 中，SEM 和 DTF 均被实现用于从 EEG 运动相关电位估计连接。应用 SEM 方法估计连接的结果显示了在运动开始前 alpha 频段获得的具有统计显著性的皮层连接模式。运动前 alpha 频段期间的连接模式主要涉及左顶区，其与左、右前运动皮层区、左感觉运动区以及双侧前额脑区功能连接。

较强的功能连接对应于左顶区与双侧大脑半球前运动区之间的链接。在运动准备和手指运动开始后，可以观察到连接模式的变化。特别是，功能连接链接的起源位于左侧感觉运动皮层区。从那里，建立了与左前额区和双侧前运动区的功能链接。一种功能链接将右顶区与右感觉运动区连接起来。在先前条件下非常活跃的左顶区，转而与左感觉运动区和右前运动皮层区相连。

如前所述，功能连接链接的起源位于左侧感觉运动皮层区 (SMl)。从那里，在左前额区和双侧前运动区（左和右）之间建立了功能链接 [[39]](#c08.xhtml#c8-bib-0039)。模型阶数、ROI 的数量和位置在应用算法前确定。

## 8.6 用于连接估计的 Stockwell 时频变换

在非常近期的实践中，提出了另一种用于脑连接估计的有效方法 [[40](#c08.xhtml#c8-bib-0040)–[42](#c08.xhtml#c8-bib-0042)]。Stockwell 时频变换 (S 变换) [[43]](#c08.xhtml#c8-bib-0043) 是识别连接网络中链接权重的有效方法。与自回归 (AR) 方法相比，该方法更准确，且对时频参数变化的敏感度更低。其定义如下：
