
LDA 已被广泛用于 EEG 分类。在文献 [\[34\]](#c07.xhtml#c7-bib-0034) 的一项研究中，LDA 被用于对健康老年对照组、阿尔茨海默病和血管性痴呆的 EEG 频谱参数进行分类。在这项工作中，提取的频谱特征包括绝对 EEG delta 功率、从低频到高频的衰减、振幅、alpha 功率的中心和离散度以及整个 EEG 频谱的基线功率。正则化方法使用收缩强度参数，以整个样本协方差的加权平均值来替代组内样本协方差。该参数强调协方差矩阵的较大特征值，同时弱化较小的特征值，从而创建一个修正了基于样本估计特征值偏差的合并协方差矩阵。最优收缩参数由交叉验证确定。

LDA 是 BCI 中最流行的分类算法之一。文献 [\[35\]](#c07.xhtml#c7-bib-0035) 中给出了一个例子，其中设计了一个两类 BCI，两类均服从高斯分布，但类方差不同。

在另一个 BCI 应用 [\[36\]](#c07.xhtml#c7-bib-0036) 中，EEG mu/beta 节律被用作 LDA 分类器的输入，以判断哪种节律能提供更好的分类性能。在此过程中，通用空间模式 (CSP) 被用以一种最大化一类投影能量与另一类投影能量之比的方式来投影数据。

### 7.3.4 支持向量机

在所有监督分类器中，SVM 可能是包括 BCI 在内的许多应用中最流行的一个，在许多线性（可分）和非线性（不可分）情况下均优于其他分类器。SVM 概念由 Vapnik 于 1979 年提出 \[[33](#c07.xhtml#c7-bib-0033),[37](#c07.xhtml#c7-bib-0037)–[41](#c07.xhtml#c7-bib-0041)\]。与 LDA 假设类分布为高斯分布不同，SVM 对数据分布不做任何假设。为了理解 SVM 概念，考虑一个二分类问题，针对简单的二维特征空间中的线性可分训练样本 *S* = {(**x** [1], *y* [1]), (**x** [2], *y* [2]), …, (**x**[*m*] , *y*[*m*] )}（**图 7.4**），其中 **x** ∈ *R*^(*d*) 为输入向量（此处图中特征空间维度 *d* = 2），*y*[*i*]  ∈ {1, − 1}, *i* = 1, …, *m* 为类标签。判别函数定义为：

(7.15)![equation](images/c7-disp-0015.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>f</mi><mfenced open="(" close=")"><mi mathvariant="bold">x</mi></mfenced><mo>=</mo><mo mathvariant="italic">sgn</mo><mfenced open="(" close=")"><mrow><mfenced open="&#9001;" close="&#9002;"><mrow><mi mathvariant="bold">w</mi><mo>,</mo><mi mathvariant="bold">x</mi></mrow></mfenced><mo>+</mo><mi>b</mi></mrow></mfenced><mo>=</mo><mfenced open="{" close=""><mtable><mtr><mtd><maligngroup/><mo>+</mo><mn>1</mn><mspace width="0.2em"/><mi mathvariant="bold">x</mi><mo>&#8712;</mo><mtext mathvariant="italic">first class</mtext><mspace width="0.2em"/></mtd></mtr><mtr><mtd><maligngroup/><mo>&#8722;</mo><mn>1</mn><mspace width="0.2em"/><mi mathvariant="bold">x</mi><mo>&#8712;</mo><mtext mathvariant="italic">second class</mtext></mtd></mtr></mtable></mfenced></math>

在此公式中，**w** 决定判别平面（或超平面）的方向。显然，存在无限多个可能的平面能够正确分类训练数据。最优分类器寻找的超平面使得最佳泛化超平面到每组点的距离相等或最远。当不存在分类误差且最近向量到超平面的距离最大时，实现最优分离。

在可分情况下，寻找分离超平面的一种方法是构建每个数据集的所谓*凸包*。包围的区域即为数据集的凸包。通过检查凸包，可以确定位于每个类凸包上的最近两点（注意这些点不一定与实际数据点重合）。通过构建一个垂直于且等效于这两点的平面，应能得到一个具有鲁棒性的最优超平面分类器。

对于最优分离超平面的设计，通常利用少数几个被称为*支持向量* (SVs) 的点（例如 **图 7.4** 中圈出的三个数据特征点）。

SVM 公式从最简单的情况开始：线性机器在可分数据上训练（针对一般情况分析；非线性机器在不可分数据上训练会导致非常相似的二次规划 (QP) 问题）。然后，训练数据 {**x**[*i*] , *y*[*i*] }*, i =* 1, …*,m,y*[*i*]  *∈* {1, *−* 1}, **x**[*i*]  *∈ R*^(*d*) 被标记。考虑有一个将正例与负例分开的超平面。位于超平面上的点 **x** 满足 〈**w**, **x**〉  ***+***  *b*  ***\=* 0**，其中 **w** 垂直于超平面，*b*/‖**w**‖[**2**] 是超平面到原点的垂直距离，‖**w**‖[**2**] 是 **w** 的欧几里得范数。定义**图 7.4** 中所示的分离超平面的“间隔”，对于线性可分情况，算法仅寻找具有最大间隔的分离超平面。这里的方法是通过在线性不等式约束下最小化二次函数，将问题转化为凸优化问题。为了找到离两类数据最远的平面，最大化每一类支持规范超平面之间的间隔。支持平面被推开直到它们遇到最近的数据点，这些点随即被视为 SVs（**图 7.4** 中圈出的点）。因此，寻找 **w** 的 SVM 问题表述为：

![Figure 7.4 The SVM separating hyperplane and support vectors for a separable data case.](images/c07f004.gif)

[**图 7.4**](#c07.xhtml#R_c7-fig-0004) 可分数据情况下的 SVM 分离超平面和支持向量。

(7.16a)![equation](images/c7-disp-0017.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mfenced open="&#9001;" close="&#9002;"><mrow><msub><mi mathvariant="bold">x</mi><mi>i</mi></msub><mo>,</mo><mi mathvariant="bold">w</mi></mrow></mfenced><mo>+</mo><mi>b</mi><mo>&#8805;</mo><mo form="prefix">+</mo><mn>1</mn><mspace width="0.2em"/><mtext>for</mtext><mspace width="0.2em"/><msub><mi>y</mi><mi>i</mi></msub><mo>=</mo><mo form="prefix">+</mo><mn>1</mn></math> (7.16b)![equation](images/c7-disp-0018.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mfenced open="&#9001;" close="&#9002;"><mrow><msub><mi mathvariant="bold">x</mi><mi>i</mi></msub><mo>,</mo><mi mathvariant="bold">w</mi></mrow></mfenced><mo>+</mo><mi>b</mi><mo>&#8805;</mo><mo form="prefix">&#8722;</mo><mn>1</mn><mspace width="0.2em"/><mtext>for</mtext><mspace width="0.2em"/><msub><mi>y</mi><mi>i</mi></msub><mo>=</mo><mo form="prefix">&#8722;</mo><mn>1</mn></math>

这可以合并为一组不等式：*y*[*i*] (〈**x**[*i*] , **w**〉 + *b*) − 1 ≥ 0 ∀ *i*。这两个支持平面（H[1] 和 H[2]）之间的间隔可表示为 *γ* = 2/‖**w**‖[2]。因此，为了最大化这个间隔，我们需要：
