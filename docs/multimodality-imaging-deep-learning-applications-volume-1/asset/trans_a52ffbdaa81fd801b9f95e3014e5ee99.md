
-   [风险分层结果](https://wiki.example.org/feynmans_learning_method)可通过分析深度学习系统的最终性能并与其他标准机器学习系统（SVM 和 ELM）进行对比来总结，如图 [11.2](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig2) 所示。结果体现在两个方面：(i) 图像裁剪以去除背景，以及 (ii) 评估数据规模的影响。

#### 11.4.1 图像预处理（针对 DL、ELM 和 SVM）

在使用交叉验证（CV）方法（如图 [11.5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig5) 所示）评估测试数据的正确性之前，必须先去除背景信息。因此，对超声肝脏图像进行边缘剥离处理，以消除背景，确保仅保留感兴趣区域的组织。对于输入 Symtosis^(TM) 系统的图像以及使用 K10 CV 协议的 SVM、ELM 和 DL 架构，分层精度分别为 SVM 82%、ELM 92%、DL 100%。图 [11.7](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig7) 展示了边缘剥离百分比与准确性在 63 名患者中的关系曲线，表明在 K10 交叉验证程序中，15% 的背景剥离可达到最高精度。图 [11.8](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig8) 展示了相应的精度柱状图。我们的研究表明，SVM 和 ELM 的背景敏感性低于 DL。在 DL 情形中，可能的原因是它在初始轮次过度适配，且没有任何迭代。图 [11.8](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig8) 中，(a)、(b) 和 (c) 分别对应 SVM、ELM 和 DL 的研究架构，显示 15% 裁剪图像的对应柱状图。对于 K10 交叉验证的 15% 拉伸超声肝脏图像，表 [11.2](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t2) 给出了准确率、AUC、灵敏度、特异度和阳性预测值（PPV）的平均值。DL 的结果在准确率、灵敏度、特异度和 PPV 方面比 SVM 和 ELM 高出 100%。AUC 达到完美的 1.0，高于 SVM 和 ELM。深度学习在裁剪技术方面表现出稳健的性能，我们的实验已证明这一点。裁剪功能用于去除背景噪声信息。在 15% 边缘区削减时，深度学习可实现 100% 的准确性。然而，进一步增加裁剪会去除肝脏 FLD 数据，导致准确率下降，从而使优化收获值降低。这表明 FLD 组织信息并不总是集中在图像中。当区域边缘剥离至 15% 时，初始模型即可取得有效结果，原因是在此情形下肝脏组织表现最佳且噪声特性较低。值得注意的是，在典型的学习机器系统（如 SVM 或 ELM）中，这些高级功能并不存在。

![Figure 11.7. Accuracy versus cropping percentage of background borders. The accuracy was calculated using the K10 protocol in the (a) SVM, (b) ELM, and (c) DL frameworks. (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f7_online.jpg)

**Figure 11.7.** Accuracy versus cropping percentage of background borders. The accuracy was calculated using the K10 protocol in the (a) SVM, (b) ELM, and (c) DL frameworks. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

![Figure 11.8. Accuracy bar chart. (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f8_online.jpg)

**Figure 11.8.** Accuracy bar chart. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

**Table 11.2.** Comparative performance of three models using the K10 cross-validation. protocol: SVM versus ELM versus DL. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

| Classifier type || Average ACC\* (%) || Average sensitivity (%) || Average specificity (%) || Average PPV (%) || Average AUC |
| --- | --- | --- | --- | --- | --- |
| SVM || 82.08 || 64.21 || 93.56 || 86.31 || 0.79 |
| --- | --- | --- | --- | --- | --- |
| ELM || 92.22 || 93.33 || 90.83 || 84.58 || 0.92 |
| DL || 100.00 || 100.00 || 100.00 || 100.00 || 1.00 |

\* Accuracy.

#### 11.4.2 数据规模对分层准确率的影响

了解训练和测试过程中数据规模对 DL 模型的影响至关重要，并需与 SVM 和 ELM 技术进行比较。Symtosis^(TM) 系统采用图 [11.5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig5) 所示的方法，使用四套交叉验证（K2、K3、K5、K10）实现。图 [11.9](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig9) 展示了结果。结果表明，DL 模型在准确率方面优于 SVM 和 ELM。

![Figure 11.9. Accuracy bar chart for all CV protocols. (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f9_online.jpg)

**Figure 11.9.** Accuracy bar chart for all CV protocols. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

#### 11.4.3 使用“肝脏分割指数”进行分层分析

在 SVM、ELM 和 DL 三种范式中，理解 Symtosis^(TM) 类别特征的表现至关重要。核心思想是提取特征、标准化，并计算区分正常与异常肝脏患者的指数。我们定义该指数为肝脏分割指数（LSI），公式如下：

$$\\text{LSI} = \\frac{|\\mu\\_{Nor} - \\mu\\_{Abnor}|}{\\mu\\_{Nor}} \\times 100$$

其中，\\(\\mu\\_{Nor}\\) 和 \\(\\mu\\_{Abnor}\\) 分别为正常和异常特征的平均值，给出为

$$\\mu\\_{Nor} = \\frac{\\sum_{j = 1}^{P\\_{Nor}}\\sum_{i = 1}^{N}x_{i}^{j}}{P\\_{Nor} \\times N};\\quad\\mu\\_{Abnor} = \\frac{\\sum_{j = 1}^{P\\_{Abnor}}\\sum_{i = 1}^{N}x_{i}^{j}}{P\\_{Abnor} \\times N},$$

(11.1)

其中 \\(P\\_{Nor}\\) 和 \\(P\\_{Abnor}\\) 分别表示正常和异常/患病特征的数量，\\(N\\) 表示特征总数。表 [11.3](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t3) 显示了利用三类正常与两类异常策略计算的特征平均值；表 [11.4](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11t4) 则展示了相应的 LSI 值。值得注意的是，DL 与 ELM/SVM 架构之间存在重要区别：SVM/ELM 采用 Gabor、GLRM 和 GLCM \[[5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib5)\] 特征图，而 DL 则通过特征图的划分实现更高精度。

**Table 11.3.** Average feature values for normal and abnormal patients. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

| ELM/SVM  || DL |
| --- | --- |
