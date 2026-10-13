

# 3.6 分类与评估

纹理特征被输入到机器学习算法（[Bishop, C. M., & Nasrabadi, N. M. (2006)](#979-8-3693-1642-9.ch011.xhtml#r8) `k Nearest Neighbor(kNN)`、`Support vector machine(SVM)`、`Naive Bayesian(NB)`、`Linear discriminant analysis`、`Quadratic discriminant analysis(QDA)`）中进行学习、训练和分类器模型创建。对模型进行测试和评估，以评价系统的性能。性能基于性能指标进行评估：`Accuracy`（准确率）、`Recall`（召回率）、`Precision`（精确率）、`F1 score`（F1分数）、`Kappa value`（Kappa值）和 `Matthew’s correlation coefficient(MCC)`（马修斯相关系数），这些指标是利用列联表或混淆矩阵（`CM`）的条目计算得出的（Mahesh, V. G., Raj, A. N. J., & Nersisson, R,2022）。`CM` 是一个 2x2 矩阵，它通过 `true positive(TP)`（真阳性）、`true negative(TN)`（真阴性）、`false positive(FP)`（假阳性）和 `false negative`（假阴性）提供分类摘要。

| 图 6. 列联表或混淆矩阵 |
| --- |
| ![Figure979-8-3693-1642-9.ch011.f06](i/ch011.f06.png) |

性能度量计算如下：

![Mathtype979-8-3693-1642-9.ch011.m15](i/ch011.m15.png) (8)

![Mathtype979-8-3693-1642-9.ch011.m16](i/ch011.m16.png) (9)

![Mathtype979-8-3693-1642-9.ch011.m17](i/ch011.m17.png) (10)

![Mathtype979-8-3693-1642-9.ch011.m18](i/ch011.m18.png) 其中

Y = ![Mathtype979-8-3693-1642-9.ch011.m19](i/ch011.m19.png) (11)

![Mathtype979-8-3693-1642-9.ch011.m20](i/ch011.m20.png) (12)

![Mathtype979-8-3693-1642-9.ch011.m21](i/ch011.m21.png) 其中

`P[o]` = `Accuracy` 且 ![Mathtype979-8-3693-1642-9.ch011.m22](i/ch011.m22.png) (13)

# 4. 结果与讨论

本研究的目标是在模式识别（`PR`）方法中对生物特征数据进行加密以用于认证。拟议方法论的详细实现如[图 7](#9799-8-3693-1642-9.ch011.xhtml#f07)所示。实验所用的生物特征数据为来自 Texas 3D 人脸识别数据集的面部图像，该数据集同时包含 RGB 和范围/深度图像。仿真在 963 张 RGB 图像上进行。这 963 张图像按 3:2 的比例分割用于训练和测试。因此，训练集有 578 张图像，测试集由 385 张图像组成。最初，训练集和测试集的图像均被转换为灰度图并调整大小作为预处理步骤。随后，使用 `RSA algorithm`（RSA 算法）对图像进行加密，然后将加密图像与实际图像融合以增强安全性。

现在，来自训练和测试数据集的两组图像 `Encrypted`（加密）和 `fused`（融合）被提供给特征提取和选择过程，如第 3.5 节所述。生成的特征矩阵 `F[xs_tr]` 和 `F[xs_te]` 分别用于训练和测试。特征集 `F[xs_tr]` 被标记了类别标签，并将标记后的矩阵提供给 `k Nearest Neighbor(kNN)`、`Support vector machine(SVM)`、`Naive Bayesian(NB)`、`Linear discriminant analysis`、`Quadratic discriminant analysis(QDA)` 机器学习算法进行学习、训练和构建分类器模型。在此过程中，可学习参数被调整以减少训练误差。

| 图 7. 拟议方法论的实现 |
| --- |
| ![Figure979-8-3693-1642-9.ch011.f07](i/ch011.f07.png) |

对于 `kNN classifier`（kNN 分类器），在保持欧氏距离度量的情况下，最近邻数从 2 变化到 6。`kNN model`（kNN 模型）构建完成后，使用 `F[xs_te]` 对其进行测试。利用公式 (8) 到 (13) 计算的指标，对所有最近邻值的测试结果进行了性能评估。评估后获得的性能指标显示在[图 8](#979-8-3693-1642-9.ch011.xhtml#f08)中。

| 图 8. kNN 模型计算的性能指标 |
| --- |
| ![Figure979-8-3693-1642-9.ch011.f08](i/ch011.f08.png) |

从评估中可以看出，与其他参数相比，`accuracy`（准确率）和 `precision`（精确率）指标的值较高，表明模型在正确预测类别方面表现良好。

| 图 9. SVM 模型计算的性能指标 |
| --- |
| ![Figure979-8-3693-1642-9.ch011.f09](i/ch011.f09.png) |

此外，`SVM algorithm`（SVM 算法）使用线性核和 rbf 核进行训练。对于 rbf 核，设置了超参数 `C` 和 `gamma` 并随后进行调优。参数 `C` 控制误差，而 `gamma` 提供决策边界的曲率权重。此处 `C` 固定为 1（默认值），`gamma` 从 0.1 变化到 0.7。所有变体的模型均经过测试和评估。评估的性能指标如[图 9](#979-8-3693-1642-9.ch011.xhtml#f09)所示。结果显示，当 `gamma` 从 0.1 变化到 0.3 时指标有变化，但对于后续变化，指标保持几乎恒定。因此，`gamma` 值超过 0.3 后对性能没有显著影响。`SVM model`（SVM 模型）的性能表现为较高的 `F1 score`（F1分数）和在 `gamma=0.3` 时高达 92.58% 的 `precision`（精确率）。由于 `F1score` 是 `Precision`（精确率）和 `Recall`（召回率）的调和平均数，其较高值指向更好的分类质量。

| 图 10. NB、LDA 和 QDA 分类器模型计算的性能指标 |
| --- |
| ![Figure979-8-3693-1642-9.ch011.f10](i/ch011.f10.png) |

