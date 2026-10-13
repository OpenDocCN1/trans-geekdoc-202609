
其中 `α[n_i]` 是时刻 `n` 对应的权重。上述结合所有先前状态向量的思想已在文献 [6] 所述的机器翻译系统中得到采用，尽管其形式略有不同（另见第 [19.3.2](#Chp019_997-1102_B9780443292385000251.xhtml) 节）。

[图 18.37](#Chp018_885-995_B978044329238500024X.xhtml#f0200) 摘自前述文献，阐释了采用加权机制的基本原理。法语单词为输入，英语单词为对应的输出序列。相应注意力权重的值以像素形式可视化；权重越大，像素越白。例如请注意，输出单词 “produce” 是对三个连续时刻的信息加权得到的结果，这三个时刻对应单词 “peut plus produire”，而单词 “destruction” 对应两个单词，即 “la destruction”。

![Figure 18.37 The values of the attention weights in grayscale, showing the degree of dependence of the words in the output sequence (English) to those of the input sequence (French) (from [6]). Note, for example, that in order to produce the word “Syria,” the network “attends” the words “La Syrie.”](images/B978044329238500024X/gr037.jpg)

[图 18.37](#Chp018_885-995_B978044329238500024X.xhtml#cf1845) 灰度图显示了注意力权重的值，反映了输出序列（英语）中的单词对输入序列（法语）中单词的依赖程度（源自 [6]）。例如请注意，为了生成单词 “Syria”，网络会 “关注” 单词 “La Syrie”。

在文献 [220] 中，带有注意力机制的网络被用于图像描述的自动生成。在所述系统中，采用一种 CNN 网络的变体来生成一组特征向量。每个特征向量对应原始图像的一个 `portion`（区域）。这一步骤相当于原始图像的一个 `encoding`（编码）阶段。这些向量进而被用于形成 LSTM 网络的输入序列，其中采用了注意力权重。该网络被训练以根据 LSTM 状态计算输出单词的概率。[图 18.38](#Chp018_885-995_B978044329238500024X.xhtml#f0205) 摘自 [220]，展示了模型在生成单词时 “关注” 的图像部分。

![Figure 18.38 The original image is shown at the top left. The resulting image description is “A person is standing on the beach with a surfboard.” The use of attention weights highlights the corresponding part of the image, where the output word more heavily depends on. As an example, observe that while the output produces the word “surfboard,” the attention weights that are associated with the pixels within the corresponding region in the image get the largest values (from [220]).](images/B978044329238500024X/gr038.jpg)

[图 18.38](#Chp018_885-995_B978044329238500024X.xhtml#cf1855) 原始图像显示在左上角。生成的图像描述为 “A person is standing on the beach with a surfboard.” 注意力权重的使用高亮显示了输出单词更强依赖的图像对应部分。例如请观察，当输出生成单词 “surfboard” 时，与图像中对应区域内像素相关的注意力权重获得了最大值（源自 [220]）。

将注意力机制集成到模型中的一个有趣之处在于，可以追踪模型的行为以及输出信息是如何形成的；当网络的可解释性问题变得重要时，这很有用。也就是说，理解网络做出决策的 “原因” 和 “方式”。关于相关讨论，请参阅例如 [179]。

实现注意力的不同路径也是可能的。在文献 [58] 中，提出了所谓的 `neural Turing machine`（NTM，神经图灵机），其中记忆模块与神经网络（前馈或 LSTM）并行应用。一种 `learnable`（可学习）的注意力机制被用于有选择地对记忆进行读写。涉及强化学习技术的 NTM 扩展见文献 [224]。在文献 [194,217] 中，由输入数据生成的记忆被允许在产生输出前被读取多次。这类似于基于记忆内容进行多步推理；即基于输入的 “故事” 进行推理。

### 备注 18.7

*   **储备计算**：储备计算一词主要指两个紧密相关的循环网络家族，它们是独立提出的，即 `echo state networks`（ESN，回声状态网络）[88] 和 `liquid state machines`（液态机）[125]。后者实现的是脉冲神经元而非连续值神经元。

*   原始 ESN 的主要思想是仅训练与输出神经元相关的参数。与输入和状态向量相关的权重是按照特定规则 `randomly`（随机）生成的。未训练的部分称为 `reservoir`（储备池/储备层），产生的状态称为 `echoes`（回声）。其基本原理源于这样一个想法：如果一个随机 RNN 具备特定属性，那么仅训练输出参数就足够了。储备池应具备的主要属性是所谓的 `echo state property`（回声状态特性）。这基本上是一个与网络动力学相关的稳定性条件 [122]。文献 [27] 讨论了一种非参数贝叶斯公式化方法；在输出权重上施加先验分布，在给定训练数据的预测生成语境下，这些权重被边缘化掉了。

## 18.14 对抗样本

在本版编撰之时，深度神经网络在性能和准确率方面处于最先进水平，往往可与人类相媲美，有时甚至超越人类。然而，我们似乎尚不具备断言这些模型真正 “理解” 其 “学会” 执行的任务的地位；尽管例如它们可以在分类任务中以极高的概率预测正确标签。文献 [200] 表明，可以构造 `adversarial`（对抗）样本，`consistently`（持续/稳定地）欺骗机器学习模型。“对抗性” 一词意味着可以有意在输入集的模式上施加 `small worst-case`（微小的最坏情况）扰动，从而导致模型以高概率预测错误标签。最有趣的是，这种微小噪声扰动的添加，在图像情况下（如 [200]）几乎难以被人眼察觉，在音乐情况下（如 [100,192]）几乎难以被人耳察觉。[图 18.39](#Chp018_885-995_B978044329238500024X.xhtml#f0210)（摘自 [200]）总共展示了九幅图像。一个神经网络（AlexNet）已被训练用于识别图像内容。左侧三幅图像取自相应的测试集，均被正确识别。中间的图像是添加到左侧对应图像上的噪声图像。结果图像显示在右侧。人类预测正确标签毫无困难。然而，AlexNet 将这三幅图像全部分类为 “ostrich, struthio camelus”（鸵鸟）类别！

![Figure 18.39 The images on the left have been classified correctly. All the images on the right have been classified as “ostrich, Struthio camelus”! The images in the center show the noise (after some magnification) added to obtain the images on the right (example taken from [200]).](images/B978044329238500024X/gr039.jpg)
