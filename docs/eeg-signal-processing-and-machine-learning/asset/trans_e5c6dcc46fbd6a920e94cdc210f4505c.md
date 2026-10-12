

## 10.6.2 混合波束成形 – 粒子滤波

在 EEG 或 MEG 源定位中，未知参数的数量往往多于已知测量值的数量，因此系统是欠定的。*偶极子源定位* 假设一个或多个电流偶极子代表电源 [\[80\]](#c10.xhtml#c10-bib-0080)。为了表达和构建该问题，假设在时间 *k* 来自 *M* 个传感器的测量多通道信号 **y**[k] 由 *q* 个偶极子产生，因此我们可以将 **y**[k] 建模为：

(10.70)
![equation](images/c10-disp-0070.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><munder><mo>min</mo><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup></munder><mfenced open="&#8214;" close="&#8214;"><mrow><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup><mi mathvariant="bold">y</mi></mrow></mfenced><mspace width="1em"/><mtext>subject to</mtext><mspace width="0.2em"/><munder><mo>min</mo><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup></munder><mfenced open="&#8214;" close="&#8214;"><mrow><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup><mi mathvariant="bold">n</mi></mrow></mfenced><mo>,</mo><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup><mi mathvariant="bold">H</mi><mfenced open="(" close=")"><msub><mi mathvariant="normal">&#961;</mi><mn>1</mn></msub></mfenced><mo>=</mo><mn>0</mn><mo>,</mo><mtext>and</mtext><mspace width="0.2em"/><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup><mi mathvariant="bold-italic">H</mi><mfenced open="(" close=")"><msub><mi mathvariant="normal">&#961;</mi><mn>2</mn></msub></mfenced><mo>=</mo><mi mathvariant="bold">I</mi> <ce:anchor id="pp:330 np:331" role="page-break"/> <ce:anchor id="pp:331 np:332" role="page-break"/></math>

项 **W**^(*T*) **H**(*ρ* [1]) 使第一个源失效。对于更多源，在检测新源之前应使更多源失效。**W** 的最优解随后可按 [\[74\]](#c10.xhtml#c10-bib-0074) 找到：

(10.71)
![equation](images/c10-disp-0071.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msup><mi mathvariant="bold">W</mi><mi>T</mi></msup><mo>=</mo><msubsup><mover accent="true"><mi mathvariant="bold">I</mi><mo stretchy="true">~</mo></mover><mi>d</mi><mi>T</mi></msubsup><msup><mfenced open="(" close=")"><mrow><msup><mover accent="true"><mi mathvariant="bold">H</mi><mo stretchy="true">~</mo></mover><mi>T</mi></msup><msup><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">C</mi><mi>y</mi></msub><mo>+</mo><mi>&#955;</mi><msub><mi mathvariant="bold">C</mi><mi>n</mi></msub></mrow></mfenced><mrow><mo form="prefix">&#8722;</mo><mn>1</mn></mrow></msup><mover accent="true"><mi mathvariant="bold">H</mi><mo stretchy="true">~</mo></mover></mrow></mfenced><mrow><mo form="prefix">&#8722;</mo><mn>1</mn></mrow></msup><msup><mover accent="true"><mi mathvariant="bold">H</mi><mo stretchy="true">~</mo></mover><mi>T</mi></msup><msup><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">C</mi><mi>y</mi></msub><mo>+</mo><mi>&#955;</mi><msub><mi mathvariant="bold">C</mi><mi>n</mi></msub></mrow></mfenced><mrow><mo form="prefix">&#8722;</mo><mn>1</mn></mrow></msup></math>

其中 ![images](images/c10-i0032.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msubsup><mover accent="true"><mi mathvariant="bold">I</mi><mo stretchy="true">~</mo></mover><mi>d</mi><mi>T</mi></msubsup><mo>=</mo><mfenced open="\[" close="\]"><mrow><mn>0</mn><mspace width="0.2em"/><mi mathvariant="bold">I</mi></mrow></mfenced></math> 和 ![images](images/c10-i0033.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msup><mover accent="true"><mi mathvariant="bold">H</mi><mo stretchy="true">~</mo></mover><mi>T</mi></msup><mo>=</mo><mfenced open="\[" close="\]"><mrow><mi mathvariant="bold">H</mi><mfenced open="(" close=")"><msub><mi>&#961;</mi><mn>1</mn></msub></mfenced><mspace width="0.2em"/><mi mathvariant="bold">H</mi><mfenced open="(" close=")"><msub><mi>&#961;</mi><mn>2</mn></msub></mfenced></mrow></mfenced></math>。**C**[*n*] 和 **C**[*y*] 分别是噪声和包含第一个源的背景 EEG 的协方差矩阵。

在许多实际情况下，我们没有关于真实源位置的先验知识。在这种情况下，如果我们错误地定位了第一个源，其他源的定位也可能失败。为了规避此问题，通过多次迭代来寻找源，使得在每一轮中，在搜索当前源位置时使其他源失效；随后源进行交换，在先前估计的源 2 失效的同时估计源 1。

为了在真实 MEG 上检验该方法，在听觉范式下记录了事件相关场 (ERF)。每 0.5 秒向受试者双侧呈现 1500 次听觉刺激。刺激为持续 0.1 秒的宽带噪声。选择该数据集是因为刺激序列在左侧和右侧初级听觉皮层产生活动。数据从一名 28 岁男性受试者处采集。使用 275 通道径向梯度计系统进行全头 MEG 记录。采样率为 1000 Hz，记录数据经离线带通滤波 (0.03–40 Hz)。在目视剔除含有眨眼和运动伪迹的试次后，对剩余试次进行平均。两种方法 (BF 和失效 BF) 均使用的估计噪声协方差矩阵 **C** *n*，是由刺激前 0.1 秒片段计算得出的。在该实验中，考虑了两个偶极子：一个在大脑右半球，一个在左半球。

[图 10.13](#c10.xhtml#c10-fig-0013)a 和 b 显示了 BF 方法在轴向和冠状视图下的功率分布及估计位置。估计位置用十字标记表示。使用失效 BF 方法获得的估计功率分布和估计位置显示在 [图 10.13](#c10.xhtml#c10-fig-0013)c–f 中。[图 10.13](#c10.xhtml#c10-fig-0013)c 和 d 显示了在使第二个偶极子失效时第一个偶极子的位置，[图 10.13](#c10.xhtml#c10-fig-0013)e 和 f 显示了在使第一个偶极子失效时第二个偶极子的位置。失效 BF 方法在三次迭代后收敛。从 [图 10.13](#c10.xhtml#c10-fig-0013)a 和 b 可以看出，对于 BF 方法，由于源之间的部分相关性，源向头部中心蔓延。相反，失效 BF 将源定位在左、右半球初级听觉皮层生物学上合理的位置。使用失效 BF 获得的功率也比使用 BF 方法获得的功率更聚焦。此外，与 BF 不同，实施失效 BF 时，未在球模型中心附近观察到虚假激活 [\[74\]](#c10.xhtml#c10-bib-0074)。

![Figure 10.13 Topographies or power profiles of real MEG data obtained using (a) BF method in axial view, (b) BF method in coronal view, (c) deflation BF while deflating the second source in axial view, (d) deflation BF while deflating the second source in coronal view, (e) deflation BF while deflating the first source in axial view, (f) deflation BF while deflating the first source in coronal view [74].](images/c10f013.gif)

[**图 10.13**](#c10.xhtml#R_c10-fig-0013) 使用 (a) BF 方法轴向视图、(b) BF 方法冠状视图、(c) 使第二源失效时的失效 BF 轴向视图、(d) 使第二源失效时的失效 BF 冠状视图、(e) 使第一源失效时的失效 BF 轴向视图、(f) 使第一源失效时的失效 BF 冠状视图获得的真实 MEG 数据地形图或功率分布 [\[74\]](#c10.xhtml#c10-bib-0074)。

