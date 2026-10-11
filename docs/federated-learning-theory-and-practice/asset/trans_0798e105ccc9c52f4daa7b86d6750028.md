
如果通过计算基进行测量，则有概率得到状态 |0〉，其概率为 *P*(state = |0⟩) = ∥*e*^(−*i**ϕ*/2)cos(*θ*/2)∥²，以及状态 |1〉，其概率为 *P*(state = |1⟩) = ∥*e*^(*i**ϕ*/2)sin(*θ*/2)∥²。然而，每次测量只会给出 |0〉 或 |1〉 之一。为了获得该概率分布的知识，必须多次准备并测量量子电路。这种重复被称为 *shots*（测量次数）。给定足够的 shots，|0〉 和 |1〉 的数量可以非常接近此处所示的理论预测 *P*(state = |0⟩) 和 *P*(state = |1⟩)。因此，该量子比特的 *expectation value*（期望值）可推导为 *P*(state = |1⟩) = ∥*e*^(*i**ϕ*/2)sin(*θ*/2)∥²。期望值是量子模型的实际输出，可用作学习任务中的 *prediction*（预测）。例如，该输出可以是时间序列的预测或函数近似。然而，量子模型需要进行 *trained*（训练），类似于经典机器学习中通常所做的那样。必须将量子模型的输出与某些目标值进行比较，并对电路参数进行更新。如 [Fig. 17.5](#Chp017_311-328_B9780443190377000272.xhtml#f0030) 所示，迭代过程类似于经典机器学习。唯一的区别在于，这次更新的是量子电路参数，而不是神经网络权重。[Fig. 17.6](#Chp017_311-328_B9780443190377000272.xhtml#f0035) 展示了 VQC 的一般形式。通常，VQC 包括一个 *encoding circuit*（编码电路）以将数据加载到系统中；*variational circuit*（变分电路），即实际被训练的部分；以及最终的 *measurement*（测量）以从量子系统中检索信息。

![Figure 17.5 Concept of Updating a Parameterized Quantum Circuit.](OEBPS/images/B9780443190377000272/gr005_u5.jpg)

[Figure 17.5](#Chp017_311-328_B9780443190377000272.xhtml#cf0175) Concept of Updating a Parameterized Quantum Circuit.

![Figure 17.6 Generic Architecture for Variational Quantum Circuits. Here U(x) is the quantum circuit block for encoding the (classical) input data x into a quantum state, and V(θ) is the variational circuit block with tunable or learnable parameters θ that will be optimized via gradient-based or gradient-free methods. A quantum measurement over some or all of the qubits follows. The measured results are classical values and can be further processed via quantum or classical components.](OEBPS/images/B9780443190377000272/gr006_u3.jpg)

[Figure 17.6](#Chp017_311-328_B9780443190377000272.xhtml#cf0180) Generic Architecture for Variational Quantum Circuits. Here *U*(**x**) is the quantum circuit block for encoding the (classical) input data **x** into a quantum state, and *V*(***θ***) is the variational circuit block with tunable or learnable parameters ***θ*** that will be optimized via gradient-based or gradient-free methods. A quantum measurement over some or all of the qubits follows. The measured results are classical values and can be further processed via quantum or classical components.

在 QML 领域，VQC 在标准机器学习任务中的应用取得了不同程度的成功。值得注意的例子包括函数近似 [\[20](#Chp017_311-328_B9780443190377000272.xhtml#br0100),[57\]](#Chp017_311-328_B9780443190377000272.xhtml#br0285)、分类 \[[2](#Chp017_311-328_B9780443190377000272.xhtml#br0010),[7](#Chp017_311-328_B9780443190377000272.xhtml#br0035),[15](#Chp017_311-328_B9780443190377000272.xhtml#br0075)–[17](#Chp017_311-328_B9780443190377000272.xhtml#br0085),[29](#Chp017_311-328_B9780443190377000272.xhtml#br0145),[32](#Chp017_311-328_B9780443190377000272.xhtml#br0160),[38](#Chp017_311-328_B9780443190377000272.xhtml#br0190),[41](#Chp017_311-328_B9780443190377000272.xhtml#br0205),[50](#Chp017_311-328_B9780443190377000272.xhtml#br0250),[53](#Chp017_311-328_B9780443190377000272.xhtml#br0265),[55](#Chp017_311-328_B9780443190377000272.xhtml#br0275),[57](#Chp017_311-328_B9780443190377000272.xhtml#br0285),[68](#Chp017_311-328_B9780443190377000272.xhtml#br0340),[70](#Chp017_311-328_B9780443190377000272.xhtml#br0350),[79](#Chp017_311-328_B9780443190377000272.xhtml#br0395),[81](#Chp017_311-328_B9780443190377000272.xhtml#br0405),[86](#Chp017_311-328_B9780443190377000272.xhtml#br0430)\]、生成建模 [\[24](#Chp017_311-328_B9780443190377000272.xhtml#br0120),[59](#Chp017_311-328_B9780443190377000272.xhtml#br0295),[77](#Chp017_311-328_B9780443190377000272.xhtml#br0385),[80](#Chp017_311-328_B9780443190377000272.xhtml#br0400),[94\]](#Chp017_311-328_B9780443190377000272.xhtml#br0470)、深度强化学习 [\[13](#Chp017_311-328_B9780443190377000272.xhtml#br0065),[14](#Chp017_311-328_B9780443190377000272.xhtml#br0070),[18](#Chp017_311-328_B9780443190377000272.xhtml#br0090),[42](#Chp017_311-328_B9780443190377000272.xhtml#br0210),[43](#Chp017_311-328_B9780443190377000272.xhtml#br0215),[52](#Chp017_311-328_B9780443190377000272.xhtml#br0260),[78](#Chp017_311-328_B9780443190377000272.xhtml#br0390),[87\]](#Chp017_311-328_B9780443190377000272.xhtml#br0435)、序列建模 [\[6](#Chp017_311-328_B9780443190377000272.xhtml#br0030),[20](#Chp017_311-328_B9780443190377000272.xhtml#br0100),[84\]](#Chp017_311-328_B9780443190377000272.xhtml#br0420)、语音识别 [\[88\]](#Chp017_311-328_B9780443190377000272.xhtml#br0440)、度量与嵌入学习 [\[51](#Chp017_311-328_B9780443190377000272.xhtml#br0255),[60\]](#Chp017_311-328_B9780443190377000272.xhtml#br0300)、迁移学习 [\[53\]](#Chp017_311-328_B9780443190377000272.xhtml#br0265) 以及 FL [\[12](#Chp017_311-328_B9780443190377000272.xhtml#br0060),[19](#Chp017_311-328_B9780443190377000272.xhtml#br0095),[88\]](#Chp017_311-328_B9780443190377000272.xhtml#br0440)。以下详述 VQC 中的常见操作。

### 17.3.1 Quantum encoder（量子编码器）

量子门仅作用于量子态。要使量子电路作用于经典数据集，关键的第一步是定义 *encoding*（编码）方法，即将经典向量或值数组转换为量子态。编码方案很重要，因为它与硬件实现的效率和潜在的量子优势相关。在 NISQ 时代，量子比特数量和电路深度受到限制。因此，经典值必须用少量量子比特编码，同时不能有太多量子操作或明显的电路深度。关于 QML 中使用的各种编码方法的更深入介绍，请参阅 [\[71\]](#Chp017_311-328_B9780443190377000272.xhtml#br0355)。一个通用的 *N*\-qubit 量子态可以表示为

```
${|\psi\rangle} = \sum\limits_{(q_{1},q_{2},\ldots,q_{N}) \in \{ 0,1\}^{N}}c_{q_{1},\ldots,q_{N}}{|q_{1}\rangle} \otimes {|q_{2}\rangle} \otimes {|q_{3}\rangle} \otimes \ldots \otimes {|q_{N}\rangle},$
```

![Image](OEBPS/images/B9780443190377000272/si14_u13.png)(17.2)

其中 *c*[*q*[1], …, *q*[*N*]] ∈ ℂ 是每个量子态的 *amplitude*（振幅），*q*[*i*] ∈ {0, 1}。振幅 *c*[*q*[1], …, *q*[*N*]] 的平方是测量后处于 |*q*[1]⟩ ⊗ |*q*[2]⟩ ⊗ |*q*[3]⟩ ⊗ … ⊗ |*q*[*N*]⟩ 态的 *probability*（概率），且总概率之和应为 1，即

```
$\sum\limits_{(q_{1},q_{2},\ldots,q_{N}) \in \{ 0,1\}^{N}}||c_{q_{1},\ldots,q_{N}}||^{2} = 1.$
```

![Image](OEBPS/images/B9780443190377000272/si19_u12.png)(17.3)
