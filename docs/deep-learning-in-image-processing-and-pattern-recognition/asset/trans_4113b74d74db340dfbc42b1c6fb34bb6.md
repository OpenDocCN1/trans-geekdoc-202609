

## 2. 变分模态分解

近年来，一些学者将数学形态学与小波相结合，提出了一种新的非线性小波形态小波。文献 [8] 将形态小波应用于电力扰动检测，并成功识别了电力传输过程中的不良状态。例如，庄宁 [9] 等人将分形维数与 EMD（经验模态分解）相结合，以提取脑电信号的特征，从而识别不同的情绪表现。郑志 [10] 等人将 LMD（局部均值分解）分解方法与广义分形维数相结合，以识别齿轮故障。然而，实际测量信号通常伴随着异常事件，例如噪声干扰和间歇性信号，这会导致模态混叠，并极大地影响后续的故障诊断率。同时，计算分形维数的一种常用方法是覆盖法（盒计数法）。该方法存在不可避免的缺点。由于该方法本身使用规则网格划分方法，因此在某些情况下分形维数的估计非常不稳定 [11]。

针对上述问题，本文提出了一种基于变分模态分解（VMD）计算数学形态学分形维数（VMD-MMFD-KPCA）的方法。利用信号的变分模态分解（VMD），最大程度地消除信号中的干扰信息，以解决传统 EMD 分解的模态混叠问题。在使用形态学分形维数计算信号维数时，避免了传统盒维数估计的不稳定性，包括有效区分不同的故障类型。在此基础上，引入 KPCA 降维方法，降低通过维数计算的高维数据的维度，消除样本中的冗余和重复，为后续故障诊断提供数据依据。与传统的故障诊断方法相比，该方法在特征提取和诊断方面表现出更好的性能。最后，通过仿真电路证明了该方法的有效性。

VMD 分解是一种非递归信号分解算法。通过对信号进行自适应分解，获得不同频带中的本征模态函数（IMF）。在求解模态函数的过程中，使用图像延拓来避免 EMD（经验模态分解）等其他分解方法中的端点效应。VMD 对非线性故障信号的处理有助于提取后续故障信号的特征。分解后的 IMF 具有独立的中心频率和稀疏性，在参数适当时可以有效避免模态混叠。

- (1) 为了获得单向频谱，使用希尔伯特变换分析和计算每个模态信号，然后使用频率平移法将模态频谱移动到基带：

$$\left[ \left( \delta(t) + \frac{j}{\pi t} \right) * v_{k}(t) \right] e^{j \omega_{k} t}$$

$\delta(t)$ 是狄拉克函数；$v_k$ 和 $\omega_k$ 分别是分解的第一个 IMF 分量及其中心频率。

- (2) 通过梯度的平方范数估计带宽，约束表达式为：

$$
\begin{gathered}
\min _{\left\{v_{k}\right\},\left\{\omega_{k}\right\}} \sum_{k=1}^{K}\left\|\partial_{t}\left[\left(\delta(t)+\frac{1}{\pi t}\right) * v_{k}(t)\right] e^{-j \omega_{k} t}\right\|_{2}^{2} \\
s.t. \quad \sum_{k=1}^{K} v_{k}(t)=f(t)
\end{gathered}
$$

$\partial_t$ 是梯度计算，$*$ 是卷积运算符号。

- (3) 为了更高效地获得最优解，使用拉格朗日算子 $\tau(t)$ 和惩罚因子 $\alpha$ 将约束问题转化为无约束问题。展开的拉格朗日函数表达式为：

$$
L(\{v_k\}, \{\omega_k\}, \tau) = \alpha \sum_{k=1}^{K} \left\| \partial_{\mathbf{l}} \left( \delta(t) + \frac{j}{\pi t} * v_k(t) \right) e^{-j \omega_k t} \right\|_2^2 + \left\| f(t) - \sum_{k=1}^{K} v_k(t) \right\|_2^2 + \left[ \tau(t), f(t) - \sum_{k=1}^{K} v_k(t) \right] \tag{3}
$$

- (4) 使用交替方向乘子法迭代更新每个模态分量和中心频率，获得无约束函数的鞍点，即为该问题的最佳解。$\overline{v_l}, \omega_k, \tau$ 的迭代更新表达式如下：

$$
\hat{v}_k^{n+1}(\omega) = \frac{\hat{f}(\omega) - \sum_{i \neq k} \hat{v}_i(\omega) + \frac{\hat{\tau}(\omega)}{2}}{1 + 2\alpha(\omega - \omega_k)^2} \tag{4}
$$

$$
\omega_k^{n+1} = \frac{\int_{0}^{\infty} \omega |\hat{\partial}_k(\omega)|^2 d\omega}{\int_{0}^{\infty} |\hat{\partial}_k(\omega)|^2 d\omega} \tag{5}
$$

$$
\hat{\tau}^{n+1}(\omega) = \hat{\tau}^n(\omega) + \gamma \left[ \hat{f}(\omega) - \sum_{k=1}^{K} \hat{v}_k^{n+1}(\omega) \right] \tag{6}
$$

在公式 (6) 中，$n$ 是迭代次数，$\gamma$ 是噪声容忍参数。

- (5) 判断迭代终止条件。

$$
\sum_{k=1}^{K} \left\| \frac{\hat{v}_k^{n+1} - \hat{v}_k^n}{\|\hat{v}_k^n\|} \right\|_2^2 < \varepsilon \tag{7}
$$

其中 $\varepsilon$ 是判断精度。当 $\varepsilon > 0$ 时，迭代停止，循环结束。步骤流程图如图 1 所示：

![图 1](img/e4200cc4308edaf8913e513b0f96dbb6_444_0.png)

## 3. 基于数学形态学的分形维数计算方法

估计分形维数的关键在于在不同尺度上测量信号，这可以使用多尺度形态学来实现 [12]。在收集和覆盖信号的过程中，使用极大函数，即结构元素 $g(n)$，进行等效变换，并分析尺度范围 $\varepsilon = 1, 2, \cdots, \varepsilon_{\max}$。该算法包括两个基本算子：膨胀和腐蚀。对于一维离散时间信号 $f(n) (n = 0, 1, 2, \cdots)$，每个尺度的膨胀和腐蚀结果分别为：

$$f \Theta g^{\oplus\varepsilon}(n) = (f \Theta g) \Theta g \cdots \Theta g \tag{8}$$

$$f \oplus g^{\oplus\varepsilon}(n) = ((f \oplus g) \oplus g \cdots \oplus g \tag{9}$$

其中 $\Theta$ 表示腐蚀运算；$\oplus$ 表示膨胀运算；$g^{\oplus\varepsilon}(n)$ 表示在尺度 $\varepsilon$ 中使用的结构元素；$f$ 表示信号；$g$ 表示结构元素；$\varepsilon$ 次是膨胀和腐蚀的次数。不同尺度下离散信号的覆盖面积定义为：

$$A_{g}(\epsilon)=\sum_{n=1}^{N}\left(f \circ \varepsilon g(n)-f \circ \varepsilon g(n)\right) \tag{10}$$

当 $\varepsilon$ 趋近于零时，$A_{g}(\varepsilon)$ 满足：

$$\lg\frac{A_{g}(\epsilon)}{\varepsilon^{2}}\approx D_{M}^{*}\cdot\lg\left(\frac{1}{\epsilon}\right)+c \tag{11}$$

其中 $D_{M}$ 是信号的 Minkowski-Bouligand 维数，$c$ 是常数。上述方程 $\lg\frac{A_{g}(\varepsilon)}{\varepsilon^{2}}$ 和 $\lg\left(\frac{1}{\varepsilon}\right)$ 通过最小二乘拟合得到的直线的斜率为 $D_{M}$，即最终所需的 $f(n)$ 分形维数。

通常，选择单位结构元素 $g(n)$ 为 {0,0,0}，因为这种结构不仅确保维数估计不受信号幅值范围的影响，而且降低了算法的计算复杂度。原则上，最大分析尺度 $\varepsilon_{\max}$ 是小于 $N/2$ 的正整数（$N$ 是离散信号的采样点数）。当数据长度较大时，适当减少 $\varepsilon_{\max}$ 可以减少计算量 [13]。在本文中，长度为 256。

## 4. 核主成分分析

KP法用于表示建模数据之间的非线性关系。它可以将线性不可分的输入数据有效地投影到可线性分离的高维空间中，然后在特征空间 $H$ 中执行线性 PCA。假设样本集为 $x_1, x_2, ..., x_N \in R^m$，其中：$N$ 是样本数量，$m$ 是变量数量。这些样本通过非线性映射 $\varphi$ 投影到特征空间 $H$ 中，可以表示为：

$$\phi:x_{i}\in R^{m}\to\phi(x_{i})\in R^{h} \tag{12}$$

其中 $h$ 是特征空间的维数。

特征空间 $H$ 中向量 $\phi(x_i)$ 和 $\phi(x_j)$ ($i, j = 1, 2, \cdots, N$) 的内积为：

$$\phi(x_{i})^{T}\phi(x_{j})=\langle\phi(x_{i}),\phi(x_{j})\rangle=k(x_{i},x_{j}) \tag{13}$$

其中 $k$ 是核函数。

高维特征空间 $H$ 中样本的协方差矩阵为：

$$Q=\frac{1}{N-1}\sum_{j=1}^{N}\phi(x_{j})\phi(x_{j})^{T} \tag{14}$$

类似于线性 PCA，特征空间中的 KPCA 等价于求解特征值问题。设特征向量为 $V_k$，特征值为 $\mu_k$，其特征方程为：

$$\mu_{k}V_{k}=QV_{k}=\frac{1}{N-1}\sum_{j=1}^{N}\phi(x_{j})\phi(x_{j})^{T}V_{k}=\frac{1}{N-1}\sum_{j=1}^{N}\langle\phi(x_{j}),V_{k}\rangle\phi(x_{j}) \tag{15}$$

在公式 (15) 中，协方差矩阵 $Q$ 中的每个特征向量 $V_k$ 可以看作是 $\phi(x_1), \phi(x_2), ..., \phi(x_N)$ 的线性组合 [14]，即：

$$V_{k}=\sum_{i=1}^{N}v_{ki}\phi(x_{i}),\qquad k=1,2,\cdots,N \tag{16}$$

