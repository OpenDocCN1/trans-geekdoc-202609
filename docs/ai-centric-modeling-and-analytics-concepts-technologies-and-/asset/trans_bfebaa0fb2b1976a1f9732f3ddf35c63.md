
![](img/66ecdb8eb8654ae1c99705e55a45a836_133_0.png)

## FIGURE 6.8 多层感知器

来源：Khang (2021)

简单来说，卷积是一种应用于矩阵的滑动窗口函数，其中该矩阵的每个元素精确地代表图像的一个像素，而滑动窗口被称为滤波器、特征检测器或核（Anuj Kumar & Khang, 2023）。

近年来，CNN 已被应用于模糊的 NLP 领域（Liao & Zhou, 2021; Peng & Han, 2021）。在图像处理的情况下，该输入矩阵可以方便地被表示句子或文档的矩阵所替代；每一行对应一个词元。

与图像处理不同，图像处理中核在图像的局部 patch 上滑动，而在 NLP 情况下，核在矩阵的整行上滑动，从而在 NLP 应用中将滤波器宽度固定为矩阵的宽度。

图 6.9 给出了文本分类 CNN 架构的详细可视化。识别出两个滤波器，具有三种区域大小：2、3 和 4。

卷积的结果生成了特征图。这些特征图经过池化处理，池化是一种降维步骤，并生成六个单变量特征向量。这些向量进一步连接成一个特征向量，作为输入馈送到最终的 Softmax 层以对文本进行分类，如图 6.9 所示。

假设二分类，在输出层获得两种可能的输出状态或类别。

由于神经网络的高计算需求，针对计算机视觉和 NLP 领域也发展出了一种新颖的神经架构搜索基准概念，该概念具有预先计算的神经架构（Klyuchnikov et al., 2022）。

![](img/66ecdb8eb8654ae1c99705e55a45a836_134_0.png)

## FIGURE 6.9 卷积神经网络

### 6.8.3 循环神经网络

循环神经网络（RNNs）是一类人工神经网络（ANN），在自然语言处理、语音识别、语言翻译等领域被广泛利用。

以序列和时间序列数据为基础，RNN 是时间性和顺序性应用（如 NLP）的合适选择。

与信息流单向的 CNN 不同，RNN 包含反馈回路，例如通过时间反向传播（BPTT），以确保信息不断供应。这些双向循环神经网络（BRNNs）基于前向投影预测未来，并基于后向投影评估过去（Rana et al., 2021）。

为了在 RNN 中促进强化学习，特定层固定的权重在反向传播和梯度下降过程中不断调整；梯度是损失函数的斜率。

由于 RNN 的工作方式，参数在各层之间共享，BPTT 在每个时间步累加误差。社交媒体平台上地理标记的当前趋势导致使用 RNN 进行位置特定情感分析（Qi et al., 2019）。

机器翻译、医学文本解释（Mugisha & Paik, 2021）、音乐生成和情感分类等丰富多样的应用都可以用不同类型的 RNN 来解决。除了 BRNN 之外，另一种流行的 RNN 架构是长短期记忆（LSTM）。

该 RNN 架构解决了在复杂数据集的深层网络中常见的梯度消失问题。LSTM 网络解决了 RNN 变得更大、更复杂时遇到的问题，尤其是基于梯度学习方法的那种（Khang et al., 2023a）。

长短期记忆在关键的 NLP 问题中发挥了关键作用，例如与基于语言的应用相关的隐私和安全问题（Feng et al., 2020）。它们与物联网平台很好地集成，以解决安全和隐私违规问题（Breve et al., 2022）。

基于长短期记忆的 RNN 本质上根据短期和长期记忆对数据进行分离，这意味着 LSTM 在隐藏层中具有三个门，即输入门、输出门和遗忘门，控制所需的信息流以进行预测（Liang & Zhang, 2021）。

通过使用 RNN，LSTM 在虚假新闻检测中实现了高达 0.94 的精度。此外，客户评论的情感分析是商业决策的另一个流行应用（Houssein et al., 2021; Jain et al., 2022）。

## 6.9 结论

区块链与 NLP 的整合是一个新兴趋势，正引起 NLP 社区的兴趣（Shahbazi & Byun, 2021）。区块链技术与 NLP 的整合可以带来安全透明的数据共享、去中心化应用和新商业模式的新机遇（Khang & Khang, 2021）。

以下是区块链整合可能对 NLP 有益的一些潜在未来趋势：

- **安全数据共享：**区块链技术的主要好处之一是能够安全地存储和共享数据。在 NLP 的背景下，这可用于安全地存储和共享敏感数据，例如医疗记录或财务数据（Khang et al., 2024）。

- **去中心化应用：**区块链技术可以促进去中心化 NLP 应用的开发，这些应用更能抵抗审查，并提供更透明的用户体验。

- **数据使用透明度：**借助区块链技术，数据所有权和使用情况可以变得更加透明。这对希望了解其数据如何被使用的用户有益，也有助于研究人员获取更多数据用于研究。

- **智能合约：**智能合约可用于在 NLP 背景下自动执行和强制执行数据共享协议的条款。这可以确保数据仅用于商定的目的，并有助于防止滥用。

- **基于代币的激励：**区块链代币可用于激励数据共享和参与 NLP 任务。这有助于创建新的商业模式并为用户共享数据提供激励。

- **欺诈检测：**区块链技术可用于检测 NLP 任务中的欺诈，例如情感分析或虚假新闻检测。通过验证数据的来源和准确性，区块链可以帮助防止恶意行为者操纵 NLP 任务的结果。

总体而言，区块链技术与 NLP 的整合有可能创造安全透明的数据共享、去中心化应用和新商业模式的新机遇。尽管仍处于早期阶段，区块链与 NLP 的整合是一个令人兴奋的研究领域，很可能会带来该领域的创新。

# 参考文献

Ahmed H. A., Bawany N. Z., Shamsi J. A., (2021). “CaPBug——一种用于自动错误分类和优先级排序的框架，使用 NLP 和机器学习算法，” IEEE Access, 9, 50496–50512. https://doi.org/10.1109/ACCESS.2021.3069248

Alawad M., et al., (2021). “用于癌症登记的隐私保护深度学习 NLP 模型，” IEEE Transactions on Emerging Topics in Computing, 9(3), 1219–1230, 2021. https://doi.org/10.1109/TETC.2020.2983404

Anuj Kumar G., Khang A., (2023). AI-Aided IoT Technologies and Applications in the Smart Business and Production, 使用物联网（IoT）实现智能车辆停车系统, p. 8. CRC Press. https://doi.org/10.1201/9781003392224-8

Bose P., Roy S., Ghosh P., (2021). “关于 COVID-19 研究当前趋势和未来方向的比较 NLP 研究，” IEEE Access, 9, 78341–78355. https://doi.org/10.1109/ACCESS.2021.3082108

Breve B., Cimino G., Deufemia V., (2022). “使用 NLP 模型识别触发-动作物联网平台中的安全和隐私违规规则，” IEEE Internet of Things Journal. https://doi.org/10.1109/JIOT.2022.3222615

Bunyamin M. A. F., Pudjiantoro T. H., Renaldi F., Hadiana A. I., (2022). “使用朴素贝叶斯和情感评分组合分析印度尼西亚新国家宫殿的情感，” In 2022 International Conference on Science and Technology, ICOSTECH 2022. Institute of Electrical and Electronics Engineers Inc. https://doi.org/10.1109/ICOSTECH54296.2022.9829075

Chitty-Venkata K. T., Emani M., Vishwanath V., Somani A. K., (2022). “用于 Transformer 的神经架构搜索：综述，” IEEE Access, 10, 108374–108412. https://doi.org/10.1109/ACCESS.2022.3212767

Dalian, Institute of Electrical and Electronics Engineers, IPEC 2020: proceedings of 2020 Asia-Pacific Conference on Image Processing, Electronics and Computers: China, April 14–16, 2020. https://doi.org/10.1201/9781003145011

Elnagar A., Yagi S. M., Nassif A. B., Shahin I., Salloun S. A., (2021). “方言阿拉伯语的系统文献综述：识别与检测，” IEEE Access, 9, 31010–31042 (Institute of Electrical and Electronics Engineers Inc.). https://doi.org/10.1109/ACCESS.2021.3059504

Feng Q., He D., Liu Z., Wang H., Choo K. K. R., (2020). “SecureNLP：多方隐私保护自然语言处理系统，” IEEE Transactions on Information Forensics and Security, 15, 3709–3721. https://doi.org/10.1109/TIFS.2020.2997134
