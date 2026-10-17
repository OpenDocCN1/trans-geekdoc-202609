

实验结果显示了两种拟议的 CNN 方法与之前的 CNN 方法相对于步骤数的准确率和训练时间，如 [表 3.2](#bodymatter-003.xhtml#b_9783110670905-003_tab_002) 所示。拟议的“CNN 方法 2”在 110,000 步之后，其准确率（98.92%）高于之前的 CNN 方法和拟议的“CNN 方法 1”。但是，考虑训练时间，拟议的“CNN 方法 1”的性能是最快的，如 [图 3.8](#bodymatter-003.xhtml#b_9783110670905-003_fig_008) 所示。虽然之前的 CNN 和拟议的两个 CNN 的参数不同，但所有系统的准确率相对于训练系统的步骤数是相似的，如 [图 3.9](#bodymatter-003.xhtml#b_9783110670905-003_fig_009) 所示。由于书写风格不当，系统在某些情况下的预测似乎不正确，如 [表 3.3](#bodymatter-003.xhtml#b_9783110670905-003_tab_003) 所示。

表 3.2：之前的 CNN 和拟议的 CNN 的准确率。

| 步骤 || CNN 方法 2 || CNN 方法 1 || CNN 由 Younis 和 Alkhateeb 实现 \[[23](#bodymatter-003.xhtml#b_9783110670905-003_ref_023)\] |

| --- | --- | --- | --- |

| || 准确率 || 训练时间（秒） || 准确率 || 训练时间（秒） || 准确率 || 训练时间（秒） |

| 10,000 || 95.37% || 2,337 || 95.20% || 796 || 94.97% || 1,354 |

| --- | --- | --- | --- | --- | --- | --- |

| 20,000 || 97.13% || 4,613 || 96.99% || 1,571 || 97.03% || 2,698 |

| 30,000 || 97.92% || 6,867 || 97.70% || 2,342 || 97.60% || 4,050 |

| 40,000 || 98.23% || 9,196 || 98.05% || 3,132 || 97.99% || 5,391 |

| 50,000 || 98.42% || 11,456 || 98.29% || 3,907 || 98.25% || 6,738 |

| 60,000 || 98.50% || 13,706 || 98.39% || 4,671 || 98.41% || 8,083 |

| 70,000 || 98.66% || 16,037 || 98.51% || 5,469 || 98.53% || 9,436 |

| 80,000 || 98.79% || 18,276 || 98.61% || 6,228 || 98.59% || 10,782 |

| 90,000 || 98.79% || 20,632 || 98.72% || 7,036 || 98.67% || 12,132 |

| 100,000 || 98.84% || 22,852 || 98.78% || 7,789 || 98.80% || 13,502 |

| 110,000 || 98.92% || 25,127 || 98.85% || 8,564 || 98.85% || 14,821 |

![Figure 3.8: Accuracy versus training time.](graphic/converted/b_9783110670905-003_fig_008.png)

Figure 3.8: Accuracy versus training time.

表 3.3：一些被错误分类的图像。

| 样本 MNIST |

| --- |

| 图像 || ![](graphic/converted/b_9783110670905-003_ingr_001.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_002.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_003.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_004.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_005.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_006.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_007.jpg) || ![](graphic/converted/b_9783110670905-003_ingr_008.jpg) |

| 实际数字 || 9 || 2 || 7 || 3 || 4 || 5 || 2 || 6 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- |

| 预测数字 || 4 || 7 || 2 || 5 || 9 || 3 || 7 || 1 |

![Figure 3.9: Accuracy vs. number of steps for training the CNN.](graphic/converted/b_9783110670905-003_fig_009.png)

Figure 3.9: Accuracy vs. number of steps for training the CNN.

## 3.7 结论

本章讨论了用于识别 MNIST 字符数据集手写字符的 MLP、RNN 和 CNN。使用两种 CNN 方法实现的手写数字识别采用了不同的参数。从实验结果可以看出，CNN 在识别手写字符方面更准确。拟议的“CNN 方法 2”提供了 98.92% 的准确率，而拟议的“CNN 方法 1”为 MNIST 字符数据集提供了 98.85% 的准确率。实验结果表明，与其他方法相比，拟议的“CNN 方法 2”在准确率方面更好，而拟议的“CNN 方法 1”在训练时间方面更好，适用于 MNIST 数据集。通过使用更多数量的滤波器，系统的准确率将更好。但是，训练时间将非常高。为了进一步改进，需要增加训练系统的步骤数。

## 参考文献

\[1\]Arica N. & Vural F.T.Y. 面向脱机手写的字符识别概述。IEEE Transactions on Systems, Man and Cybernetics – Part C: Applications and Reviews, 2001, 31(2), 216–233. [→](#bodymatter-003.xhtml#xref_d63256e7363)

\[2\]Tappert C.C., Suen C.Y., & Wakahara T. 在线手写识别的最新技术。IEEE Transactions on Pattern Analysis and Machine Intelligence, 1990, 12(8), 787–808. [→](#bodymatter-003.xhtml#xref_d63256e7366)

\[3\]Quiles M.G. & Romero R.A.F. 基于多层感知机的计算机视觉系统用于控制移动机器人。International Congress of Mechanical Engineering, OuroPreto, Brazil, November, 2005. [→](#bodymatter-003.xhtml#xref_d63256e7372)

\[4\]Ruck D.W., Rogers S.K., & Kabrisky M. 使用多层感知机进行特征选择。Journal of Neural Network Computing, 1990, 2(2), 40–48. [→](#bodymatter-003.xhtml#xref_d63256e7375)

\[5\]Yang J.B., Shen K.Q., Ong C.J., & Li X.P. MLP 神经网络的特征选择：使用概率输出的随机排列。IEEE Transactions on Neural Networks, 2009, 20(12), 1911–1922. [→](#bodymatter-003.xhtml#xref_d63256e7379)

\[6\]Lee H., Grosse R., Ranganath R., & Ng A.Y. 用于可扩展无监督学习的分层表示的卷积深度置信网络。International Conference on Machine Learning, ACM, 2009, 609–616. [→](#bodymatter-003.xhtml#xref_d63256e7382)

\[7\]Vu N.T., Adel H., Gupta P., & Schutze H. 结合循环神经网络和卷积神经网络用于关系分类。NAACL HLT, 2016,534–539. [→](#bodymatter-003.xhtml#xref_d63256e7385)

\[8\]Le Cun Y., Bottou L., Bengio Y., & Haffner P. 应用于文档识别的基于梯度的学习。Proceedings of the IEEE, 1998, 86(11),2278–2324. [→](#bodymatter-003.xhtml#xref_d63256e7388)

\[9\]Krizhevsky A., Sutskever I., & Hinton G.E. 使用深度卷积神经网络的 Imagenet 分类。Advances in neural information processing systems, 2012,1097–1105. [→](#bodymatter-003.xhtml#xref_d63256e7391)

\[10\]Le Cun B.B., Denker J.S., Henderson D., Howard R.E., Hubbard W., & Jackel L.D. 使用反向传播网络的手写数字识别。Advances in neural information processing systems, Citeseer, 1990. [→](#bodymatter-003.xhtml#xref_d63256e7394)

\[11\]Arica N. & Vural F.T.Y. 连笔手写的光学字符识别。IEEE Transactions on Pattern Analysis and Machine Intelligence, June, 2002, 24(6), 801–113. [→](#bodymatter-003.xhtml#xref_d63256e7461)

\[12\]Khedher M.Z., Abandah G.A., & Al-Khawaldeh A.M. 优化特征选择以识别手写阿拉伯字符。Proceedings of World Academy of Science Engineering and Technology, February 2005, 4. [→](#bodymatter-003.xhtml#xref_d63256e7464)

\[13\]Hanmandlu M. & Ramana Murthy O.V. 基于模糊模型的手写数字识别。Pattern Recognition, 2007, 40, 1840–1854. [→](#bodymatter-003.xhtml#xref_d63256e7467)

\[14\]Arora S., Bhattacharjee D., Nasipuri M., Basu D.K., & Kundu M. 结合多种特征提取技术用于手写 Devnagari 字符识别。IEEE Region 10 and the Third international Conference on Industrial and Information Systems, Kharagpur, India, December 2008. [→](#bodymatter-003.xhtml#xref_d63256e7470)

\[15\]Kimura Y. 使用遗传算法进行字符识别的特征选择。Fourth International Conference on Innovative Computing, Information and Control, IEEE, 2009. [→](#bodymatter-003.xhtml#xref_d63256e7477)

\[16\]Graves A. & Schmidhuber J. 使用多维循环神经网络的脱机手写识别。Advances in Neural Information Processing Systems 22, NIPS'22, Vancouver, MIT Press, 2009, 545–552. [→](#bodymatter-003.xhtml#xref_d63256e7480)

