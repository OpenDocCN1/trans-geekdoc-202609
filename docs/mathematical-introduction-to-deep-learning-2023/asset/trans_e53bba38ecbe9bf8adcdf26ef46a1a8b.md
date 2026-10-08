

*练习 1.1.3.* 令 $\theta=(\theta_{1}, \theta_{2}, \ldots, \theta_{10}) \in \mathbb{R}^{10}$ 满足

$$ \theta=\left(\theta_{1}, \theta_{2}, \ldots, \theta_{10}\right)=\left(1,0,2,-1,2,0,-1,1,2,1\right) $$

并令 $m:\mathbb{R}\to\mathbb{R}$ 和 $q:\mathbb{R}\to\mathbb{R}$ 对于所有 $x\in\mathbb{R}$ 满足

$$ m(x)=\max\left\{-x,0\} \quad \quad \text{且} \quad \quad q(x)=x^{2}. $$

明确指定 $\left(\mathcal{N}_{q, m, q}^{\theta, 1}\right)(0)$，$\left(\mathcal{N}_{q, m, q}^{\theta, 1}\right)(1)$ 和 $\left(\mathcal{N}_{q, m, q}^{\theta, 1}\right)(1/2)$ 并证明你的结果是正确的（参见定义 1.1.3）。

*练习 1.1.4.* 令 $\theta=(\theta_{1}, \theta_{2}, \ldots, \theta_{15}) \in \mathbb{R}^{15}$ 满足

$$ \left(\theta_{1}, \theta_{2}, \ldots, \theta_{15}\right)=\left(1,-2,0,3,2,-1,0,3,1,-1,1,-1,2,0,-1\right) $$

并令 $\Phi:\mathbb{R}^{2}\to\mathbb{R}^{2}$ 和 $\Psi:\mathbb{R}^{2}\to\mathbb{R}^{2}$ 对于所有 $x, y\in\mathbb{R}$ 满足 $\Phi(x, y)=(y, x)$ 和 $\Psi(x, y)=(xy, xy)$。

a) 证明或反驳以下陈述：$\left(\mathcal{N}_{\Phi, \Psi}^{\theta, 2}\right)(1,-1)=(4,4)$ 成立（参见定义 1.1.3）。

b) 证明或反驳以下陈述：$\left(\mathcal{N}_{\Phi, \Psi}^{\theta, 2}\right)(-1,1)=(-4,-4)$ 成立（参见定义 1.1.3）。

## 1.1.3 全连接前馈人工神经网络的权重和偏置参数

*备注 1.1.5*（全连接前馈人工神经网络的权重和偏置）。令 $L\in\{2,3, 4,\ldots\}$，$v_{0}, v_{1}, \ldots, v_{L-1}\in\mathbb{N}_{0}$，$l_{0}, l_{1}, \ldots, l_{L},\mathfrak{d}\in\mathbb{N}$，$\theta=\left(\theta_{1}, \theta_{2}, \ldots, \theta_{\mathfrak{d}}\right)\in\mathbb{R}^{\mathfrak{d}}$ 对于所有 $k\in\{0,1,\ldots,L-1\}$ 满足

$$ \mathfrak{d}\geq\sum_{i=1}^{L}l_{i}(l_{i-1}+1) \quad \quad \text{且} \quad \quad v_{k}=\sum_{i=1}^{k}l_{i}(l_{i-1}+1), $$

令 $W_{k}\in\mathbb{R}^{l_{k}\times l_{k-1}}$，$k\in\{1,2,\ldots,L\}$，和 $b_{k}\in\mathbb{R}^{l_{k}}$，$k\in\{1,2,\ldots,L\}$，对于所有 $k\in\{1,2,\ldots,L\}$ 满足

$$ W_{k}=\begin{pmatrix} \theta_{v_{k-1}+1} & \theta_{v_{k-1}+2} & \cdots & \theta_{v_{k-1}+l_{k-1}} \\ \theta_{v_{k-1}+l_{k-1}+1} & \theta_{v_{k-1}+l_{k-1}+2} & \cdots & \theta_{v_{k-1}+2l_{k-1}} \\ \theta_{v_{k-1}+2l_{k-1}+1} & \theta_{v_{k-1}+2l_{k-1}+2} & \cdots & \theta_{v_{k-1}+3l_{k-1}} \\ \vdots & \vdots & \vdots & \vdots \\ \theta_{v_{k-1}+(l_{k-1})l_{k-1}+1} & \theta_{v_{k-1}+(l_{k-1})l_{k-1}+2} & \cdots & \theta_{v_{k-1}+l_{k}l_{k-1}} \end{pmatrix} $$

和

$$ b_{k}=\left(\theta_{v_{k-1}+l_{k}l_{k-1}+1},\theta_{v_{k-1}+l_{k}l_{k-1}+2},\ldots,\theta_{v_{k-1}+l_{k}l_{k-1}+l_{k}}\right), $$

并令 $\Psi_{k}:\mathbb{R}^{l_{k}}\to\mathbb{R}^{l_{k}}$，$k\in\{1,2,\ldots,L\}$ 为函数。则

![](img/dec290f673e6357c31893c67b579ffe1_25_0.png)

图 1.2：人工神经网络（ANN）的图形化说明。该 ANN 具有 2 个隐藏层，长度 $L=3$，其中输入层有 3 个神经元（对应于 $l_{0}=3$），第一个隐藏层有 6 个神经元（对应于 $l_{1}=6$），第二个隐藏层有 3 个神经元（对应于 $l_{2}=3$），输出层有 1 个神经元（对应于 $l_{3}=1$）。在这种情况下，我们有一个具有 39 个权重参数和 10 个偏置参数的 ANN，总共有 49 个参数。该 ANN 的实现是从 $\mathbb{R}^{3}$ 到 $\mathbb{R}$ 的函数。

(i) 成立

$$ \mathcal{N}^{\theta, l_{0}} _ {\psi_{1}, \psi_{2}, \ldots, \psi_{L}} = \Psi_{L} \circ \mathcal{A}^{\theta, v_{L - 1}} _ {l_{L}, l_{L - 1}} \circ \Psi_{L - 1} \circ \mathcal{A}^{\theta, v_{L - 2}} _ {l_{L - 1}, l_{L - 2}} \circ \Psi_{L - 2} \circ \cdots \circ \mathcal{A}^{\theta, v_{1}} _ {l_{2}, l_{1}} \circ \Psi_{1} \circ \mathcal{A}^{\theta, v_{0}} _ {l_{1}, l_{0}} \quad (1.16) $$

(ii) 对于所有 $k \in \{1,2, \ldots,L \}$ 和 $x \in \mathbb{R}^{l_{k - 1}}$，成立 $\mathcal{A}^{\theta, v_{k - 1}} _ {l_{k}, l_{k - 1}}(x) = W_{k}x + b_{k}$

（参见定义 1.1.1 和 1.1.3）。

## 1.2 激活函数

在本节中，我们回顾文献中几种常见的激活函数（关于全连接前馈人工神经网络中激活函数的使用，参见上述定义 1.1.3 和下文定义 1.3.4；关于卷积神经网络（CNNs）中激活函数的使用，参见下文定义 1.4.5；关于残差网络（ResNets）中激活函数的使用，参见下文定义 1.5.4；关于循环神经网络（RNNs）中激活函数的使用，参见下文定义 1.6.3 和 1.6.4）。

### 1.2.1 多维版本

为了描述多维激活函数，我们经常使用函数多维版本的概念。该概念是下一个概念的主题。

**定义 1.2.1**（一维函数的多维版本）。令 $ T \in \mathbb{N} $，$ d_{1}, d_{2}, \ldots, d_{T} \in \mathbb{N} $ 并令 $ \psi: \mathbb{R} \rightarrow \mathbb{R} $ 为一个函数。则我们将

$$ \mathfrak{M}_{\psi, d_{1}, d_{2}, \ldots, d_{T}}: \mathbb{R}^{d_{1} \times d_{2} \times \ldots \times d_{T}} \rightarrow \mathbb{R}^{d_{1} \times d_{2} \times \ldots \times d_{T}} $$

定义为满足对于所有 $ x = (x_{k_{1}, k_{2}, \ldots, k_{T}})_{(k_{1}, k_{2}, \ldots, k_{T}) \in(\prod_{i = 1}^{T}\{1, 2, \ldots, d_{i}\})} \in \mathbb{R}^{d_{1} \times d_{2} \times \ldots \times d_{T}} $，

$ y = (y_{k_{1}, k_{2}, \ldots, k_{T}})_{(k_{1}, k_{2}, \ldots, k_{T}) \in(\prod_{i = 1}^{T}\{1, 2, \ldots, d_{i}\})} \in \mathbb{R}^{d_{1} \times d_{2} \times \ldots \times d_{T}} $，对于 $\forall k_{1} \in\{1, 2, \ldots, d_{1}\}$，$k_{2} \in\{1, 2, \ldots, d_{2}\}$，$\ldots$，$k_{T} \in\{1, 2, \ldots, d_{T}\}$：$y_{k_{1}, k_{2}, \ldots, k_{T}} = \psi(x_{k_{1}, k_{2}, \ldots, k_{T}})$，有

$$ \mathfrak{M}_{\psi, d_{1}, d_{2}, \ldots, d_{T}}(x) = y $$

并且我们称 $\mathfrak{M}_{\psi, d_{1}, d_{2}, \ldots, d_{T}}$ 为 $\psi$ 的 $d_{1} \times d_{2} \times \ldots \times d_{T}$ 维版本。

**示例 1.2.2**（定义 1.2.1 的示例）。令 $A \in \mathbb{R}^{3 \times 1 \times 2}$ 满足

$$ A = ((1, -1), (-2, 2), (3, -3)) $$

并令 $\psi: \mathbb{R} \rightarrow \mathbb{R}$ 对于所有 $x \in \mathbb{R}$ 满足 $\psi(x) = x^{2}$。则

$$ \mathfrak{M}_{\psi, 3, 1, 2}(A) = ((1, 1), (4, 4), (9, 9)) $$

**示例 1.2.2 的证明**。注意 (1.18) 建立了 (1.20)。因此，示例 1.2.2 的证明完成。

**练习 1.2.1**。令 $A \in \mathbb{R}^{2 \times 3}$，$B \in \mathbb{R}^{2 \times 2 \times 2}$ 满足

$$ A = \begin{pmatrix} 3 & -2 & 5 \\ 1 & 0 & -2 \end{pmatrix} \quad \text{且} \quad B = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}, \begin{pmatrix} -3 & -4 \\ 5 & 2 \end{pmatrix} $$

并令 $\psi: \mathbb{R} \rightarrow \mathbb{R}$ 对于所有 $x \in \mathbb{R}$ 满足 $\psi(x) = |x|$。明确指定 $\mathfrak{M}_{\psi, 2, 3}(A)$ 和 $\mathfrak{M}_{\psi, 2, 2, 2}(B)$ 并证明你的结果是正确的（参见定义 1.2.1）。

*练习 1.2.2.* 令 $\theta = (\theta_1, \theta_2, \ldots, \theta_{14}) \in \mathbb{R}^{14}$ 满足

$$ (\theta_1, \theta_2, \ldots, \theta_{14}) = (0, 1, 2, 2, 1, 2, 1, 0, 1, 1, 1, -3, -1, 4, 0, 1) \quad (1.22) $$

并令 $f : \mathbb{R} \to \mathbb{R}$ 和 $g : \mathbb{R} \to \mathbb{R}$ 对于所有 $x \in \mathbb{R}$ 满足

$$ f(x) = \frac{1}{1 + |x|} \quad \text{且} \quad g(x) = x^2 \quad (1.23) $$

明确指定 $\left(\mathcal{N}_{\overline{\mathcal{N}}_{f, 3}, \overline{\mathcal{N}}_{g, 2}}^{g, 1}\right)(1)$ 和 $\left(\mathcal{N}_{\overline{\mathcal{N}}_{g, 2}, \overline{\mathcal{N}}_{f, 3}}^{f, 1}\right)(1)$ 并证明你的结果是正确的（参见定义 1.1.3 和 1.2.1）。

### 1.2.2 单隐藏层全连接前馈人工神经网络

![](img/dec290f673e6357c31893c67b579ffe1_27_0.png)

图 1.3：由两个仿射变换组成的全连接前馈人工神经网络（ANN）的图形化说明（即由 3 层组成：一个输入层，一个隐藏层，和一个输出层），其中输入层上有 $\mathcal{I} \in \mathbb{N}$ 个神经元（即 $\mathcal{I}$ 维输入层），隐藏层上有 $\mathcal{H} \in \mathbb{N}$ 个神经元（即 $\mathcal{H}$ 维隐藏层），输出层上有 1 个神经元（即 1 维输出层）。

