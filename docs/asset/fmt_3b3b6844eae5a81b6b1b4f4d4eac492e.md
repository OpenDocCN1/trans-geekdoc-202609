
\mathcal{E}_{L, \mathbb{I}}(\Phi) = (\mathbb{I}^{* (L-\mathcal{L}(\Phi))}) \bullet \Phi

$$

（参见定义 1.3.1、2.1.1 和 2.1.6）。

### 引理 2.2.9（全连接前馈人工神经网络扩展的长度）

设 $d, \mathbf{i} \in \mathbb{N}$，$\Psi \in \mathbb{N}$ 满足 $\mathcal{D}(\Psi) = (d, \mathbf{i}, d)$（参见定义 1.3.1）。则：

- (i) 对于所有 $n \in \mathbb{N}_0$，成立 $\mathcal{H}(\Psi^{*n}) = n$，$\mathcal{L}(\Psi^{*n}) = n+1$，$\mathcal{D}(\Psi^{*n}) \in \mathbb{N}^{n+2}$，且

$$

\mathcal{D}(\Psi^{*n}) = \begin{cases} 

(d, d) & : n = 0 \\ 

(d, \mathbf{i}, \mathbf{i}, \ldots, \mathbf{i}, d) & : n \in \mathbb{N} 

\end{cases} \tag{2.80}

$$

- (ii) 对于所有 $\Phi \in \mathbb{N}$ 以及 $L \in \mathbb{N} \cap [\mathcal{L}(\Phi), \infty)$ 且满足 $\mathcal{O}(\Phi) = d$，成立

$$

\mathcal{L}(\mathcal{E}_{L, \Psi}(\Phi)) = L \tag{2.81}

$$

（参见定义 2.1.6 和 2.2.8）。

### 引理 2.2.9 的证明

在整个证明过程中，设 $\Phi \in \mathbb{N}$ 满足 $\mathcal{O}(\Phi) = d$。观察到，引理 2.1.7 以及 $\mathcal{H}(\Psi) = 1$ 的事实表明，对于所有 $n \in \mathbb{N}_0$，成立：

$$

\mathcal{H}(\Psi^{*n}) = n\mathcal{H}(\Psi) = n \tag{2.82}

$$

（参见定义 2.1.6）。将此结果与 (1.78) 以及引理 1.3.3 结合，确保了：

$$

\mathcal{H}(\Psi^{*n}) = n, \quad \mathcal{L}(\Psi^{*n}) = n+1, \quad \text{且} \quad \mathcal{D}(\Psi^{*n}) \in \mathbb{N}^{n+2}. \tag{2.83}

$$

接下来我们声称，对于所有 $n \in \mathbb{N}_0$，成立：

$$

\mathbb{N}^{n+2} \supseteq \mathcal{D}(\Psi^{*n}) = \begin{cases} 

(d, d) & : n = 0 \\ 

(d, \mathbf{i}, \mathbf{i}, \ldots, \mathbf{i}, d) & : n \in \mathbb{N}. 

\end{cases} \tag{2.84}

$$

现在我们通过对 $n \in \mathbb{N}_0$ 进行归纳来证明 (2.84)。注意，以下事实：

$$

\Psi^{*0} = (\mathbf{I}_d, 0) \in \mathbb{R}^{d \times d} \times \mathbb{R}^{d} \tag{2.85}

$$

在基础情形 $n = 0$ 时建立了 (2.84)（参见定义 1.5.5）。

对于归纳步骤，假设存在某个 $n \in \mathbb{N}_0$ 满足：

$$

\mathbb{N}^{n+2} \supseteq \mathcal{D}(\Psi^{*n}) = \begin{cases} 

(d, d) & : n = 0 \\ 

(d, \mathbf{i}, \mathbf{i}, \ldots, \mathbf{i}, d) & : n \in \mathbb{N}. 

\end{cases} \tag{2.86}

$$

注意，(2.86)、(2.41)、(2.83)、命题 2.1.2 的条目 (i) 以及 $\mathcal{D}(\Psi) = (d, \mathbf{i}, d) \in \mathbb{N}^{3}$ 的事实意味着：

$$

\mathcal{D}(\Psi^{*(n+1)}) = \mathcal{D}(\Psi \bullet (\Psi^{*n})) = (d, \mathbf{i}, \mathbf{i}, \ldots, \mathbf{i}, d) \in \mathbb{N}^{n+3} \tag{2.87}

$$

（参见定义 2.1.1）。因此，归纳法证明了 (2.84)。结合 (2.83) 建立了条目 (i)。

观察到，(2.79)、命题 2.1.2 的条目 (iii)、(2.82) 以及 $\mathcal{H}(\Phi) = \mathcal{L}(\Phi) - 1$ 的事实意味着，对于所有 $L \in \mathbb{N} \cap [\mathcal{L}(\Phi), \infty)$，成立：

$$

\begin{split}

\mathcal{H}(\mathcal{E}_{L, \Psi}(\Phi)) &= \mathcal{H}((\Psi^{\bullet (L - \mathcal{L}(\Phi))}} \bullet \Phi) = \mathcal{H}(\Psi^{\bullet (L - \mathcal{L}(\Phi))}}) + \mathcal{H}(\Phi) \\

&= (L - \mathcal{L}(\Phi)) + \mathcal{H}(\Phi) = L - 1.

\end{split} \tag{2.88}

$$

因此，$\mathcal{H}(\mathcal{E}_{L, \Psi}(\Phi)) = \mathcal{L}(\mathcal{E}_{L, \Psi}(\Phi)) - 1$ 这一事实证明了：

$$

\mathcal{L}(\mathcal{E}_{L, \Psi}(\Phi)) = \mathcal{H}(\mathcal{E}_{L, \Psi}(\Phi)) + 1 = L. \tag{2.89}

$$

这就建立了条目 (ii)。因此，引理 2.2.9 的证明完毕。

### 引理 2.2.10（全连接前馈人工神经网络扩展的实化）

*设* $a \in C(\mathbb{R}, \mathbb{R})$，$\mathbb{I} \in \mathbf{N}$ *满足* $\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}) = \mathrm{id}_{\mathbb{R}^{\mathbb{I}(1)}}$ *（参见定义 1.3.1 和 1.3.4）。则：*

- (i) 对于所有 $n \in \mathbb{N}_0$，成立

$$

\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n}) = \mathrm{id}_{\mathbb{R}^{\mathbb{I}(1)}} \tag{2.90}

$$

- (ii) 对于所有 $\Phi \in \mathbf{N}$ 以及 $L \in \mathbb{N} \cap [\mathcal{L}(\Phi), \infty)$ *且满足* $\mathcal{O}(\Phi) = \mathbb{I}(1)$ *，成立*

$$

\mathcal{R}^{\mathbf{N}}_{a}(\mathcal{E}_{L, \mathbb{I}}(\Phi)) = \mathcal{R}^{\mathbf{N}}_{a}(\Phi) \tag{2.91}

$$

*（参见定义 2.1.6 和 2.2.8。)*

### 引理 2.2.10 的证明

在整个证明过程中，设 $\Phi \in \mathbf{N}$，$L, d \in \mathbb{N}$ 满足 $\mathcal{L}(\Phi) \leq L$ 且 $\mathbb{I}(1) = \mathcal{O}(\Phi) = d$。我们声称，对于所有 $n \in \mathbb{N}_0$，成立：

$$

\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n}) \in C(\mathbb{R}^{d}, \mathbb{R}^{d}) \quad \text{且} \quad \forall x \in \mathbb{R}^{d}: \ (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n}))(x) = x. \tag{2.92}

$$

现在我们通过对 $n \in \mathbb{N}_0$ 进行归纳来证明 (2.92)。注意，(2.41) 以及 $\mathcal{O}(\mathbb{I}) = d$ 的事实表明 $\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* 0}) \in C(\mathbb{R}^{d}, \mathbb{R}^{d})$ 且 $\forall x \in \mathbb{R}^{d}$: $(\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* 0}))(x) = x$。这在基础情形 $n = 0$ 时建立了 (2.92)。

对于归纳步骤，观察到对于所有 $n \in \mathbb{N}_0$，若 $\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n}) \in C(\mathbb{R}^{d}, \mathbb{R}^{d})$ 且 $\forall x \in \mathbb{R}^{d}$: $(\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n}))(x) = x$，则成立：

$$

\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{*(n+1)}) = \mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I} \bullet (\mathbb{I}^{* n})) = (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I})) \circ (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n})) \in C(\mathbb{R}^{d}, \mathbb{R}^{d}) \tag{2.93}

$$

*且*

$$

\begin{split}

\forall x \in \mathbb{R}^{d}: \ (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{*(n+1))})(x) &= ((\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I})) \circ [\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n})])(x) \\

&= (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I})) (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I}^{* n})(x)) = (\mathcal{R}^{\mathbf{N}}_{a}(\mathbb{I})) (x) = x. \tag{2.94}

\end{split}

$$

因此，归纳法证明了(2.92)。这就建立了第 (i) 项。注意 (2.79)、命题 2.1.2 中的第 (v) 项、第 (i) 项，以及事实 $\mathcal{I}(\mathbb{I})=\mathcal{O}(\mathbb{I})$ 确保

$$

\begin{align*}

\mathcal{R}_{a}^{\mathbb{N}}(\mathcal{E}_{L,\mathbb{I}}(\Phi)) &= \mathcal{R}_{a}^{\mathbb{N}}([\mathbb{I}^{*}(L-L(\Phi))] \bullet \Phi) \\

&\in C(\mathbb{R}^{\mathcal{I}(\Phi)},\mathbb{R}^{\mathcal{O}(\mathbb{I})}) = C(\mathbb{R}^{\mathcal{I}(\Phi)},\mathbb{R}^{\mathcal{I}(\mathbb{I})}) = C(\mathbb{R}^{\mathcal{I}(\Phi)},\mathbb{R}^{\mathcal{O}(\Phi)})

\end{align*}

$$

以及

$$

\begin{align*}

\forall x \in \mathbb{R}^{\mathcal{I}(\Phi)}: \; (\mathcal{R}_{a}^{\mathbb{N}}(\mathcal{E}_{L,\mathbb{I}}(\Phi)))(x) &= (\mathcal{R}_{a}^{\mathbb{N}}([\mathbb{I}^{*}(L-L(\Phi))] \bullet \Phi))(x) \\

&= (\mathcal{R}_{a}^{\mathbb{N}}(\Phi))(x).

\end{align*}

$$

这就建立了第 (ii) 项。引理 2.2.10 的证明至此完成。

**引理 2.2.11**（全连接前馈 *ANN* 扩展的架构）。设 $d,\mathbb{I},L,\mathfrak{L}\in\mathbb{N}$，$l_{0},l_{1},\ldots,l_{L-1}\in\mathbb{N}$，$\Phi,\Psi\in\mathbf{N}$ 满足

$$

\mathfrak{L}\geq L, \quad \mathcal{D}(\Phi)=(l_{0},l_{1},\ldots,l_{L-1},d), \quad \text{以及} \quad \mathcal{D}(\Psi)=(d,\mathbb{I},d)

$$

（参见 *定义* 1.3.1）。则 $\mathcal{D}(\mathcal{E}_{\mathfrak{L},\Psi}(\Phi))\in\mathbb{N}^{\mathfrak{L}+1}$ 且

$$

\mathcal{D}(\mathcal{E}_{\mathfrak{L},\Psi}(\Phi)) = \begin{cases}(l_{0},l_{1},\ldots,l_{L-1},d) & \text{： } \mathfrak{L}=L \\

(l_{0},l_{1},\ldots,l_{L-1},\mathbb{I},\mathbb{I},\ldots,\mathbb{I},d) & \text{： } \mathfrak{L}>L

\end{cases}

$$

（参见 *定义* 2.2.8）。

*引理 2.2.11 的证明。* 注意到 *引理* 2.2.9 中的第 (i) 项表明

$$

\mathcal{H}(\Psi^{\bullet(\mathfrak{L}-L)}) = \mathfrak{L}-L, \quad \quad \mathcal{D}(\Psi^{\bullet(\mathfrak{L}-L)}) \in \mathbb{N}^{\mathfrak{L}-L+2}

$$

以及

$$

\mathcal{D}(\Psi^{\bullet(\mathfrak{L}-L)}) = \begin{cases}(d,d) & \text{： } \mathfrak{L}=L \\

(d,\mathbb{I},\mathbb{I},\ldots,\mathbb{I},d) & \text{： } \mathfrak{L}>L

\end{cases}

$$

（参见 *定义* 2.1.6）。结合 *命题* 2.1.2 可得

$$

\mathcal{H}((\Psi^{\bullet(\mathfrak{L}-L)} \bullet \Phi)) = \mathcal{H}(\Psi^{\bullet(\mathfrak{L}-L)})+\mathcal{H}(\Phi) = (\mathfrak{L}-L)+L-1 = \mathfrak{L}-1,

$$

$$

\mathcal{D}((\Psi^{\bullet(\mathfrak{L}-L)} \bullet \Phi)) \in \mathbb{N}^{\mathfrak{L}+1},

$$

以及

$$

\mathcal{D}(((\Psi^{\bullet(\mathfrak{L}-L)} \bullet \Phi)) = \begin{cases}(l_{0},l_{1},\ldots,l_{L-1},d) & \text{： } \mathfrak{L}=L \\

(l_{0},l_{1},\ldots,l_{L-1},\mathbb{I},\mathbb{I},\ldots,\mathbb{I},d) & \text{： } \mathfrak{L}>L

\end{cases}

$$

这与 (2.79) 共同建立了 (2.98)。引理 2.2.11 的证明至此完成。

## 2.2.4 不同长度全连接前馈 ANNs 的并行化

**定义 2.2.12**（不同长度全连接前馈 ANNs 的并行化）。设 $n \in \mathbb{N}$，$\Psi = (\Psi_1, \dots, \Psi_n) \in \mathbb{N}^n$ 满足对于所有 $j \in \{1, 2, \dots, n\}$ 有

$$

\mathcal{H}(\Psi_j) = 1 \quad \text{且} \quad \mathcal{I}(\Psi_j) = \mathcal{O}(\Psi_j) \tag{2.104}

$$

（参见定义 1.3.1）。则我们用
