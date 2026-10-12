
作为情境特征，考虑了以下因素：(i) 驾驶员相关，如性格、睡眠质量、昼夜节律和身体状况；(ii) 车辆相关，即噪声、座椅舒适度和温度；(iii) 道路相关，包括道路单调性、车辆密度和车道数。

然后，利用不同时间段上的核分布估计来估算疲劳可能性。特定环境因素提供的情境信息被用作疲劳的先验。后验概率在最后阶段通过基于 HMM 的疲劳识别方法来捕获。HMM 状态由情境信息条件化。

### 13.2.2 核主成分分析与隐马尔可夫模型

从 EEG 信号中估算近似熵（`ApEn`）和柯尔莫哥洛夫复杂度（`Kc`），并用于表征不同精神疲劳状态下 EEG 数据的复杂性和不规则性 [\[18\]](#c13.xhtml#c13-bib-0018)。采用核主成分分析（`KPCA`）算法从复杂度参数中提取非线性特征，并提高 `HMM` 的泛化性能。

在 `KPCA` 中，协方差矩阵是基于信号的非线性函数（如径向基函数）计算的，而非信号本身，即 ![images](images/c13-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msub><mi>C</mi><mi>x</mi></msub><mo>=</mo><mfrac><mn>1</mn><mi>L</mi></mfrac><msubsup><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>L</mi></msubsup><mi>&#966;</mi><mfenced open="(" close=")"><msub><mi>x</mi><mi>i</mi></msub></mfenced><mi>&#966;</mi><msup><mfenced open="(" close=")"><msub><mi>x</mi><mi>i</mi></msub></mfenced><mi>T</mi></msup></math>。其余的特征选择和数据降维阶段遵循传统的主成分分析（`PCA`）。

训练两个 `HMM`，一个代表正常/警觉状态（`HMM[N]`），另一个代表疲劳状态（`HMM[F]`），训练数据为相应精神疲劳状态下记录的 EEG 数据段。模型参数由给定的训练数据估算，随后用于对相同的训练数据进行分类。最后，利用正确分类的试次来估算 `HMM[N]` 和 `HMM[F]`。未知 EEG 数据段的分类基于通过 Viterbi 算法 [\[21\]](#c13.xhtml#c13-bib-0021) 计算的最大单一最佳路径概率 ![images](images/c13-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mover accent="true"><mi mathvariant="normal">V</mi><mo stretchy="true">&#175;</mo></mover><mo>&#8739;</mo><mi>HMM</mi></mrow></mfenced></math> 的选择。对所有 EEG 片段计算 ![images](images/c13-i0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mover accent="true"><mi mathvariant="normal">V</mi><mo stretchy="true">&#175;</mo></mover><mo>&#8739;</mo><msub><mi>HMM</mi><mi mathvariant="normal">N</mi></msub></mrow></mfenced></math> 和 ![images](images/c13-i0004.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mover accent="true"><mi mathvariant="normal">V</mi><mo stretchy="true">&#175;</mo></mover><mo>&#8739;</mo><msub><mi>HMM</mi><mi mathvariant="normal">F</mi></msub></mrow></mfenced></math> 将导致这些概率的传播，从而实现逐样本分类。

研究结论表明，随着精神疲劳程度的增加，这两个复杂度参数均显著下降，提示这些参数可以作为精神疲劳程度的良好指标。采用该方法，实现了 84% 的分类准确率。

此外，联合 `KPCA`–`HMM` 方法能显著降低特征向量的维度。

### 13.2.3 基于回归的疲劳估计

EEG 频谱特征此前已被用于对疲劳状态进行评分。例如，在文献 [\[22\]](#c13.xhtml#c13-bib-0022) 中，作者结合 EEG 对数子带功率谱、相关性分析、`PCA` 和线性回归模型，在基于虚拟现实的驾驶模拟器中间接估计驾驶员的困倦程度。支持向量回归等回归技术适用于疲劳或困倦的在线分类、监测和估计，可应用于驾驶员或飞行员疲劳，以预防相关危害。在文献 [\[5\]](#c13.xhtml#c13-bib-0005) 中，利用 Welch 方法（汉明窗和 50% 重叠）从 EEG 功率谱密度中提取频谱特征。计算五个 EEG 频带（即 delta、theta、alpha、beta 和 gamma）中的功率，并从每个通道提取比率 `P[theta + alpha] / P[beta]` 和 `P[theta] / P[beta]`，24 个通道共产生 168 个特征。这些特征被用作其回归模型的输入，并对结果进行了比较。

他们还提出了动态时间规整作为回归输出获得的估计疲劳水平与作为反应时间考虑的实际疲劳水平之间的相似性度量。最低相似性被视为规整距离值，最高相似性被视为信号间的相似性。

他们得出结论，使用 RBF 核和滑动五秒窗口可获得最佳性能。

### 13.2.4 正则化回归

文献 [\[23\]](#c13.xhtml#c13-bib-0023) 的作者通过将模糊集与域适应相结合，解决了基于 EEG 信号的在线驾驶员困倦估计问题。他们尝试在应用模糊集进行分类之前，通过在线校准来缓解被试间的变异性。

为构建该问题，在特征空间中，迁移学习中的域 `D` 由一个 `d` 维特征空间 `X` 和一个边缘概率分布 `P(x)` 组成，即 `D = {X, P(x)}`，其中 `x` ∈ `X`。

如果 `χ^(z)` ≠ `χ^(t)` 或 `P^(z)(x)` ≠ `P^(t)(x)`，则两个域 `D^(z)` 和 `D^(t)` 是不同的。在迁移学习中，任务 `T` 由一个输出空间 `Y` 和一个条件概率分布 `Q(y|x)` 组成。如果 `Y^(z)` ≠ `Y^(t)`，或 `Q^(z)(y|x)` ≠ `Q^(t)(y|x)`，则两个任务 `T^(z)` 和 `T^(t)` 是不同的。

给定第 `z` 个源域 `D^(z)` 及其 `n[z]` 个样本 ![images](images/c13-i0005.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mfenced open="(" close=")"><mrow><msubsup><mi mathvariant="bold">x</mi><mi>i</mi><mi>z</mi></msubsup><mo>,</mo><msubsup><mi>y</mi><mi>i</mi><mi>z</mi></msubsup></mrow></mfenced><mo>,</mo><mi>i</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>n</mi><mi>z</mi></msub></math>，以及包含 `m` 个校准样本的目标域 `D^(t)` ![images](images/c13-i0006.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mfenced open="(" close=")"><mrow><msubsup><mi mathvariant="bold">x</mi><mi>j</mi><mi>t</mi></msubsup><mo>,</mo><msubsup><mi>y</mi><mi>j</mi><mi>t</mi></msubsup></mrow></mfenced><mo>,</mo><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>m</mi></math>，域适应旨在学习一个目标预测函数 `f(x)` : `x` → `y`，使其在 `D^(t)` 上具有较低的期望误差，前提假设为 `χ^(z)` = `χ^(t)`、`Y^(z)` = `Y^(t)`、`P^(z)(x)` ≠ `P^(t)(x)` 和 `Q^(z)(y|x)` ≠ `Q^(t)(y|x)`。
