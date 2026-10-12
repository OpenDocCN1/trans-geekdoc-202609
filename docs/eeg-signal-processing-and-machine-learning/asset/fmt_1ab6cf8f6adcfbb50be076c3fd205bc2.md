
(10.37) ![equation](images/c10-disp-0037.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>ED</mi><mo>=</mo><mfrac><mn>1</mn><msub><mi>N</mi><mi>d</mi></msub></mfrac><munderover><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><msub><mi>N</mi><mi>d</mi></msub></munderover><munder><mo>min</mo><mi>j</mi></munder><mfenced open="{" close="}"><mfenced open="&#8214;" close="&#8214;"><mrow><msub><mover accent="true"><mi mathvariant="bold">s</mi><mo stretchy="true">~</mo></mover><mi>i</mi></msub><mo>&#8722;</mo><msub><mi mathvariant="bold">s</mi><mi>j</mi></msub></mrow></mfenced></mfenced><mo>+</mo><mfrac><mn>1</mn><msub><mi>N</mi><mi mathvariant="italic">ud</mi></msub></mfrac><munderover><mo>&#8721;</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><msub><mi>N</mi><mi mathvariant="italic">ud</mi></msub></munderover><munder><mo>min</mo><mi>i</mi></munder><mfenced open="{" close="}"><mfenced open="&#8214;" close="&#8214;"><mrow><msub><mover accent="true"><mi mathvariant="bold">s</mi><mo stretchy="true">~</mo></mover><mi>i</mi></msub><mo>&#8722;</mo><msub><mi mathvariant="bold">s</mi><mi>j</mi></msub></mrow></mfenced></mfenced></math>

其中 *i* 和 *j* 分别是估计源和实际源位置的索引，*N*[*d*] 和 *N*[*ud*] 分别是估计源和未检测源的总数。

USP 和 FSP 分别定义为 USP = *N*[*un*] */Nreal* × 100% 和 FSP = *N*[*false*] */N*[*estimated*] × 100%，其中 *N*[*un*] 、*N*[*real*] 、*N*[*false*] 和 *N*[*estimated*] 分别是未检测源、真实源、误检源和估计源的数量。

在实践中，可以使用三种类型的头部体积导体模型：均匀球体头部体积导体模型、BEM 或 FEM 模型。由于 FEM 计算量非常大，目前使用的是受试者特定的 BEM 模型，尽管它是针对过度简化的球体头部模型 [[59]](#c10.xhtml#c10-bib-0059)。

在 ED、USP 和 FSP 方面，LRT1（即 p = 1）已被验证能给出最佳的定位结果。

利用脑信号的时间特性来提高定位性能也已被尝试。可以增加一个额外的时间约束，假设对于每个位置，源幅度随时间的变化是最小的。要添加的约束是 ![images](images/c10-i0026.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mo>min</mo><msubsup><mfenced open="&#8214;" close="&#8214;"><mrow><mi mathvariant="bold">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8722;</mo><mi mathvariant="bold">s</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced></mrow></mfenced><mi>F</mi><mn>2</mn></msubsup></math>，其中 *n* 表示时间索引。

### 10.4.8 联合 ICA–LORETA 方法

在另一项研究 [[60]](#c10.xhtml#c10-bib-0060) 中，基于 Infomax ICA 的盲源分离（BSS）已作为预处理方案，在应用 LORETA 定位失配负波（MMN）的潜在源之前实施。MMN 是一种非自主的听觉 ERP，当规律模式被打破时，在 100–200 ms 处达到峰值。这种 ERP 似乎对应于一种原始智能。MMN 信号主要产生在上颞皮层 [[61](#c10.xhtml#c10-bib-0061)–[65](#c10.xhtml#c10-bib-0065)]。

LORETA 分析是利用与选定 ICA 成分相关的头皮图来寻找这些图的发生源。只有大于标准化数据标准差 2.5 倍的值（在 LORETA 空间分辨率中）被接受为激活。

逆问题也已在贝叶斯框架内得到解决 [[66]](#c10.xhtml#c10-bib-0066)。在这类方法中，通常需要一些关于先验概率的信息。我们再次考虑 EEG 生成模型：

(10.38) ![equation](images/c10-disp-0038.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="bold">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>=</mo><mi mathvariant="bold">Hs</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>+</mo><mi mathvariant="normal">v</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></math>

其中 **x**(*n*) 是一个 *n*[*e*]  × 1 向量，包含时间 *n* 处的 EEG 采样值，**H** 是一个 *n*[*e*]  × *m* 矩阵，表示头部介质模型，**s**(*n*) 包含时间 *n* 处源的 *m* × 1 向量采样值，**v**(*n*) 是时间 *n* 处噪声采样的 *n*[*e*]  × 1 向量。关于源的先验信息对其位置和时间特性施加了一些约束。估计可以使用最大后验（MAP）准则来执行，其中估计器试图找到 **s**(*n*) 以最大化给定测量值 **x**(*n*) 时 **s**(*n*) 的概率分布。估计器表示为：

(10.39) ![equation](images/c10-disp-0039.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mover accent="true"><mi mathvariant="bold-italic">s</mi><mo stretchy="true">&#38;c.circ;</mo></mover><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>=</mo><mo mathvariant="italic">max</mo><mfenced open="\[" close="\]"><mrow><mi>p</mi><mo stretchy="true">(</mo><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo stretchy="true">)</mo></mrow></mfenced></math>

根据贝叶斯规则，后验概率为：

(10.40) ![equation](images/c10-disp-0040.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mo>=</mo><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mo>/</mo><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced></math>

其中 *p*( ***x*** (*n*) ∣  ***s*** (*n*)) 是似然函数，*p*( ***x*** (*n*)) 是测量值的边缘分布，*p*( ***s*** (*n*)) 是先验概率。后验概率可以用能量函数来表示，即：

(10.41) ![equation](images/c10-disp-0041.png) <math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>&#8739;</mo><mi>z</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced><mo>=</mo><mfrac><mn>1</mn><mrow><mi>z</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfrac><mo mathvariant="italic">exp</mo><mfenced open="\[" close="\]"><mrow><mo form="prefix">&#8722;</mo><mi>U</mi><mfenced open="(" close=")"><mrow><mi mathvariant="bold-italic">s</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></mrow></mfenced></mrow></mfenced></math>
