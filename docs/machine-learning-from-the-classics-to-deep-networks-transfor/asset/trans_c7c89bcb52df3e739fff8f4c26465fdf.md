

## 深度信念网络

$P\left( h_{i}^{k}|\mathbf{h}^{k + 1} \right) = \sigma\left( \sum\limits_{j = 1}^{I_{k + 1}}\theta_{ij}^{k + 1}h_{j}^{k + 1} \right),\quad k = 1,2,\ldots,K - 1,\ i = 1,2,\ldots,I_{k}.$

![Equation](images/B9780443292385000251/si29.png)

![Figure 19.3 (A) A graphical model corresponding to a sigmoidal belief (Bayesian) network. (B) A graphical model corresponding to a deep belief network. It is a mixture of directed and undirected edges connecting nodes. The top layer involves undirected connections and it corresponds to an RBM.](images/B9780443292385000251/gr003.jpg)

**图 19.3** (A) 对应于 S 型信念（贝叶斯）网络的图模型。(B) 对应于深度信念网络的图模型。它是连接节点的有向边和无向边的混合。顶层涉及无向连接，并对应于一个 RBM。

S 型网络的一个变体在文献 [80] 中被提出，后来被称为 `deep belief network`（深度信念网络）。它与 S 型网络的区别在于，顶层的两层构成了一个 `RBM`。因此，它是一种由有向边和无向边组成的混合类型网络。相应的图模型如 **图 19.3(B)** 所示。所有涉及变量的联合概率由下式给出：

$P\left( \mathbf{x},\mathbf{h}^{1},\ldots,\mathbf{h}^{K} \right) = P\left( \mathbf{x}|\mathbf{h}^{1} \right)\left( \prod\limits_{k = 1}^{K - 2}P\left( \mathbf{h}^{k}|\mathbf{h}^{k + 1} \right) \right)P\left( \mathbf{h}^{K - 1},\mathbf{h}^{K} \right).$

![Equation](images/B9780443292385000251/si30.png) (19.5)

众所周知，由于汇聚边的存在（见第 15.3.3 节），学习规模相对较大的贝叶斯网络是难以处理的。为此，可以调用变分近似方法来绕过这一障碍（见第 16.3 节）。

文献 [80] 提出了一条替代路径，遵循的方案类似于之前用于神经网络预训练的方案。换句话说，从输入层开始的所有隐藏层都被视为 `RBMs`，并采用了一种自底向上的贪婪逐层预训练理念。必须强调的是，通过这种方案恢复的条件概率只能被视为真实条件概率的近似。毕竟，原始图是有向的，而不是 `RBM` 假设所施加的无向图。唯一的例外在于顶层，在那里 `RBM` 假设是有效的。

一旦自底向上的过程完成，估计出的未知参数值将被用于初始化另一种微调训练算法；这种方案在文献 [79] 中为训练 S 型网络而开发，被称为 `wake-sleep`（唤醒-睡眠）算法。`wake-sleep` 方案的目标是在自顶向下的过程中调整权重，以最大化网络生成观测数据的概率。该方案具有变分近似的特点，如果随机初始化，收敛需要很长时间。然而，使用从预训练获得的值进行初始化，该过程可以显著加速 [83]。

