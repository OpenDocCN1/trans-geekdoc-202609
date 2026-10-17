
# 自注意力机制的复杂度随序列长度呈二次方增长

自注意力机制的复杂度随序列长度呈二次方增长。摘要或问答等任务可能需要长输入，因此这种二次依赖限制了性能。三条研究路线试图解决此问题。第一种减小注意力矩阵的尺寸，第二种使注意力变得稀疏，第三种修改注意力机制以使其更高效。

## 减小注意力矩阵的尺寸

Liu 等人 (2018b) 引入了*内存压缩注意力*。这对键和值应用步长卷积，以一种与卷积网络中下采样非常相似的方式减少位置数量。现在注意力作用于相邻位置的加权组合之间，其中权重是可学习的。沿着类似的思路，Wang 等人 (2020b) 观察到注意力机制中的量在实践中通常是低秩的，并开发了 *LinFormer*，它在计算注意力矩阵之前将键和值投影到一个更小的子空间上。

## 使注意力稀疏

Liu 等人 (2018b) 提出了*局部注意力*，其中相邻的 Token 块仅相互关注。这创建了一个块对角交互矩阵（参见图 12.15）。信息无法在块之间传递，因此此类层通常与全注意力层交替使用。沿着同一思路，GPT3 (Brown 等人, 2020) 使用卷积交互矩阵并将其与全注意力交替。Child 等人 (2019) 和 Beltagy 等人 (2020) 尝试了各种交互矩阵，包括具有不同膨胀率的卷积结构，但允许某些查询与所有其他键交互。Ainslie 等人 (2020) 引入了*扩展 Transformer 构造* (图 12.15h)，它使用一组与所有其他 Token 交互的全局嵌入。这只能在编码器版本中完成，否则这些会隐式地允许系统“窥视未来”。当与相对位置编码结合时，该方案需要特殊的编码来映射到、从以及在这些全局嵌入之间。*BigBird* (Ainslie 等人, 2020) 将全局嵌入、卷积结构与可能连接的随机采样相结合。其他工作研究了学习注意力矩阵的稀疏模式 (Roy 等人, 2021; Kitaev 等人, 2020; Tay 等人, 2020)。

## 修改注意力机制以提高效率

最后，人们注意到计算注意力的 softmax 操作中分子和分母的项具有 `exp[k^T q]` 的形式。这可以被视为核函数，因此可以表示为点积 `g[k]^T g[q]`，其中 `g[•]` 是非线性变换。这种公式解耦了查询和键，使注意力计算更高效。不幸的是，为了复制指数项的形式，变换 `g[•]` 必须将输入映射到无限空间。线性 Transformer (Katharopoulos 等人, 2020) 认识到这一点，并用不同的相似度度量替换了指数项。*Performer* (Choromanski 等人, 2020) 用有限维映射近似这种无限映射。关于将 Transformer 扩展到更长序列的更多细节，请参见 Tay 等人 (2023) 和 Prince (2021a)。

---

### 问题 12.10

---

### Transformer 的训练

训练 Transformer 具有挑战性，需要学习率预热 (Goyal 等人, 2018) 和 Adam 优化器 (Kingma & Ba, 2015)。确实，Xiong 等人 (2020a) 和 Huang 等人 (2020a) 表明，如果没有学习率预热，梯度会消失，且 Adam 更新的幅度会减小。几个相互作用的因素导致了这个问题。残差连接导致梯度爆炸（图 11.6），但归一化层可以防止这种情况。Vaswani 等人 (2017) 使用 `LayerNorm` 而非 `BatchNorm`，因为 NLP 任务中批次间的统计量高度可变，尽管后续工作已为 Transformer 修改了 `BatchNorm` (Shen 等人, 2020a)。`LayerNorm` 位于残差块之外，导致梯度在反向传播通过网络时收缩 (Xiong 等人, 2020a)。此外，残差连接和主自注意力机制的相对权重随着我们在初始化时穿过网络而变化（见图 11.6c）。还有额外的复杂因素：查询和键参数的梯度小于值参数的梯度 (Liu 等人, 2020)，这使得使用 Adam 成为必要。这些因素以复杂的方式相互作用，使训练不稳定，从而需要学习率预热。

已经有各种尝试来稳定训练，包括 (i) 一种称为 *TFixup* 的 FixUp 变体 (Huang 等人, 2020a)，它允许移除 `LayerNorm` 组件，(ii) 改变网络中 `LayerNorm` 组件的位置 (Liu 等人, 2020)，以及 (iii) 重新加权残差分支中的两条路径 (Liu 等人, 2020; Bachlechner 等人, 2021)。Xu 等人 (2021b) 引入了一种称为 *DTFixup* 的初始化方案，允许在较小数据集上训练 Transformer。详细讨论请参见 Prince (2021b)。

## 视觉领域的应用

ImageGPT (Chen et al., 2020a) 和 Vision Transformer (Dosovitskiy et al., 2021) 都是早期应用于图像的 Transformer 架构。Transformer 已被用于图像分类 (Dosovitskiy et al., 2021; Touvron et al., 2021)、目标检测 (Carion et al., 2020; Zhu et al., 2020b; Fang et al., 2021)、语义分割 (Ye et al., 2019; Xie et al., 2021; Gu et al., 2022)、超分辨率 (Yang et al., 2020a)、动作识别 (Sun et al., 2019; Girdhar et al., 2019)、图像生成 (Chen et al., 2021b; Nash et al., 2021)、视觉问答 (Su et al., 2019b; Tan & Bansal, 2019)、图像修复 (Wan et al., 2021; Zheng et al., 2021; Zhao et al., 2020b; Li et al., 2022)、图像着色 (Kumar et al., 2021) 以及许多其他视觉任务 (Khan et al., 2022; Liu et al., 2023b)。

## Transformer 与卷积网络

Transformer 已与卷积神经网络结合用于许多任务，包括图像分类 (Wu et al., 2020a)、目标检测 (Hu et al., 2018a; Carion et al., 2020)、视频处理 (Wang et al., 2018c; Sun et al., 2019)、无监督目标发现 (Locatello et al., 2020) 以及各种文本/视觉任务 (Chen et al., 2020d; Lu et al., 2019; Li et al., 2019)。Transformer 在视觉任务上可超越卷积网络，但通常需要大量数据才能实现卓越性能。通常，它们在 JRT (Sun et al., 2017) 和 LAION (Schuhmann et al., 2021) 等海量数据集上进行预训练。Transformer 不具备卷积网络的归纳偏置，但通过使用海量数据，它可以克服这一劣势。

## 从像素到视频

非局部网络 (Wang et al., 2018c) 是将自注意力应用于图像数据的早期尝试。Transformer 最初被应用于局部邻域内的像素 (Parmar et al., 2018; Hu et al., 2019; Parmar et al., 2019; Zhao et al., 2020a)。ImageGPT (Chen et al., 2020a) 将其扩展以建模小图像中的所有像素。Vision Transformer (ViT) (Dosovitskiy et al., 2021) 使用不重叠的图像块来分析更大的图像。

从那时起，开发了许多多尺度系统，包括 SWin Transformer (Liu et al., 2021c)、SWinV2 (Liu et al., 2022)、多尺度 Vision Transformer (MViT) (Fan et al., 2021) 和金字塔视觉 Transformer (Wang et al., 2021)。Crossformer (Wang et al., 2022b) 对空间尺度间的交互进行建模。Ali et al. (2021) 提出了交叉协方差图像 Transformer，其中通道而非空间位置相互注意，从而使注意力矩阵的大小与图像大小无关。双重注意力视觉 Transformer (DaViT) 由 Ding et al. (2022) 开发，在子窗口内的局部空间注意力和通道间的全局空间注意力之间交替。Chu et al. (2021) 同样在子窗口内的局部注意力和通过空间下采样实现的全局注意力之间交替。Dong et al. (2022) 将 图 12.15 的思想改编到 2D 图像域中，其中元素间的交互被稀疏化。

随后，Transformer 被改编用于视频处理 (Arnab et al., 2021; Bertasius et al., 2021; Liu et al., 2021c; Neimark et al., 2021; Patrick et al., 2021)。关于应用于视频的 Transformer 的综述可参见 Selva et al. (2022)。

## 结合图像与文本

CLIP (Radford et al., 2021) 使用对比预训练任务为图像及其标题学习一个联合编码器。系统摄入 `N` 张图像及其标题，并生成图像与标题之间兼容性的矩阵。损失函数鼓励正确配对获得高分，错误配对获得低分。Ramesh et al. (2021) 和 Ramesh et al. (2022) 训练一个扩散解码器来反转 CLIP 图像编码器，用于文本条件图像生成（见第 18 章）。

# 习题

## 习题 12.1

考虑一个处理长度为 `D` 的 `N` 个输入以产生相同大小的 `N` 个输出的自注意力机制。计算查询、键和值使用了多少权重和偏置？会有多少注意力权重 `a[•, •]`？在一个将所有 `DN` 个输入关联到所有 `DN` 个输出的全连接网络中，会有多少权重和偏置？

## 习题 12.2

为什么我们可能希望确保自注意力机制的输入与输出大小相同？

## 习题 12.3*

证明自注意力机制（公式 12.8）关于数据 `X` 的排列 `XP` 是等变的，其中 `P` 是一个排列矩阵。换句话说，证明：

![c12-fig-5018.jpg](img/c12-fig-5018.jpg)

(12.18)

***

附录 B.4.4

排列矩阵

***

## 习题 12.4

考虑 Softmax 操作：

![c12-fig-5019.jpg](img/c12-fig-5019.jpg)

(12.19)

在有五个输入的情况下，其值为：`z[1] = -3`，`z[2] = 1`，`z[3] = 100`，`z[4] = 5`，`z[5] = -1`。计算所有 `i, j` ∈ {1, 2, 3, 4, 5} 的 25 个导数 `∂y[i]/∂z[j]`。你得出什么结论？

## 习题 12.5

为什么如果 `H` 个头中的值、查询和键各自的维度为 `D/H`（其中 `D` 是数据的原始维度），实现会更高效？

## 习题 12.6

BERT 使用两个任务进行预训练。第一个任务要求系统预测缺失（被掩盖）的单词。第二个任务要求系统将句子对分类为在原文中是否相邻。识别这些任务分别是生成式还是对比式的（见第 9.3.6 节）。你认为为什么要使用两个任务？提出两个可用于预训练语言模型的新颖对比任务。

## 习题 12.7

考虑向一个包含 `N` 个 Token 的预计算掩码自注意力机制中添加一个新 Token。描述为纳入此新 Token 所必须进行的*额外*计算。

## 习题 12.8

视觉 Transformer 中的计算量随图像块数量呈二次方增长。利用 图 12.15 的原则，设计两种减少计算量的方法。

## 习题 12.9

考虑用 16 × 16 的网格图像块表示图像，每个图像块由长度为 512 的图像块嵌入表示。比较 DaViT Transformer 执行注意力所需的计算量：(i) 在图像块之间，使用所有通道；(ii) 在通道之间，使用所有图像块。

## 习题 12.10*

注意力权重通常计算为：

![c12-fig-5020.jpg](img/c12-fig-5020.jpg)

(12.20)

考虑将 ![c12-fig-5021.jpg](img/c12-fig-5021.jpg) 替换为点积 `g[k[m]]^T g[q[n]]`，其中 `g[•]` 是一个非线性变换。展示这如何使注意力权重的计算更高效。

# 第 13 章

## 图神经网络

第 10 章介绍了卷积网络，其专门处理规则数据阵列（如图像）。第 12 章介绍了 Transformer，其专门处理可变长度序列（如文本）。本章介绍*图神经网络*。顾名思义，这些是处理图（即由边连接的节点集合）的神经架构。

处理图面临三个新挑战。首先，其拓扑结构是可变的，很难设计既足够表达强又能应对这种变化的网络。其次，图可能非常庞大；表示社交网络用户连接的图可能有十亿个节点。第三，可能只有一个单一的整体图可用，因此用许多样本训练并用新数据测试的常规协议并不总是合适的。

本章首先展示图的真实世界示例。随后描述如何对这些图进行编码，以及如何为图构建监督学习问题。文中讨论了处理图的算法要求，这自然引出了`图卷积网络`，这是一种特定类型的图神经网络。

### 13.1 什么是图？

图是一种非常通用的结构，由一组`节点`或`顶点`组成，成对的节点通过`边`或`链接`相连。图通常是稀疏的；可能存在的边中只有一小部分实际存在。

现实世界中的某些对象天然呈现为图的形式。例如，路网可以视为图，其中节点代表物理位置，边代表它们之间的道路（图 13.1a）。化学分子是小型图，节点代表原子，边代表化学键（图 13.1b）。电路是图，节点代表元件和接点，边代表电气连接（图 13.1c）。

![Figure 13.1 Real-world graphs. Some objects, such as a) road networks, b) molecules, and c) electrical circuits, are naturally structured as graphs.](img/c13-fig-0001.jpg)

图 13.1 真实世界的图。某些对象，如 a) 路网、b) 分子和 c) 电路，天然地以图的形式构建。

此外，许多数据集也可以用图来表示，即使这不是它们显而易见的表面形式。例如：

*   社交网络是图，节点是人，边代表他们之间的友谊。
*   科学文献可视为图，节点是论文，边代表引用关系。
*   维基百科可视为图，节点是条目，边代表条目间的超链接。
*   计算机程序可表示为图，节点是语法标记（程序流中不同位置的变量），边代表涉及这些变量的计算。
*   几何点云可表示为图。此处，每个点是一个节点，边连接到其他附近的点。
*   细胞中的蛋白质相互作用可表示为图，节点是蛋白质，如果两个蛋白质相互作用，它们之间就有一条边。

此外，集合（无序列表）可视为一种图，其中每个成员都是一个节点并连接到其他所有成员。图像可视为具有规则拓扑的图，其中每个像素是一个节点，边连接到相邻像素。

#### 13.1.1 图的类型

图可通过多种方式分类。图 13.2a 中的社交网络包含`无向边`；有连接的每对个体已达成共识成为朋友，因此这种关系没有方向性之分。相反，图 13.2b 中的引用网络包含`有向边`。每篇论文引用其他论文，这种关系天然是单向的。

![Figure 13.2 Types of graphs. a) A social network is an undirected graph; the connections between people are symmetric. b) A citation network is a directed graph; one publication cites another, so the relationship is asymmetric. c) A knowledge graph is a directed heterogeneous multigraph. The nodes are heterogeneous in that they represent different object types (people, places, companies) and multiple edges may represent different relations between each node. d) A point set can be converted to a graph by forming edges between nearby points. Each node has an associated position in 3D space, and this is termed a geometric graph (adapted from Hu et al., 2022). e) The scene on the left can be represented by a hierarchical graph. The topology of the room, table, and light are all represented by graphs. These graphs form nodes in a larger graph representing object adjacency (adapted from Fernández-Madrigal & González, 2002).](img/c13-fig-0002.jpg)
