
且 $q(n)$ 是双谱的二维逆傅里叶变换，以及 $\sigma_{\phi_n} = \sqrt{\sum_i \phi_n^2(i)}$。这些测度联合用于估计纺锤波的周期性。对于纯周期性活动，我们期望这些估计给出相似的结果。在这种情况下，[式 (12.8)](#c12.xhtml#c12-disp-0009) 表现出峰值（类似于 AMDF），其中第一个峰值表示纺锤波频率。

基于这项研究，总结表明：(*i*) 纺锤波活动可能不会均匀地主导大脑的所有区域；(*ii*) 在纺锤波活动期间，额区记录仍表现出频率成分和耦合的丰富混合。反之，在后区可能观察到较差的耦合，同时显示出纺锤波的优势活动；(*iii*) 结论是纺锤波活动可使用至少二阶非线性进行建模。

### 12.6.4 基于张量分解的睡眠分期

文献 [\[41\]](#c12.xhtml#c12-bib-0041) 引入了一种用于单通道睡眠 EEG 分解的新型监督方法。通过应用张量分解代替传统的奇异值分解 (SVD)，传统 SSA 算法的性能得到了显著提升。在该方法中，数据固有的频率多样性也得到了有效利用，以突出感兴趣的子空间。

[第 5 章](#c05.xhtml) 中解释的传统 SSA 未利用数据固有的非平稳性，因此可能在实际数据分解中失效。基于张量的 SSA (TSSA) 已被提出作为解决该问题的方案 [\[41\]](#c12.xhtml#c12-bib-0041)。与 SSA 类似，TSSA 的第一阶段包含一个嵌入操作，随后采用张量分解方法代替 SVD。在嵌入阶段，长度为 $n$ 的一维时间序列 **x** 被映射为张量 $\underline{\mathbf{X}}$。为此，首先使用大小为 $l$ 的非重叠窗口对 **x** 进行分段，从 **x** 获得一个 $\lfloor n/l \rfloor \times l$ 的矩阵 **X**：

(12.10)![equation](images/c12-disp-0011.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="bold">X</mi><mo>=</mo><mfenced open="\[" close="\]"><mtable><mtr><mtd><maligngroup/><msub><mi>x</mi><mn>1</mn></msub><mspace width="2.5em"/><msub><mi>x</mi><mn>2</mn></msub><mspace width="1em"/><mo>&#8943;</mo><mspace width="1.25em"/><msub><mi>x</mi><mi>l</mi></msub></mtd></mtr><mtr><mtd><maligngroup/><msub><mi>x</mi><mrow><mi>l</mi><mo>+</mo><mn>1</mn></mrow></msub><mspace width="1.75em"/><msub><mi>x</mi><mrow><mi>l</mi><mo>+</mo><mn>2</mn></mrow></msub><mspace width="0.5em"/><mo>&#8943;</mo><mspace width="1em"/><msub><mi>x</mi><mrow><mn>2</mn><mi>l</mi></mrow></msub></mtd></mtr><mtr><mtd><maligngroup/><mo>&#8942;</mo><mspace width="3.5em"/><mo>&#8945;</mo><mspace width="3.5em"/><mo>&#8942;</mo></mtd></mtr><mtr><mtd><maligngroup/><msub><mi>x</mi><mrow><mfenced open="(" close=")"><mrow><mi>I</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>l</mi></mrow></msub><mspace width="0.75em"/><msub><mi>x</mi><mrow><mfenced open="(" close=")"><mrow><mi>I</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>l</mi><mo>+</mo><mn>1</mn></mrow></msub><mspace width=".5em"/><mo>&#8943;</mo><mspace width=".5em"/><msub><mi>x</mi><mi mathvariant="italic">Il</mi></msub></mtd></mtr></mtable></mfenced></math>

其中 $I = \lfloor n/l \rfloor$。然后，如 [图 12.9](#c12.xhtml#c12-fig-0009) 所示，通过将张量的每个切片视为 **X** 的窗口化版本，将该矩阵转换为张量 $\underline{\mathbf{X}}$。矩阵到张量的转换可用以下方程解释：

(12.11)![equation](images/c12-disp-0012.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><munder accentunder="false"><mi mathvariant="bold">X</mi><mo>\_</mo></munder><mrow><mi>i</mi><mo>&#8759;</mo></mrow></msub><mo>=</mo><mi mathvariant="bold">X</mi><mfenced open="(" close=")"><mrow><mi>i</mi><mo>,</mo><mfenced open="(" close=")"><mrow><mi>j</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>o</mi><mo>+</mo><mn>1</mn><mo>:</mo><mfenced open="(" close=")"><mrow><mi>j</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>o</mi><mo>+</mo><msub><mi>l</mi><mn>1</mn></msub></mrow></mfenced></math> ![Figure 12.9 I × K matrix X is converted to tensor images where J is the number of segments obtained by window size l 1 and overlapping interval l 1 − o.](images/c12f009.gif)

[**图 12.9**](#c12.xhtml#R_c12-fig-0009) $I \times K$ 矩阵 **X** 被转换为张量 $\underline{\mathbf{X}}$，其中 $J$ 是由窗口大小 $l_1$ 和重叠间隔 $l_1 - o$ 获得的分段数。

![Figure 12.10 Block diagram of the single‐channel source separation system using an adaptive procedure for selecting the desired subspace. This is carried out by tuning a set of weights governed by the EMD process.](images/c12f010.gif)

[**图 12.10**](#c12.xhtml#R_c12-fig-0010) 单通道源分离系统的框图，采用自适应过程选择所需子空间。这是通过调整由 EMD 过程控制的一组权重来实现的。

![images](images/c12-i0006.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mtext>where</mtext><mspace width="0.2em"/><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>J</mi><mo>;</mo><mspace width="1em"/><mi>J</mi><mo>=</mo><mfenced open="&#8970;" close="&#8971;"><mrow><mfrac><mrow><mi>l</mi><mo>&#8722;</mo><msub><mi>l</mi><mn>1</mn></msub></mrow><mi>o</mi></mfrac><mo>+</mo><mn>1</mn></row></mfenced><mo>,</mo><mspace width="1.5em"/><mtext>and</mtext><mspace width="0.75em"/><mi>i</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>I</mi></math> 其中 $l_1 - o$ 是连续窗口的重叠间隔，$l_1$ 是窗口大小。然后，使用交替最小二乘法估算构建张量的因子，以最佳拟合 PARAFAC 模型。

与 SSA 相同，在 TSSA 中子群定义为 $I = I_1 \cup I_2 \cup \dots I_m$ 且 $\underline{\mathbf{X}} = \sum_{i=1}^m \underline{\mathbf{X}}_{I_i}$。在该工作中，经验模态分解 (EMD) 已被用于选择包含感兴趣频率范围内固有模态函数 (IMF) 的子群 [\[41\]](#c12.xhtml#c12-bib-0041)。[图 12.10](#c12.xhtml#c12-fig-0010) 表示整体系统的框图。最后，通过汉克尔化可以获得原始信号的重构，该过程通过将信号分段转换为汉克尔矩阵来执行。然后，通过一一对应重构数据。
