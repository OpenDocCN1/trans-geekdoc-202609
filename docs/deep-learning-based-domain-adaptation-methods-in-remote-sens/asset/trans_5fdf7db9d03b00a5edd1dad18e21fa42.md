

在多个关键基准测试中表现优异，为当前及未来的研究工作提供了富有洞察力的指导。

- 我们总结了该领域的现有方法，并提出了我们对未来趋势和值得进一步探索的主题的看法。

如图2所示，本文的结构安排如下。在第二节中，我们回顾了遥感领域自适应方法的基础知识，包括“基础知识”和“方法学分类与数学符号”。在第三节中，我们采用逐篇论文的方式对现有文献进行了全面综述，并从四个角度进行了分类。在第四节中，我们首先介绍了基准数据集。然后，我们在多种遥感任务的不同基准数据集上进行了详细的性能比较。在第五节中，我们讨论了未来的研究趋势和主题，以及我们的观点。最后，我们在第六节中结束了本综述。

## 二、 基础知识

如图2所示，我们首先介绍基础知识，包括一些基本的数学符号。随后，我们整理并呈现了该领域不同方法的方法学分类以及数学定义。

### A. 数学符号

如图2所示，我们提供了现有方法的详细分类，基于任务分类、输入模式、监督范式和算法粒度四个角度进行归类。具体的方法学分类如图3所示。

表I展示了初步的数学符号。对于本综述关注的四个任务（图3），现有方法总是构建一个模型，使用训练集 ($\mathcal{D}_{train}$) 对其进行优化，并在测试集 ($\mathcal{D}_{test}$) 上评估其性能。这些训练集和测试集分区来自一个综合数据集 ($\mathcal{D}$ = $\mathcal{D}_{train}$ $\cup$ $\mathcal{D}_{test}$)。因此，尽管训练集和测试集之间可能存在潜在的数据分布差异，我们仍然将它们视为来自同一领域的样本。当领域自适应被整合到上述四个任务中时，问题定义将发生显著变化。

对于领域自适应遥感 (DA-RS) 任务，它总是涉及源数据集 ($\mathcal{D}_{S}$) 和目标数据集 ($\mathcal{D}_{T}$)。如果源数据集和目标数据集的类别集分别表示为 $\mathcal{C}_{S}$, $\mathcal{C}_{T}$，通常这两个集合具有相同数量的类别 ($N_{\mathcal{C}_{S}}$ = $N_{\mathcal{C}_{T}}$)。

$$ \mathcal{D}_{S} = \{\mathcal{D}_{S}^{i}\}_{i=1}^{N_{S}}, \quad \mathcal{D}_{T} = \{\mathcal{D}_{T}^{i}\}_{i=1}^{N_{T}} \quad (1) $$

源数据集和目标数据集的第 $i$ 个子集分别包含 $K_{S}^{i}$ 和 $K_{T}^{i}$ 个样本，其中 $K_{S}^{i}$ $\ge$ 0 且 $K_{T}^{i}$ $\ge$ 0。这一过程可以通过公式2进行表述。

$$ \mathcal{D}_{S}^{i} = \{(\mathbf{x}_{S}^{i,j}, \mathbf{y}_{S}^{i,j})\}_{j=1}^{K_{S}^{i}}, \quad \mathcal{D}_{T}^{i} = \{(\mathbf{x}_{T}^{i,j}, \mathbf{y}_{T}^{i,j})\}_{j=1}^{K_{T}^{i}} \quad (2) $$

为了优化 DA-RS 任务的模型，$\mathcal{D}_{T}$ 被划分为训练子集和测试子集 ($\mathcal{D}_{T-train}$, $\mathcal{D}_{T-test}$)，其中 $\mathcal{D}_{T}$ = $\mathcal{D}_{T-train}$ $\cup$ $\mathcal{D}_{T-test}$。因此，对于一个给定的 DA-RS 任务，训练数据集包括源数据集 $\mathcal{D}_{S}$ 和目标数据集的训练子集 ($\mathcal{D}_{T-train}$)，而测试数据集 $\mathcal{D}_{test}$ 仅由 $\mathcal{D}_{T-test}$ 组成。这意味着 $\mathcal{D}_{S}$ 和 $\mathcal{D}_{T}$ 的一部分都将在训练阶段被利用。值得注意的是，训练阶段中 $\mathcal{D}_{T}$ 的比例可能为 0，这意味着在某些情况下，目标数据集将不用于训练目的。

如公式1和公式2所示，源数据集由 $N_{S}$ 个子集组成，而目标数据集包含 $N_{T}$ 个子集，约束条件为 $N_{S}$ $\ge$ 1 且 $N_{T}$ $\ge$ 1。这表明两个数据集各自至少包含一个子集。

### B. 方法学分类

#### 1) DA-RS 任务的问题定义

如图3所示，本综述主要回顾了四个 DA-RS 任务，分别是 DA-RSCls、DA-RSSeg、DA-RSdet 和 DA-RSCLD。具体说明如图4所示。

**DA-RSCls。**

如图4 (a)所示，分类器包含单一的编码器。在前向传播过程中，源图像和目标图像 ($\mathbf{x}_{S}$, $\mathbf{x}_{T} \in \mathbb{R}^{B \times C \times H \times W}$) 被输入到编码器 ($f_{cls}(\cdot)$) 中以生成预测结果，如公式3所示。在分类任务中，预测结果 ($\mathbf{P}_{S-cls}$, $\mathbf{P}_{T-cls} \in \mathbb{R}^{B \times N_{C}}$) 被表示为各类别上的后验概率。这里，$N_{C}$ 表示类别的数量。

$$ \mathbf{P}_{S-cls} = f_{cls}(\mathbf{x}_{S}), \quad \mathbf{P}_{T-cls} = f_{cls}(\mathbf{x}_{T}) \quad (3) $$

为了优化编码器，基本损失 $\mathcal{L}_{DA-cls}$ 如公式4所示，其中 $\mathcal{L}_{ce}$ 表示交叉熵损失。基于这种优化范式，现有方法整合了多种损失组件来构建组合损失，包括对抗损失、自训练损失等。

$$ \mathcal{L}_{DA-cls} = \frac{1}{B}\sum_{i=1}^{B} \mathcal{L}_{ce}(\mathbf{P}_{S-cls}^{i}, \mathbf{P}_{T-cls}^{i}; y_{S}^{i}, y_{T}^{i}) \quad (4) $$

**DA-RSSeg。**

如图4 (b)所示，分割器采用“编码器-解码器”架构 ($f_{seg}(\cdot)$)。$\mathbf{x}_{S}$ 和 $\mathbf{x}_{T}$ 分别通过分割器生成像素级预测结果 ($\mathbf{P}_{S-seg}$, $\mathbf{P}_{T-seg} \in \mathbb{R}^{B \times N_{C} \times H \times W}$)，如公式5所示。这些预测中的每个像素代表一个后验概率，从而允许将语义分割视为一种逐像素的分类任务。

$$ \mathbf{P}_{S-seg} = f_{seg}(\mathbf{x}_S), \quad \mathbf{P}_{T-seg} = f_{seg}(\mathbf{x}_T) \quad (5) $$

与 DA-RSCls 任务中采用的基本损失函数（公式5）类似，交叉熵损失也被用作优化分割器的基线损失 ($\mathcal{L}_{DA-seg}$)。该公式表示为公式6和公式7。

$$ \mathcal{L}_{DA-seg}^i = \frac{1}{HW} \sum_{h=1}^{H} \sum_{w=1}^{W} \boldsymbol{P}_{S-cd}^{i,h,w} \boldsymbol{P}_{T-cd}^{i,h,w} y_S^{i,h,w} y_T^{i,h,w} \quad (6) $$

$$ \mathcal{L}_{DA-seg} = -\frac{1}{B} \sum_{i=1}^{B} \mathcal{L}_{DA-seg}^i \quad (7) $$

**DA-RSDet。**

物体检测提出了重大挑战，因为它试图同时在图像中定位和分类物体。通过利用领域自适应，即使面对来自不同数据分布的样本，检测器也能实现精确检测。如图4 (c)所示，基本检测器由编码器和头部组成，这提供了“单阶段检测器”和“两阶段检测器”架构的概览。

与 DA-Cl s 和 DA-Seg 任务类似，源图像和目标图像都将传输到检测器 ($f_{det}(\cdot)$) 并生成最终预测结果 ($\mathcal{P}_{S-det}, \mathcal{P}_{T-det}$)。具体而言，在“单阶段检测器”中，这些预测结果结构化为一个单一的张量，整合了定位和分类结果。相反，在“两阶段检测器”中，预测结果是由专门用于定位和分类的不同分支生成的。无论不同检测器类型之间的变化如何，都需要使用边界框的回归损失 ($\mathcal{L}_{reg}$) 和实例后验概率的分类损失 ($\mathcal{L}_{cls}$)。总体而言，DA-Det 优化的基本损失函数 ($\mathcal{L}_{DA-det}^i$) 可以从公式8到公式10进行表述。

$$ \mathcal{P}_{S-det} = f_{det}(\boldsymbol{x}_S), \quad \mathcal{P}_{T-det} = f_{det}(\boldsymbol{x}_T) \quad (8) $$

$$ \mathcal{L}_{DA-det}^i = \mathcal{L}_{reg}(\boldsymbol{P}_{S-det}^i, \boldsymbol{P}_{T-det}^i; \boldsymbol{y}_S^{i-box}, \boldsymbol{y}_T^{i-box}) + \mathcal{L}_{cls}(\boldsymbol{P}_{S-det}^i, \boldsymbol{P}_{T-det}^i; \boldsymbol{y}_S^{i-cls}, \boldsymbol{y}_T^{i-cls}) \quad (9) $$

$$ \mathcal{L}_{DA-det} = -\frac{1}{B} \sum_{i=1}^{B} \mathcal{L}_{DA-det}^i \quad (10) $$

**DA-RSCD。**

变化检测是遥感中的一项基本任务，旨在检测和分析同一地理区域随时间发生的变化。如图4 (d)所示，变化检测模型通过接受图像对作为输入来运行。$\boldsymbol{x}_A$ 和 $\boldsymbol{x}_B$ 分别表示变化前（事件前）和变化后（事件后）的图像。在 RSCD 任务中，$\boldsymbol{x}_A$ 和 $\boldsymbol{x}_B$ 显示出极小的差异，表明领域偏移程度较低。在 DA-RSCD 任务中，$\boldsymbol{x}_A$ 和 $\boldsymbol{x}_B$ 表现出显著的领域偏移问题，这通常由使用不同的传感器或不同的成像条件引起。

**表 I: 初步数学符号**

| 数据级符号 | | 方法级符号 | |
| :--- | :--- | :--- | :--- |
| 符号 | 描述 | 符号 | 描述 |
| $\mathcal{D}$ | 数据集 | $\mathcal{L}(\cdot)$ | 损失 |
| $\mathcal{D}_{train}$, $\mathcal{D}_{test}$ | 训练集、测试集 | $\theta$ | 模型参数 |
| $\mathcal{D}_{S}$, $\mathcal{D}_{T}$ | 源数据集、目标数据集 | $f(\cdot)$, $h(\cdot)$, $g(\cdot)$ | 模块函数 |
| $\mathbf{x}$, $\mathbf{y}$ | 输入、目标、标签 | $\alpha$, $\beta$, $\gamma$, … | 超参数 |
| $\mathbf{X}$, $\mathbf{Y}$ | 输入集、标签集 | minimax | “最小-最大”准则 |
| $\mathcal{C}$ | 类别集 | argmax | “argmax”操作 |

![](img/6f3fe8f45739aa0bcfea4346d3596801_3_0.png)
图3: 本综述中领域自适应遥感任务的方法学分类概览。

![](img/6f3fe8f45739aa0bcfea4346d3596801_3_1.png)
![](img/6f3fe8f45739aa0bcfea4346d3596801_3_2.png)
![](img/6f3fe8f45739aa0bcfea4346d3596801_3_3.png)
![](img/6f3fe8f45739aa0bcfea4346d3596801_3_4.png)
图4: 本综述中四个领域自适应遥感任务的概览。

变化检测器 ($f_{cd}(\cdot)$) 的架构与分割器相似。$\boldsymbol{x}_A$ 和 $\boldsymbol{x}_B$ 被输入到一个“编码器-解码器”结构中，以生成二值预测结果 ($\boldsymbol{P}_{cd} \in \mathbb{R}^{N \times C \times H \times W}$)，其中 $N_C = 2$。这一过程表示为公式11。

$$ \boldsymbol{P}_{cd} = f_{cd}(\boldsymbol{x}_A, \boldsymbol{x}_B) \quad (11) $$

DA-RSCD 的优化可以被视为一个二值分割优化问题。基本损失函数 ($\mathcal{L}_{DA-cd}$) 的具体公式详述于公式12，其中 $\mathcal{L}_{bce}$ 表示二元交叉熵损失。

$$ \mathcal{L}_{DA-cd} = -\frac{1}{BHW} \sum_{i=1}^{B} \sum_{h=1}^{H} \sum_{w=1}^{W} \mathcal{L}_{bce}(\boldsymbol{p}_{cd}^{i,h,w}, y^{i,h,w}) \quad (12) $$

DA-RSCD 任务与上述三个 DA-RS 任务的区别在于，其领域偏移问题出现在图像对内部。相反，DA-RSCls、DA-RSSeg 和 DA-RSDet 面临的领域偏移挑战体现在源数据集和目标数据集之间。

#### 2) 不同输入模式的数学定义

在输入模式的分类中，主要有五种不同类型的 DA-RS 方法，根据源和目标子集的数量进行分类（图3）。具体定义见表II。

**表 II: 不同输入模式的数学定义。本表中的公式可参考公式1。**

| 输入模式 | 源输入: $\mathcal{D}_S = \{ \mathcal{D}_S^i \}_{i=1}^{N_S}$ | 目标输入: $\mathcal{D}_T = \{ \mathcal{D}_T^i \}_{i=1}^{N_T}$ |
| :--- | :--- | :--- |
| 一对一 | $N_S = 1$ | $N_T = 1$ |
| 一对多 | $N_S = 1$ | $N_T > 1$ |
| 多对多 | $N_S > 1$ | $N_T > 1$ |
| 零对一/多 | 不可用 | $N_T \geq 1$ |

- 单源单目标 (“一对一”)。当 $N_S$ 和 $N_T$ 设置为 1 时，这对应于不同任务上的标准领域自适应配置。在此模式下，模型被训练以适应从源域到目标域。
- 单源多目标 (“一对多”)。当 $N_S$ 为 1 而 $N_T$ 设置为大于 1 的值时，主要目标是开发能够在不同目标域上表现良好的模型。在此模式下的一种典型领域自适应任务被称为域泛化 (DG)。
- 多源单目标 (“多对一”)。当 $N_S$ 设置为大于 1 的值而 $N_T$ 设置为 1 时，目标是开发能够利用来自多个源域的集体知识来增强模型在未见过的目标域上的泛化能力的模型。此场景中的另一个关键挑战是减轻不同源子集之间领域偏移的不利影响。
- 多源多目标 (“多对多”)。当 $N_S$ 和 $N_T$ 都设置为大于 1 的值时，任务将变得更加复杂。模型需要有效地优化，以从多个源域泛化到多个目标域。
- 无源单目标 / 多目标 (“零对一/多”)。在此模式下，$N_T$ 设置为大于 1 的值，而由于在适应阶段源数据集不可用，$N_S$

