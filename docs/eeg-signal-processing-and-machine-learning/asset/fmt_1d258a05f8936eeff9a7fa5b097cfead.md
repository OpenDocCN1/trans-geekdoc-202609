
## 7.4 Common Spatial Patterns

CSP 是一种流行的多通道信号（特别是 EEG）分类的特征提取和优化方法。传统上，CSP 旨在估计基于方差区分两个类别的空间滤波器。CSP 是 BCI 系统中最成功的特征提取算法之一。一个直接的 BCI 应用涉及 EEG 的二分类，例如真实或想象的左右手运动的分类。CSP（**w**）最小化空间协方差矩阵的瑞利商，以实现两类数据 **X**[1] 和 **X**[2] 之间的方差不平衡。在应用 CSP 之前，信号经过带通滤波和中心化。CSP 的目标是找到一个空间滤波器 **w** ∈ ℜ^c，使得一类投影样本的方差最大化，而另一类的最小化。用于 CSP 估计的最大化准则如下 [[157]](#c07.xhtml#c7-bib-0157), [[158]](#c07.xhtml#c7-bib-0158)：

(7.57)![equation](images/c7-disp-0063.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msup><mi mathvariant="bold">w</mi><mfenced open="(" close=")"><mi mathvariant="italic">CSP</mi></mfenced></msup><mo>=</mo><mo mathvariant="italic">arg</mo><munder><mo>max</mo><mi mathvariant="bold">w</mi></munder><mfrac><mrow><mi mathvariant="italic">tr</mi><mfenced open="(" close=")"><mrow><msup><mi mathvariant="bold">w</mi><mi>T</mi></msup><msub><mi mathvariant="bold">C</mi><mn>1</mn></msub><mi mathvariant="bold">w</mi></mrow></mfenced></mrow><mrow><mi mathvariant="italic">tr</mi><mfenced open="(" close=")"><mrow><msup><mi mathvariant="bold">w</mi><mi>T</mi></msup><msub><mi mathvariant="bold">C</mi><mn>2</mn></msub><mi mathvariant="bold">w</mi></mrow></mfenced></mrow></mfrac></math>

`p(O|λ)` 然后利用这些参数计算。每次迭代后，该概率增加，直到参数 `A`、`B` 和 `π` 达到其最优值，此时算法终止，概率不再有任何显著变化。

已有使用 HMM 进行 EEG 识别或分类的报道。可以设想从 EEG 中检测 ERP 波形。另一个例子是从颅内 EEG 信号中检测癫痫样放电。这些波形通常具有特定的形态，可遵循用于 QRS 检测的类似 HMM 进行检测。

在一个 BCI 应用中，针对四种不同的运动任务，估计单次试验五电极 EEG 的 AR 系数。然后应用 PCA 来减少参数数量（因为 HMM 对高维数据的计算需求非常大），接着使用 HMM 将运动分类为四个任务之一 [[151]](#c07.xhtml#c7-bib-0151)。在此应用中，特征的均值和方差用于定义状态。AR 阶数和 HMM 状态数经验设定。在类似的 HMM 方法中，稀疏 AR 系数连同从中导出的度量（如偏导相干性 `PDC` 和定向传递函数 `DTF`）被解释为通道间的信息流 [[152]](#c07.xhtml#c7-bib-0152) 并加以利用。AR 模型阶数选择为对应于一系列模型阶数中最低贝叶斯信息准则 (`BIC`) 或施瓦茨信息准则值 [[153]](#c07.xhtml#c7-bib-0153) 的阶数。状态数也被选择为聚类数。

Obermaier 等人 [[154]](#c07.xhtml#c7-bib-0154) 使用 HMM 对 BCI 应用中左右手想象运动期间的单次试验 EEG 进行在线分类。在他们的设计中，使用了一个三状态 HMM 模型，每个状态由三个高斯分量的 `GMM` 参数表征。在他们的实验中，他们获得的 HMM 错误率低于线性判别分类器。

在另一个应用中，EEG 数据被用于利用 HMM 估计精神疲劳 [[155]](#c07.xhtml#c7-bib-0155)。在这项工作中，近似熵 (`ApEn`) 和柯尔莫哥洛夫复杂度 (`Kc`) 被用于表征不同精神疲劳状态下 EEG 数据的复杂性和不规则性。然后将核主成分分析 (`KPCA`) 和 HMM 结合以区分这两种状态。`KPCA` 算法被用于从 EEG 复杂度参数中提取非线性特征并提高 HMM 的泛化性能。两个 HMM（一个代表正常状态，另一个代表疲劳状态）分别利用相应精神疲劳状态下记录的 EEG 数据段进行训练。

也有使用 HMM 对睡眠 EEG 进行评分的报道。例如，全脑网络的时空复杂性及睡眠期间的状态转换已被详细表征 [[156]](#c07.xhtml#c7-bib-0156)。为了获得大脑网络状态在人类睡眠周期中如何演变的最无偏估计，使用 HMM 分析了连续同步的 EEG 和 fMRI 数据。据称，所提出的 HMM 促进了发现清醒-非快速眼动 (`REM`) 睡眠周期期间不同大脑网络间的动态协同编排。
