

![](img/ca72c1626f4850f058a9edc138c1ac73_221_0.png)

图 4.34: 将一个完全连接的 CRF 添加到 CNN 的输出中，以提高分割边界的清晰度。改编自 [Che+15] 的图 3。获得 Jay Chen 的许可使用。

corresponds to the following conditional model:

```
p(\boldsymbol{y}|\boldsymbol{x}) = \frac{1}{Z(\boldsymbol{x})} \left[ \sum_{i \sim j} \psi_{ij}(y_i, y_j) \right] \prod_i p(y_i|\boldsymbol{x}_i)
```

在以下章节中，我们将讨论这种及其他 CRF 模型在计算机视觉中的一些应用。

### 4.4.2.1 语义分割

The task of **semantic segmentation** is to assign a label to every pixel in an image. We can easily solve this problem using a CNN with one softmax output node per pixel. However, this may fail to capture long-range dependencies, since convolution is a local operation.

**语义分割**的任务是为图像中的每个像素分配一个标签。我们可以使用每个像素具有一个 softmax 输出节点的 CNN 轻松解决这个问题。然而，由于卷积是一种局部操作，这可能无法捕获长距离依赖关系。

One way to get better results is to feed the output of the CNN into a CRF. Since the CNN already uses convolution, its outputs will usually already be locally smooth, so the benefits from using a CRF with a local grid structure may be quite small. However, we can sometimes get better results if we use a **fully connected CRF**, which has connections between all the pixels. This can capture long range connections which the grid-structured CRF cannot. See Figure 4.34 for an illustration, and [Che+17a] for details.

获得更好结果的一种方法是将 CNN 的输出馈送到 CRF 中。由于 CNN 已经使用卷积，其输出通常已经是局部平滑的，因此使用具有局部网格结构的 CRF 的益处可能非常小。但是，如果我们使用**完全连接的 CRF**，有时可以获得更好的结果，该 CRF 在所有像素之间都有连接。这可以捕获网格结构 CRF 无法捕获的长距离连接。有关说明，请参见图 4.34，有关详细信息，请参见 [Che+17a]。

Unfortunately, exact inference in a fully connected CRF is intractable, but in the case of Gaussian potentials, it is possible to devise an efficient mean field algorithm, as described in [KK11]. Interestingly, [Zhe+15] showed how the mean field update equations can be implemented using a recurrent neural network (see Section 16.3.4), allowing end-to-end training. Alternatively, if we are willing to use a finite number of iterations, we can just "unroll" the computation graph and treat it as a fixed-sized feedforward circuit. The result is a graph-structured neural network, where the topology of the GNN is derived from the graphical model (cf., Section 9.4.10). The advantage of this compared to standard CRF methods is that we can train this entire model end-to-end using standard gradient descent methods; we no longer have to worry about the partition function (see Section 4.4.3), or the lack of convergence that can arise when combining approximate inference with standard CRF learning.

不幸的是，完全连接的 CRF 中的精确推理是不可处理的，但在高斯势的情况下，可以设计一个高效的均值场算法，如 [KK11] 所述。有趣的是，[Zhe+15] 展示了如何使用循环神经网络实现均值场更新方程（参见第 16.3.4 节），从而允许端到端训练。或者，如果我们愿意使用有限次数的迭代，我们可以直接“展开”计算图并将其视为固定大小的前馈电路。结果是一个图结构神经网络，其中 GNN 的拓扑由图形模型推导（参见第 9.4.10 节）。与标准 CRF 方法相比，这的优势在于我们可以使用标准梯度下降方法对整个模型进行端到端训练；我们不再需要担心配分函数（参见第 4.4.3 节），也不需要担心将近似推理与标准 CRF 学习相结合时可能出现的收敛性缺失问题。

![](img/ca72c1626f4850f058a9edc138c1ac73_222_0.png)

Figure 4.35: Pictorial structures model for a face and body. Each body part corresponds to a node in the CRF whose state space represents the location of that part. The edges (springs) represent pairwise spatial constraints. The local evidence nodes are not shown. Adapted from a figure by Pedro Felzenszwalb.

图 4.35: 面部和人体的图形结构模型。每个身体部位对应 CRF 中的一个节点，其状态空间表示该部件的位置。边（弹簧）表示成对空间约束。未显示局部证据节点。改编自 Pedro Felzenszwalb 的图。

### 4.4.2.2 可变形部件模型

Consider the problem of **object detection**, i.e., finding the location(s) of an object of a given class (e.g., a person or a car) in an image. One way to tackle this is to train a binary classifier that takes as input an image patch and specifies if the patch contains the object or not. We can then apply this to every image patch, and return the locations where the classifier has high confidence detections; this is known as a **sliding window detector**, and works quite well for rigid objects such as cars or frontal faces. Such an approach can be made efficient by using convolutional neural networks (CNNs); see Section 16.3.2 for details.

考虑**目标检测**的问题，即在图像中找到给定类别（例如人或汽车）的对象的位置。解决这个问题的一种方法是训练一个二进制分类器，以图像块作为输入并指定该图像块是否包含该对象。然后我们可以将其应用于每个图像块，并返回分类器具有高置信度检测的位置；这被称为**滑动窗口检测器**，对于汽车或正面人脸等刚性物体效果相当好。使用卷积神经网络（CNN）可以使这种方法变得高效；有关详细信息，请参见第 16.3.2 节。

However, such methods can work poorly when there is occlusion, or when the shape is deformable, such as a person’s or animal’s body, because there is too much variation in the overall appearance. A natural strategy to deal with such problems is break the object into parts, and then to detect each part separately. But we still need to enforce spatial coherence of the parts. This can then be done using a pairwise CRF, where node $y_i$ specifies the location of part $i$ in the image (assuming it is present), and where we connect adjacent parts by a potential function that encourages them to be close together. For example, we can use a pairwise potential of the form $\psi(y_i, y_j | \boldsymbol{x}) = \exp(-d(y_i, y_j))$, where $y_i \in \{1, \dots, K\}$ is the location of part $i$ (a discretization of the 2d image plane), and $d(y_i, y_j)$ is the distance between parts $i$ and $j$. (We can make this "distance" also depend on the inputs $\boldsymbol{x}$ if we want, for example we may relax the distance penalty if we detect an edge.) In addition we will have a local evidence term of the form $p(y_i|\boldsymbol{x})$, which can be any kind of discriminative classifier, such as a CNN, which predicts the distribution over locations for part $i$ given the image $\boldsymbol{x}$. The overall model has the form

然而，当存在遮挡或形状可变形时（例如人或动物的身体），此类方法可能效果不佳，因为整体外观的变化太大。处理此类问题的一种自然策略是将对象分解为部件，然后分别检测每个部件。但我们仍然需要强制执行部件的空间一致性。这可以使用成对 CRF 来完成，其中节点 $y_i$ 指定图像中部件 $i$ 的位置（假设它存在），并且我们通过一个势函数连接相邻部件，该函数鼓励它们彼此靠近。例如，我们可以使用形式为 $\psi(y_i, y_j | \boldsymbol{x}) = \exp(-d(y_i, y_j))$ 的成对势，其中 $y_i \in \{1, \dots, K\}$ 是部件 $i$ 的位置（二维图像平面的离散化），$d(y_i, y_j)$ 是部件 $i$ 和 $j$ 之间的距离。（如果我们愿意，可以使这个“距离”也依赖于输入 $\boldsymbol{x}$，例如，如果我们检测到边缘，可以放宽距离惩罚。）此外，我们将有一个形式为 $p(y_i|\boldsymbol{x})$ 的局部证据项，它可以是任何类型的判别式分类器，例如 CNN，用于预测给定图像 $\boldsymbol{x}$ 时部件 $i$ 的位置分布。整体模型的形式为

```
p(\boldsymbol{y}|\boldsymbol{x}) = \frac{1}{Z(\boldsymbol{x})} \left[ \prod_i p(y_i | f(\boldsymbol{x})_i) \right] \left[ \prod_{(i,j) \in E} \psi(y_i, y_j | \boldsymbol{x}) \right]
```

where $E$ is the set of edges in the CRF, and $f(\boldsymbol{x})_i$ is the $i$’th output of the CNN.

其中 $E$ 是 CRF 中的边集，$f(\boldsymbol{x})_i$ 是 CNN 的第 $i$ 个输出。

We can think of this CRF as a series of parts connected by springs, where the energy of the system increases if the parts are moved too far from their expected relative distance. This is illustrated in Figure 4.35. The resulting model is known as a **pictorial structure** [FE73], or **deformable parts model** [Fel+10]. Furthermore, since this is a conditional model, we can make the spring strengths be image dependent.

我们可以将这个 CRF 看作是一系列由弹簧连接的部件，如果部件被移动得远离其预期相对距离，系统的能量就会增加。图 4.35 对此进行了说明。生成的模型称为**图形结构** [FE73] 或**可变形部件模型** [Fel+10]。此外，由于这是一个条件模型，我们可以使弹簧强度取决于图像。

We can find the globally optimal joint configuration \( y^* = \text{argmax}_y p(y|x, \theta) \) using brute force enumeration in \( O(K^T) \) time, where \( T \) is the number of nodes and \( K \) is the number of states (locations) per node. While \( T \) is often small, (e.g., just 10 body parts in Figure 4.35), \( K \) is often very large, since there are millions of possible locations in an image. By using tree-structured graphs, exact inference can be done in \( O(TK^2) \) time, as we explain in Section 9.3.2. Furthermore, by exploiting the fact that the discrete states are ordinal, inference time can be further reduced to \( O(TK) \), as explained in [Fel+10].

我们可以使用 \( O(K^T) \) 时间的穷举枚举来找到全局最优联合配置 \( y^* = \text{argmax}_y p(y|x, \theta) \)，其中 \( T \) 是节点数，$K$ 是每个节点的状态（位置）数。虽然 $T$ 通常很小（例如，图 4.35 中只有 10 个身体部件），但 $K$ 通常非常大，因为图像中有数百万个可能的位置。通过使用树结构图，精确推理可以在 \( O(TK^2) \) 时间内完成，如第 9.3.2 节所述。此外，通过利用离散状态是有序的事实，推理时间可以进一步减少到 \( O(TK) \)，如 [Fel+10] 所述。

Note that by "augmenting" standard deep neural network libraries with a dynamic programming inference "module", we can represent DPMs as a kind of CNN, as shown in [Gir+15]. The key property is that we can backpropagate gradients through the inference algorithm.

请注意，通过在标准深度神经网络库中“增加”动态规划推理“模块”，我们可以将 DPM 表示为一种 CNN，如 [Gir+15] 所示。关键属性是我们可以通过推理算法反向传播梯度。

### 4.4.3 参数估计

In this section, we discuss how to perform maximum likelihood estimation for CRFs. This is a small extension of the MRF case in Section 4.3.9.1.

在本节中，我们将讨论如何对 CRF 进行最大似然估计。这是第 4.3.9.1 节中 MRF 情况的一个小扩展。

#### 4.4.3.1 对数线性势

In this section we assume the log potential functions are linear in the parameters, i.e.,

```
\(\psi_c(y_c; x, \theta) = \exp(\theta_c^\top \phi_c(x, y_c))\) (4.142)
```

在本节中，我们假设对数势函数对参数是线性的，即，

Hence the log likelihood becomes

```
\(\ell(\theta) \triangleq \frac{1}{N} \sum_n \log p(y_n|x_n, \theta) = \frac{1}{N} \sum_n \left[ \sum_c \theta_c^\top \phi_c(y_{nc}, x_n) - \log Z(x_n; \theta) \right]\) (4.143)
```

因此，对数似然变为

```
\(Z(x_n; \theta) = \sum_y \exp(\theta^\top \phi(y, x_n))\) (4.144)
```

where

其中

is the partition function for example \( n \).

是示例 \( n \) 的配分函数。

We know from Section 2.4.3 that the derivative of the log partition function yields the expected sufficient statistics, so the gradient of the log likelihood can be written as follows:

```
\(\frac{\partial \ell}{\partial \theta_c} = \frac{1}{N} \sum_n \left[ \phi_c(y_{nc}, x_n) - \frac{\partial}{\partial \theta_c} \log Z(x_n; \theta) \right]\) (4.145)
```

根据第 2.4.3 节，我们知道对数配分函数的导数给出了预期充分统计量，因此对数似然的梯度可以写成如下形式：

```
\(= \frac{1}{N} \sum_n \left[ \phi_c(y_{nc}, x_n) - \mathbb{E}_{p(y|x_n, \theta)} [\phi_c(y, x_n)] \right]\) (4.146)
```

Since the objective is convex, we can use a variety of solvers to find the MLE, such as the stochastic meta descent method of [Vis+06], which is a variant of SGD where the stepsize is adapted automatically.

由于目标是凸的，我们可以使用各种求解器来寻找最大似然估计，例如 [Vis+06] 的随机元下降方法，这是一种随机梯度下降（SGD）的变体，其中步长会自动调整。

#### 4.4.3.2 一般情况

In the general case, a CRF can be written as follows:

```
p(\boldsymbol{y}|\boldsymbol{x};\boldsymbol{\theta}) = \frac{\exp(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta}))}{Z(\boldsymbol{x}; \boldsymbol{\theta})} = \frac{\exp(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta}))}{\sum_{\boldsymbol{y}'} \exp(f(\boldsymbol{x}, \boldsymbol{y}';\boldsymbol{\theta}))} \tag{4.147}
```

在一般情况下，CRF 可以写成如下形式：

where \(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta})\) is a scoring (negative energy) function, where high scores correspond to probable configurations. The gradient of the log likelihood is

```
\(\nabla_\theta \ell(\boldsymbol{\theta}) = \frac{1}{N} \sum_{n=1}^N \nabla_\theta f(\boldsymbol{x}_n, \boldsymbol{y}_n; \boldsymbol{\theta}) - \nabla_\theta \log Z(\boldsymbol{x}_n; \boldsymbol{\theta}) \tag{4.148}\)
```

其中 \(f(\boldsymbol{x}, \boldsymbol{y};\boldsymbol{\theta})\) 是一个评分（负能量）函数，高分对应于可能的配置。对数似然的梯度是

Computing derivatives of the log partition function is intractable provided we can compute the corresponding expectations, as we discuss in Section 4.3.9.2. Note, however, that we need to compute these derivatives for every training example, which is slower than the MRF case, where the log partition function is a constant independent of the observed data (but dependent on the model parameters).

计算对数配分函数的导数是不可处理的，前提是我们可以计算相应的期望，如第 4.3.9.2 节所述。然而，请注意，我们需要为每个训练示例计算这些导数，这比 MRF 情况更慢，在 MRF 情况中，对数配分函数是与观测数据无关但与模型参数有关的常数。

### 4.4.4 结构化预测的其他方法

Many other approaches to structured prediction have been proposed, going beyond CRFs. For example, **max margin Markov networks** [TGK03], and the closely related **structural support vector machine** [Tso+05], can be seen as non-probabilistic alternatives to CRFs. More recently, [BYM17] proposed **structured prediction energy networks**, which are a form of energy based model (Chapter 24), where we predict using an optimization procedure, \(\hat{\boldsymbol{y}}(\boldsymbol{x}) = \text{argmin}_\boldsymbol{y} \mathcal{E}(\boldsymbol{x}, \boldsymbol{y})\). In addition, it is common to use graph neural networks (Section 16.3.6) and sequence-to-sequence models such as transformers (Section 16.3.5) for this task.

已提出许多其他结构化预测方法，超出了 CRF 范畴。例如，**最大边缘马尔可夫网络** [TGK03] 和密切相关的**结构支持向量机** [Tso+05] 可以被视为 CRF 的非概率替代方案。更近期地，[BYM17] 提出了**结构化预测能量网络**，这是一种基于能量的模型（第 24 章），其中我们使用优化程序进行预测，\(\hat{\boldsymbol{y}}(\boldsymbol{x}) = \text{argmin}_\boldsymbol{y} \mathcal{E}(\boldsymbol{x}, \boldsymbol{y})\)。此外，通常使用图神经网络（第 16.3.6 节）和序列到序列模型（如变换器，第 16.3.5 节）来完成此任务。

## 4.5 比较有向和无向 PGM

In this section, we compare DPGMs and UPGMs in terms of their modeling power, we discuss how to convert from one to the other, and present a unified representation.

在本节中，我们将比较 DPGM 和 UPGM 的建模能力，讨论如何将一种转换为另一种，并提出一种统一的表示。

### 4.5.1 CI 属性

Which model has more "expressive power", a DPGM or a UPGM? To formalize the question, recall from Section 4.2.4 that \(G\) is an I-map of a distribution \(p\) if \(I(G) \subseteq I(p)\), meaning that all the CI statements encoded by the graph \(G\) are true of the distribution \(p\). Now define \(G\) to be **perfect map** of \(p\) if \(I(G) = I(p)\), in other words, the graph can represent all (and only) the CI properties of the distribution. It turns out that DPGMs and UPGMs are perfect maps for different sets of distributions (see Figure 4.36). In this sense, neither is more powerful than the other as a representation language.

哪个模型具有更多的“表达能力”，DPGM 还是 UPGM？为了形式化这个问题，回顾第 4.2.4 节，$G$ 是分布 $p$ 的 I-图，如果 \(I(G) \subseteq I(p)\)，这意味着图 $G$ 编码的所有 CI 语句对于分布 $p$ 都成立。现在定义 $G$ 为 $p$ 的**完美图**，如果 \(I(G) = I(p)\)，换句话说，图可以表示分布的所有（且仅所有）CI 属性。结果表明，DPGM 和 UPGM 是不同分布集合的完美图（参见图 4.36）。从这个意义上说，两者作为表示语言都并不比另一个更强大。

As an example of some CI relationships that can be perfectly modeled by a DPGM but not a UPGM, consider a v-structure \(A \rightarrow C \leftarrow B\). This asserts that \(A \perp B\), and \(A \not\perp B | C\). If we drop the arrows, we get \(A - C - B\), which asserts \(A \perp B | C\) and \(A \not\perp B\), which is not consistent with the independence statements encoded by the DPGM. In fact, there is no UPGM that can precisely

作为可以由 DPGM 完美建模但 UPGM 无法建模的某些 CI 关系的示例，考虑 v-结构 \(A \rightarrow C \leftarrow B\)。这断言 \(A \perp B\)，以及 \(A \not\perp B | C\)。如果我们去掉箭头，就会得到 \(A - C - B\)，它断言 \(A \perp B | C\) 和 \(A \not\perp B\)，这与 DPGM 编码的独立性语句不一致。实际上，没有 UPGM 可以精确

