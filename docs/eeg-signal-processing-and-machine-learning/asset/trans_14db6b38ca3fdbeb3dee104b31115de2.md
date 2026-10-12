

## 11.3 癫痫发作 EEG 的混沌行为

(11.9) ![equation](images/c11-disp-0010.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="1.75em"/><msub><mi>P</mi><mtext mathvariant="italic">Background</mtext></msub><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>k</mi><mo>=</mo><mn>0</mn></mrow><mrow><mi>N</mi><mo>&#8722;</mo><mn>1</mn></mrow></munderover><msubsup><mi>S</mi><mi>k</mi><mtext mathvariant="italic">Background</mtext></msubsup><mspace width="0.2em"/><mtext>and</mtext><mspace width="0.5em"/><msub><mi>P</mi><mtext mathvariant="italic">Seizure</mtext></msub><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>k</mi><mo>=</mo><mn>0</mn></mrow><mrow><mi>N</mi><mo>&#8722;</mo><mn>1</mn></mrow></munderover><msubsup><mi>S</mi><mi>k</mi><mtext mathvariant="italic">Seizure</mtext></msubsup></math>

据称，对于某些经过良好调整的模型参数，可以实现低至 20% 的误报率 [[57]](#c11.xhtml#c11-bib-0057)。

文献 [[60]](#c11.xhtml#c11-bib-0060) 建议了一种用于新生儿癫痫发作检测的时频 (TF) 方法，其中在时频域中定义了一个模板：

(11.10) ![equation](images/c11-disp-0011.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>Z</mi><mi mathvariant="italic">ref</mi></msub><mfenced open="(" close=")"><mrow><mi>&#964;</mi><mo>,</mo><mi>v</mi></mrow></mfenced><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>L</mi></munderover><mo mathvariant="italic">exp</mo><mfenced open="(" close=")"><mfrac><mrow><mo form="prefix">&#8722;</mo><msup><mfenced open="(" close=")"><mrow><mi>v</mi><mo>&#8722;</mo><msub><mi>&#945;</mi><mi>i</mi></msub><mi>&#964;</mi></mrow></mfenced><mn>2</mn></msup></mrow><mrow><mn>2</mn><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfrac></mfenced></math>

其中，*L* 是信号片段中可能的癫痫尖波数量，时间尺度 *α*[*i*] s 和方差 *σ* ² 可随模板的位置和宽度分别变化。*Z*[*ref*] (*n*, *f*) 在时频域中具有可变的位置和方差，类似于癫痫发作波形，并被用作模板。该模板在时域和频域上均与时频域 EEG *X*(*n*, *f*) 进行卷积，即：

(11.11) ![equation](images/c11-disp-0012.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>&#951;</mi><mrow><mi>&#945;</mi><mo>,</mo><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></msub><mfenced open="(" close=")"><mrow><mi>n</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>=</mo><mi>X</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>,</mo><mi>f</mi></mrow></mfenced><mo>&#42;</mo><mo>&#42;</mo><msub><mi>Z</mi><mi mathvariant="italic">ref</mi></msub><mfenced open="(" close=")"><mrow><mi>n</mi><mo>,</mo><mi>f</mi></mrow></mfenced></math>

其中，** 表示关于离散时间和频率的二维卷积，而实离散信号 *x* 的 *X*(*n*, *k*) 定义为：

(11.12) ![equation](images/c11-disp-0013.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>X</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>,</mo><mi>k</mi></mrow></mfenced><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>q</mi><mo>=</mo><mfrac><mi>n</mi><mn>2</mn></mfrac></mrow><mrow><mi>N</mi><mo>&#8722;</mo><mfrac><mi>n</mi><mn>2</mn></mfrac></mrow></munderover><mi>x</mi><mfenced open="(" close=")"><mrow><mi>q</mi><mo>+</mo><mfrac><mi>n</mi><mn>2</mn></mfrac></mrow></mfenced><mi>x</mi><mfenced open="(" close=")"><mrow><mi>q</mi><mo>&#8722;</mo><mfrac><mi>n</mi><mn>2</mn></mfrac></mrow></mfenced><msup><mi>e</mi><mrow><mo form="prefix">&#8722;</mo><mi>j</mi><mn>2</mn><mi mathvariant="italic">&#960;kq</mi></mrow></msup><mspace width="0.2em"/></math>

其中 *N* 是以采样点数表示的信号长度。假设方差固定，可以估计 *α* [*i*] s 以最大化一个检验准则，从而最小化 *Z*[*ref*] 与期望波形之间的差异。该准则与一个阈值电平进行比较，以判断是否存在癫痫发作。该方法已应用于真实的新生儿 EEG，据报道在某些情况下误检率 (FDR) 低至 15% [[60]](#c11.xhtml#c11-bib-0060)。

遗憾的是，新生儿 EEG 信号在癫痫发作开始时并不表现出任何独特的时频模式。此外，由于新生儿大脑活动不成熟及其大脑代谢的快速变化，信号中包含许多癫痫型尖波。因此，尽管上述方法对某些合成数据效果良好，但由于新生儿癫痫发作的本质如前所述，它们往往无法有效检测所有类型的新生儿癫痫发作。

在 Karayiannis 等人的一项工作中，开发了一种级联基于规则的神经网络算法，用于检测新生儿 EEG 中的癫痫发作片段 [[61]](#c11.xhtml#c11-bib-0061)。该方法假设新生儿癫痫发作表现为微妙但某种程度上具有刻板重复的波形，这些波形在幅度和频率上演变，最终衰减。分别考虑了伪正弦波、复杂形态和节律性尖波串三种不同形态的癫痫发作模式。这些模式如 [图 11.4](#c11.xhtml#c11-fig-0004) 所示 [[61]](#c11.xhtml#c11-bib-0061)。

新生儿癫痫发作的自动检测随后分三个阶段进行。每个 EEG 导联单独处理，不利用空间和导联间信息。在第一阶段，利用频谱幅度分离节律性活动爆发。在第二阶段，减轻伪迹，如拍打、吸吮、呼吸功能和心电图 (ECG) 产生的伪迹；在最后阶段，执行聚类操作以区分癫痫性发作、非癫痫性发作以及受不同伪迹影响的正常 EEG。作为该阶段的结果，孤立且不一致的候选癫痫发作片段被消除，最终识别出癫痫发作片段。

在另一种机器学习方法中，比较了常规前馈神经网络 (FFNN) [[62]](#c11.xhtml#c11-bib-0062) 和量子神经网络 (QNN) [[63]](#c11.xhtml#c11-bib-0063) 在上述所有阶段对某些频域特征进行分类的性能。这些特征与 Gotman 等人 [[56]](#c11.xhtml#c11-bib-0056) 使用的特征几乎相同，记为：第一优势频率、第二优势频率、优势频率带宽、第一优势频率贡献的功率百分比、第二优势频率贡献的功率百分比、峰值比和稳定性比（一个测量 EEG 片段幅度稳定性的时域参数）。结果还表明，使用 FFNN 或 QNN 没有显著差异，结果将大致相同 [[61]](#c11.xhtml#c11-bib-0061)。总体算法非常易于实现，其灵敏度和特异性均已被证明高于 80%。

文献 [[64]](#c11.xhtml#c11-bib-0064) 中，在提取小波域特征、排序并使用不同分类器进行分类之前，对新生儿 EEG 进行了预处理。

Temko 等人 [[65]](#c11.xhtml#c11-bib-0065) 仅使用了九个 EEG 导联，即 F[3]、F[4]、C[3]、C[4]、Cz、T[3]、T[4]、O[1] 和 O[2]，用于他们的新生儿癫痫发作检测系统。他们使用了大量统计和动力学特征，并利用支持向量机 (SVM) 和高斯混合模型 (GMM) 对其进行分类。

