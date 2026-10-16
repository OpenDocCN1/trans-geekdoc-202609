
$${\\overline{\\eta}}\_{K10}^{\\text{ML}} = \\frac{\\sum\\limits\_{c = 1}^{C = 10}\\eta\_{K10}^{ML}\\text{(}c\\text{)}}{C}$$  

(6.6)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn26.gif" position="float"/

$$\\quad\\sigma\_{K10}^{ML} = \\sqrt{\\frac{\\sum\\limits\_{c = 1}^{C = 10}\\left\\lbrack \\eta\_{K10}^{ML}\\text{(}c\\text{)} - \\quad{\\overline{\\eta}}\_{K10}^{\\text{ML}} \\right\\rbrack^{2}}{C - 1}}.$$  

(6.7)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn27.gif" position="float"/

This process was repeated for two different kinds of validation datasets and performance evaluated.

### 6.3 结果

第一步是使用交叉验证技术评估我们的深度学习系统（PE）性能，随后基于两个假设对斑块特征进行表征。PE 在章节 [6.3.1](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6s6-3-1) 中显示，特征表征在章节 [6.3.2](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6s6-3-2) 中讨论。最后，我们使用最广泛使用的面部生物特征数据集来评估我们的深度学习架构。

#### 6.3.1 深度学习数据分析及与机器学习的对比

##### 6.3.1.1 深度学习分类准确率（有无增强）

如图 [6.3](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig3) 所示，我们使用 13 层卷积神经网络（CNN）构建深度学习架构，最后一层为 softmax 层。输出层分别估计了风险属于有症状或无症状两组的可能性（二分类）。未使用增强时，K10 协议的准确率最高，AUC（使用 MEDCALC 17.0 计算）为 86.17% 和 0.86（*p*‑value < 0.0001），而使用增强后准确率为 89.7% 和 0.91（*p*‑value < 0.0001）。我们在 500 步结束时计算每种组合的实时准确率，以更全面地了解模型性能。

![Figure 6.3. The conceptual view of the deep learning architecture consisting of five CLs, five APLs, two DenLs, and one flattened layer. The dotted line in the middle shows the missing three CLs and three APLs. (Reproduced with permission from \[49\]. Copyright 2021 Springer.)](images/bk978-0-7503-2244-7ch6f3_online.jpg)

**Figure 6.3.** The conceptual view of the deep learning architecture consisting of five CLs, five APLs, two DenLs, and one flattened layer. The dotted line in the middle shows the missing three CLs and three APLs. (Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

##### 6.3.1.2 深度学习与机器学习的对比实验

对比实验的协议是将深度学习系统与机器学习系统在相同数据集上进行比较。我们还将我们创新的深度学习系统与使用相同斑块数据的已报道机器学习系统进行对比 \[[20](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib20), [35](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib35)\]. 图 [6.4](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig4) 展示了使用 K10 交叉验证技术对两种 AI 算法的结果。机器学习系统的准确率为 84.05%，而深度学习系统在未使用增强时为 86.17%，使用增强后为 89.7%（如图 [6.4](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig4)(a) 所示）。AUC 方面，机器学习系统为 0.83（*p*‑value < 0.0001），未使用增强的深度学习系统为 0.86（*p*‑value < 0.0001），使用增强后为 0.91（*p*‑value < 0.0001）。需要记住的关键点是，与深度学习系统不同，机器学习系统的设计与实现过程涉及精确的阶段。特征必须手动计算，离线训练系统需随时监控以进行优化。在讨论章节中，我们将详细阐述这些显著差异。

![Figure 6.4. (a) Bar charts showing the accuracy comparison between (i) machine learning (light grey), (ii) deep learning without augmentation (DL w/o Aug) (dark grey), and (iii) deep learning with augmentation (DL w/ Aug) (black). (b) ROC curves showing the AUC comparison: ML (0.83, p-value < 0.0001) versus DL w/o Aug (0.86, p-value < 0.0001) systems showing an improvement of 3.61%. (c) ROC curves showing the AUC comparison: ML (AUC: 0.83, p-value < 0.0001) versus DL w/ Aug (AUC: 0.91, p-value < 0.0001) showing an improvement of 8%. (Reproduced with permission from \[49\]. Copyright 2021 Springer.)](images/bk978-0-7503-2244-7ch6f4_online.jpg)

**Figure 6.4.** (a) Bar charts showing the accuracy comparison between (i) machine learning (light grey), (ii) deep learning without augmentation (DL w/o Aug) (dark grey), and (iii) deep learning with augmentation (DL w/ Aug) (black). (b) ROC curves showing the AUC comparison: ML (0.83, *p*‑value < 0.0001) versus DL w/o Aug (0.86, *p*‑value < 0.0001) systems showing an improvement of 3.61%. (c) ROC curves showing the AUC comparison: ML (AUC: 0.83, *p*‑value < 0.0001) versus DL w/ Aug (AUC: 0.91, *p*‑value < 0.0001) showing an improvement of 8%. (Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

##### 6.3.1.3 功效分析

功效分析用于检验招募样本量的有效性。在 95% 置信区间（CI）和 5% 误差范围内，所需样本量为 183 份。因此，我们实际招募的样本量（346 份扫描）约比所需的多出 47%。功效分析的计算公式为

$$n = \\left\\lbrack {\\left( z^{\*} \\right)^{2} \\times \\left( \\frac{\\widehat{p}\\left( {1 - \\widehat{p}} \\right)}{{MoE}^{2}} \\right)} \\right\\rbrack,$$  

(6.8)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn28.gif" position="float"/

其中 *z*\*inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch6ieqn29.gif"/是 *z*‑score，MoE 为误差范围，\\(\\widehat{p}\\)则是数据比例。

##### 6.3.1.4 使用生物面部数据（BFD）集对深度学习和机器学习系统进行验证

斑块照片的金标准依赖于临床医生的经验以及图像拍摄时的光照条件。因此，我们使用最广泛使用的“生物面部数据” \[[42](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib42\] 并配备强类别金标准，以进一步测试深度学习架构。该数据库包含 1440 张照片，分为 72 类，每类 20 份样本。补充材料 A 包含该数据集的样本照片。我们将深度学习模型的输出层调整为 72 个节点，以适应 BFD 实验，因为原输出层仅有两类。使用 K10 方法时，准确率为 99.84%，AUC 为 0.99（*p*‑value < 0.0001）。机器学习系统用于基准，结果为准确率 97.9% 和 AUC 0.95（*p*‑value < 0.0001），与深度学习方法几乎相同。我们使用诊断 odds ratio（DOR）来验证模型的性能；深度学习的 DOR 大于机器学习。

#### 6.3.2 深度学习框架中的斑块特征表征

