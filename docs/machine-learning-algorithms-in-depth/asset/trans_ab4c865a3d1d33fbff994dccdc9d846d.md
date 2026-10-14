
```
plt.plot(hist.history['accuracy'], 'b', lw=2.0, label='train')
plt.plot(hist.history['val_accuracy'], '--r', lw=2.0, label='val')
plt.title('GNN model')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend(loc='upper left')
plt.show()
```

图 11.13 显示了训练集和验证数据集的分类损失和准确率。

![](img/325742126d3ff007c6c385f4ffb5c3be_298_0.png)

图 11.13 用于训练和验证数据集的 GNN 模型损失和准确率

图 11.14 显示了经过第一个 GCN 层后 CORA 数据集嵌入的 t-SNE 隐藏层表示。

![](img/325742126d3ff007c6c385f4ffb5c3be_298_1.png)

图 11.14 经过第一个 GCN 层后 CORA 数据集嵌入的 t-SNE 隐藏层表示

在以下章节中，我们将回顾计算机视觉和自然语言处理领域的深度学习研究。

## 11.5 ML 研究：深度学习

在计算机视觉（CV）领域，CNN 架构已从 LeNet 的卷积、ReLU 和最大池化操作（Yann LeCun et al.’s “Gradient-Based Learning Applied to Document Recognition,” In Proceedings of the IEEE, 1998）演进到 GoogLeNet 的 inception 模块（Christian Szegedy et al.’s “Going Deeper with Convolutions,” *计算机视觉与模式识别*, 2015）。inception 模块通过采用不同大小的卷积核创建可变感受野。反过来，这使得能够捕捉新特征图堆栈中的稀疏相关模式。GoogLeNet 在 ImageNet 数据集上提供了高准确率，其参数比 AlexNet（Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton’s “ImageNet Classification with Deep Convolutional Neural Networks,” Conference on Neural Information Processing Systems, 2012）或 VGG（Karen Simonyan and Andrew Zisserman’s “Very Deep Convolutional Networks for Large-Scale Image Recognition,” International Conference on Learning Representations, 2015）更少。我们看到了 ResNet 模型中残差连接的引入（Kaiming He et al.’s “Deep Residual Learning for Image Recognition,” Conference on Computer Vision and Pattern Recognition, 2015），它已成为任意深度现代神经网络的标准架构选择。快进到视觉 Transformer（ViT）模型（Alexey Dosovitskiy et al.’s “An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale,” International Conference on Learning Representations, 2021）采用了对图像块的类 Transformer 架构。图像被划分为固定大小的块，每个块都进行线性和位置嵌入，得到的向量序列被输入到标准 Transformer 编码器，然后接一个 MLP 头用于分类。

在生成模型领域，生成对抗网络（GANs），由 Ian Goodfellow et al 在 “Generative Adversarial Networks”（Conference and Workshop on Neural Information Processing Systems, 2014）中提出，借鉴了博弈论的思想并使用两个网络训练以近似数据分布：一个生成器用于生成图像，一个判别器用于区分真实图像和伪造图像。另一方面，基于似然的生成模型使用似然函数对数据的分布进行建模。基于似然的生成模型中最受欢迎的子类是变分自编码器（VAE），由 Diederik P. Kingma 和 Max Welling 在 “Auto-Encoding Variational Bayes”（International Conference on Learning Representations, 2014）中提出。VAE 由一个将数据作为输入并将其转换为潜在表示的编码器，以及一个接收潜在表示并返回重构的解码器组成。beta-VAE 是 VAE 的一种修改，特别强调发现解耦的潜在因子（Irina Higgins et al.’s “beta-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework,” International Conference on Learning Representations, 2017）。

将焦点转向扩散模型，它们因能够生成高分辨率图像而变得流行，是使用变分推断训练的参数化马尔可夫链，用于产生与输入数据匹配的样本。扩散模型包括前向过程，其中图像通过添加高斯噪声逐渐变得更嘈杂，以及反向过程，其中噪声被转换回目标分布的样本（Jonathan Ho, Ajay Jain, and Pieter Abbeel’s “Denoising Diffusion Probabilistic Models,” Conference and Workshop on Neural Information Processing Systems, 2020）。

在自然语言处理（NLP）领域，例如机器翻译的架构，已从 Seq2Seq LSTM 模型演进到基于 Transformer 的模型，如 BERT（Jacob Devlin et al.’s “BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding,” North American Chapter of the Association for Computational Linguistics, 2019）。预训练的 BERT 模型只需一个额外的输出层即可微调，从而为广泛的任务，如问答和语言推理，创建最先进的模型，而无需实质性的任务特定架构修改。零样本和少样本学习随着大型 Transformer 模型而流行，例如 GPT-3，由 Tom B. Brown et al. 在 “Language Models are Few-Shot Learners”（Conference and Workshop on Neural Information Processing Systems, 2020）中提出。GPT-3 的应用范围从文本补全到代码补全。例如，OpenAI 的 codex 模型是 GPT-3 系列的后代，在自然语言以及数十亿行代码上训练，充当 AI 结对程序员，可以将注释转换为代码并在上下文中补全下一行或函数。

许多学习任务需要处理包含丰富关系信息的图数据，从建模社交网络到预测蛋白质结构都需要一种能够处理图数据的模型。图神经网络（GNNs）是通过图节点之间的消息传递来捕捉依赖关系的神经模型（Thomas N. Kipf and Max Welling’s “Semi-Supervised Classification with Graph Convolutional Networks,” International Conference on Learning Representations, 2017）。近年来，GNN 的变体，如图卷积网络（GCNs）、图注意力网络（GATs）和图循环网络（GRNs），在许多深度学习任务上展示了突破性的性能。

最后，摊销变分推断（D. P. Kingma’s “Variational Inference and Deep Learning: A New Synthesis,” University of Amsterdam, 2017）是一个有趣的研究领域，因为它结合了深度神经网络的表达能力和表示学习与概率图模型的领域知识。我们曾看到 MDN 的一个此类应用，当我们使用神经网络将观测空间映射到近似后验分布的参数时。

深度学习研究是一个非常活跃的领域。对于最先进的发展和应用，读者被鼓励查阅 Conference and Workshop on Neural Information Processing Systems、International Conference on Learning Representations，以及附录 A 中提到的研究会议。

## 11.6 练习

- 11.1 CNN 中的感受野是什么？
- 11.2 通过推导反向传播解释残差连接的好处。
- 11.3 比较使用 CNN、RNN 和 Transformer 神经网络的优缺点。
- 11.4 给出一个使用摊销变分推断的神经网络的例子。
- 11.5 通过示例展示 GCN 前向方程 $D^{-1/2}(A+I)D^{-1/2}XW + b$ 背后的直觉。

## 总结

- 自编码器是训练用于重构输入的无监督神经网络。自编码器的瓶颈层可用于降维或特征提取。
- 变分自编码器由一个将数据作为输入并将其转换为潜在表示的编码器，以及一个接收潜在表示并返回重构的解码器组成。
- 摊销变分推断的想法是，与其优化一组自由参数，我们可以引入一个参数化函数，将观测空间映射到近似后验分布的参数。
- 混合密度网络是混合模型，其中均值、协方差和混合比例等参数由神经网络学习。
- 注意力允许模型通过调整注意力权重自适应地关注输入的不同部分。
- Transformer 是一种 Seq2Seq 模型，在编码器和解码器中都使用注意力。自注意力是 Transformer 架构的关键组件。
- 图神经网络是通过在图的节点之间传递消息来捕捉依赖关系的神经模型。
