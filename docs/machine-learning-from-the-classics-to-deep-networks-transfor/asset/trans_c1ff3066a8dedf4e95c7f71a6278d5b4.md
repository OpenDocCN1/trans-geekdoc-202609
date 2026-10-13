

## EM 算法步骤

1.  **期望步 (E-step)：** 在第 $(j+1)$ 次迭代中，计算 $p(\mathcal{X}^{(l)}|\mathcal{X}, \boldsymbol{\xi}^{(j)})$ 和
    $$Q(\boldsymbol{\xi}, \boldsymbol{\xi}^{(j)}) = \mathbb{E}[\ln p(\mathcal{X}, \mathcal{X}^{(l)}; \boldsymbol{\xi})] \tag{12.40}$$
    其中期望是相对于 $p(\mathcal{X}^{(l)}|\mathcal{X}; \boldsymbol{\xi}^{(j)})$ 计算的。

2.  **最大化步 (M-step)：** 确定 $\boldsymbol{\xi}^{(j+1)}$ 使得
    $$Q(\boldsymbol{\xi}^{(j+1)}, \boldsymbol{\xi}^{(j)}) \ge Q(\boldsymbol{\xi}, \boldsymbol{\xi}^{(j)}) \tag{12.41}$$

3.  **根据准则检查收敛性。** 如果不满足，则返回步骤 1。

一个可能的收敛准则是检查 $\|\boldsymbol{\xi}^{(j+1)} - \boldsymbol{\xi}^{(j)}\| < \epsilon$ 是否成立，其中 $\epsilon$ 为某个用户定义的常数。使用 EM 预设处理联合 PDF $p(\mathcal{X}, \mathcal{X}^{(l)}; \boldsymbol{\xi})$ 在计算上是可行的。例如，当在指数族 PDF 范围内工作时，E-step 可能只需要计算潜在变量的少数几个统计量。指数族分布在计算上很方便，将在第 [12.8](#Chp012_583-634_B9780443292385000184.xhtml#s0075) 节中更详细地讨论。

### 备注 12.3

*   EM 算法由 Arthur Dempster、Nan Laird 和 Donald Rubin 在 1977 年的开创性论文 [12] 中提出并命名。该论文推广了先前发表的结果，例如 [2,38]，并作为统计学中的强大工具产生了重大影响。完整的收敛性证明见 [47]。相关讨论见例如 [29]。

*   可以证明 EM 算法收敛到 $p(\mathcal{X}; \boldsymbol{\xi})$ 的一个（通常是局部）最大值，这正是我们最初的目标。似然函数永不减小。其收敛速度比牛顿型搜索技术的二次收敛要慢，尽管在最优点附近可能实现加速。然而，该算法的收敛过程平稳，其复杂度比牛顿型方案更具吸引力，且不涉及矩阵求逆。感兴趣的读者可参考例如 [14,30,33,43] 获取更多信息。

*   EM 算法可以修改以获得 MAP 估计。为此，M-step 改为（问题 [12.4](#Chp012_583-634_B9780443292385000184.xhtml#o0095)）
    $$
    \boldsymbol{\xi}^{(j + 1)} = \arg\max_{\boldsymbol{\xi}}\left\{ \mathcal{Q}(\boldsymbol{\xi},\boldsymbol{\xi}^{(j)}) + \ln p(\boldsymbol{\xi}) \right\}, \tag{12.42}
    $$
    其中 $p(\boldsymbol{\xi})$ 是与 $\boldsymbol{\xi}$ 相关的先验 PDF（如果将其视为随机向量）。

*   EM 算法可能对初始点 $\boldsymbol{\xi}^{(0)}$ 的选择敏感。在实践中，可以从不同的初始点多次运行算法，并保留最佳结果。根据应用的不同，也使用过其他初始化程序。

