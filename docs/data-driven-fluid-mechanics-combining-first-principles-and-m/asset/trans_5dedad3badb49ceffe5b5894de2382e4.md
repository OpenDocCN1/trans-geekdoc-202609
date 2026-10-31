
如果 X 表示系统对给定输入的瞬态响应，那么考虑 t → ∞ 时的稳态或平均状态而不是早期数据的均值是有意义的。为书写方便，我们无论如何都将从数据中减去的该基态称为“均值”。用 y_k(x) 表示 X 的第 k 列，我们现在构造均值减去的矩阵

$$\mathbf{Y} = [\mathbf{y}'_1\ \mathbf{y}'_2\ \cdots\ \mathbf{y}'_m],\qquad (6.20)$$

其中 $\mathbf{y}'_j = \mathbf{y}_j - \mathbf{y}_0$ 是第 $j$ 个均值减去的快照。最简单地，POD 可以通过对 Y 进行 SVD 得到。特别地，如果我们有

$$\mathbf{Y} = \mathbf{\Phi}\mathbf{\Sigma}\mathbf{\Psi}^*,\qquad (6.21)$$

则 POD 模由 $\mathbf{\Phi}$ 的列 $\phi_j(x)$ 给出，它们随时间通过相应的系数 $a_j(t) = \sigma_j\psi_j(t)^*$ 演化（对于具有标准内积的实数据，$\psi_j(t)^* = \psi_j(t)^T$）。即，参照 (6.1)，数据的 POD 展开由第 6.2.2 节所述的 SVD 的双线性展开给出：

$$\mathbf{y}_k(x) = \sum_{j=1}^{q} \phi_j(x)\sigma_j\psi_j^*(t_k).\qquad (6.22)$$

由于我们已安排数据使得空间位置仅取决于行号，而时间位置仅取决于列，因此左奇异向量和右奇异向量分别仅取决于空间和时间，从而可以直接使用 SVD 得到我们数据中的这种变量分离。第 6.2.2 节所述的 SVD 的最优性意味着将该和截断到 $r$ 项可给出对完整数据集的最接近的秩-$r$ 近似。

在 (6.19) 中组装数据矩阵时，我们选择将速度的 $v$ 分量测量值放在所有 $u$ 测量值之下，尽管我们也可以以其他方式排列数据，例如交替的行包含速度的 $u$ 和 $v$ 分量。从第 6.2.2 节讨论的 SVD 的置换性质来看，改变排列不会影响分解，除了将 POD 模中的条目置换到适当的位置之外。同样，我们可以重新排列数据矩阵的列，而完全不影响 POD 模。事实上，这一事实可用于证明 POD 不需要时间分辨数据，因为打乱时间分辨快照的顺序可以得到非时间分辨的快照序列。

根据第 6.2.2 节，$\mathbf{Y}$ 的右奇异向量是矩阵 $\mathbf{Y}^*\mathbf{Y}$ 的特征向量。这个 $m \times m$ 矩阵可以解释为所有快照之间的相关矩阵：

$$\mathbf{Y}^*\mathbf{Y} = \begin{bmatrix} \langle \mathbf{y}'_1,\mathbf{y}'_1\rangle_x & \langle \mathbf{y}'_2,\mathbf{y}'_1\rangle_x & \cdots & \langle \mathbf{y}'_m,\mathbf{y}'_1\rangle_x \\ \langle \mathbf{y}'_1,\mathbf{y}'_2\rangle_x & \langle \mathbf{y}'_2,\mathbf{y}'_2\rangle_x & \cdots & \langle \mathbf{y}'_m,\mathbf{y}'_2\rangle_x \\ \vdots & \vdots & \ddots & \vdots \\ \langle \mathbf{y}'_1,\mathbf{y}'_m\rangle_x & \langle \mathbf{y}'_2,\mathbf{y}'_m\rangle_x & \cdots & \langle \mathbf{y}'_m,\mathbf{y}'_m\rangle_x \end{bmatrix},\qquad (6.23)$$

其中 ⟨·,·⟩ₓ 表示空间内积。类似地，如果我们令 z′ⱼ(t) 为 Y 的第 j 行的行向量，则有

$$\mathbf{YY}^* = \begin{bmatrix} \langle z'_1, z'_1 \rangle_t & \langle z'_1, z'_2 \rangle_t & \dots & \langle z'_1, z'_n \rangle_t \\ \langle z'_2, z'_1 \rangle_t & \langle z'_2, z'_2 \rangle_t & \dots & \langle z'_2, z'_n \rangle_t \\ \vdots & \vdots & \ddots & \vdots \\ \langle z'_n, z'_1 \rangle_t & \langle z'_n, z'_2 \rangle_t & \dots & \langle z'_n, z'_n \rangle_t \end{bmatrix}, \tag{6.24}$$

其中 ⟨·,·⟩ₜ 是时间维度的内积。同样根据第 6.2.2 节，POD 模 φⱼ 是矩阵 YY* 的特征向量。这个 n × n 矩阵可以解释为 Y 中成对行之间的时间相关矩阵。

请注意，两个矩阵 YY* 和 Y*Y 通常大小不同，其中 YY* 为 n × n，而 Y*Y 为 m × m。由于 Y 的 SVD 与这些方阵的特征分解相关，因此计算并处理这两个矩阵中较小的那个可能最容易。例如，如果快照非常大但数量相对较少，则 m ≪ n，因此计算 Y*Y 的（完整或部分）特征分解以获得 POD 系数 aⱼ(t) 可能更易处理。然后可以根据第 6.2.2 节中 SVD 的性质使用 φⱼ = σⱼ⁻¹ Y aⱼ 计算 POD 模。这正是 Sirovich (1987) 中引入的计算 POD 的“快照方法”。相反，如果 n ≪ m，则可以改从计算 YY* 的特征分解开始。

## 6.4 连续系统的本征正交分解

到目前为止，我们一直将 POD 视为从给定数据集计算得出的东西。然而，实际上，如果我们的数据来自对给定系统的测量，那么 POD 理想情况下应与我们收集并用于分析的确切数据无关。也就是说，我们可以另行将 POD 视为系统的属性，我们希望从数据中准确计算它。回顾 (6.23) 和 (6.24) 中出现的离散数据的内积，这些可以被视为积分的离散近似

$$\langle y'_j, y'_k \rangle_x = \int_{\Omega_x} y'(x,t_j) y'(x,t_k) dx, \tag{6.25}$$

$$\langle z'_j, z'_k \rangle_t = \int_{\Omega_t} z'(x_j,t) z'(x_k,t) dt, \tag{6.26}$$

其中第一个方程是适当数量空间维度的空间积分，而 Ωₓ 和 Ωₜ 定义了感兴趣的空间和时间域。请注意，正确近似这些积分的愿望可能导致需要为离散数据包含积分权重，如第 6.2.2 节所述。³ 请注意，

> ³ 为了更一般化，我们也可以在这些积分中包含额外的权重函数，但为简单起见我们省略了它。

根据上下文，有时最方便的做法是将 (6.25) 和 (6.26) 中的积分除以积分域的大小，使得内积变为平均值/期望值。更一般地，我们可以将 (6.25) 和 (6.26) 视为时间和空间的连续函数（而不是针对离散指标 j 和 k 计算）。我们也可以稍微更一般地思考，将这些积分视为计算某个随机过程的期望值。基于此，我们可以定义空间相关函数

$$C(x,x') = \mathbb{E}[y'(x,t) y'(x',t)],\tag{6.27}$$

其中 $\mathbb{E}$ 是期望，取自时间和/或系综。连续设定下的 POD 相当于寻找模 $\phi_j(x)$，它们是积分方程的特征函数

$$\int_{\Omega_x} C(x,x') \phi_j(x') dx' = \sigma_j^2 \phi_j(x).\tag{6.28}$$

正如所用符号所指示的，特征值 $\sigma_j^2$ 为实数且为正，且该方程是 (6.12) 的连续等价形式。请注意，可以证明在离散有限维上下文中讨论的 POD 的许多相同性质，例如正交性和最优性，也扩展到连续设定中的等价概念。在系统空间齐次（即在平移下不变）的情况下，$C(x,x') = C(x - x')$ 仅是 $x - x'$ 的函数，并且可以很容易地从 (6.28) 证明 POD 模变为傅里叶模。为了说明这一点，如果我们将积分变量改为 $r = x - x'$，则 (6.28) 可表示为

$$\int_{\Omega_r} C(r) \frac{\phi_j(x + r)}{\phi_j(x)} dr = \sigma_j^2.\tag{6.29}$$

(6.29) 的右边与 $x$ 无关，因此特征函数 $\phi_j$ 必须具有 $\frac{\phi_j(x+r)}{\phi_j(x)}$ 与 $x$ 无关的性质。我们可以验证傅里叶模（即 $\exp(2\pi i k x)$）满足此性质。在齐次方向上域有限的情况下，周期性边界条件决定了空间波数 $k$ 的允许值。类似地，如果系统仅在某些方向上齐次（如通道流中的流向和展向），则 POD 模在这些空间齐次方向上变为傅里叶模。

除了仅查看空间相关张量之外，我们还可以考虑时空相关张量

$$C(x,x',t,t') = \mathbb{E}[y'(x,t) y'(x',t')],\tag{6.30}$$

其中现在期望可以被视为对所有时空坐标 $(x,t)$ 和 $(x',t')$ 对的随机场不同实现进行的系综平均。在这种时空设定下，(6.28) 的等价形式则由下式给出

$$\int_{\Omega_x,\Omega_t} C(x,x',t,t') \tilde{\phi}_j(x',t') dx' dt' = \sigma_j^2 \tilde{\phi}_j(x,t).\tag{6.31}$$
