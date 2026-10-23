
## 23.4.3.1 Sampling-based spatial methods

为了克服 GCNs 的域依赖性和存储限制，Hamilton、Ying 和 Leskovec [HYL17] 提出了 **GraphSAGE**，一个用于学习归纳节点嵌入的框架。与通过与拉普拉斯矩阵相乘来对所有一跳邻居的信号进行平均不同，SAGE 为每个节点采样固定邻域（大小为 *q*）。这消除了对固定图结构的强依赖，并允许泛化到新图。在每个 SAGE 层中，节点会从其邻域中采样的节点聚合信息（见图 23.5）。在 GraphEDM 符号中，传播规则可以写为：

$\mathbf{H}^{l+1}_{:,i} = \sigma(\Theta_1^l \mathbf{H}^l_{:,i} + \Theta_2^l \text{AGG}(\{\mathbf{H}^l_{:,j} \mid v_j \in \text{Sample}(\text{nbr}(v_i), q)\})),$ (23.27)

其中 $\text{AGG}(\cdot)$ 是一个聚合函数。该聚合函数可以是任何置换不变算子，例如平均（SAGE-mean）或最大池化（SAGE-pool）。由于 SAGE 使用固定大小的邻域（而不是整个邻接矩阵），它还降低了训练 GCN 的计算复杂度。

## 23.4.3.2 Attention-based spatial methods

注意力机制（第 15.4 节）在语言模型中已被成功使用，其中它们例如允许模型识别长序列输入中的相关部分。受其在语言中成功应用的启发，类似的想法已被提出用于图卷积网络。这类基于图的注意力模型通过在节点特征之上学习的参数化补丁，在消息传递步骤中学习关注重要邻居。这与依赖于固定权重的方法（如 GCN）相比，在归纳设置中提供了更大的灵活性。

**图注意力网络**（GAT）模型 [Vel+18] 是 GCN 的基于注意力的版本。在每个 GAT 层中，它会关注每个节点的邻域并学习选择性地挑选节点以实现某些下游任务的最佳性能。其直觉与 SAGE [HYL17] 相似，使得 GAT 适用于归纳和跨归纳问题。然而与 SAGE 不同，SAGE 将卷积步骤限制为固定大小邻域，而 GAT 允许每个节点关注其所有邻居——为每个邻居分配不同的权重。注意力参数通过反向传播训练，然后注意力分数使用 softmax 激活进行行归一化。

## 23.4.3.3 Geometric spatial methods

Monti 等人 [Mon+17] 提出了 **MoNet**，一个通用框架，当节点特征位于几何空间中时效果特别好，例如 3D 点云或网格。MoNet 使用预定义空间域（例如空间坐标）中的参数函数学习注意力补丁，然后在 resulting 图域中应用卷积滤波器。

MoNet 概括了引入流形上卷积构造的空间方法，例如测地线 CNN（GCNN）[Mas+15] 和各向异性 CNN（ACNN）[Bos+16]。GCNN 和 ACNN 都使用在特定坐标系上定义的固定补丁，因此无法泛化到图结构数据。然而，MoNet 框架更通用；任何伪坐标（即节点特征）都可用于诱导补丁。更正式地，如果 $\mathbf{U}^s$ 是伪坐标，$\mathbf{H}^l$ 是来自另一个域的特征，则 MoNet 层可以用我们的符号表示为：

$$\mathbf{H}^{\ell+1} = \sigma\left(\sum_{k=1}^{K}(\mathbf{W} \odot g_k(\mathbf{U}^s))\mathbf{H}^{\ell}\Theta_k^{\ell}\right),$$ (23.28)

其中 $g_k(U^s)$ 是学习的参数化补丁，是 $N \times N$ 矩阵。实际上，MoNet 使用高斯核来学习补丁，使得：

$$g_k(\mathbf{U}^s) = \exp\left(-\frac{1}{2}(\mathbf{U}^s - \boldsymbol{\mu}_k)^\top \boldsymbol{\Sigma}_k^{-1}(\mathbf{U}^s - \boldsymbol{\mu}_k)\right),$$ (23.29)

其中 $\boldsymbol{\mu}_k$ 和 $\boldsymbol{\Sigma}_k$ 是学习参数，且 $\boldsymbol{\Sigma}_k$ 被限制为对角。

## 23.4.4 Non-Euclidean Graph Convolutions

正如我们在第 23.3.3 节中所讨论的，双曲几何能够学习层次图的浅层嵌入，其失真小于欧几里得嵌入。然而，浅层嵌入的一个主要缺点是它们在图之间泛化能力很差（如果有的话）。另一方面，利用节点特征的图神经网络在许多归纳图嵌入任务上取得了良好的结果。

因此，自然地，最近出现了将图神经网络扩展以学习非欧几里得嵌入的兴趣。这样做的一个主要挑战再次围绕卷积本身的性质。我们如何在非欧几里得空间中执行卷积，在该空间中标准操作如内积和矩阵乘法未定义？

双曲图卷积网络（HGCN）[Cha+19a] 和双曲图神经网络（HGNN）[LNK19] 通过利用欧几里得切空间在双曲空间中应用图卷积，该空间提供了双曲流形在某一点处的一阶近似。对于每个图卷积步骤，节点嵌入被映射到原点处的欧几里得切空间，在那里应用卷积，然后映射回双曲空间。这些方法在表现出层次结构的图上取得了显著改进（图 23.6）。

## 23.5 Deep graph embeddings

在本节中，我们使用图神经网络在无监督和半监督情况下设计图嵌入。

## 23.5.1 Unsupervised embeddings

本节讨论 GNN 的无监督损失，如图 23.7 所示。

## 23.5.1.1 Structural deep network embedding

**结构深度网络嵌入**（SDNE）方法 [WCZ16] 使用保持一阶和二阶节点邻近性的自编码器。SDNE 编码器将邻接矩阵的一行作为输入（设置 $s(\mathbf{W}) = \mathbf{W}$）并产生节点嵌入 $\mathbf{Z} = \mathrm{ENC}(\mathbf{W}; \theta^E)$。（注意，这忽略了任何节点特征。）SDNE 解码器返回 $\widehat{\mathbf{W}} = \mathrm{DEC}(\mathbf{Z}; \Theta^D)$，一个重建

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_754_0.png)

(a) GCN 层。

(b) HGCN 层。

图 23.6：欧几里得（左）和双曲（右）树图的嵌入。双曲嵌入学习嵌入空间中的自然层次结构（深度由颜色指示）。经 [Cha+19a] 许可转载。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_754_1.png)

图 23.7：无监督图神经网络。图结构和输入特征被映射为图神经网络编码器的低维嵌入。然后解码嵌入以计算图正则化损失（无监督）。经 [Cha+20] 许可转载。

训练以恢复原始图邻接矩阵。SDNE 通过最小化以下损失来保持二阶节点邻近性：

$$\| (s(\mathbf{W}) - \widehat{\mathbf{W}}) \cdot \mathbb{I}(s(\mathbf{W}) > 0) \|_F^2 + \alpha_{\text{SDNE}} \sum_{ij} s(\mathbf{W})_{ij} \| \mathbf{Z}_i - \mathbf{Z}_j \|_2^2 \tag{23.30}$$

第一项类似于矩阵分解正则化目标，只是 $\widehat{\mathbf{W}}$ 不是通过外积计算的。第二项被基于距离的浅层嵌入方法使用。

## 23.5.1.2 (Variational) graph auto-encoders

Kipf 和 Welling [KW16b] 使用图卷积（第 23.4.2 节）学习节点嵌入 $\mathbf{Z} =$ GCN$(\mathbf{W}, \mathbf{X}; \Theta^E)$。解码器是外积：DEC$(\mathbf{Z}; \Theta^D) = \mathbf{Z}\mathbf{Z}^\top$。图重建项是真实邻接与预测边相似度分数之间的 sigmoid 交叉熵：

$$\mathcal{L}_{G,\text{RECON}}(\mathbf{W}, \widehat{\mathbf{W}}; \Theta) = - \left( \sum_{i,j} (1 - \mathbf{W}_{ij}) \log(1 - \sigma(\widehat{\mathbf{W}}_{ij})) + \mathbf{W}_{ij} \log \sigma(\widehat{\mathbf{W}}_{ij}) \right). \tag{23.31}$$
