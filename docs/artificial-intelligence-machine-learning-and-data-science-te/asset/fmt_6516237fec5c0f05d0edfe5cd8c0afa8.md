
# SVM 性能分析与未来展望

## SVM 性能对比

SVM 速度相当快。总体而言，SVM 耗时最少（使用 80% 训练数据时为 0.11 秒），而 BLSTM 在特征提取过程中耗时最长（使用 60% 训练数据时为 20.48 秒）。因此 SVM 适合用于评估，如 [Figure 3.11](#ch11.xhtml#f25) 所示。根据 [Figures 3.7](#ch11.xhtml#f21)、[3.8](#ch11.xhtml#f22)、[3.9](#ch11.xhtml#f23)、[3.12](#ch11.xhtml#f26) 和 [3.13](#ch11.xhtml#f27)，提高性能的重要方面之一是训练算法。在此分析中，选择 BLSTM 是因为它比 SVM 和 LSTM 更敏感、更准确。

![Figure 3.10 F1-score at 50% to 90% TTR using BLSTM, LSTM, and SVM.](html/images/9780367720919_C003_010.jpg)

**Figure 3.10** F1-score at 50% to 90% TTR using BLSTM, LSTM, and SVM.

## 实验结果分析

在此评测中，SVM 正确区分了 6902 名患者与 2211 名个体。在 89.13% 的患者中，SVM 正确识别了癌症与非癌症类别（健康个体和其他肺部疾病患者）的对比。基于 SVM 的自动呼吸评估使肺癌患者能在安全对象中被区分开来，并能区分各种疾病状态的患者。它可能提供癌症患者与健康人群之间的区分度，如 [Figure 3.12](#ch11.xhtml#f26) 所述。

![Figure 3.11 Execution time at 50% to 90% TTR using BLSTM, LSTM, and SVM.](html/images/9780367720919_C003_011.jpg)

**Figure 3.11** Execution time at 50% to 90% TTR using BLSTM, LSTM, and SVM.

LSTM 正确分类了总计 9113 例中的 2211 名患者为 6902 例。在 95.47% 的 LSTM 结果中，癌症相对于非癌症患者呈阳性。存在癌症受害者与健康社会之间分离程度的分类。

共有 6379 个训练样本和 2734 个测试样本，训练测试比为 70%–30%。这 118 个样本包含 6902 个结节和 2211 个非结节。[Table 3.2](#ch11.xhtml#t9) 显示了正确分类和错误分类的结节及非结节。获得的灵敏度和特异性百分比分别为 95.77 和 96.65。如 [Figure 3.14](#ch11.xhtml#f28) 所示，ROC 曲线反映了各种测试比率下的总机器输出。测量 ROC 是为了验证 BLSTM 正确区分结节与非结节的能力。ROC 作为测试分类器性能区分能力的有效工具。ROC 曲线由 FPR 和 TPR 绘制而成。[Figure 3.14](#ch11.xhtml#f28) 显示了 BLSTM 分类器的 ROC 曲线。

![Figure 3.12 Analysis among sensitivity, specificity accuracy using SVM.](html/images/9780367720919_C003_012.jpg)

**Figure 3.12** Analysis among sensitivity, specificity accuracy using SVM.

学习过程在预处理层面、肺分割和特征提取方面均已妥善完成。

![Figure 3.13 Analysis among sensitivity, specificity accuracy using LSTM.](html/images/9780367720919_C003_013.jpg)

**Figure 3.13** Analysis among sensitivity, specificity accuracy using LSTM.

遵循精度、灵敏度、准确率等最高的程序，估计结果误差较小。这涉及对数据集分割策略进行更多分析以获得最大量。观察到肿瘤的高代谢和更好的 CT 图像。对于此类影像疾病，如肺癌、乳腺癌、脑肿瘤和心血管疾病，确实可使用所提方法进行观察。该程序可为患者提供更详细的切片集。

![Figure 3.14 ROC curve analysis using BLSTM.](html/images/9780367720919_C003_014.jpg)

**Figure 3.14** ROC curve analysis using BLSTM.

因此，护理治疗仅记录此类切片，而非所有角度。似乎作者提出了这一概念，将提供诸多优势：如通过最小化记录切片的使用来限制在图像上停留的时间、提高有效性、减少功耗、降低经济成本、节省时间和金钱、减少扫描费用等。每个人都能更轻松地处理。

## 3.10 Future Enhancement

研究者在所提方法中仅使用了分水岭标记分割，并建议了包括对比在内的其他几种分割方法，这将在未来提高特征效率。此外，还必须考察其他几种用于图像改进的滤波器和方法。通过增加给定的数据量，可提高额外肿瘤属性的准确性。应应用基于人工智能的其他分类方法，如 AlexNet、GoogLeNet 等。

## 3.11 Conclusion

所提肺癌检测方法可识别肺部肿瘤。CT 图像经预处理后，使用标记控制分水岭进行分割。学习过程在预处理层面、肺分割和特征提取方面均已妥善完成。遵循精度、灵敏度、准确率等最高的程序，估计结果误差较小。这涉及对数据集分割策略进行更多分析以获得最大量。对于特征提取，使用分割后的图像。通过提取的特征在肺内发现肿瘤。对于医学诊断，同时使用有监督和无监督分类器。通过使用 BLSTM，最大准确率为 96.14%，LSTM 适度使用为 95.47%，SVM 为 89.13%。该系统从而引导放射科医生预测肿瘤分期并提高准确性。研究者已检验机器学习技术，为医疗专业人员和放射科医生提供诊断设备，支持他们基于组织学特征为患者选择治疗方案。将人工智能方法与医疗援助相结合，有助于肺癌诊疗，本分析讨论了此类优势及整个护理周期中存在的不足。

**Conflict of interest:** No conflict of interest.

## References

*   [Alahmari S.S.](#ch11.xhtml#r058b) and D. Cherezov, “Radiomics improves pulmonary nodule malignancy prediction in lung cancer screening.” *IEEE Access* 6: 77796–77806 (2018).

*   [Albu, Adriana](#ch11.xhtml#r059b), Radu-Emil Precup, and Teodor-Adrian Teban. “Results and challenges of artificial neural networks used for decision-making and control in medical applications.” *Facta Universitatis, Series: Mechanical Engineering* 17, no. 3: 285–308 (2019).

*   [Altaf, Fouzia](#ch11.xhtml#r060b), Syed M.S. Islam, Naveed Akhtar, and Naeem Khalid Janjua. “Going deep in medical image analysis: Concepts, methods, challenges, and future directions.” *IEEE Access* 7: 99540–99572 (2019).

*   [Asan, Onur](#ch11.xhtml#r061b), Alparslan Emrah Bayrak, and Avishek Choudhury. “Artificial intelligence and human trust in healthcare: Focus on clinicians.” *Journal of Medical Internet Research* 22, no. 6: e15154 (2020).

*   [Chen, Ying](#ch11.xhtml#r062b), Yerong Wang, Fei Hu, and Ding Wang. “A lung dense deep convolution neural network for robust lung parenchyma segmentation.” *IEEE Access* (2020).

*   [Cui, Sunan](#ch11.xhtml#r063b), Yi Luo, Huan-Hsin Tseng, Randall K. Ten Haken, and Issam El Naqa. “Artificial neural network with composite architectures for prediction of local control in radiotherapy.” *IEEE Transactions on Radiation and Plasma Medical Sciences* 3, no. 2: 242–249 (2018).

*   [Dartmouth-Hitchcock Medical Centre](#ch11.xhtml#r064b), “A new machine learning model can classify lung cancer slides at the pathologist level.” *Sch of Comp. Dub Inst of Tech* (2019).
