

(iii) 针对不同分类器、传感器模态和特征集组合的 ER 准确率和 F1 分数的表征；(iv) 对每种模态的扩展特征集的探索；以及 (v) 对 DF 和 FF 方法中多模态分类的系统分析。研究表明，FF 在分类准确性和计算复杂度方面是最具竞争力的技术。

不同于以往大多使用二维（2D）显示器来激发情感状态的情感计算研究，文献 [10] 采用了沉浸式虚拟现实（VR）方法。这使得研究人员能够在封闭的实验室条件下模拟具有高水平存在感和交互性的环境。我们展示了使用头戴式设备通过生理和行为测量进行的情感识别研究的系统性观点。这些设备强调了该领域的演变，提供了聚合分析的清晰视角，并揭示了当前存在的问题以及未来研究的指南。

专注于情感计算（这是一项识别、解释、处理和模拟人类情感的人工智能领域），文献 [17] 展示了 2015 年至 2020 年间关于情感计算的相关科学文献。论文从计算机科学的角度介绍了趋势，并比较了新实现中的算法。该综述提供了关于数据集、情感激发方法、特征提取与选择、分类算法以及性能评估的概述。

## 面部表情识别

基于深度学习技术，文献 [18] 探讨了面部表情识别（FER）。作者应对了以下挑战性问题：(i) 与面部表情无关的因素多样性；(ii) FER 训练数据的缺乏以及 (iii) 对现有面部数据集的内在分析。用于 FER 的深度迁移学习通过训练期间使用的加权聚类损失函数（weighted-cluster loss）得到了补偿。

在文献 [19] 中，作者通过提出一种基于注意力网络的端到端方法，重新审视了疼痛相关面部表情的分析。作者提出的方法通过对基于注意力的神经网络进行加权聚合，结合了面部表情的空间和时间维度，并使用运动图像（MHIs）序列和双向长短期记忆（LSTM）循环神经网络（RNN），该方法被用于疼痛识别。

围绕人机交互（HCI）环境，文献 [21] 利用多模态数据集进行情感计算研究，解决了与对话 HCI 相关的情感和认知负荷的挑战性问题。该数据集使用了基于通用框架实现的实验性移动和交互传感器设计。这项工作包含六个顺序实验，包括兴趣、过载、正常、容易、理解和挫败。

文献 [21] 在多阶段架构中识别了面部关键点检测。第一阶段是获取像素级信息。第二阶段涉及将获取的信息与全局上下文信息中每个关键点之间的空间关系相结合。论文考虑了一种由两个主要部分组成的流水线架构：(i) 用于局部上下文子集的深度网络，通过带有额外内核卷积滤波器的全卷积数据集（Datasets）生成检测热图；(ii) 膨胀跳跃卷积子网络，该网络结合了空洞卷积和跳跃连接网络，用于细化局部外观热图。

围绕儿童机器人交互（CRI），文献 [22] 提出了一种儿童情感识别系统，通过同时使用视觉（RGB-红、绿、蓝）和红外热成像（IRTI）相机来识别面部。在基于颜色的 Viola-Jones 算法检测面部感兴趣区域（ROIs）的基础上，该论文的一项新贡献是计算了热图像上每个 ROI 的误差概率，使用由训练专家手动标记的参考帧，以便根据专家标准选择位置更好的 ROI。结果显示：(i) 所提的 ROI 位置方法对面部关键点的跟踪误差低于传统的 Viola-Jones 算法；(ii) 所提系统已集成到社交机器人中，用于识别儿童机器人交互期间婴儿幼儿的情绪。

文献 [23] 提出了一种应用于情感和强度识别的机器学习算法比较，以解决现有情感识别系统中缺乏对观察到的面部情感强度进行编码以及多样性不足的问题。该工作比较了多种算法：(i) 用于特征提取的 Gabor 滤波器、方向梯度直方图（HOG）和局部二值模式（LBP），以及 (ii) 用于分类的支持向量机（SVM）、随机森林（RF）和最近邻算法（KNN）。实验表明，该类别可以在实时行为识别中进行研究。

文献 [24] 针对基于部的情感识别采用了迁移学习方法。该研究基于这样一个事实：实践中可用的数据集很少，且某些数据集包含演员的情感表达，而不是采用真实世界的分类。即使脸部只能从不利的角度可见，迁移学习方法也允许作者使用特征训练。这最大限度地减少了从零开始训练网络的努力，并在不仅考虑新场景还考虑初始训练阶段的修改情况时，实现了动态的情感识别。正如论文所示，迁移学习和底层方法提供了情感检测在复杂情感识别过程中的相关性。

文献 [25] 的作者提出了一种航空领域的情感识别方法，旨在填补飞行员在飞行程序（如起飞、爬升、下降、进场和着陆）期间的情绪及其反应的空白。围绕传感架构和一系列模拟实验，该研究表明可以在各种环境中识别不同飞行员的情绪。

正如我们在引言中提到的，辅助技术是一个充满许多挑战的研究领域。其中一些挑战出现在本特刊中，我们将鼓励更多研究。其他领域尚未被涵盖，为在该领域发现新想法留下了空间。

作者贡献：K.K：总体协调。所有作者均已阅读并同意发表的手稿。

资助：本研究未收到任何资助。

利益冲突：作者声明无冲突。

## 参考文献

| 1 | Elshour, D. et al. | Uncovering the Potential of GSR for Stress Monitoring | Sensors, 2020, 2082. |
|---|---|---|---|
| 2 | Can, Y. et al. | A Comparison of Machine Learning Methods for Daily Life | Sensors, 2020, 838 |
| 3 | Siola, P. et al. | Evaluation of EEG Methods for Emotion Recognition | Sensors, 2020, 4402 |
| 4 | Saeed, M. et al. | Systematic Analysis of EEG Features for Stress Detection | Sensors, 2020, 1886 |
| 5 | Thiam, P. et al. | Deep Learning-Based Classification for Stress Detection | Sensors, 2019, 5561 |
| 6 | Gault, C. et al. | A Multimodal Approach for Acute Stress Detection | Sensors, 2019, 2999 |
| 7 | Joni, J. et al. | Deep Learning for Emotion Recognition in VR | Sensors, 2019, 4723 |
| 8 | Thiam, P. et al. | Two-Stream Attention Network for Pain Recognition | Sensors, 2020, 839 |
| 9 | Chin, Y. et al. | Dilated Skip Convolution for Facial Landmark Detection | Sensors, 2019, 5350 |
| 10 | Gault, C. et al. | Visual and Thermal Image Processing for Facial Landmark Detection | Sensors, 2019, 2841 |
| 11 | Mahi, M.I.H.H. | Recognition of Emotion Intents Using Machine Learning Algorithms | Sensors, 2019, 1887 |
| 12 | Franzoni, V. et al. | Enhancing Mouth-Bouth Emotion Recognition Using Transfer Learning | Sensors, 2020, 5222 |

