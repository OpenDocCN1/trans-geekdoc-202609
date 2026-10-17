
各行业都开发了 AI 工具，公司和研究人员可以使用这些工具开发 AI 解决方案（见表 3.1）。`IBM Watson` 提供了用于语音分析的 NLP AI 工具。它用于理解单词的语法和含义，并快速回答人类问题。另一组 AI 服务是 `Microsoft Azure AI` [23]。它是一个灵活的服务，受益于研究和 AI 实践，允许数据科学家和开发者实现他们的 AI 解决方案。它具有自定义的 API，可提供高质量的语言、语音、视觉和决策 AI 模型。它还提供了可互操作的 AI 云基础设施，支持 `Visual Studio Code` 和 `Jupyter Notebooks` 等常用开发平台，以及 `PyTorch` 和 `TensorFlow` 等开源框架。

同样，`Google` 开发了 `Google AI` 来提供 AI 服务和工具，例如 `Dialogflow` 和 `TensorFlow`，研究人员和开发者可以进行自定义以满足其解决方案需求。`Google AI` 解决方案的示例包括 AI 叫中心、用于文档处理的 `DocAi`、使用大规模语言进行语音和翻译的 `Translation Hub`，以及 `Vertex Vision AI` [24]，后者允许通过简单的用户界面实现和监控计算机视觉。它还通过集成仓库、数据流和视频视频分析等组件来分析图像和视频。

`Amazon Web Services` (`AWS`) 和 `OpenAI GPT-3` 是这些 AI 服务的替代方案。`AWS` 提供了构建交互界面的各种服务，例如 `Amazon Lex` 和类似 `SageMaker` 的 ML。相反，`GPT-3` 依赖通过 API 进行语言建模，适用于文本生成和聊天机器人的各种 AI 应用。

## 3.5.2 机器学习实现工具

`Scikit-Learn`：`Scikit-Learn` 是一个流行的 ML 库，支持监督和无监督学习算法，包括线性回归、逻辑回归、决策树、聚类和 k-means [25]。它的特点是用于预测数据分析的工具简单且高效。它在各种场景下都易于访问、使用和部署。它基于 `NumPy`、`SciPy` 和 `matplotlib` 构建。该库是开源的，并遵循 `BSD` 许可协议可商业使用 [26]。`Scikit-Learn` 为以下用途提供系列算法：

- 分类：包括 k-近邻和随机森林，用于识别对象的类别（例如图像识别）。
- 回归：例如梯度提升和逻辑回归，用于预测与对象相关的连续值属性（例如股票价格）。
- 聚类：例如 k-means 和 HDBSCAN，自动将对象分组。
- 降维：例如特征选择和主成分分析 (`PCA`)，减少需要考虑的随机变量数量。
- 模型选择：例如交叉验证和网格搜索，用于选择参数和验证模型。

**梯度提升（Gradient Boosting）：** 它是一种在分类等各种应用中强大且流行的 ML 技术。

## 3.5.3 深度学习实现工具

DL 与 ML 有一些共同的框架，如 `TensorFlow`、`Keras` 和 `PyTorch`。然而，其他框架如 `CNTK`、`Caffe`、`MxNet` 和 `Theano` 则是专门为 DL 解决方案设计的。

- **TensorFlow：** `TensorFlow` 是一个开源 DL 库。它用于用 Python 编写程序并在 CPU 或 GPU 上运行，而无需编写 C++ 或 CUDA 级代码即可利用 GPU。
- **PyTorch：** `PyTorch` 是一个依赖 `Torch` 库的 ML 框架。该软件最初由 Meta AI 创建，现在是 Linux 基金会的一部分。它是开源的，采用修改后的 BSD 许可协议。
- **Keras：** `Keras` 是一个在 Python 中处理 ANN 的开源库。它桥接了 `TensorFlow` 库，并在 2.3 之前的之前支持多种后端，包括 `Theano`、`Microsoft Cognitive Toolkit`、`PlaidML` 和 `TensorFlow`。`Keras` 遵循最佳实践以减轻认知负载，提供清晰简单的 API，最大限度地减少在常见情况下必须采取的操作，并提供可操作的错误信息 [29]。
- **Microsoft Cognitive Toolkit (CNTK)：** 这是一个允许用户设计各种流行模型类型（如前馈 DNN、CNN 和 RNN/LSTMs）的框架。它结合了跨多个服务器和 GPU 的自动并行化和微分的随机梯度下降学习。`CNTK` 采用开源许可，供公开使用。
- **Caffe：** `Caffe` 框架由伯克利视觉与学习中心联合社区贡献者开发。它是一个遵循 BSD 许可的开源框架，提供了更快速、更模块化的 DL 框架。它用于计算机视觉任务、图像分类和帧处理。它是一个带有 Python 接口的 C++ 库。`Caffe` 框架是 Google DeepDream 项目的基础基础 [30]。
- **MXNet：** 它是一个具有“遗忘背景”以节省内存的开源框架，对于处理长序列的 RNN 特别有帮助。其特点是可扩展性，支持多 GPU 和多机器训练。它允许用高层语言编写自定义层。
- **Theano：** 它是一个强大的数值计算库，可以与 `Keras` 等其他库并行使用。它的主要目的是为了研究和开发简化 DL 模型的实现。`Theano` 的速度使其成为 DL 和计算密集型项目等复杂任务的理想选择。

工具和框架的选择取决于特定的项目需求、团队的专业知识以及实现的目标。许多从业者结合使用这些工具来高效、有效地实现目标。

## 3.6 评估

工具和框架的选择取决于特定的项目需求、团队的专业知识以及实现的目标。许多从业者结合使用这些工具来高效、有效地实现目标。

常用的评估指标描述如下：

- **准确率 (Accuracy)：** 衡量预测准确的百分比。
- **精确率 (Precision)：** 也称为正性预测值，衡量真阳性的比例。
- **召回率 (Recall)：** 也称为灵敏度或真阳性率，衡量正确识别的正样本百分比。
- **F1 分：** 精确率和召回率的调和平均数，介于 0 到 1 之间。
- **特异性 (Specificity)：** 也称为真阴性率 (`TNR`)，衡量正确识别的负样本百分比。
- **AUC-ROC (受试者工作曲线面积)：** 主要用于二分类，接近 1 表示分离性良好，接近 0 则表示性能较差。

# AI 61 综合对比分析

- BLEU（双语言评估辅助理解）：它根据人类生成的参考文本与机器生成文本之间的相似性来衡量预测文本的质量。其范围在 0 到 1 之间，大于 0.3 被认为是好分 [42]。
- 困惑度（NLP）：它衡量语言模型预测文本样本的程度。它被用于比较不同的语言模型、微调单个模型参数或识别数据集中的问题。困惑度越低，效果越好，但它仅作为初步衡量，不用于最终决策，因为它没有反映准确性。一个模型可能在提供高错误率的同时具有低困惑度，会对模型预测的准确性产生负面影响 [43, 44]。

## 3.7 案例研究与应用

如今，AI、ML 和 DL 已成为开发智能解决方案不可或缺的工具。例如医疗保健、NLP、金融、零售、自动驾驶汽车、娱乐和农业。选择最优的 AI、ML、DL 模型取决于需求和目标。`IBM Watson` 用于肿瘤学、疾病爆发预测和医学图像分析是医疗保健领域基于解决方案的 AI、ML 和 DL 的示例，旨在改善患者健康并确保疾病早期发现。在金融领域，算法交易、AI 驱动的聊天机器人和欺诈检测帮助许多银行和金融机构回答查询、支持客户、为高频交易做出决策并识别欺诈交易。然而，虚拟助手、语言翻译和情感分析确保了对自然语言更好的理解和响应；提供了语言之间准确的翻译；并利用社交媒体数据对公众关于品牌、产品和政治问题的情绪进行深度分析。AI、ML 和 DL 在生活中成功集其他示例还包括自动驾驶和驾驶行为分析、目标检测、个性化和内容推荐、库存管理、视觉搜索、作曲和视频游戏设计、精准农业、疾病检测以及作物产量预测。

## 3.8 未来方向与挑战

AI、ML 和 DL 是开发智能系统非常有前景的技术。将这些技术整合到日常生活中使理解和解决问题变得容易得多。医疗保健、医学诊断的进步、药物发现和个性化治疗方案严重依赖 AI。自动系统（包括自动驾驶汽车和无人机）将继续进步，其中安全功能的改进和自主性的提高将发挥重要作用。此外，AI 在气候变化建模和预防自然灾害方面将发挥至关重要的作用。同样，在教育领域，AI 帮助开发虚拟教室、在线作业和自适应评估等个性化学习平台。此类自动化和智能系统可能会受到网络攻击。在这方面，AI 可以检测和识别网络威胁、发现异常并识别模式。

考虑到之前提到的所有优点，AI、ML 和 DL 技术面临若干挑战，包括数据质量、模型偏差、互操作性、可解释性、安全性和扩展性。在训练步骤中，如果数据存在偏差或质量低，会导致偏偏的 AI 模型。为了获得更好的结果，良好的数据预处理和良好的算法实现是必须的。此外，开发 AI 系统特定领域，部署它们的所有内容非常有挑战。开发复杂的 AI 和 DL 模型以及训练大模型会导致决策难以解释，并可能耗尽计算资源。确保 AI 系统（特别是自动系统）免受网络攻击仍然是一个大问题。解决这些挑战对于确保 AI 技术持续高效进步至关重要。

## 3.9 结论

AI、ML 和 DL 的世界已指数级增长，并成为开发无需人工干预的智能解决方案的主要工具。这些新兴技术整合到生活的各个领域，提供了各种工具、资源和框架，用于解决复杂问题和驱动创新。选择最优工具或框架取决于用户的需求和解决方案目标，以及用户的专业知识。

![](img/8c7c0992f9872f35977e949607bd4072_92_0.png)

图 3.1 用一个图表简化的 AI、ML 和 DL。

![](img/8c7c0992f9872f35977e949607bd4072_93_0.png)

表 3.1 基于 AI、ML 和 DL 开发解决方案的最常用工具和框架对比

| 工具/框架 | 用途 | 困难 | 中等 | 容易 | 编程 C++ | Scala | 多种 |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| AI IBM Watson | AI 服务与工具 | | | | | | |
| Microsoft Azure AI | AI 服务和云端工具 | | | | | | |
| Google Cloud | AI 服务和 ML 工具 | | | | | | |
| Amazon AI | | | | | | | |
| OpenAI-GPT3 | 通过 API 的语言模型 | | | | | | NA / (API) |
| ML Scikit-Learn | ML 库 | | | | | | |
| DL TensorFlow | DL 框架 | | | | | | |
| PyTorch | | | | | | | |
| Keras | | | | | | | |
| Caffe | | | | | | | |
| MXNet | | | | | | | |
| Theano | | | | | | | |
| CNTK | | | | | | | |

注：AI，人工智能；API，应用程序接口；DL，深度学习；ML，机器学习。

表 3.2 用于 AI、ML 和 DL 的最常用评估对比

| 评估参数 | 公式子 | 目标分类 | 目标回归 | 目标检测 | NLP | 目标 |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| 准确率 (Accuracy) | $Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$ | ✓ | | | | 预测多个类别。 |
| F1 分 (F1-score) | $F1_{score} = 2 * \frac{Precision * Recall}{Precision + Recall}$ | ✓ | | | | 寻找精确率和召回率之间的平衡。 |
| 召回率 (Recall) | $Recall = \frac{TP}{TP + FN}$ | ✓ | | | | 评估模型识别所有实例的能力。 |
| 精确率 (Precision) | $Precision = \frac{TP}{TP + FP}$ | ✓ | | | | 评估正类预测的质量。 |
| 特异性 (Specificity) | $Specificity = \frac{TN}{TN + FP}$ | ✓ | | | | 正确识别负实例。 |
| AUC-ROC | $AUC = \sum_{i=1}^{N} \frac{TP^*}{TP^* + FN^*}$ | | | | | 评估区分能力。 |
| 平均绝对误差 (MAE) | $MAE = \frac{\dots}{\dots}$ | | | | | (注：原文公式不全) |
| 均方误差 (MSE) | $MSE = \frac{\dots}{\dots}$ | | | | | (注：原文公式不全) |
| 均方根误差 (RMSE) | $RMSE = \sqrt{\dots}$ | | | | | (注：原文公式不全) |
| R 平方 (R-square) | $R^2 = \dots$ | | | | | (注：原文公式不全) |
| 平均平均精度 (mAP) | $mAP = \dots$ | | | | | (注：原文公式不全) |
| 交并比 (IoU) | $IoU = \dots$ | | | | | (注：原文公式不全) |
| 惩罚项 (Brevity) | $\dots$ | | | | | (注：原文公式不全) |
| 困惑度 (Perplexity) | $Perplexity = \dots$ | | | | | (注：原文公式不全) |

*(注：由于原文中部分公式显示不全，翻译时保持了结构并仅翻译了描述性文字)*

# 人工智能综合对比分析

- [19] Y. Huang, "基于人工智能的个性化英语教学平台设计," Journal of Information & Knowledge Management, vol. 21, no. Supp. 2, p. 2240017, 2022.
- [20] Y. Ran, Zhou, P. Lin, Y. Wen, and R. Deng, "预测性维护综述：系统、过程与方法," arXiv preprint arXiv:1912.07383, 2019.
- [21] P. Szolovits, R. S. Patil, and W. B. Schwartz, "医学诊断中的人工智能," Annals of Internal Medicine, vol. 108, no. 1, p. 80–87, 1998.
- [22] W. Konen, "通用AI学习中用于与研究的通用棋游戏," 2019 IEEE conference on (CoG). IEEE, 2019, p. 1–8.
- [23] M. A., "Azure AI：利用人工智能驱动业务结果并提升客户体验," azure.microsoft.com/en-us/solutions/ai/
- [24] G. C. Ai, "Vertex AI," https://cloud.google.com/vertex-ai.
- [25] B. Topuz, and N. C. Alp, "建筑学中的机器学习," Autonomy in Construction, vol. 154, p. 10512, 2023.
- [26] scikit learn, "scikit-learn: Python中的机器学习," https://scikit-learn.org/stable/
- [27] A. Natekin, and A. Knoll, "梯度提升算法，大规模," Frontiers in Neurocomputing, vol. 7, p. 21, 2023.
- [28] C. Bentéjak, A. Csorgő, and G. Martínez-Muñoz, "梯度提升算法的对比分析," Artificial Intelligence, vol. 54, p. 1933–1967, 2021.
- [29] Keras, "简单、灵活、强大," 2015, https://keras.io/
- [30] Yongqing, J. Ea, and Shahamer, "Caof: 来自BAIR的深度学习框架," 2017, https://caof.berkeley.org.
- [31] W. Chouki, H. Lamaazi, and N. Benamar, "使用深度学习的RPL排名攻击检测," 2022年信息、计算与技术创新与智能国际会议 (3CT). IEEE, 2022, p. 1–6.
- [32] Priyanka, "超越准确率：召回率、F1分数、ROC-AUC," 2022, https://medium.com/priyankads/beyond-accuracy-recall-f1-score-roc-auc-f62fe0979966.
- [33] W. Chouki, H. Lamaazi, and N. Benamar, "一种用于RPL网络瓶颈攻击检测的新型深度学习框架," 2022年信息、计算与技术创新与智能国际会议 (3CT). IEEE, 2022, p. 457–462.
- [34] A. Kumar, "机器学习——敏感性与特异性的差异," 2023, https://vitalflux.com/ml-metrics-sensitivity-vs-specificity-difference/
- [35] TURING, "理解AUC-ROC曲线及其在Python中分类的用法," https://python.com/kb/auc-roc-curves-and-their-usage-for-classification-in-python.
