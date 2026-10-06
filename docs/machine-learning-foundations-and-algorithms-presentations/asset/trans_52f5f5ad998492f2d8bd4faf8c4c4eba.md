

## 图神经网络 (GNNs)

![](img/f01928df50903c99ce023dd3c527a33d_555_0.png)

新符号：$\mathcal{G} = \{\mathbf{A}, \mathbf{X}\}$

- 邻接矩阵 $\mathbf{A} \in \mathbb{R}^{N \times N}$
- 特征矩阵 $\mathbf{X} \in \mathbb{R}^{N \times F}$

- **核心思想**：在节点对之间传递消息并聚合
- **另一种解释**：在节点之间传递消息以优化节点（可能可能的边）的表示/特征

## 回顾：网格上的卷积神经网络 (CNNs)

带有 3x3 滤波器的单层 CNN：

![](img/f01928df50903c99ce023dd3c527a33d_556_0.png)

针对单个像素的更新：

- 独地转换消息 $W_i h_i$
- 将所有结果相加 $\sum_i W_i h_i$

$h_0 \quad h_1 \quad \dots$
$h_i$

$h_i \in \mathbb{R}^F$ 是像素/节点的（隐藏层）激活值

## 回顾：网格上的卷积神经网络 (CNNs)

### 带有 3x3 滤波器的单层 CNN：

![](img/f01928df50903c99ce023dd3c527a33d_557_0.png)

### 针对单个像素的更新：

- 独地转换消息 $W_i h_i$
- 将所有结果相加 $\sum_i W_i h_i$

$h_i \in \mathbb{R}^F$ 是像素/节点的（隐藏层）激活值

### 全量更新：

```
$h_4^{(l+1)} = \sigma \left(W_0^{(l)}h_0^{(l)} + W_1^{(l)}h_1^{(l)} + \dots + W_8^{(l)}h_8^{(l)} \right)$
```

## 图卷积网络 (GCNs)

考虑这个无向图：

![](img/f01928df50903c99ce023dd3c527a33d_558_0.png)

## 图卷积网络 (GCNs)

考虑这个无向图：

计算红色节点的更新：

聚合来自邻居节点的所有信息以更新表示

![](img/f01928df50903c99ce023dd3c527a33d_559_0.png)

## 图卷积网络 (GCNs)

考虑这个无向图：

计算红色节点的更新：

聚合来自邻居节点的所有信息以更新表示

![](img/f01928df50903c99ce023dd3c527a33d_560_0.png)

理想的属性：

- 所有位置的权重共享
- 对排列的不不变性
- 线性复杂度 O(E)

```
更新规则: $h_i^{(l+1)} = \sigma \left( h_i^{(l)} W_0^{(l)} + \sum_{j \in \mathcal{N}_i} \frac{1}{c_{ij}} h_j^{(l)} W_1^{(l)} \right)$
```

可扩展性：消息下采样 [Hamilton et al., NIPS 2017]

$\mathcal{N}_i$ : 邻居索引 $c_{ij}$ : 归一常数（固定/可训练）

Kipf & Welling (ICLR 2017)，Duvenaud 等人 (NIPS 2015) 和 Li 等人 (ICLR 2016) 的相关之前工作

Gerhard Neumann | 机器学习 | KIT | SS 2024

## 带有边嵌入的 GNNs

![](img/f01928df50903c99ce023dd3c527a33d_561_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_561_1.png)

边特征

节点特征

形式化：$v\to e : h_{(i,j)}^l = f_e^l([h_i^l, h_j^l, \mathbf{x}_{(i,j)}^l])$
$e\to v : h_j^{l+1} = f_v^l(\sum_{i\in\mathcal{N}_j} h_{(i,j)}^l, \mathbf{x}_j)$

## 带有边嵌入的 GNNs

![](img/f01928df50903c99ce023dd3c527a33d_562_0.png)

### 优点：

- 支持边特征
- 比 GCN 表达能力更
- 非常通用

### 缺点：

- 需要存储中间的激活值
- 限于小图

形式化：$v\leftarrow e : h_{(i,j)}^l = f_e^l([h_i^l, h_j^l])$
$e\leftarrow v : h_j^{l+1} = f_v^l(\sum_{i\in\mathcal{N}_j} h_{(i,j)}^l, \mathbf{x}_j)$

## 带有注意力机制的图神经网络 (GNNs)

![](img/f01928df50903c99ce023dd3c527a33d_563_0.png)

[来自 Veliković 等人 (ICLR 2018) 的图]

```
$$\vec{h}'_i = \sigma \left( \frac{1}{K} \sum_{k=1}^K \sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j \right)$$
```
i 等人 (CVPR 2017), Vos (NIPS 2017), Veliković 等人 (ICLR 2018)

Gerhard Neumann | 机器学习 | KIT | SS 2024

## 注意力机制

### 多头注意力：

末层
$$\vec{h}_i' = \sigma \left(\frac{1}{K} \sum_{k=1}^K \sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j\right)$$

前层
$$\vec{h}_i' = \sigma \left(\sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j\right)$$

- K 个不同的头
- 在末层平均，在前层层拼接
- || 表示拼接
$$\frac{\exp\left(\text{LeakyReLU}(\vec{a} || \vec{h}_j)\right)}{\sum_{k \in \mathcal{N}_i} \exp\left(\text{LeakyReLU}(\vec{a} || \vec{h}_k)\right)}$$
### 注意力权重：$\alpha_{ij} =$

- Softmax 激活
- 由 $\mathbf{W} \in \mathbb{R}^{F' \times F}$ 和 $\vec{a} \in \mathbb{R}^{F'}$ 参数

## 带有注意力机制的图神经网络 (GNNs)

![](img/f01928df50903c99ce023dd3c527a33d_565_0.png)

优点：

- 不需要存储中间的激活值（当使用点积注意力时）
- 比带有边嵌入的 GNNs 慢

缺点：

- 表达能力可能低于带有边嵌入的 GNNs
- 可能更难优化

[来自 Veliković 等人 (ICLR 2018) 的图]

## GNNs / GCNs 的分类与链接预测

输入：特征矩阵 $X \in \mathbb{R}^{N \times E}$，预处理的邻接矩阵 $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_566_0.png)

节点分类：$softmax(z_n)$，例如 Kipf & Welling (ICLR 2017)

$H^{(l+1)} = \sigma \left(\hat{A}H^{(l)}W^{(l)}\right)$ $Z = H^{(L)}$

权重共享：每个消息传递层都有自己的权重

## GNNs / GCNs 的分类与链接预测

输入：特征矩阵 $X \in \mathbb{R}^{N \times E}$，预处理的邻接矩阵 $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_567_0.png)

$H^{(l+1)} = \sigma \left(\hat{A}H^{(l)}W^{(l)}\right)$

权重共享：每个消息传递层都有自己的权重

## GNNs / GCNs 的分类与链接预测

输入：特征矩阵 $X \in \mathbb{R}^{N \times E}$，预处理的邻接矩阵 $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_568_0.png)

节点分类：$softmax(\mathbf{z}_n)$，例如 Kipf & Welling (ICLR 2017)

图分类：$softmax(\sum_n \mathbf{z}_n)$，例如 Duvenaud 等人 (NIPS 2015)

链接预测：$p(A_{ij}) = \sigma(\mathbf{z}_i^T \mathbf{z}_j)$
Kipf & Welling (NIPS 2016)
“图自动编码器”

权重共享：每个消息传递层都有自己的权重

## 图上的半监督分类

设置：
某些节点已标记（黑色圆圈）
所有其他节点均未标记

任务：
预测未标记节点的标签

![](img/f01928df50903c99ce023dd3c527a33d_569_0.png)

## 图上的半监督分类

设置：
某些节点已标记（黑色圆圈）
所有其他节点均未标记

任务：
预测未标记节点的标签

![](img/f01928df50903c99ce023dd3c527a33d_570_0.png)

仅在标记节点上评估损失：

```
$$\mathcal{L} = -\sum_{l\in\mathcal{Y}_L} \sum_{f=1}^{F} Y_{lf} \ln Z_{lf}$$
```

- $\mathcal{Y}_L$ 标记节点索引集
- $\mathbf{Y}$ 标签矩阵
- $\mathbf{Z}$ GCN 输出（经过 softmax）

## 图上的半监督分类

设置：
某些节点已标记（黑色圆圈）
所有其他节点均未标记

任务：
预测未标记节点的标签

![](img/f01928df50903c99ce023dd3c527a33d_571_0.png)

仅在标记节点上评估损失：

$$\mathcal{L} = -\sum_{l \in \mathcal{Y}_L} \sum_{f=1}^{F} Y_{if} \ln Z_{if}$$

$\mathcal{Y}_L$ 标记节点索引
$Y$ 标签矩阵
$Z$ GCN 输出（经过 softmax）

| 方法 | Citeseer | Cora | Pubmed | NELL |
|---|---|---|---|---|
| ManiReg [3] | 60.1 | 59.5 | 70.7 | 21.8 |
| SemiEmb [28] | 59.6 | 59.0 | 71.1 | 26.7 |
| LP [37] | 45.3 | 58.0 | 63.0 | 26.5 |
| DeepWalk [22] | 43.2 | 67.2 | 65.3 | 25.1 |
| ICA [18] | 69.1 | 75.1 | 79.9 | 58.3 |
| Planetoid* [29] | 64.1 (6cks) | 75.7 (13s) | 77.2 (25s) | 61.0 (185s) |
| GCN (本文) | 70.3 (7s) | 81.5 (4s) | 79.0 (38s) | 66.0 (48s) |
| GCN (随机划分) | 67.9 ± 0.5 | 80.1 ± 0.5 | 78.9 ± 0.7 | 58.4 ± 1.7 |

