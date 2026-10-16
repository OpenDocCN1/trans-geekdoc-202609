
| 异常 | 正常 | 平均异常肝值 | SD* 异常 | 异常 | 平均异常肝值 | SD 异常 |
| Gabor | 0.500 | 0.506 | Deep features | 0.259 | 0.247 |
| --- | --- | --- | --- | --- | --- | --- |
| GLRM | 0.295 | 0.258 |
| GLCM | 0.486 | 0.287 |  |  |  |
| 正常 | 平均正常肝值 | SD 正常 | 正常 | 平均正常肝值 | SD 正常 |
| Gabor | 0.462 | 0.380 | Deep features | 0.285 | 0.246 |
| GLRM | 0.321 | 0.396 |
| GLCM | 0.504 | 0.284 |
\* 标准差.

**表 11.4.** 肝分离指数。(经授权自 \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. 版权所有 2018 Elsevier.)

| 分类器 | 肝分离指数 (LSI) (%) |
| --- | --- |
| --- | --- |
| --- | --- |
| ELM/SVM | Gabor | GLRM | GLCM |
| --- | --- | --- | --- |
| 7.65 | 8.81 | 3.66 |
| DL | 深度学习特征 |
| 9.86 |

表 [11.4](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t4) 清楚显示，DL 特征的 LSI 值高于 ML 特征的 LSI 值。图表见图 [11.10](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig10) (i) 显示 LSI (%) 与深度特征的关系。可以看到 LSI 值随特征数量增加而逐渐上升（箭头 (a)），当特征数量达到 800 时（箭头 (b)），随后上升明显（箭头 (c)）。

![Figure 11.10. (i) LSI (%) 与特征数量的关系，使用 DL 框架。(ii) (a) SVM、(b) ELM、和 (c) DL 使用 K = 10 ROC 曲线。(Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f10_online.jpg)

**Figure 11.10.** (i) LSI (%) 与特征数量的关系，使用 DL 框架。(ii) (a) SVM、(b) ELM、和 (c) DL 使用 *K* = 10 ROC 曲线。(Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

### 11.5 性能评估：ROC、可靠性和时间分析

交叉验证 (CV) 技术用于测试 DL 架构。ROC 分析在章节 [11.5.1](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-5-1) 中提及。可靠性分析为各种交叉验证的 *K* 折叠包含在章节 [11.5.2](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-5-2)，时间分析在章节 [11.5.3](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-5-3) 中呈现。

#### 11.5.1 ROC 分析

图 [11.10](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig10)(ii) 展示了 SVM、ELM 和 DL 的 ROC 曲线。DL 的 AUC 相较于 SVM 和 ELM 有了更大的提升。

#### 11.5.2 可靠性分析

可靠性分析针对所有 *K* 折叠的交叉验证进行。可靠性指数 (RI) *ζ*[*N*[*L*]](%) 以下公式给出：

$$\zeta_{N_{L}}\\left( \\% \\right) = \\left( {1 - \\frac{\\mu_{N_{L}}}{\\sigma_{N_{L}}}} \\right) \\times 100,$$  

(11.2) 其中 *μ*[*N*[*L*]] 是 *N*[*L*] 肝图像的准确率平均值，*σ*[*N*[*L*]] 是准确率的标准差。图 [11.11](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig11) 展示了可靠性分析的柱状图。柱状图清晰地表明 DL 架构的可靠性优于 SVM 和 ELM。

![Figure 11.11. 可靠性指数的柱状图。(Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f11_online.jpg)

**Figure 11.11.** 可靠性指数的柱状图。(Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

#### 11.5.3 时间分析

DL 架构的时间分析与 SVM、ELM 相比在表 [11.5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t5) 中给出。可以看到 DL 架构的平均训练时间和测试时间均高于 SVM 和 ELM。此外，为了衡量综合性能，我们计算了分类精度乘积和测试时长作为 PE 指数（表 [11.5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t5)）。

**表 11.5.** 时间分析。(Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

| 分类器类型 | 平均训练时间 (ms) | 平均测试时间 (ms) | PE 指数测试 |
| --- | --- | --- | --- |
| --- | --- | --- | --- |
| SVM | 0.029 016 | 0.002 262 | 0.188 269 |
| --- | --- | --- | --- |
| ELM | 0.007 020 | 0.001 560 | 0.143 868 |
| DL | 1.300 937 | 0.002 476 | 0.247 600 |

ms: 毫秒。

### 11.6 讨论

本研究的目标是使用 Symtosis^(TM) 系统，结合深度学习方法，以及 SVM 和 ELM 等机器学习基准模型，对 FLD（也称为肝脂肪变性）进行分类。以往的标准机器学习方法包括 SVM \[[11](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib11)\]、BPNN \[[8](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib8)\]、PNN \[[27](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib27)\]、模糊分类器 (FC) \[[26](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib26), [28](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib28)\] 和决策树 (DT) \[[6](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib6)\]。标准机器学习方法的局限性在于肝图像的低声强特征和分层结构，这限制了特征图的精度。此外，样本量较小且动态拟合不同的情况 \[[5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib5), [29](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib29)–[33](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib33)\] 可以用于机器学习方法。本章中，深度学习被用于诊断和分层 FLD。Symtosis^(TM) 系统通过生物特征数据进行验证，并被证明准确 \[[34](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib34), [35](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib35), [38](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib38), [39](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib39)\]。

*基准测试*

在肝脏检测和风险分类方面，深度学习应用较少。因此，我们选择使用最新的机器学习模型，这些模型已应用于超声图像，以此作为我们深度学习方法的基准。表 [11.6](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t6) 展示了我们的基准测试结果。用于超声图像的机器学习方法，如肝、甲状腺和卵巢超声，主要来自几个大型组织。这一点至关重要。表 [11.6](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t6) 的核心是第 5 列，显示机器学习方法对特征图的修改。这些属性主要包括纹理、波长、Gabor、傅里叶和更高阶谱 (HOS) 特征。

**表 11.6.** 基准测试。(Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

| 参考文献 | 疾病 | 数据集 | 样本数量 | 特征开采 | 分类器类型 | 准确率 (%) |
| --- | --- | --- | --- | --- | --- | --- |
| Acharya *et al* (2012) \[[5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib5)\] | FLD | 肝超声图像 | 100 | HOS、纹理、DWT | DT | 93.3 |
| --- | --- | --- | --- | --- | --- | --- |
| Acharya *et al* (2014) \[[36](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib36)\] | HT | 甲状腺超声图像 | 526 | 小波变换 | FC | 84.6 |
