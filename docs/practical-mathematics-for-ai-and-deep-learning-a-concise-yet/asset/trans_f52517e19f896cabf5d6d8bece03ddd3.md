

```python
1. row_wise_L1 = tf.abs(
2.     tf.map_fn(lambda x: x - 2. features,
3.               tf.expand_dims(2. features, [1])))
4.
5. sim_scores = tf.exp(-tf.reduce_sum(row_wise_L1), axis=[3]))
6. sim_score_out = tf.reduce_sum(sim_scores, axis=[1])
```

因此，对于大小为 n 的整个批次，我们得到一组维度为 K 的 n 个向量。我们可以将这些向量连接到中间层输出 `f(images/890.jpg)`，并将结果送入判别器的下一层。生成器样本和训练数据的小批量特征是分别计算的。现在，如果生成器生成一批外观相似的图像，判别器可以很容易地从小批量判别特征获得非常高的值中捕捉到这一点。

*   **其他代价函数**：对于 VAE，我们使用 KL 散度来定义损失函数；对于 GAN，我们使用 **Jensen-Shannon (JS) 散度** 来定义损失函数。通过一个简单的例子，我们可以看到这两种度量都具有一些可能抑制梯度下降稳定学习的特性。Wasserstein 距离或土方距离是量化两个概率分布相似性的另一种度量。使用该度量，我们可以定义另一类称为 WGAN 或 Wasserstein GAN 的 GAN，其表现出更好的学习稳定性。实验观察表明，WGAN 总是能避免模式崩塌。

*   **在判别器和生成器中均使用类别标签信息**：条件 GAN 意味着生成器和判别器都可以基于某种辅助信息 `y` 进行条件化。这里，`y` 可以是类别标签或来自其他模态的数据。例如，`y` 可以是自由文本形式的图像描述，或结构化形式，或者 `y` 可以是图像类别。

# Wasserstein GAN (WGAN)

WGAN 基于我们在 *[第 4 章：基础统计与概率论](#c04.xhtml)* 中遇到的两个分布 `images/2911.jpg` 和 `images/2912.jpg` 之间的 Wasserstein 距离或 **Earth Movers’ (EM) 距离（土方距离）**。我们已经看到，使用极大极小目标训练 GAN 等价于最小化 JS 散度：`images/2913.jpg`。WGAN 将优化问题重新表述为真实分布与生成分布之间 Wasserstein 距离的最小化：`images/2914.jpg` 和 `images/2915.jpg`。EM 距离是连续的，且几乎处处可导（即不可导点的集合非常少）。因此，我们可以将判别器训练至最优，并避免梯度消失问题。

概率分布可以解释为在一个区域上堆叠单位质量的泥土。因此，两个不同的概率分布代表在该区域上堆叠单位量泥土的两种方式。EMD 是将一堆泥土转变为另一堆所需的最小成本。移动泥土的成本是移动的泥土量乘以移动的距离。以下定义是对上述内容的正式表述。

**定义** (**Wasserstein 距离或 EMD**)：设 `images/2916.jpg` 表示所有边缘分布为 `p(x)` 和 `q(y)` 的联合分布 `x, y` 的集合。则我们定义：

`images/2917.jpg`

此处，移动的距离由范数 `images/2918.jpg` 给出，待移动的泥土量由联合分布 `images/2919.jpg` 给出。

WGAN 网络拓扑与 GAN 相同。我们有 `images/2920.jpg`，令生成器函数 `G` 为 `images/2921.jpg`，一个带有参数 `images/1449.jpg` 的参数化函数或神经网络，它将高斯噪声向量 `z` 变换为 `X` 中的一个点。设 `images/2923.jpg` 表示 `images/2924.jpg` 的分布。对于固定的 `z`，`images/2924.jpg` 可视为参数 `images/1449.jpg` 的函数。因此，WGAN 的目标是 `images/2927.jpg`。

# EM 距离的一些性质

设 `P` 为 `X` 上的一个固定分布，`images/2928.jpg` 为一个带有参数 `images/1914.jpg` 的参数化函数。设 `Q` 表示 `images/2930.jpg` 的分布。对于固定的 `z`，`images/2931.jpg` 可视为参数 `images/1449.jpg` 的函数。

1.  **如果 g 在 θ 上连续，则 EMD (P, Q) 也连续：**

    设 `images/2933.jpg` 和 `images/1914.jpg` 为参数空间中接近的两个参数，即 `images/2935.jpg` 0，因为 `g` 在 `images/2936.jpg` 上连续，因此 `images/2937.jpg` 和 `images/2938.jpg` 应该非常接近，即 `images/2939.jpg` `images/2940.jpg`。

    EMD 定义为下确界，所以它是一个下界，因此：

    `images/2941.jpg`

    EMD 是一种度量，所以利用三角不等式：

    `images/2942.jpg`，当 `images/2943.jpg` 时。

2.  **如果 g 是局部 Lipschitz 连续并满足 1，则 EMD (P, Q) 处处连续且几乎处处可导**（即它可能仅在一小部分点集上不可导）。

    Lipschitz 连续性衡量函数对输入微小变化的敏感程度。如果存在一个开球 `images/2946.jpg` 和一个实数 `K`，使得函数 `images/2944.jpg` 在点 `images/2945.jpg` 处满足：

    `images/2947.jpg`

    则称该函数在该点局部 Lipschitz 连续。

    这里，`K` 给出了当输入度量 `images/2948.jpg` 发生微小扰动时，`f` 扰动程度的上界。

    这里，`images/2949.jpg` 是一个神经网络。使 `images/2949.jpg` 满足 Lipschitz 条件的一种粗糙方法是通过权重裁剪，将权重矩阵的每个元素截断到一个小的闭区间内，如 `[-0.01, 0.01]`。然而，这限制了网络的容量。还有其他先进方法，如梯度惩罚和谱权重归一化，用于在神经网络中强制执行 Lipschitz 约束。

    如果存在 `images/2952.jpg` 周围的一个开集 `U`，使得对于所有 `images/2954.jpg`：

    `images/2955.jpg`

    则 `images/2949.jpg` 在 `images/2952.jpg` 处局部 Lipschitz 连续。

    不等式的最后一部分对欧几里得范数成立。取 `images/2956.jpg`，我们有：

    `images/2957.jpg`

    现在，`images/2958.jpg`

    因此，`images/2959.jpg`。因此，`images/2960.jpg` 是局部 Lipschitz 的，根据 Rademacher 定理，我们知道它几乎处处可导。

3.  **1 和 2 对 JS 和 KL 不成立**：让我们以 *[图 12.14](#c12.xhtml#fig12_14)* 中所示的两个简单分布 `P` 和 `Q` 为例，它们沿垂直 y 轴均匀分布，`images/2961.jpg` 但被一个正数 `images/2962.jpg` 平移。区间 `[a, b]` 上均匀分布的任意样本的概率为 `images/2963.jpg` = 1（若 b=1, a=0）。我们可以写出 `P, Q` 如下：

    `images/2964.jpg` `images/2965.jpg`

    `P` 沿 y 轴在 `[0, 1]` 上均匀分布。请参考下图：

    `images/Image49337.jpg`

    **图 12.14：** *来自分布 P 和 Q 的样本*

    此处，`images/2966.jpg`，`images/2967.jpg`，因为 `images/2968.jpg` 和 `images/2969.jpg`，因为它们没有公共区域，在 `P` 非零的地方 `Q` 变为零，反之亦然。

    `images/2970.jpg`

    和 `images/2971.jpg`，因为这是我们需要移动单位概率质量的距离。

    在 `θ = 0` 时，`KL(P, Q)=KL(Q, P)=JS(P, Q) = EMD(P,Q) = 0`。但对于所有 `0 < θ < 1`，只有 EMD 作为 `.` 的函数平滑变化。两个 KL 和 JS 都具有无限间断和跳跃间断。

    这表明 KL 和 JS 不像 EMD 那样表现出连续性和可导性；因此，与它们相比，EMD 更适合神经网络训练。

# WGAN 训练

利用线性规划公式和 Kantorovich-Rubinstein 对偶性，可以推导出 EMD 的一种等价公式。您可以参考 *延伸阅读 [13]* 部分。

