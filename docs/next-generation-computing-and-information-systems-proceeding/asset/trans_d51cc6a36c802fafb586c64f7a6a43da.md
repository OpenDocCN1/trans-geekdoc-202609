

## 5.1 客观评估方法

表 2 所示结果基于三种标准测量技术：感知评估技术 (PET)、短时客观评估技术 (STOE) 和长时失真技术 (LTDT)。相应的条形图如图 6 所示。

### 表 2. 高系统噪声集成水平下的 PET、STOE 和 LTDT 结果：∼15 dB、∼10 dB 和 20 dB。

| 指标 | 噪声 | A1 | A2 | A3 | A4 | A5 | A6 | A7 |
|---|---|---|---|---|---|---|---|---|
| PET 高 | 1.62 | 1.34 | 2.14 | 2.88 | 2.06 | 2.92 | 1.32 | 1.84 |
| 低 | 1.18 | 1.95 | 1.69 | 2.18 | 2.42 | 2.64 | 2.86 | 1.22 |
| 平均 | 2.19 | 2.17 | 2.05 | 2.53 | 2.40 | 1.85 | 1.39 | 1.43 |
| STOE 高 | 1.71 | 0.80 | 0.84 | 0.86 | 0.83 | 1.36 | 1.59 | 0.68 |
| 低 | 1.65 | 0.71 | 0.98 | 1.51 | 0.73 | 0.69 | 0.04 | 0.67 |
| 平均 | 0.23 | 0.76 | 0.34 | 1.05 | 0.85 | 1.02 | 0.51 | 0.92 |
| LTDT 高 | 1.43 | 2.15 | 1.14 | 2.36 | 2.27 | 2.98 | 2.65 | 2.48 |
| 低 | 2.93 | 1.48 | 1.22 | 0.76 | 0.59 | 1.35 | 1.66 | 2.65 |
| 平均 | 1.02 | 2.21 | 2.53 | 1.50 | 2.47 | 1.21 | 0.55 | 0.52 |

![](img/9eefc6d2972274efeb1680c6a31895e5_174_0.png)

### 图 6. 七个 DNN 层级的平均 PET 和 STOE 结果。

## 5.2 主观评估方法

在所有数据集上进行了三种类型的实验，并在图 7 中发现了显著结果。实验的性能变化如下：0.1、0.001 和 0.0001。所有技术之间的性能比较也在该图中显示。DNN 层根据最高精度进行设置。表 3 显示了其他选定技术（LR、SVM 和 CNN 模型）基于精确率和召回率的比较。表 3 呈现了测试结果，统计了应用于测试集的 SVM、CNN 和 CSVM 算法。评估中包含总共 20,000 条文本，每个类别代表 2,000 条文本的数据量。根据表 2，文本分类的 CNN 算法和 CSVM 算法非常相似。这是因为，卷积神经网络提取形态特征后，利用 SVM 多类分类器解决非线性问题，并避免了维度灾难。在单个事件分类方面，CNN 优于 SVM 和 LR。Twitter 数据的复杂性主要源于其复杂的结构，因为推文通常包含错误、缩写、省略和单词的音节表述。训练集的制作涉及人工标注程序，可能包含不同程度的不确定性。另一方面，CNN 能够从推文中推导出高层抽象，而 SVM、LR 和其他高度依赖训练集有效性的机器学习算法则不然。CNN 在跨事件主题分类方面的能力表明，公司可以在新事件早期利用从以前飓风事件开发的现有知识库对 Twitter 主题进行分类。该知识库是根据以前的飓风事件构建的。在跨事件分类中，CNN 优于 SVM 和 LR，因为它可以提供一个通用解决方案，推断不同事件之间的相似性和不相似性模式。然而，由于 CNN 比 SVM 和 LR 需要训练更多参数，完成所需时间更长。由于社交媒体数据的持续流和快速积累，使用 CNN 进行在线学习变得具有挑战性。

![](img/9eefc6d2972274efeb1680c6a31895e5_175_0.png)

### 图 7. PET、STOE、LTDT 与三种技术平均结果的比较。

### 表 3. LR、SVM 和 CNN 模型的精确率和召回率比较。

| 数据集 | LR 精确率 | LR 召回率 | SVM 精确率 | SVM 召回率 | CNN 精确率 | CNN 召回率 | CSVM 精确率 | CSVM 召回率 |
|---|---|---|---|---|---|---|---|---|
| 科学与技术 | 0.95 | 0.92 | 0.93 | 0.92 | 0.96 | 0.95 | 0.97 | 0.98 |
| 教育 | 0.75 | 0.91 | 0.88 | 0.90 | 0.87 | 0.93 | 0.94 | 0.98 |
| 时尚 | 0.70 | 0.88 | 0.78 | 0.85 | 0.95 | 0.96 | 0.99 | 0.98 |
| 娱乐 | 0.94 | 0.92 | 0.95 | 0.92 | 0.98 | 0.96 | 0.99 | 0.97 |
| 金融 | 0.92 | 0.87 | 0.94 | 0.90 | 0.98 | 0.97 | 0.98 | 0.99 |
| 家居家具 | 0.80 | 0.78 | 0.82 | 0.88 | 0.94 | 0.94 | 0.96 | 0.98 |
| 游戏 | 0.96 | 0.94 | 0.95 | 0.94 | 0.98 | 0.96 | 0.96 | 0.99 |
| 房地产 | 0.94 | 0.92 | 0.96 | 0.94 | 0.99 | 0.98 | 0.98 | 0.99 |
| 政治 | 0.77 | 0.83 | 0.83 | 0.91 | 0.93 | 0.95 | 0.95 | 0.97 |

## 6 结论

本工作旨在探讨在 COVID-19 管理背景下，基于 CNN 的深度学习模型在社交媒体主题分类方面的性能。根据本研究对 CNN 模型的规格说明，我们在三个人工标记的 Twitter 数据集上使用了该分类器。这些数据集分为五组：援助与捐赠、资源与基础设施、损害与伤亡、信息来源、以及警告与建议。尽管测试中使用的 CNN 是一个简单模型，并未针对当前任务进行进一步调整，但研究结果表明，与考虑的数据集上的传统技术直接对比时，其性能要优越得多。在单事件相关实验中，CNN 分类器始终优于两种流行的分类技术 SVM 和 LR，在各类别中精确率范围为 0.63 至 0.98，召回率范围为 0.60 至 0.99。与 SVM 相比，CNN 模型表现出更优越的性能，凸显了其在处理多样化社交媒体主题方面的有效性。

## 参考文献

- Cao, M., Bai, Y., Cao, Z., Nie, L., Zhang, M. (2023). “基于关键词引导的预筛选的高效图像-文本检索。” In IEEE Transactions on Circuits and Systems for Video Technology. doi: 10.1109/TCSVT.2023.3339489.
- Dao, S. D., Huynh, D., Zhao, H., Phung, D., Cai, J. (2023). “基于预训练视觉-语言模型的开放词汇多标签图像分类。” In Proceedings of the 2023 IEEE International Conference on Multimedia and Expo (ICME), Brisbane, Australia, pp. 2135–2140. doi: 10.1109/ICME55011.2023.00365.
- Gao, Q., & Lim, S. (2019). 用于高光谱图像分类的支持向量机与联合稀疏模型的概率融合。GIScience & Remote Sensing, 56, 1129–1147
- Hou, Q., Han, M., Qu, F., & He, J.S. (2020). 超越文本理解社交媒体：Twitter 上的可靠实践。Computational Social Networks, 8, 1–20.
- Jones, P., Sharma, S., Moon, C., & Samatova, N.F. (2017). 面向任务中心文档策展的网络融合引导型仪表板界面。Proceedings of the 22nd International Conference on Intelligent User Interfaces.
- Khan, M.A., Sarfraz, M.S., Alhaisoni, M.M., Albesher, A.A., Wang, S., & Ashraf, I. (2020). StomachNet: 用于胃部异常分类的最优深度学习特征融合。IEEE Access, 8, 197969–197981.
- Miao, J., Luo, Z., Wang, Y., & Li, G. (2016). 用于人参鉴别的电子鼻与近红外反射光谱的比较与数据融合。Analytical Methods, 8, 1265–1273.
- Nasersharif, B., & Yazdani, M. (2021). 基于线性预测特征训练的分类器用于重放攻击检测的进化融合。Expert Systems, 38.
- Saeedi, J., & Faeze, K. (2013). 数字多焦点图像融合的分类与模糊基础方法。Pattern Analysis and Applications, 16, 365–379.
- Takruri, M., Rashid, M.W., & Attia, H. (2016). 用于提升黑色素瘤识别精度的多分类器决策融合。2016 5th International Conference on Electronic Devices, Systems and Applications (ICEDSA), 1–5.
- Tao, Y., Cui, Z., & Wenjun, Z. (2018). 基于标签向量融合的多标签文本分类方法。2018 International Conference on Promising Electronic Technologies (ICPET), 80–85
- Wang, L., Chen, X., Ye, Z., Jiang, S. (2023). “基于双向 Transformer 的多模态多标签文本分类。” In Proceedings of the 2023 5th International Conference on Robotics and Computer Vision (ICRCV), Nanjing, China, pp. 119–123. doi: 10.1109/ICRCV59470.2023.10329110.
- Yang, F., & Bansal, M. (2015). 基于相似性回归的标志检索特征融合。2015 IEEE Winter Conference on Applications of Computer Vision, 959–959.
- Yang, Y., Hsu, J., Löfgren, K., & Cho, W. (2022). 更正：Twitter 和 Weibo 中框架主题的跨平台比较：社交媒体文本挖掘的机器学习方法。Social Network Analysis and Mining, 12
- Yuan, H., Su, H., Liu, H., Wang, Y., Yang, H., & Hou, J. (2021). PQA-Net: 基于多视图投影的深度无参考点云质量评估。IEEE Transactions on Circuits and Systems for Video Technology, 31, 4645–4660

