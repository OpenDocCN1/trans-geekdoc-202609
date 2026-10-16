
**图 6.7.** (a) 深度学习（DL）架构的层级，(b) 症状性类的特征图示例，(c) 无症状性类的特征图示例。(经授权复制自\[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. 版权所有 2021 Springer.)

##### 6.3.2.5 假设 2：混沌分布

正如绪言所述，第二个假设是：症状性个体的斑块表现出比无症状个体更大的不可预测性（混沌或异质）。一种直接量化斑块随机性的方法是将其描述为一种混沌行为，使用曼德布罗特的基本混沌测量方程——分形维度（FD），记作 `D`。我们依据此假设，分别计算症状性和无症状性群体的 FD。若症状性的 FD 高于无症状性的 FD，则假设成立，说明斑块特征假设成立，深度学习（DL）分类是有效的。利用曼德布罗特方程，我们对两类群体分别使用标准化方程和方法计算 `D`，结果如图 [6.8](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig8) 所示：

$$D = \\frac{\\log{(N)}}{\\log{(r)}}\\quad$$  

(6.9) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn31.gif" position="float"/>

其中 `D` 为无量纲的自相似物体数目，`N` 表示覆盖该图案的方框数量，`r` 表示放大倍数。需要注意的是，对数使用以自然数 e 为底的 Napier 对数。症状性和无症状性的 `D` 值分别为 1.45（基于 176 张照片）和 1.36（基于 135 张图像），均在置信区间 (CI: 0.05 到 0.09) 范围内，验证了 `D`（症状性）> `D`（无症状）。

![Figure 6.8. Fractal dimension (D) analysis of (a) the symptomatic class and (b) the asymptomatic class. (Reproduced with permission from \[49\]. Copyright 2021 Springer.)](images/bk978-0-7503-2244-7ch6f8_online.jpg)

**图 6.8.** 症状性类和无症状性类的分形维度（`D`）分析。(Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

##### 6.3.2.6 使用深度学习的动脉粥样斑块分离指数（APSI）

该指标的目标是评估深度学习（DL）如何区分症状性与无症状性患者。因此，训练数据集被送入 DL 系统，计算其先前描述的平均特征强度（MFS）。动脉粥样斑块分离指数（APSI）\[[20](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib20)\] 根据症状性与无症状性数据集之间的百分比差异进行计算。90% 的分类准确率进一步得到该差异的支撑。APSI 采用机器学习（ML）和深度学习（DL）技术计算，如表 [6.3](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6t3) 所示，数学表达式为：

$${APSI}\_{K10}^{AI\\ model}\\left( \\% \\right) = \\left( \\frac{\\mid{MFS}\_{AF} - {MFS}\_{AS}\\mid}{{MFS}\_{AF}} \\right)\*100.$$  

(6.10) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch6eqn32.gif" position="float"/>

其中 AI model 代表 ML 或 DL，K10 为交叉验证（CV）协议，`MFS`[*A**F*] 与 `MFS`[*A**S**] 分别表示症状性和无症状性的平均特征强度。

**表 6.3.** 使用 ML 和 DL 系统的动脉粥样斑块分离指数（APSI）。(Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

| 人工智能类型 | 症状性（AF）平均特征强度 | 无症状性（AS）平均特征强度 | 动脉粥样斑块分离指数（APSI） |
| --- | --- | --- | --- |
| 深度学习 | 56.89 ± 25.80 | 20.39 ± 25.80 | |
| *A**P**S**I*[*K*10]^(*D**L*)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-2244-7ch6ieqn1.gif"/ **\= 64.15%** |
| (*p*‑value < 0.0001; CI: 0.48 to 0.23) |
| 机器学习 | 72.38 ± 25.93 | 35.7 ± 25.93 | |
| *A**P**S**I*[*K*10]^(*M**L**)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-2244-7ch6ieqn2.gif"/ **\= 50.67%** |
| (*p*‑value < 0.0001; CI:0.67 to 0.38) |
|  |  |  |  |

表 [6.3](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6t3) 显示，DL 模型的 APSI 高于 ML 模型。深度学习范式下两类特征学习更为平衡，而机器学习则不然。

### 6.4 讨论

本研究是首次利用深度学习架构对症状性与无症状性斑块进行分类。与机器学习相比，我们的模型在准确率和 AUC（曲线下面积）上均更高，准确率比已发表工作提升了 6.0%（*p*-value < 0.0001） \[[20](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib20), [35](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib35)\]。我们通过在一组面部生物特征数据集\[[42](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib42)\]上运行算法，验证了 DL 系统，结果显示准确率为 99%。随后，我们使用广为认可的动物数据集（ASSIRA）\[[45](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib45)\]进一步验证 DL 系统，准确率达 97.56%。

#### 6.4.1 关于症状性与无症状性斑块的数据集不平衡

我们的数据集包含两类斑块：症状性（196 张图像）和无症状性（150 张图像），类别规模存在轻微不平衡。这是因为这些图像均来源于定期进行超声检查的个体。为避免过拟合，我们采用了两种替代策略：(i) 在 DL 系统的全连接层中使用 L2 正则化；(ii) 在控制层中使用丢弃（dropout）层的概率。为防止过拟合，丢弃层的概率被固定为 0.5，这有助于保持 DL 系统各层的权重均衡。

#### 6.4.2 与文献中已有技术的对比

表 [6.4](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6t4) 总结了我们的 DL 模型与文献中已有分类方法的对比 \[[21](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib21), [35](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib35), [46](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib46)–[48](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib48)\]。

**表 6.4.** 与文献中已有分类方法的对比表。(Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

| 作者, 年份^# | 斑块 | 数据规模 | 特征提取 | 分类器类型 | ML 与 DL 对比 | 准确率 (%) | AUC (*p*-value) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Christodoulou *et al* (2003) | 仅斑块 | 230（-） | 纹理 | SOM *k*‑NN | ML | 73.1 68.8 | 0.753 0.738 NG |
| Acharya *et al* (2011) | 仅斑块 | 346（Cyprus） | 纹理 | SVM | ML | 83 | NG (*p* = 0.0000) |
| Acharya *et al* (2012) | 仅斑块 | 346（Cyprus） | DWT | SVM | ML | 83.7 | NG (*p* < 0.0001) |
| Acharya *et al* (2013) | 仅斑块 | 146（Portugal） | 痕迹变换与模糊纹理 | 模糊分类器 | ML | 93.1 | NG (*p* < 0.0001) |
| 346（UK） | SVM with RBF | ML | 85.3 | NG (*p* < 0.0001) |
| Gastounioti *et al* (2014) | 仅斑块（无切片） | 56（US 图像） | FDR | SVM | ML | 88.0 | 0.90 NG |
| 提出的 DL（无增强） | 仅斑块 | 346（Cyprus） | DL 自动特征 | CNN（13 层） | DL | **86.17** | **0.86 (*p* < 0.0001)** |

