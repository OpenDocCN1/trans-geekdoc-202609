

# 推荐系统的深度生成模型 125

在时间 $t-1$ 处，用户的隐特征为 $u_{t-1}$。LSTM 根据 $u_{t-1}$ 和 $t-1$ 计算 $u_t$，以便捕捉用户偏好的演化。类似地，LSTM 的输入是给定该物品的一组用户，而物品的隐表示 $v_i$ 可以通过 LSTM 计算。为了处理不断变化的用户和物品特征，RRRN 还假设用户具有静态特征，标记为 $u_i$ 和 $m_i$。结合用户 $i$ 的动态隐特征 $u_{it}$ 和静态隐特征 $u_i$，以及物品 $j$ 的动态隐特征 $v_{jit}$ 和静态隐特征 $v_{jt}$，评分预测公式为：

```
$\hat{r}_{jit} = u_{it}^T v_{jit} + u_i^T v_{jt}$
```

目标函数是学习 LSTM 的权重和静态隐特征，使得 $r_{jit}$ 接近真实值。

## 6.4 深度生成模型

CTR（节 6.2.4）是一个稳健的模型，它将 LDA 和 PMF 整合成一个用于推荐的统一框架。尽管如此，CTR 的性能很大程度上依赖于 LDA 主题模型的表示能力。遗憾的是，当辅助信息非常稀疏时，LDA 学习到的隐表示并十分有效。前一节表明，深度学习（DL）模型在学习数据表示方面非常出色。在推荐领域，PMF 及其变体仍然是处于最先进的技术，因为它们能够捕捉并学习物品（以及用户）之间的隐式关系 [32]。这使得我们需要将生成式模型与深度学习模型相结合，以创建一个兼顾两者优点的统一框架。。此，我们引入了关于生成式深度学习的两篇最新论文：CDAE [13] 和 CVAE [14]。

### 6.4.1 协同去噪自动编码器

CDAE [13] 是一个层次贝叶斯模型，桥接了生成模型与用于推荐的深度学习之间的差距。图 6.8 显示了 CDAE 的图形结构，它由两部分组成：(a) 堆叠去噪自动编码器 (AAE) [33] 和 (b) PMF 组件。DAE 是一种用于学习输入数据表示（或编码）的前馈神经网络。与 AE 类似，DAE 具有输入层、隐藏层和输出层。这两个模型之间的区别在于输入层，在 DAE 中，输入在传递到网络之前会经过损坏（corrupted）。然后训练 AE 来重构原始的受损版本。图 6.8(a) 显示了 CDAE 的图形结构，(b) 解释了 $W$ 表示神经网络的权重，$X_c$ 是受损坏的数据（即输入层），$X_0$ 是 $J \times S$ 的原始数据，$J$ 是物品数量，$S$ 是词汇表大小。输入 $X$ 通常是物品的文本内容，如产品评论和图像。$l$ 表示神经网络的某一层，$L$ 是总层数，$\{g_1, \dots, g_L\}$ 是 SDAE 的中间层（函数近似器）。物品隐向量 $v$、用户隐向量 $u$ 和观测评分 $R$ 与 CTR 相同。算法 3 的第 1–9 行说明了 DAE 模块（即图 6.8 中的橙色框），第 10–19 行说明了 PMF 模块。在这里，$X_{0j}^*$ 表示物品 $j$ 的词袋，$gt_{lj}^*$ 是隐层 $g_l$ 的某行。本质上，CDAE 遵循与算法 2 中讨论的 CTR 相同的生成原理。一个关键区别是，CDAE 使用 DAE 在隐空间中嵌入物品内容（即第 11–12 行）。可以观察到隐向量 $v_i$ 的内容是从 $g_{l/2}$ 得到的，它是 SDAE 的中间层。CDAE 的目标定义为：

```
$$\arg \min_{W_{bi}} \|X_0 - X_i\|_F^2 + \sum_j \frac{\lambda}{j} \|W_{ij}\|^2$$
```

其中 $W_{bi}$ 是正则化参数，$\|\cdot\|_F$ 是 Frobenius 范数。与 CTR 类似，后验 $P(U, V|X)$ 通过 MAP 估计得到：

```
$$\arg \min_{W_{bi}} \|X_0 - X_i\|_F^2 + \sum_j \frac{\lambda}{j} \|W_{ij}\|^2$$
```

![](img/6dce7dba01af52e1c2fa47d5b0405142_0.png)

物品隐向量 $v$、用户隐向量 $u$ 和观测评分 $R$ 与 CTR 相同。算法 3 的 1–9 行说明 DAE 模块，10–19 行说明 PMF 模块。用户-物品对 $(i,j)$ 采样 $R_{ij} \sim \mathcal{N}(u_i^T v_j, C_{ij}^{-1})$

#### 算法 3：CDAE 的生成过程

1. 对于 SDAE 的每一层 $l \in L$：
2. 对于权重矩阵 $\mathbf{W}_l$ 的每一列 $n$：
3. 采样 $\mathbf{W}_{l,sn} \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
4. 结束
5. 采样偏置向量 $\mathbf{b}_l \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
6. 对于 $\mathbf{g}$ 的每一行 $j$：
7. 采样 $g_{l,js} \sim \mathcal{N}(\sigma((g_{l,js})\mathbf{W}_l + \mathbf{b}_l), \lambda_d^{-1}\mathbf{I}_K)$
8. 结束
9. 结束
10. 对于每个物品 $j \in J$：
11. 采样输入 $X_{0,j^*} \sim \mathcal{N}(g_{Lj,j^*}, \lambda_v^{-1}\mathbf{I}_J)$
12. 采样隐偏移向量 $\epsilon_j \sim \mathcal{N}(0, \lambda_v^{-1}\mathbf{I}_K)$
13. 设置隐向量为 $\mathbf{v}_j = \epsilon_j + g_{Lj/2^*}$
14. 结束
15. 对于每个用户 $u \in U$：
16. 采样 $u_i \sim \mathcal{N}(0, \lambda_u^{-1}\mathbf{I}_K)$
17. 结束
18. 对于每个用户-物品对 $(i,j)$：
19. 采样 $R_{ij} \sim \mathcal{N}(u_i^T v_j, C_{ij}^{-1})$
20. 结束

### 6.4.2 协同变分自动编码器

尽管 CDAE 是一个性能强大的深度学习模型，但它并非完美。去噪组件通过损坏输入来工作，这会损害表示。其次，DAE 没有概率方法；而是频率派方法，这使得难以进行贝斯推断。为了克服这些局限性，Li 等人 [14] 了一种名为 CVAE 的模型。CVAE 的图形结构如图 6.9 所示，顶部部分（红框）表示 VAE 组件，底部部分表示 PMF 组件。首先，VAE 在隐 $Z$ 中引入了随机性，与确定性相比产生了更好的表示。其次，概率性 VAE 允许模型与 PMF 等其他生成模型无缝集成。CVAE 的生成过程如算法 4 所示。

#### 算法 4：CVAE 的生成过程

```
1. 对于 VAE 的每一层 $l \in L$：
2.   对于权重矩阵 $\mathbf{W}_l$ 的每一列 $n$：
3.     采样 $\mathbf{W}_{l,sn} \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
4.   结束
5.   采样偏置向量 $\mathbf{b}_l \sim \mathcal{N}(0, \lambda_w^{-1}\mathbf{I}_K)$
6.   对于 $\mathbf{g}$ 的每一行 $j$：
7.     采样 $g_{l,js} \sim \mathcal{N}(\sigma(g_{l,js}\mathbf{W}_l + \mathbf{b}_l), \lambda_d^{-1}\mathbf{I}_K)$
8.   结束
9.   结束
10. 对于每个物品 $j \in J$：
11.   采样输入 $X_{0,j^*} \sim \mathcal{N}(g_{Lj,j^*}, \lambda_v^{-1}\mathbf{I}_J)$
12.   采样隐偏移向量 $\epsilon_j \sim \mathcal{N}(0, \lambda_v^{-1}\mathbf{I}_K)$
13.   设置隐向量为 $\mathbf{v}_j = \epsilon_j + g_{Lj/2^*}$
14. 结束
15. 对于每个物品 $j \in J$：
16.   采样 $\mu_j \sim \mathcal{N}(g_lW_\mu + b_\mu, \lambda_\mu^{-1}\mathbf{I}_K)$
17.   采样 $\Sigma_j \sim \mathcal{N}(g_lW_\sigma + b_\sigma, \lambda_\sigma^{-1}\mathbf{I}_K)$
18.   采样 $Z_j \sim \mathcal{N}(\mu, \Sigma)$
19. 结束
20. 对于每个用户-物品对 $(i,j)$：
21.   采样 $R_{ij} \sim \mathcal{N}(u_i^T v_j, C_{ij}^{-1})$
22. 结束
```

**参数推断**：本质上，有两种学习 CVAE 参数的方法：(1) 部分变分或 MAP 估计。在这里，我们将解释限制在先验概率上。关于完整变分估计的细节，建议读者参考 [14]。CVAE 的核心推断问题是学习后验分布 $P(Z, U, V|X, R)$。然而，与 LDA 一样

