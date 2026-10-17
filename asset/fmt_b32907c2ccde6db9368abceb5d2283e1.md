
This activity is also known as post-movement beta synchronization (PMBS), another informative and consistent event that begins during movement and lasts approximately 600 ms [79]. It is observed bilaterally after finger or foot movements, without significant bilateral coherence. The frequency band varies across individuals: ~16–21 Hz for finger movements [83] and ~19–26 Hz for foot movements [84]. PMBS amplitude is similar in fast and slow finger movements. This is interesting because fast and slow movements involve different neural pathways. Furthermore, this activity elicited by hand movements is significantly larger compared to finger movements [79]. Wrist movements produce larger beta oscillations compared to finger movements, which can be interpreted as the transition of motor cortical neuronal populations from enhanced neural firing during motor behavior to cortical de-excitation or cortical idling state [79]. This implies that moving more fingers produces larger beta waves. Beta activity is also important in grasp signal generation because it has less overlap with other frequency components [85].

### 17.2.4 Gamma Band Oscillations

Oscillations (ERS) of neural activity in the gamma band (35–45 Hz) have also received attention recently. This activity is very prominent after visual stimuli or before motor tasks. It may serve as a carrier for alpha and low beta oscillations and is associated with sensory information binding and sensorimotor integration. Gamma band activity, along with the other band activities mentioned above, can be observed at roughly the same time after performing a motor task. Gamma band ERS appears immediately before movement, while beta band ERS occurs immediately after the event.

Different methods have attempted to detect or highlight gamma band ERS. For example, the authors of reference [86] applied empirical mode decomposition (EMD) to single-channel (Cz) EEG, followed by time-frequency analysis, improving gamma band ERS detection. In another recent work by the same team, the power of filtered and artifact-removed Cz channel EEG signals in the 30–60 Hz range was measured during imagined movement [87]. This work used `FieldTrip` [88] for most EEG signal processing.

### 17.2.5 Long Delta Wave Activity

Unlike the known ERS and ERD activities in the alpha, beta, and gamma bands, long delta oscillations begin immediately after finger movements and last for several seconds. Although less reported in the literature, due to their high power and insensitivity to noise, they can serve as salient features for distinguishing movement from non-movement states.

The main task of BCI is how to utilize the above frequency band EEG behaviors before, during, and after imagined movement, or after specific brain stimulation, to generate control signals. Subsequent chapters will explore this issue. Research in reference [89] shows that delta band EEG signals contain useful information that can be used to infer finger kinematics and decode repetitive finger movements. Furthermore, the features with the highest decoding accuracy are highly correlated delta band EEG activities, mainly localized to the contralateral central scalp region. Delta band activity is also highly correlated with 3D reaching and grasping BCI movements [90]. Overall, using linear decoders with memory, finger kinematics can be inferred to a certain extent from whole-scalp delta band filtered EEG amplitude fluctuations [89].

### 17.2.6 Event-Related Potentials (ERP)

ERP variability is widely used in the design of many BCI systems. In important applications such as spelling BCIs, the P300 response to novel/target stimuli, particularly its P3b subcomponent, is examined and quantified using the oddball paradigm. ERPs are also used in many other BCI applications. Beverina et al. [91] used P300 and steady-state visual evoked potentials (SSVEP). They used SVM to classify ERP feature patterns. Their SSVEP method used signals from occipital electrodes (`Oz`, `O2`, `PO8`). Stimulus time points were considered random, and training with visual feedback [42] was suggested. Brain waves can normally be amplified through feedback. Another work used SSVEP in a visually refined immersive 3D game [92]. Phase-reversal checkerboard pattern evoked SSVEP was used for this BCI scheme. Multiple BCI applications using ERPs (particularly P300) will be discussed in subsequent chapters of this chapter.

## 17.3 Main Issues in BCI

Figure 17.5 shows a simple and popular BCI system architecture. Feature extraction and feature classification for specific body movements are the primary goals of most BCI systems.

![Figure 17.5 A typical BCI system using scalp EEGs when visual feedback is used.](img/c17f005.gif)

**Figure 17.5** A typical BCI system based on scalp EEG when visual feedback is used.

如前所述，BCI（脑机接口）的主要问题在于将控制信号从背景 EEG（脑电图）中分离出来。同时，皮层连接性作为识别各种任务相关脑活动的一个有趣标识，必须得到研究和利用。随后，对不同领域各种特征的检测和评估将提供控制信号。然而，首先必须对 EEG 信号进行预处理，因为这些信号天然地受到各种内部和外部干扰的污染。数据的预处理和调理（包括去噪和伪迹去除）可以进一步增强信号。以盲源分离（BSS）为例，在实施源分离算法之前，可能还需要进行预白化。

### 17.3.1 EEG 的预处理

为了获得无伪迹的 EEG 以提取控制信号，必须从眼动、心电图（ECG）以及任何其他内部或外部干扰效应等伪迹中恢复 EEG 信号。

眼动伪迹在额叶和枕叶 EEG 记录中都非常明显。相反，ECG 伪迹则更多地出现在枕叶电极上。不同的研究人员已做出许多尝试来去除这些伪迹。

大部分噪声和伪迹已被新型 EEG 机器自带的硬件滤除。作为可能最主要的残留伪迹，干扰性眼动（眼电伪迹；OA）在 EEG 中产生的信号振幅约为皮层信号的 10 倍，且持续时间在 200 至 400 ms 之间。

研究人员已有一些工作致力于去除 OA。某些研究人员尝试基于时域和频域的回归技术来估计传播因子，如文献 [\[93\]](#c17.xhtml#c17-bib-0093) 所述。这种尝试需要在 EEG 记录期间有一个参考电眼图（EOG）通道。

主成分分析（PCA）和支持向量机（SVM）也被用于此目的 [\[94\]](#c17.xhtml#c17-bib-0094)。在这些方法中，假设 EEG 和 OA 在统计上是不相关的。自适应滤波也已被采用 [\[95\]](#c17.xhtml#c17-bib-0095)。这种方法单独考虑 EEG 信号，因此忽略了 EEG 通道间的互信息。独立成分分析（ICA）也已在一些方法中使用。在这些工作中，EEG 信号被分离为其组成的独立成分（IC），在手动去除与伪迹相关的 IC 后，利用估计的分离矩阵将 IC 反投影回 EEG [\[96\]](#c17.xhtml#c17-bib-0096)。文献 [\[97\]](#c17.xhtml#c17-bib-0097) 中，一种基于二阶统计的 BSS 算法将混合的 EEG 和 EOG 信号分离为统计独立的源。随后对反转的 EOG 通道重复第二次分离。比较两轮中估计的 IC，并去除符号不同的那些 IC。尽管由于 BSS 的符号模糊性，结果无法被完全证实，但声称使用此方法可显著减轻伪迹。正如所注意到的，该方法也需要分离 EOG 通道。

在一种鲁棒方法中，EEG 首先通过迭代 SOBI（二阶盲识别）进行分离，随后利用 SVM 有效去除 EOG 伪迹 [\[98\]](#c17.xhtml#c17-bib-0098)。该方法也可轻松扩展至 ECG 伪迹的去除。所提算法包含 BSS、伪迹 IC 的自动去除，以及最后将 IC 反投影到头皮，从而提供无伪迹的 EEG。这在 图 17.6 中有所描述。如前所述，迭代 SOBI 在第一阶段已被有效用于分离 IC。在第二阶段，仅仔细选择了四个特征，用于将正常脑电节律与 EOG 进行分类。这些特征如下：

![Figure 17.6 A hybrid BSS‐SVM system for EEG artefact removal \[98\].](images/c17f006.gif)

**图 17.6** 用于 EEG 伪迹去除的混合 BSS-SVM 系统 [\[98\]](#c17.xhtml#c17-bib-0098)。

*   **特征 I**：信号峰值振幅与方差之间的较大比率表明数据中存在异常值。这是眼动的典型识别特征，因为它会在 EEG 轨迹上造成大幅偏转。数学描述如下：

(17.2)![equation](img/c17-disp-0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>f</mi><mn>1</mn></msub><mo>=</mo><mfrac><mrow><mo mathvariant="italic">max</mo><mfenced open="(" close=")"><mfenced open="|" close="|"><msub><mi mathvariant="bold">u</mi><mi>n</mi></msub></mfenced></mfenced></mrow><msubsup><mi>&#963;</mi><mi>n</mi><mn>2</mn></msubsup></mfrac><mspace width="1em"/><mtext>for</mtext><mspace width="0.2em"/><mi>n</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>N</mi></math> 

其中 **u**[n] 是 N 个 IC 中的一个，max(.) 是返回向量中最大元素的标量值函数，σ[n] 是 **u**[n] 的标准差，|∙| 表示绝对值。正常脑电活动紧密分布在其均值附近。因此，预期比率较低，而眼动信号则表现出较大的值。

*   **特征 II**：这是偏度的度量，即数据的三阶统计量，定义如下：(17.3)![equation](img/c17-disp-0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>f</mi><mn>2</mn></msub><mo>=</mo><mfenced open="|" close="|"><mfrac><mrow><mi>E</mi><mfenced open="{" close="}"><msubsup><mi mathvariant="bold">u</mi><mi>n</mi><mn>3</mn></msubsup></mfenced></mrow><msubsup><mi>&#963;</mi><mi>n</mi><mn>3</mn></msubsup></mfrac></mfenced><mspace width="1em"/><mtext>for</mtext><mspace width="0.2em"/><mi>n</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>N</mi><mspace width="0.2em"/></math> 

针对零均值数据。包含眼动的 EEG 通常具有正或负偏度，因为眼动信号在此特征上具有显著较大的值。
