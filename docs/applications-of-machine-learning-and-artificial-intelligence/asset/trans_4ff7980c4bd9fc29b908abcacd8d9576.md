

# 交叉验证中的 Scikit-learn 与 SciPy

Scikit-learn 是用于计算交叉验证的工具，而 SciPy 是用于处理数据集的 Python 库。此处我将 `k` 取为 10，意味着 `k-1` 个图像子集（即 9 部分图像）将用于训练数据，1 部分图像用于测试数据。

# 系统实现

在该系统中，我使用摄像头作为输入，实时视频中检测到人脸后，逐帧作为输入传递给 CNN 模型。图像帧在传递给 CNN 模型前会进行预处理，如人脸裁剪、调整大小至 48x48 并转换为灰度图像。CNN 通过提取特征处理人脸图像，随后将情绪分类为消极或积极情绪。

# 系统输出与分析

系统输出如图 14 所示，当检测到悲伤或愤怒等消极情绪时，会自动播放音乐将其转变为快乐等积极情绪，并附带情绪直方图。x 轴显示图像的像素数，y 轴显示情绪的强度级别。

图 14、15、16 和 17 绘制了悲伤、快乐、愤怒和中性情绪的柱状图，由此我们可以测量播放音乐前后情绪的强度级别。x 轴为情绪类别，y 轴为百分比。

## 图 14. 播放音乐前检测到悲伤人脸 & 悲伤情绪直方图图形化绘制

![Figure978-1-7998-7776-9.ch003.f14](i/ch003.f14.png)

在图 15 中，播放音乐后悲伤情绪转变为快乐，音乐自动停止，并绘制了直方图。

## 图 15. 播放音乐后的快乐人脸 & 快乐人脸直方图图形化绘制

![Figure978-1-7998-7776-9.ch003.f15](i/ch003.f15.png)

## 图 16. 播放音乐前的愤怒人脸 & 愤怒人脸直方图图形化绘制

![Figure978-1-7998-7776-9.ch003.f16](i/ch003.f16.png)

在图 16 中，人物处于愤怒状态，该状态由 CNN 检测到，并绘制了愤怒情绪的直方图。

## 图 17. 播放音乐后的中性人脸 & 中性人脸直方图图形化绘制

![Figure978-1-7998-7776-9.ch003.f17](i/ch003.f17.png)

在图 17 中，人物处于中性状态，该状态由 CNN 检测到，并绘制了中性情绪的直方图。

## 图 18. 显示模型准确率与错误率

![Figure978-1-7998-7776-9.ch003.f18](i/ch003.f18.png)

在图 18 中，左侧显示了在核大小为 3x3 的情况下，模型在测试数据和训练数据上的准确率。X 轴显示轮次，Y 轴显示准确率，随着轮次增加，训练数据的模型准确率也随之增加。图 18 右侧显示了模型的错误率，表明模型预测的正确程度。X 轴显示轮次，Y 轴显示损失率，随着轮次减少，模型数据的损失增加。

## 图 19. 显示 CNN 模型中的混淆矩阵

![Figure978-1-7998-7776-9.ch003.f19](i/ch003.f19.png)

图 19 揭示了 CNN 模型中图像的混淆矩阵，通过比较实际模型与预测模型，提供了关于模型在训练数据后检测情绪准确性的信息。

混淆矩阵由一个表格组成，用于描述分类模型在已知真实值的测试数据集上的性能。

## 图 20. 情绪的人工预测与神经网络预测

![Figure978-1-7998-7776-9.ch003.f20](i/ch003.f20.png)

图 20 对应表 1，显示了情绪的人工预测与神经网络预测。它展示了 CNN 在图像上的准确率。不同情绪下 CNN 的百分比如上所示，使用了图 20 中展示的混淆矩阵。

计算 CNN 预测值的公式如下，

![Mathtype978-1-7998-7776-9.ch003.m03](i/ch003.m03.svg)

# 结论

在本章中，卷积神经网络通过检查一个人的面部表情来识别人脸情绪。人脸特征（眼睛、嘴巴、鼻子）将被卷积神经网络检测并处理。如果检测到的情绪为消极情绪（如悲伤和愤怒），则会自动播放音乐，将一个人的情绪转变为积极情绪（如快乐和中性）。一旦检测到积极情绪，音乐将自动停止。CNN 易于实现且训练速度快。它在测试数据上具有良好的准确率。用于训练 CNN 的数据集是 FER-2013。CNN 通过各层进行图像处理的过程已逐步展示。本章还包含用于处理和分类图像的 CNN 架构算法和代码片段。本章展示了音乐如何通过释放多巴胺等有益激素来影响人的情绪。聆听音乐有许多健康益处，如降低血压、缓解疼痛。本章的应用包括：可用作心理治疗以治疗抑郁症、焦虑管理、愤怒管理、阿尔茨海默病患者的记忆保持、癌症患者的疼痛管理。本章绘制了积极和消极情绪的直方图，并针对不同性能指标绘制了图表。

本章解释的概念未来可结合人脑信号实现，脑信号可通过脑电图 (EEG) 连同面部表情一起测量。音乐将根据脑信号变化播放，以检测情绪。

# 参考文献

Deng, J. J. L. (2012). Music Emotion Retrieval Based on Acoustic Features . In Hu, W. (Ed.), Advances in Electric and Electronics. Lecture Notes in Electrical Engineering (Vol. 155). Springer. doi:10.1007/978-3-642-28744-2\_22

Jain, D., Shamsolmoali, P., & Sehdev, P. (2019). Extended deep neural network for facial emotion recognition. Pattern Recognition Letters , 120, 69–74. doi:10.1016/j.patrec.2019.01.008

Jing, H. (2015). Cognitive emotion model for eldercare robot in smart home. China Communications, 12(4), 32-41. doi:10.1109/CC.2015.7114067

Kuo, P., Li, T.-H. S., Ho, Y.-F., & Lin, C.-J. (2015). Development of an automatic emotional music accompaniment system by fuzzy logic and adaptive partition evolutionary genetic algorithm. IEEE Access: Practical Innovations, Open Solutions , 3, 815–824. doi:10.1109/ACCESS.2015.2443985

L., L., & F., V. (2014). Facial Expression Recognition from Webcam Based on Active Shape Models and Support Vector Machines. In Ambient Assisted Living and Daily Activities. IWAAL. Lecture Notes in Computer Science, vol 8868. Springer.

Li, Y. (2013). Simultaneous Facial Feature Tracking and Facial Expression Recognition. IEEE Transactions on Image Processing, 22(7), 2559-2573. doi:10.1109/TIP.2013.2253477

Mayank Mishra. (2020, August 26). Convolutional Neural Network, Explained. https://towardsdatascience.com/convolutional-neural-networks-explained-9cc5188c4939

Mishra, A. P. (2017, August 21). Introduction to Convolution Neural Network. Retrieved from https://www.geeksforgeeks.org/introduction-convolution-neural-network/

P., Z. H. (2015). Recognize Emotions from Facial Expressions Using a SVM and Neural Network Schema. In Engineering Applications of Neural Networks. EANN. Communications in Computer and Information Science, vol 517. Springer.

Piątkowska, E. M. (2012). Computer Recognition of Facial Expressions of Emotion . In Perner, P. (Ed.), Lecture Notes in Computer Science: Vol. 7376. Machine Learning and Data Mining in Pattern Recognition. MLDM . Springer. doi:10.1007/978-3-642-31537-4\_32

Sarkar, R. D. (2018). Emotion Based Categorization of Music Using Low Level Features and Agglomerative Clustering. In Computer Vision, Pattern Recognition, Image Processing, and Graphics. NCVPRIPG. Communications in Computer and Information Science, vol 841. Springer.

Sourina, O. (2012). Real-time EEG-based emotion recognition for music therapy. Journal on Multimodal User Interfaces, 5(1-2), 27-35.

# 第 4 章

