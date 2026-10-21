
![](img/fe161b7f6e96e35e7e853eece52c6dce_258_0.png)

图 6.14 用于人脸识别特定面部部位的拟议 CNN 模型架构。该模型源自标准 VGG-16。

类似任务。这是通过替换原本训练用于识别先前类别的输出层，以能够识别新任务中新数量类别的输出层来实现的。使用微调的一个优点是在训练阶段减少计算时间。事实上，第一层已经具备处理新任务的能力，训练将利用最后几层，而无需从头开始训练。另一个优点是性能得到改善，因为预训练模型通常是在大型数据集上训练的。

### 6.5.1 模型的建议架构

如上所述，用于特定面部部位训练的拟议模型受 VGG-16 模型启发（Parkhi et al., 2015）并需要具有预设尺寸（224, 224, 3）的输入图像。该模型有 5 个卷积块，每个块包含若干个卷积层，后接非线性激活函数，如图 6.14 所示。

正如 Fig. 6.14 所推断的那样，用于部分人脸的拟议 CNN 模型在架构上与具有 5 个卷积层和 3 个 FC 层的 VGG-F 模型相似。这些卷积层设计为集成各种最大池化层以创建高效的特征图。拟议的卷积层和 FC 层的排列的一个关键方面是减少可训练参数的数量（按公式（6.1）定义），以保持训练时间长度合理，同时保持网络精度在可接受的范围内。

### 6.5.2 训练阶段

训练 CNN 模型是为了最小化训练数据集中真实标签与预测输出之间的差异。这是通过在卷积和全连接层中定位可学习参数（核和权重）来实现的。在此建议的模型中，滤波器的权重通过使用高斯分布和标准差进行初始化（Bishop, 2006），而偏置初始化为零。为了通过前向传播评估模型的性能，可以使用多类分类问题中最常见的损失函数，即交叉熵函数（Busoniu et al., 2011）。损失函数的值标识模型在每次优化迭代后的表现好坏。此外，基于模型当前状态的误差梯度，所有可学习参数将在优化过程中更新，例如使用梯度下降和反向传播。学习率是另一个超参数，其作用是控制 CNN 模型使用提供给它的数据学习的速度。该参数的值为正且范围在 0 到 1 之间。

模型中最后两个超参数表示模型必须经过的 epoch 数量——这表示学习方法看到训练数据集的次数。它还表示完成一个 epoch 所需的批大小——建议的批大小为 64。至于实际训练，遵循两阶段过程是有用的。在第一阶段，模型使用大约 20 个 epoch 和批大小 64 进行训练。之后，将模型的结果权重保存下来。这些权重随后用于初始化第二部分训练的权重。在第二阶段，进行大约 50 个 epoch 的训练。这些 epoch 被分为十个部分，每个部分 5 个 epoch。因此，使用之前的训练权重来初始化新权重并训练模型五个 epoch。得到的新权重将用于下一次训练运行。此过程一直持续到达到选定的训练损失和验证标准。在此过程中，应以较小的训练损失（即大约 < 0.02）和较高的验证准确率（即 > 85%）为目标。

就训练数据而言，必须有足够的人脸图像和足够的身份。建议的典型数字是对应于人脸特定部位的 70,000 张图像，包含 200 个身份。这样的数据集可以分为两组，即 70% 用于训练和 30% 用于验证。最后，使用训练集训练模型，并通过前向传播计算损失，同时通过反向传播更新可学习参数。

## 6.6 讨论与结论

在本章中，我们广泛讨论了使用深度学习方法和技术进行人脸识别的最新技术现状。我们展示了如何利用深度学习方法进行身份和面部相似性匹配——使用完整正面人脸和部分面部数据。我们展示了如何从训练良好的深度学习模型中利用现成特征来高效构建准确的人脸识别系统。我们还展示了如何基于各种模型架构、可训练层和权重，从用于图像处理和分析的知名深度模型中训练特定模型。

例如，我们探讨了使用面部特征进行人脸识别的想法所围绕的问题。我们通过展示关键示例来测试机器学习在识别任务中使用完整人脸和人脸部分时的性能。特别是，我们展示了当眼睛、嘴巴、鼻子和脸颊等部位作为学习和识别线索呈现时，深度人脸识别的表现。我们还表明人脸识别系统可以遵循多种方法。例如，我们展示了如何实现最先进的 CNN 以及预训练模型（如 VGG-F），通过这些模型可以提取关键面部特征。然后可以利用众所周知的分类器，如余弦相似度度量和线性支持向量机来测试识别率。同样，考虑到面部特定部位如嘴巴、鼻子、眼睛、额头及其组合来设计从部分人脸进行高效人脸识别系统的特定模型训练也可以应用。

很明显，随着深度学习方法和技术的进步，人脸识别得到了极大的受益（Guo and Zhang, 2019）。从这个意义上说，许多以前认为无法解决的问题现在被认为是直接的。例如，给定一个个体的两张光线良好的正面照片，使用深度面部特征确认它们之间的身份匹配，现在被认为是一个已解决的问题。然而，总的来说，人脸识别仍然是一个当前问题，存在许多具有挑战性和未解决的问题。例如，使用部分面部数据作为探针的计算机化人脸识别问题仍然是一个 largely 未探索的领域，存在关键的研究挑战。鉴于人类和计算机进行人脸识别和身份验证的方式本质上不同，了解计算机在人脸识别挑战中呈现各种面部部位时会如何反应是令人 intrigued 的。

计算机辅助人脸识别从 1960 年代开始，已经走过了很长的路。然而，仍有许多挑战和障碍需要克服。这些挑战包括，例如，在不良照明、姿势变化、部分人脸、倒置人脸、老化人脸和远距离人脸中识别人脸。使用深度学习技术进行面部相似性测量的准确性问题在很大程度上仍未得到解答。例如，通过亲缘关系、兄弟姐妹和同卵双胞胎相关的人脸之间的相似性问题尚未得到令人满意的解答。此外，训练数据中的偏差问题以及深度学习系统应如何变得透明和可解释也是迫切需要令人满意解答的问题。

## 参考文献

- Bishop, C.M., 2006. Pattern Recognition and Machine Learning. Springer, Berlin.
- Busoniu, L., Ernst, D., De Schutter, B., Babuska, R., 2011. Cross-entropy optimization of control policies with adaptive basis functions. IEEE Transactions on Systems, Man, and Cybernetics, Part B 41 (1), 196–209.
- Chatfield, K., Simonyan, K., Vedaldi, A., Zisserman, A., 2016. Return of the devil in the details: delving deep into convolutional nets. In: Proceedings of the British Machine Vision Conference (BMVC).
- Day, O., Khoshgoftaar, T.M., 2017. A survey on heterogeneous transfer learning. Journal of Big Data 4 (1).
- Dora, L., Agrawal, S., Panda, R., Abraham, A., 2017. An evolutionary single Gabor kernel based filter approach to face recognition. Engineering Applications of Artificial Intelligence 62, 286–301.
- Dumoulin, V., Visin, F., 2018. A guide to convolution arithmetic for deep learning. arXiv:1603.07285v2.
- Elmahmudi, A., Ugail, H., 2019a. The biharmonic eigenface. Signal, Image and Video Processing 3, 1639–1647.
- Elmahmudi, A., Ugail, H., 2019b. Deep face recognition using imperfect facial data. Future Generation Computer Systems 41 (99), 213–225.
- Gholamalinezhad, H., Khosravi, H., 2020. Pooling methods in deep neural networks, a review. arXiv:2009.07485.
- Guo, G., Zhang, N., 2019. A survey on deep learning based face recognition. Computer Vision and Image Understanding 189, 102905.
- He, K., Zhang, X., Ren, S., Sun, J., 2015. Deep residual learning for image recognition. In: Proceedings of the British Machine Vision Conference (BMVC).
- He, L., Li, H., Zhang, Q., Sun, Z., 2018. Dynamic feature learning for partial face recognition. In: 2018 IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 7054–7063.
