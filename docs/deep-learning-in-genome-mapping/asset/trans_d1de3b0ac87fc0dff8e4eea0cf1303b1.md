

*σ* 是非线性激活函数（例如 ReLU）。

经过 *L* 层后的最终节点表示 *h[v]*^(*L*) 捕获了图的局部结构和节点特征。拟议的 [Algorithm 1](#ch1.xhtml#alg1_1) 按步骤详细说明。

| Algorithm 1 Graph Neural Network for Genome Mapping |
| --- |
| **Require:** Graph *G* = (*V*, *E*) with node features *H*^(0). |

| --- |

**Require:** Number of GNN layers *L*, weight matrices *W*^(*l*) for each layer *l*, and activation function *σ*. **Ensure:** Node embeddings *H*^(*L*) for each node *v* ∈ *V*.

1. Initialize node features *H*^((0)) **for** *each layer l* = 0 to *L −* 1 **do** each node *v* ∈ *V*

2. Aggregate information from neighbors:

   (2)

   `m[v]^((l)) = AGG({h[u]^((l)) | u ∈ N(v) ∪ {v}})`

3. Update node feature:

   (3)

   `h[v]^((l + 1)) = σ(W^((l)) ⋅ m[v]^((l)))`

4:

5:

6: **return** Final node embeddings *H*^(*L*).

| --- |

### 4.2 Graph Convolutional Networks (GCNs)

GCN 是 GNN 的一种特殊形式，其聚合步骤基于图的归一化邻接矩阵。GCN ([Rentao et al. 2024](#ch1.xhtml#ref1_27)) 层的更新规则如下：

(4)

$$H^{(l + 1)} = \\sigma\\left( {\\overset{\\sim}{D}}^{- 1/2}\\overset{\\sim}{A}{\\overset{\\sim}{D}}^{- 1/2}H^{(l)}W^{(l)} \\right)$$

其中：

*   *H*^(*l*) 是第 *l* 层的节点特征矩阵，每一行对应一个节点。
*   *A*̃ = *A* + *I* 是添加自环（即单位矩阵 *I*）后的图邻接矩阵。
*   *D*̃ 是 *A*̃ 的度矩阵。
*   *W*^(*l*) 是第 *l* 层的可学习权重矩阵。
*   *σ* 是非线性激活函数。

拟议的 [Algorithm 2](#ch1.xhtml#alg1_2) 按步骤详细说明。GCN 每一层的更新规则如下：

| Algorithm 2 GCN Layer Update |
| --- |
| **Require:** Adjacency matrix *A*̃, degree matrix *D*̃, node feature matrix *H*^(*l*) , weight matrix *W*^(*l*) , and activation function *σ*. **Ensure:** Updated node feature matrix *H*^(*l*^(+1)). |

| --- |

1. Compute normalized adjacency matrix:

   (5)

   $${\\overset{\\sim}{A}}\_{\\text{norm}} = {\\overset{\\sim}{D}}^{- 1/2}\\overset{\\sim}{A}{\\overset{\\sim}{D}}^{- 1/2}$$

2. Update node features:

   (6)

   $$H^{(l + 1)} = \\sigma\\left( {\\overset{\\sim}{A}}\_{\\text{norm}}H^{(l)}W^{(l)} \\right)$$

3. **return** Updated node features *H*^(*l*^(+1)).

| --- |

### 4.3 Training a GNN

GNN 通过最小化基于当前任务的损失函数进行训练。节点分类常用的损失函数是交叉熵损失：

(7)

$$\\mathcal{L} = - \\sum\\limits\_{v \\in V}\\sum\\limits\_{c = 1}^{C}y\_{v,c}\\log{\\hat{y}}\_{v,c}$$

其中：

*   *y[v]*[,]*[c]* 是真实标签（二进制），指示节点 *v* 是否属于类 *c*。
*   *ŷ[v]*[,]*[c]* 是节点 *v* 属于类 *c* 的预测概率，通常使用 softmax 函数获得。
*   *C* 是类的总数。

GNN 的训练过程总结在以下 [Algorithm 3](#ch1.xhtml#alg1_3) 中：

| Algorithm 3 Training Graph Neural Network |
| --- |
| **Require:** Training data (*X*, *Y* ), GNN model with parameters *θ*, learning rate *η*, and number of epochs *T*. **Ensure:** Trained GNN model parameters *θ*. |

| --- |

1. **for** *each epoch t* = 1 to *T* **do**

   Forward pass: Compute node embeddings *H*^(*L*) using [Algorithm 1](#ch1.xhtml#alg1_1).

2. Compute loss function:

   (8)

   $$\\mathcal{L} = - \\sum\\limits\_{v \\in V}\\sum\\limits\_{c = 1}^{C}y\_{v,c}\\log{\\hat{y}}\_{v,c}$$

3. Backpropagate and update parameters:

   (9)

   $$\\theta = \\theta - \\eta\\frac{\\partial\\mathcal{L}}{\\partial\\theta}$$

4:

5: **return** Trained model parameters *θ* = 0.

| --- |

GNN 主要适用于基因组映射，因为基因组统计数据可以表示为图，其中节点对应基因或基因组区域，边缘构成包括调节相互作用、基因共表达 ([Feng et al. 2024](#ch1.xhtml#ref1_8)) 在内的关系。拟议的框架可以研究丰富的节点级表示，捕获基因的特性属性及其与基因组中其他基因的关系。这将导致更准确的基因组映射和对基因特征、相互作用及突变的更好理解。我们以一套规则的形式介绍了基于 GNN 的深度学习方法用于基因组映射。这套规则概述了下一节的方法。

### 4.4 Graph Neural Network with DE Optimization for Genome Mapping

拟议的 [Algorithm 4](#ch1.xhtml#alg1_4) 将 GNN 与 DE 优化相结合，以增强基因组映射任务的性能。GNN 在选择图形中节点之间的复杂关系方面非常有效，例如生物网络中的基因或蛋白质。该架构涉及多个层，其中节点功能通过聚合机制迭代更新，该机制考虑邻接节点，使模型能够学习基础数据的丰富表示。拟议的技术中，DE 被用作优化方法 ([Joshi et al. 2024](#ch1.xhtml#ref1_12)) 以自适应地搜索控制节点特征变化的最佳权重矩阵。DE 特别适合此任务，因为它在探索搜索空间方面具有鲁棒性，并且能够处理不可微分和复杂的适应性景观，这在深度学习应用中很常见。该规则首先初始化候选解种群，每个候选解代表一组 GNN 的权重。DE 生成新的候选解，根据其适应性改进前几代。每个候选解的适应性由 GNN 的分类准确性决定，使用损失函数量化节点预测标签与实际标签之间的差异。选择方法确保只有表现最好的候选解能存活到下一代，使规则能够收敛到一组最佳权重。该规则的有效性归功于其能够建模图形数据中的复杂依赖性，同时采用一种不易陷入局部最小值的全局优化技术。因此，这种方法在计算生物学的各种应用中具有前景，特别是在基因预测、蛋白质-蛋白质相互作用预测以及其他需要理解生物网络中复杂关系的领域。

| Algorithm 4 Graph Neural Network with DE Optimization for Genome Mapping |
| --- |
| **Require:** Graph *G* = (*V*, *E*) with node features *H*^((0)) , Number of GNN layers *L*, Population size *P* for DE, Mutation factor *F* for DE, Crossover probability *CR* for DE, Number of generations *G*, Activation function *σ*. **Ensure:** Optimized GNN model parameters *θ* and node embeddings *H*^(*L*) for each node *v* ∈ *V*. |

| --- |

1. **Initialization:**

   *   Initialize node features *H*^((0)).

   *   Randomly initialize the population of weight matrices *θ*[1] , *θ*[2] ,... , *θ[P]* where each *θ[i]* contains the weight matrices *W*^(*l*) for *l* = 0, 1,..., *L*.

       *   **for** *generation g* = 1 to *G* **do**

           Iterate over DE generations

       *   **for** *each candidate solution θ[i] in population* **do**

           For each individual in the population

2. **Mutation:** Create a mutated solution *θ[i] ′* for each candidate using three randomly selected distinct individuals *θ[r]*[1] , *θ[r]*[2] , *θ[r]*[3] :

