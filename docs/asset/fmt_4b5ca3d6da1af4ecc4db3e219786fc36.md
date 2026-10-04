
$$\vec{P} = \alpha\vec{A} + \beta\vec{B} + \gamma\vec{C}, \quad \alpha, \beta, \gamma \geq 0, \quad \alpha + \beta + \gamma = 1. \quad (3)$$

注意，该方程适用于任意维空间，包括 3D 空间。现在给定 $\vec{A}, \vec{B}, \vec{C}, \vec{P}$，我们可以通过归一化面积计算 $\alpha, \beta, \gamma$。以 $\gamma$ 为例，我们可以计算为：

$$\gamma = \frac{\|\vec{AB} \times \vec{AP}\|}{\|\vec{AB} \times \vec{AC}\|} \propto \|\vec{AB} \times \vec{AP}\|, \quad (4)$$

其中 $\vec{AB} = \vec{B}-\vec{A}, \vec{AP} = \vec{P}-\vec{A}, \vec{AC} = \vec{C}-\vec{A}, \times$ 表示叉积算子，$\|\cdot\|$ 表示向量长度的 $\ell_2$ 范数。显然，重心权重为排列晶格（permutohedral lattice）定义了一个非线性映射。

将方程 (3) 代入方程 (2)，我们成功定义了一个结构化空间编码问题，其中结构化空间 $\mathcal{Z}$ 和正则项 $\phi$ 构建如下：

$$\mathcal{Z}^{\text{def}}=\{\mathbf{z} \mid \mathbf{z}^T\mathbf{e}=1, \mathbf{z} \geq \mathbf{0}\}, \quad \phi(\mathbf{z})^{\text{def}}=\lambda \sum_{n=1}^N \|\mathbf{B}-\mathbf{B}_n\| \cdot \mathbf{1}_{\mathbf{z}_n>0}, \quad (5)$$

其中 $\geq$ 表示向量的 1s，$\gtrsim$ 表示 $\mathbf{B}_n \in \mathbb{R}^3$ 的逐元素算子，$\mathbf{B}$ 中的第 $n$ 列，$\mathbf{1}_{\cdot}$ 表示当条件成立时返回 1，否则返回 0 的二进制指示（即重心权重的二值化），$\lambda \geq 0$ 是一个小的常数，用于控制 $\phi$ 对目标的贡献，使其被 $\phi$ 所主导。

**命题 1.** 假设方程 (2) 中的 $\mathbf{B}$ 代表排列晶格中的顶点，该晶格足够大以覆盖数据中点之间所有可能的投影，则存在一个使用最多三个顶点来最小化重建损失的解，且最小损失小于或等于到晶格的投影损失。

这是因为方程 (3) 使用三个顶点的线性组合定义了无损表示。唯一的损失发生在将点投影到排列晶格时。

![](img/33889d5baeb11b5b76258ce18177dcf2_250_0.png)

图 5 展示了我们的声明性防御者如何与排列晶格工作，其中三角形、圆圈和正方形分别代表晶格单元、3D 点以及它们在单元上的投影。在对抗性点云中，攻击者将点从 $\mathbf{x}_i$ 修改为 $\mathbf{x}'_i$。然后我们的防御者将 $\mathbf{x}'_i$ 投影到晶格上的 $\mathbf{x}''_i$。

**命题 2.** 假设 $\mathbf{x}_i = \alpha\vec{A} + \beta\vec{B} + \gamma\vec{C}$，其中 $\alpha, \beta, \gamma$ 为重心权重，为了保证 $\mathbf{x}_i, \mathbf{x}'_i$ 位于不同的单元，$\mathbf{x}_i$ 与 $\mathbf{x}'_i$ 之间的距离应大于 $\mathbf{x}'_i$ 到三角形边界的最距离，即：

$$|\mathbf{x}_i - \mathbf{x}'_i| > \min \left( \frac{\alpha}{\|\vec{BC}\|}, \frac{\beta}{\|\vec{AC}\|}, \frac{\gamma}{\|\vec{AB}\|} \right) \cdot s \quad (6)$$
