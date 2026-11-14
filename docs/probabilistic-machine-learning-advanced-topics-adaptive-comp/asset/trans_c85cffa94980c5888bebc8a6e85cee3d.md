

## 18.7.1 由无限宽 DNN 推导的核 (NN-GP)

在本节中，我们证明，具有一个隐藏层且宽度趋于无限大、对所有参数都具有高斯先验的 MLP，会收敛到一个具有明确定义核的高斯过程。⁶ 这一结果最初在 [Nea96; Wil98] 中得到证明，随后被扩展到深层 MLP [DFS16; Lee+18]、CNN [Nov+19] 以及通用 DNN [Yan19]。所得到的核被称为 **NN-GP** 核 [Lee+18]。

我们将考虑以下模型:

f_k(\mathbf{x}) = b_k + \sum_{j=1}^H v_{jk} h_j(\mathbf{x}), \quad h_j(\mathbf{x}) = \varphi(u_{0j} + \mathbf{x}^\mathsf{T} \mathbf{u}_j) \tag{18.174}

其中 _H_ 是隐藏单元的数量，\(\varphi()\) 是某种非线性激活函数，例如 ReLU。我们将对参数假设高斯先验:

b_k \sim \mathcal{N}(0, \sigma_b), v_{jk} \sim \mathcal{N}(0, \sigma_v), u_{0j} \sim \mathcal{N}(0, \sigma_0), \mathbf{u}_j \sim \mathcal{N}(0, \mathbf{\Sigma}) \tag{18.175}

设 \(\boldsymbol{\theta} = \{b_k, v_{jk}, u_{0j}, \mathbf{u}_j\}\) 为所有参数。将单位 _k_ 应用于一个输入向量时的期望输出由以下给出:

\mathbb{E}_{\boldsymbol{\theta}} [f_k(\mathbf{x})] = \mathbb{E}_{\boldsymbol{\theta}} \left[ b_k + \sum_{j=1}^H v_{jk} h_j(\mathbf{x}) \right] = \underbrace{\mathbb{E}_{\boldsymbol{\theta}} [b_k]}_{=0} + \sum_{j=1}^H \underbrace{\mathbb{E}_{\boldsymbol{\theta}} [v_{jk}]}_{=0} \underbrace{\mathbb{E}_{\mathbf{u}} [h_j(\mathbf{x})]}_{=0} = 0 \tag{18.176}

当函数应用于两个不同输入时，单位 _k_ 输出中的协方差由以下给出:⁷

\mathbb{E}_{\boldsymbol{\theta}} [f_k(\mathbf{x}) f_k(\mathbf{x}')] = \mathbb{E}_{\boldsymbol{\theta}} \left[ \left( b_k + \sum_{j=1}^H v_{jk} h_j(\mathbf{x}) \right) \left( b_k + \sum_{j=1}^H v_{jk} h_j(\mathbf{x}') \right) \right] \tag{18.177}

= \sigma_b^2 + \sum_{j=1}^H \mathbb{E}_{\boldsymbol{\theta}} [v_{jk}^2] \mathbb{E}_{\mathbf{u}} [h_j(\mathbf{x}) h_j(\mathbf{x}')] = \sigma_b^2 + \sigma_v^2 H \mathbb{E}_{\mathbf{u}} [h_j(\mathbf{x}) h_j(\mathbf{x}')] \tag{18.178}

现在考虑极限 \(H \rightarrow \infty\)。通过定义 \(\sigma_v^2 = \omega / H\) 来对输出幅度进行缩放。由于第 _k_ 个输出单元的输入是来自隐藏单元 _h<sub>j</sub>_(**_x_**) 的无限多随机变量之和，我们可以使用 **中心极限定理** 得出结论：输出收敛于一个高斯分布，其均值和方差由以下给出:

\mathbb{E} [f_k(\mathbf{x})] = 0, \quad \mathbb{V} [f_k(\mathbf{x})] = \sigma_b^2 + \omega \mathbb{E}_{\mathbf{u}} [h(\mathbf{x})^2] \tag{18.179}

此外，对于任何 \(N \ge 2\)，\(\{f_k(\mathbf{x}_n) : n = 1 : N\}\) 的联合分布收敛于一个多元高斯分布，其协方差由以下给出:

\mathbb{E} [f_k(\mathbf{x}) f_k(\mathbf{x}')] = \sigma_b^2 + \omega \mathbb{E}_{\mathbf{u}} [h(\mathbf{x}) h(\mathbf{x}')] \triangleq \mathcal{K}(\mathbf{x}, \mathbf{x}') \tag{18.180}

6. 我们的演示基于 `http://cbl.eng.cam.ac.uk/pub/Intranet/MLG/ReadingGroup/presentation\_matthias.pdf`.

7. 我们使用了这样一个事实：\(u \sim \mathcal{N}(0, \sigma^2)\) 意味着 \(\mathbb{E} [u^2] = \mathbb{V} [u] = \sigma^2\).

| \( h(\tilde{x}) \) | \( C(\tilde{x}, \tilde{x}') \) |
|---|---|
| \( \text{erf}(\tilde{x}^\text{T}\tilde{u}) \) | \( \frac{2}{\pi} \arcsin(f_1(\tilde{x}, \tilde{x}')) \) |
| \( \mathbb{I}(\tilde{x}^\text{T}\tilde{u} \ge 0) \) | \( \pi - \theta(\tilde{x}, \tilde{x}') \) |
| \( \text{ReLU}(\tilde{x}^\text{T}\tilde{u}) \) | \( \frac{f_2(\tilde{x}, \tilde{x}')}{\pi} \sin(\theta(\tilde{x}, \tilde{x}')) + \frac{\pi-\theta(\tilde{x}, \tilde{x}')}{\pi} \tilde{x}^\text{T}\tilde{\Sigma}\tilde{x}' \) |

表 18.4：一些神经网络 GP 核。此处我们定义 \( f_1(\tilde{x}, \tilde{x}') = \frac{2\tilde{x}^\text{T}\tilde{\Sigma}\tilde{x}'}{\sqrt{(1+2\tilde{x}^\text{T}\tilde{\Sigma}\tilde{x})(1+2(\tilde{x}')^\text{T}\tilde{\Sigma}\tilde{x}')}} \)，\( f_2(\tilde{x}, \tilde{x}') = ||\tilde{\Sigma}^{\frac{1}{2}}\tilde{x}|| \cdot ||\tilde{\Sigma}^{\frac{1}{2}}\tilde{x}'|| \)，\( f_3(\tilde{x}, \tilde{x}') = \sqrt{(\tilde{x}^\text{T}\tilde{\Sigma}\tilde{x})((\tilde{x}')^\text{T}\tilde{\Sigma}\tilde{x}')} \)，以及 \( \theta(\tilde{x}, \tilde{x}') = \arccos(f_3(\tilde{x}, \tilde{x}')) \)。结果在 [Wil98; CS09] 中推导。

![](img/ca72c1626f4850f058a9edc138c1ac73_753_0.png)

图 18.28：带有由无限宽单层 MLP 推导的 NNGP 核的 GP 的示例输出，其中激活函数的形式为 \( h(x) = \text{erf}(x \cdot u + u_0) \)，\( u \sim \mathcal{N}(0, \sigma) \) 且 \( u_0 \sim \mathcal{N}(0, \sigma_0) \)。由 `nngp_1d.ipynb` 生成。经 Matthias Bauer 友好许可使用。

因此 MLP 收敛于 GP。要计算核函数，我们需要求值

\( C(x, x') = \mathbb{E}_u [h(u_0 + u^T x) h(u_0 + u^T x')] = \mathbb{E}_u [h(\tilde{u}^T \tilde{x}) h(\tilde{u}^T \tilde{x}')] \quad (18.181) \)

其中我们定义了 \( \tilde{x} = (1, x) \) 和 \( \tilde{u} = (u_0, u) \)。让我们定义

\( \tilde{\Sigma} = \begin{pmatrix} \sigma_0^2 & 0 \\ 0 & \Sigma \end{pmatrix} \quad (18.182) \)

那么我们有

\( C(x, x') = \int h(\tilde{u}^T \tilde{x}) h(\tilde{u}^T \tilde{x}') \mathcal{N}(\tilde{u} | \mathbf{0}, \tilde{\Sigma}) d\tilde{u} \quad (18.183) \)

对某些激活函数，这可以以封闭形式计算，如表 18.4 所示。

这有时被称为神经网络核。请注意，这是一个非平稳核，其样本路径几乎是不连续的，并且对于较大的正输入或负输入会趋于常数值，如图 18.28 所示。

## 18.7.2 神经切核 (NTK)

在 18.7.1 节中，我们在所有权重都是随机的假设下推导了 NN-GP 核。一个自然的问题是：我们是否可以从已训练的 DNN 中推导出一个核，或者更一般地，在训练过程中推导出一个核。事实证明，这是可以做到的，如下所示。
设 \(\boldsymbol{f} = [f(\boldsymbol{x}_n; \boldsymbol{\theta})]_{n=1}^N\) 为 \(N \times 1\) 预测向量，设 \(\nabla_{\boldsymbol{f}} \mathcal{L} = [\frac{\partial \mathcal{L}}{\partial f(\boldsymbol{x}_n)}]_{n=1}^N\) 为 \(N \times 1\) 损失梯度向量，设 \(\boldsymbol{\theta} = [\theta_p]_{p=1}^P\) 为 \(P \times 1\) 参数向量，并设 \(\nabla_{\boldsymbol{\theta}} \boldsymbol{f} = [\frac{\partial f(\boldsymbol{x}_n)}{\partial \theta_p}]\) 为 \(P \times N\) 偏导数矩阵。假设我们以固定学习率 \(\eta\) 执行连续时间梯度下降。参数随时间演变如下:

\(\partial_t \boldsymbol{\theta}_t = -\eta \nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{f}_t) = -\eta \nabla_{\boldsymbol{\theta}} \boldsymbol{f}_t \cdot \nabla_{\boldsymbol{f}} \mathcal{L}(\boldsymbol{f}_t)\) (18.184)

因此函数随时间演变如下:

\(\partial_t \boldsymbol{f}_t = \nabla_{\boldsymbol{\theta}} \boldsymbol{f}_t^T \partial_t \boldsymbol{\theta}_t = -\eta \nabla_{\boldsymbol{\theta}} \boldsymbol{f}_t^T \nabla_{\boldsymbol{\theta}} \boldsymbol{f}_t \cdot \nabla_{\boldsymbol{f}} \mathcal{L}(\boldsymbol{f}_t) = -\eta \mathcal{T}_t \cdot \nabla_{\boldsymbol{f}} \mathcal{L}(\boldsymbol{f}_t)\) (18.185)

其中 \(\mathcal{T}_t\) 是 \(N \times N\) 核矩阵

\(\mathcal{T}_t(\boldsymbol{x}, \boldsymbol{x}') \triangleq \nabla_{\boldsymbol{\theta}} f_t(\boldsymbol{x}) \cdot \nabla_{\boldsymbol{\theta}} f_t(\boldsymbol{x}') = \sum_{p=1}^P \frac{\partial f(\boldsymbol{x}; \boldsymbol{\theta})}{\partial \theta_p} \big|_{\boldsymbol{\theta}_t} \frac{\partial f(\boldsymbol{x}'; \boldsymbol{\theta})}{\partial \theta_p} \big|_{\boldsymbol{\theta}_t}\) (18.186)

如果我们让学习率 \(\eta\) 趋于无限小，并且宽度趋于无限大，可以证明该核收敛于一个常数矩阵，这被称为 **神经切核** 或 **NTK** [JGH18]。

\(\mathcal{T}(\boldsymbol{x}, \boldsymbol{x}') \triangleq \nabla_{\boldsymbol{\theta}} f(\boldsymbol{x}; \boldsymbol{\theta}_\infty) \cdot \nabla_{\boldsymbol{\theta}} f(\boldsymbol{x}'; \boldsymbol{\theta}_\infty)\) (18.187)

关于如何为各种模型（例如 CNN、图神经网络和通用神经网络）计算此核的详细信息，可参见 [Aro+19; Du+19; Yan19]。一个可用于计算 NN-GP 核和 NTK 的软件库可在 [Ano19] 中找到。

NTK 结果背后的假设是参数从其初始值几乎没有变化（这就是为什么围绕起始参数的线性近似是有效的）。这仍然可能导致最终预测（以及零最终训练误差）的变化，因为最终层权重可以学习使用随机特性，就像在核回归中一样。然而，这一现象——被称为“懒惰训练” [COB18]——并不代表 DNN 在实践中的行为 [Woo+19]，在实际中参数通常会发生很大变化。幸运的是，可以使用一种不同的参数化，它确实会在无限宽度极限下导致特性学习 [YH21]。

## 18.7.3 深度 GP

深度高斯过程或 **DGP** 是 GP 的组合 [DL13]。更正式地说，\(L\) 层的 DGP 是如下形式的分层模型

\(\text{DGP}(\boldsymbol{x}) = f_L \circ \cdots \circ \boldsymbol{f}_1(\boldsymbol{x}), \boldsymbol{f}_i(\cdot) = [f_i^{(1)}(\cdot), \dots, f_i^{(H_i)}(\cdot)], f_i^{(j)} \sim \text{GP}(0, \mathcal{K}_i(\cdot, \cdot))\) (18.188)

这与深度神经网络类似，只是隐藏节点现在是隐藏函数。

