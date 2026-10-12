
该解码器的内部表示被用作图像分类的基础。最终的像素嵌入被平均化，然后一个线性层将这些映射为激活值，并通过 softmax 层传递以预测类别概率。该系统在大量网络图像语料库上进行预训练，随后在缩放至 48×48 像素的 ImageNet 数据库上进行微调，使用的损失函数同时包含用于图像分类的交叉熵项和用于预测像素的生成损失项。尽管使用了大量外部训练数据，该系统在 ImageNet 上仅达到了 27.4% 的 top-1 错误率（图 10.15）。这优于当时的卷积架构（见图 10.21），但考虑到输入图像尺寸很小，这仍然令人印象深刻；毫不奇怪，它无法对目标物体细小或纤细的图像进行分类。

### 12.10.2 Vision Transformer (ViT)

`Vision Transformer` 通过将图像划分为 16×16 的补丁来解决图像分辨率问题（[图 12.17](#c012.xhtml#c12-fig-0017)）。每个补丁通过学习到的线性变换映射到较低维度，这些表示被送入 Transformer 网络。同样，标准的 1D 位置编码也是学习得到的。

***

Problem 12.8

***

![Figure 12.17 Vision transformer. The Vision Transformer (ViT) breaks the image into a grid of patches (16×16 in the original implementation). Each of these is projected via a learned linear transformation to become a patch embedding. These patch embeddings are fed into a transformer encoder network, and the `<cls>` token is used to predict the class probabilities.](images/c12-fig-0017.jpg)

[图 12.17](#c012.xhtml#c12-fig-0017a) Vision Transformer。Vision Transformer (ViT) 将图像分割成补丁网格（原始实现中为 16×16）。每个补丁通过学习到的线性变换投影为补丁嵌入。这些补丁嵌入被送入 Transformer 编码器网络，并使用 `<cls>` 标记来预测类别概率。

这是一个带有 `<cls>` 标记的编码器模型（见[图 12.10–12.11](#c012.xhtml#c12-fig-0010)）。然而，与 BERT 不同，它在包含来自 18,000 个类别的 3.03 亿张标注图像的大型数据库上使用 `supervised`（有监督）预训练。`<cls>` 标记通过最后一层网络映射以创建激活值，这些激活值被送入 softmax 函数以生成类别概率。预训练后，通过将最后一层替换为映射到所需类别数量的层并进行微调，将系统应用于最终的分类任务。

在 ImageNet 基准测试中，该系统实现了 11.45% 的 top-1 错误率。然而，在没有有监督预训练的情况下，其表现不如最好的当代卷积网络。卷积网络强烈的归纳偏置只能通过使用极大量的训练数据来超越。

### 12.10.3 多尺度 Vision Transformer

Vision Transformer 与卷积架构的不同之处在于它在单一尺度上运行。已经提出了几种在多个尺度上处理图像的 Transformer 模型。与卷积网络类似，这些模型通常从高分辨率、少通道的补丁开始，并逐渐降低分辨率，同时增加通道数。

多尺度 Transformer 的一个典型示例是 `shifted-window`（移动窗口）或 `SWin` Transformer。这是一个编码器 Transformer，它将图像分割成补丁，并将这些补丁分组为窗口网格，在每个窗口内独立应用自注意力（[图 12.18](#c012.xhtml#c12-fig-0018)）。在相邻的 Transformer 层中，这些窗口发生位移，因此给定补丁的有效感受野可以扩展到窗口边界之外。

![Figure 12.18 Shifted window (SWin) transformer (Liu et al., 2021c). a) Original image. b) The SWin transformer breaks the image into a grid of windows and each of these windows into a sub-grid of patches. The transformer network applies self-attention to the patches within each window independently. c) Each alternate layer shifts the windows so that the subsets of patches that interact with one another change, and information can propagate across the whole image. d) After several layers, the 2×2 blocks of patch representations are concatenated to increase the effective patch (and window) size. e) Alternate layers use shifted windows at this new lower resolution. f) Eventually, the resolution is such that there is just a single window, and the patches span the entire image.](images/c12-fig-0018.jpg)

[图 12.18](#c012.xhtml#c12-fig-0018a) 移动窗口 (SWin) Transformer (Liu et al., 2021c)。a) 原始图像。b) SWin Transformer 将图像分割成窗口网格，并将每个窗口分割成补丁子网格。Transformer 网络独立地对每个窗口内的补丁应用自注意力。c) 每隔一层移动一次窗口，以便相互作用的补丁子集发生变化，信息可以在整个图像中传播。d) 经过几层后，将 2×2 的补丁表示块拼接起来，以增加有效补丁（和窗口）大小。e) 交替层在此新的较低分辨率下使用移动窗口。f) 最终，分辨率变为仅有一个窗口，补丁覆盖整个图像。

通过拼接来自不重叠的 2×2 补丁的特征，并应用将这些拼接特征映射到原始通道数两倍的线性变换，定期降低尺度。该架构没有 `<cls>` 标记，而是对最后一层的输出特征进行平均。然后通过线性层将这些映射到所需的类别数量，并通过 softmax 函数输出类别概率。在撰写本文时，该架构最复杂的版本在 ImageNet 数据库上实现了 9.89% 的 top-1 错误率。

一个相关的想法是定期整合来自整个图像的信息。`Dual attention vision transformers`（DaViT，双注意力 Vision Transformer）交替使用两种类型的 Transformer。在第一种中，图像补丁相互注意，自注意力计算使用所有通道。在第二种中，通道相互注意，自注意力计算使用所有图像补丁。该架构在 ImageNet 上达到了 9.60% 的 top-1 错误率，接近撰写本文时的最先进水平。

***

Problem 12.9

***

## 12.11 总结

本章介绍了自注意力和 Transformer 架构。随后描述了编码器、解码器和编码器-解码器模型。Transformer 对高维嵌入集合进行操作。它每层的计算复杂度较低，且大部分计算可以使用矩阵形式并行执行。由于每个输入嵌入都与其他所有嵌入交互，它可以描述文本中的长距离依赖关系。最终，计算量与序列长度的平方成正比；降低复杂度的一种方法是稀疏化交互矩阵。

在超大规模无标签数据集上训练 Transformer 是本书中 `unsupervised learning`（无监督学习，即无标签学习）的第一个例子。编码器通过预测缺失标记来学习可用于其他任务的表示。解码器在输入上构建自回归模型，是本书中 `generative model`（生成模型）的第一个例子。生成式解码器可用于创建新的数据样本。

第 13 章讨论用于处理图数据的网络。这些网络与 Transformer 相关，因为图的节点在每个网络层中相互注意。第 14-18 章回归无监督学习和生成模型。

## Notes

