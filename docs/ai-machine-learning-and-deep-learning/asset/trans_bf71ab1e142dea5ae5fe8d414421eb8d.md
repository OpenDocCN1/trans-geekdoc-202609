
100. L. Yang, Y. E. Sagduyu, J. Zhang, and J. Li, “面向截止时间的自适应网络编码实时流量调度,” IEEE Transactions on Networking, Oct. 2015.

101. S. Kaul, R. Yates, and M. Gruteser, “实时状态：更新频率应为多少？”, IEEE INFOCOM, 2012.

102. M. Costa, Y. E. Sagduyu, T. Erpek, and M. Medard, “通过自适应分组编码稳健提升信息新鲜度,” IEEE International Conference on Communications (ICC), 2021.

103. E. T. Ceran, D. Gunduz and A. Gyurgyik, “多用户网络中信息新鲜度的强化学习方法,” IEEE International Symposium on Personal, Indoor and Mobile Radio Communications (PIMRC), 2018.

104. L. Li, K. Jamieson, G. DeSalvo, A. Rostamizadeh, and A. Talwalkar, “Hyperband：一种新颖的基于赌博机的超参数优化方法,” Journal of Machine Learning Research, 2018.

105. S. Schmidt, J. Stankowicz, J. Carmack, and S. Kuzdeba. “RiftNeXt™：可解释的深度神经射频场景分类。” In Proceedings of the 3rd ACM Workshop on Wireless Security and Machine Learning, pp. 79–84. 2021.

106. J. Kirkpatrick, R. Pascanu, N. Rabinowitz, J. Veness, G. Desjardins, A. A. Rusu, K. Milan, J. Quan, T. Ramalho, A. Grabska-Barwinska, D. Hassabis, C. Clopath, D. Kumaran, R. Hadsell, “克服神经网络中的灾难性遗忘,” arXiv preprint, arXiv:1612.00796, 2016.

107. Y. Shi, K. Davaslioglu, Y. E. Sagduyu, W. C. Headley, M. Fowler, and G. Green, “未知和动态频谱环境中的信号分类深度学习,” IEEE International Symposium on Dynamic Spectrum Access Networks (DySPAN), 2019.

108. K. Davaslioglu, S. Soltani, T. Erpek, and Y. E. Sagduyu, “DeepWiFi：基于深度学习的认知WiFi,” IEEE Transactions on Mobile Computing, 2019.

109. S. Gecgel, C. Goztepe, and G. Kurt, “基于人工神经网络的干扰检测：一次测量研究,” ACM Workshop on Wireless Security and Machine Learning (WiseML), 2019.

110. N. Soltani, K. Sankhe, S. Ioannidis, D. Jaisinghani, and K. Chowdhury, “边缘频谱感知：使用智能手机的调制分类,” IEEE International Symposium on Dynamic Spectrum Access Networks (DySPAN), 2019.

111. J.-H. Luo, J. Wu, and W. Lin, “ThiNet：深度神经网络压缩的滤波器级剪枝方法,” IEEE International Conference on Computer Vision (ICCV), 2017.

112. Y. Xu, Y. Wang, A. Zhou, W. Lin, and H. Xiong, “单级和多级量化下的深度神经网络压缩,” AAAI Conference on Artificial Intelligence, 2018.

113. S. Soltani, Y. E. Sagduyu, R. Hasan, K. Davaslioglu, H. Deng, and T. Erpek, “用于射频信号分类的 FPGA 实时嵌入式深度学习,” IEEE Military Communications Conference (MILCOM), 2019.

114. S. Soltani, Y. E. Sagduyu, R. Hasan, K. Davaslioglu, H. Deng, and T. Erpek, “FPGA 上基于深度学习的射频信号分类器的实时实验,” IEEE International Symposium on Dynamic Spectrum Access Networks (DySPAN), 2019.

115. Y. Li, J. Bradshaw, and Y. Sharma, “生成式分类器是否对对抗攻击更鲁棒？”, International Conference on Machine Learning, in Proceedings of Machine Learning Research, 2019.

Linsheng He¹ and Fei Hu¹

电气与计算机工程，阿拉巴马大学，美国

DOI: [10.1201/9781003187158-4](https://doi.org/10.1201/9781003187158-4)

## 目录

- 3.1 引言
- 3.2 攻击分类
  - 3.2.1 白盒攻击
  - 3.2.2 黑盒攻击
- 3.3 攻击概述
  - 3.3.1 对基于计算机视觉应用的攻击
  - 3.3.2 对自然语言处理应用的攻击
  - 3.3.3 对数据投毒应用的攻击
- 3.4 现实世界中的具体攻击
  - 3.4.1 对自然语言处理的攻击
  - 3.4.2 利用数据投毒的攻击
- 3.5 讨论与开放问题
- 3.6 结论
- 参考文献

## 3.1 引言

机器学习是一门交叉学科，主要研究如何使计算机更好地模拟和实现人类学习行为，以实现知识的自动获取和生成。深度学习（DL）神经网络 [1] 是一种典型的机器学习模型，它试图模仿人类大脑的生物神经网络，从示例中学习和积累知识。DL 模型的结构由一系列神经元层组成，每个神经元层都作为一个独立的计算单元。神经元通过具有不同权重和偏置的连接相连，并将激活函数的计算结果从其输入传递到下一层的神经元。因此，它们在处理难以简单建模为线性或非线性问题的复杂任务时具有优势。此外，得益于连续实值向量表示（即嵌入），它们擅长以多种方式处理图像、文本、视频和音频等数据。

经过十多年的快速发展，研究人员主要创建了经典的 DL 模型，如卷积神经网络（CNN）、循环神经网络（RNN）和生成对抗网络（GAN）。CNN [2] 包含卷积层、池化（下采样）层，最后是一个全连接层。激活函数用于连接下采样层到下一个卷积层或全连接层。CNNs 应用广泛，可被视为 DL 领域的核心模型，许多 DL 模型都是基于 CNNs 的结构构建的，可对类图像数据进行分类、分割和回归。RNNs 是从前馈神经网络改编而来的神经模型，用于学习序列输入和输出之间的映射 [3]。RNNs 允许数据具有任意长度，并在其计算图中引入循环，以有效建模时间的影响 [1]。RNNs 有许多变体，其中最流行的是长短期记忆（LSTM）网络 [4]。LSTM 是一种专门设计用于捕捉长期依赖关系的 RNN 类型。RNNs 可应用于与时间序列相关的数据，例如预测下一时刻的数据流和发展趋势。GANs [5] 已被提出并获得了大量研究关注。生成模型能够在潜在空间中生成与真实数据相似的真实数据。它由两个对抗网络组成：生成器和判别器。判别器可以区分真实样本和生成样本，而生成器则生成旨在欺骗判别器的真实样本。GAN 模型是一种经典的无监督 DL 模型，其主要用途包括高精度生成数据、无标签解决现实问题等。

DL 在过去机器学习和人工智能领域经多次尝试仍难以解决的问题上取得了突破，例如图像分类、自然语言识别、游戏、面部识别、垃圾邮件过滤、恶意软件检测和自动驾驶等安全敏感应用。因此，DL 系统已成为许多 AI 应用的关键，并吸引对手进行攻击。

典型的攻击是对目标机器学习模型的原始输入施加轻微扰动，以生成对抗样本来欺骗目标模型（也称为受害者模型）。早期研究主要集中于传统机器学习应用中的对抗样本，例如垃圾邮件过滤器、入侵检测、生物特征认证和欺诈检测 [6]。Biggio 等人 [7] 首先提出了基于梯度的方法来为线性分类器、SVM 和神经网络生成对抗示例。Barreno 等人 [6,8] 对机器学习的安全问题进行了初步研究。

尽管 DL 在许多任务中表现良好，对抗攻击可以暴露机器学习模型的漏洞，而对攻击的分析可以有效提高 DL 模型的鲁棒性和可解释性。Szegedy 等人 [9] 首次发现深度神经网络在图像分类领域存在弱点。他们证明，尽管准确率很高，现代深度网络对对抗示例非常脆弱。这些对抗样本对原始像素只有轻微扰动，人类视觉系统无法检测到这种扰动（即图像几乎看起来相同）。这种攻击导致神经网络完全改变其对图像的预测或分类结果。此外，这一现象的深远意义吸引了 DL 安全领域众多研究人员的关注。

在下一节中，我们将讨论更多对抗攻击模型及其针对不同 DL 算法及其应用场景的特殊性。

## 3.2 攻击分类
