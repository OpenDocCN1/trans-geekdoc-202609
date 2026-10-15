
对于威胁模型 A⃝，攻击者直接在 SNN 的输入上引入对抗性扰动。在此情况下，如黑色条带中 [Figure 7.24a](#chapter7.xhtml#fig7_24) 所示，DvsGesture 数据集的 SNN 未受到滤波器保护，准确率下降至 15.15%。在 NMNIST 数据集的 SNN 上也观察到类似行为，攻击将准确率降至 4%（降幅 91%，见 [Figure 7.24b](#chapter7.xhtml#fig7_24) 中的黑色条带）。我们注意到，两个数据集中，攻击算法的第一次迭代即已达到最大的准确率下降。进一步的迭代似乎不会进一步降低准确率。

![Figure 7.24: SNN robustness under the adversarial threat model A, and the threat model B with different parameters s and t of the filter. (a) Results for the DvsGesture dataset. (b) Results for the NMNIST dataset.](images/fig7_24.jpg)

[Figure 7.24:](#chapter7.xhtml#b7fig7_24) SNN robustness under the adversarial threat model A, and the threat model B with different parameters *s* and *t* of the filter. **(a)** Results for the DvsGesture dataset. **(b)** Results for the NMNIST dataset.

#### 7.4.4.3 SNN Robustness under Attack by Noise Filter-Unaware Adversary

随后，我们分析了威胁模型 B⃝ 的 SNN 稳健性，即攻击者可以在输入上引入扰动，但不清楚 DVS 滤波器的存在。对于此实验集，准确率远高于威胁模型 A⃝，证明了滤波器作为防御手段的有效性，能够保证高 SNN 稳健性。我们提出的 *R-SNN* 方法在同时变换滤波器参数 *s* 和 *t* 的情况下，其结果如 [Figure 7.24](#chapter7.xhtml#fig7_24) 所示。对于 DvsGesture 数据集的 SNN，在 *s* 和 *t* 的广泛取值范围内，准确率变化不大，保持在约 90%；但当 *t* = 500 时，准确率下降至 48%。然而，当 *t* = 1 时，*s* 的影响更为显著：准确率从 *s* = 1 的 62.5% 上升到 *s* = 4 的 83%。在其他所有情况中，差异几乎可以忽略。相反，我们可以看到 *s* 越大，滤波器处理所有数据的速度越慢。在考虑的数值中，*t* = 10 对每个 *s* 都产生了最高的准确率，最高达到 91.67%，对应 *s* = 3 和 *s* = 4。对于 NMNIST 数据集的 SNN，行为类似。当 *t* = 1 时，准确率强烈依赖 *s*。最高的 94% 准确率出现在 (*s*, *t*) = (3, 2) 和 (*s*, *t*) = (4, 2)。注意，这仅比原始准确率（即使用干净输入时）低 1%。另一方面，当 *t* ≥ 20 时，准确率跌破 90%。

#### 7.4.4.4 SNN Robustness under Attack by Noise Filter-Aware Adversary

我们还在威胁模型 C⃝ 下评估了 *R-SNN* 方法，攻击者知道滤波器的存在。此处，滤波器被纳入 SNN，具体为预处理阶段。如预期，滤波器在此场景下同样作为防御机制有效。与威胁模型 B⃝ 的差异不明显。在 DvsGesture 数据集的实验中，最高稳健性出现在 (*s*, *t*) = (3, 10) 和 (*s*, *t*) = (4, 10)，此时 SNN 的准确率为 91.67%（见 [Figure 7.25a](#chapter7.xhtml#fig7_25)）。对于 NMNIST 数据集，最高稳健性（即 94% 准确率）出现在 (*s*, *t*) = (3, 2) 和 (*s*, *t*) = (4, 2)（见 [Figure 7.25b](#chapter7.xhtml#fig7_25)）。这一结果表明，此类攻击无法战胜滤波器的存在。即使攻击者知晓滤波器，基于梯度的学习算法也无法有效学习滤波器的功能。

![Figure 7.25: SNN robustness under adversarial threat model C. (a) Results for the DvsGesture dataset. (b) Results for the NMNIST dataset.](images/fig7_25.jpg)

[Figure 7.25:](#chapter7.xhtml#b7fig7_25) SNN robustness under adversarial threat model C. **(a)** Results for the DvsGesture dataset. **(b)** Results for the NMNIST dataset.

#### 7.4.4.5 Case Study: Output Probability Variation

为了更细致地研究对抗攻击和滤波器的影响，我们对一条标记为 *left-hand wave* 的 DvsGesture 测试样本进行了全面的案例研究。[Figure 7.26](#chapter7.xhtml#fig7_26) 展示了本节各个对抗威胁模型（以及清洁输入和经过滤波的事件序列）的帧以及每个类别的输出概率。对于清洁图像，SNN 正确将事件归类为类 2，即 *left-hand wave*（见 [Figure 7.26a](#chapter7.xhtml#fig7_26)）。当使用 *s* = 2 与 *t* = 5 对输入信号进行滤波，如 [Figure 7.26b](#chapter7.xhtml#fig7_26) 所示，事件帧明显不同于前一例，但输出概率的变化极小，SNN 仍能正确分类输入。攻击被应用后，类 0（对应 *hand clap*）的输出概率超过正确类别。尽管输出概率差异巨大，但相较于清洁事件序列，帧的修改几乎不可见（见 [Figure 7.26c](#chapter7.xhtml#fig7_26)）。然而，在滤波器的作用下，威胁模型 B⃝ 和 C⃝ 中的 SNN 仍能正确分类输入。输出概率在 [Figure 7.26d](#chapter7.xhtml#fig7_26) 和 [Figure 7.26e](#chapter7.xhtml#fig7_26) 中正确类与其他类之间的差距很大，这表明我们的防御方法具有高度的稳健性。

![Figure 7.26: Detailed example of a sequence of events labeled as left-hand wave. On the left, the frames of events are shown. The histograms on the right-most column report the number of spikes emitted by the neurons of the last layer, which correspond to the output classes. (a) Clean event series. (b) Event series filtered with s = 2 and t = 5. (c) Event series under the adversarial threat model A, unfiltered. (d) Event series under the adversarial threat model B, filtered with s = 2 and t = 5. (e) Event series under the adversarial threat model C, filtered with s = 2 and t = 5.](images/fig7_26.jpg)

[Figure 7.26:](#chapter7.xhtml#b7fig7_26) Detailed example of a sequence of events labeled as *left-hand wave*. On the left, the frames of events are shown. The histograms on the right-most column report the number of spikes emitted by the neurons of the last layer, which correspond to the output classes. **(a)** Clean event series. **(b)** Event series filtered with *s* = 2 and *t* = 5. **(c)** Event series under the adversarial threat model A, unfiltered. **(d)** Event series under the adversarial threat model B, filtered with *s* = 2 and *t* = 5. **(e)** Event series under the adversarial threat model C, filtered with *s* = 2 and *t* = 5.

### 7.4.5 Summary

本节研究了基于 DVS 的系统对抗攻击对 SNN 的稳健性。我们提出的 *R-SNN* 方法通过 DVS 噪声滤波来提升对抗攻击的鲁棒性。本文是首次针对 DVS 信号进行对抗攻击的研究，也是首次将此类滤波器作为防御机制应用于此类攻击。它是一个概念证明（proof‑of‑concept），后续将在 [Section 7.5](#chapter7.xhtml#sec7_5) 中考虑更高级的噪声滤波器和专门的对抗攻击方法。

## 7.5 Dvs-Attacks: a Set of Adversarial Attacks on Event-Based Snns

