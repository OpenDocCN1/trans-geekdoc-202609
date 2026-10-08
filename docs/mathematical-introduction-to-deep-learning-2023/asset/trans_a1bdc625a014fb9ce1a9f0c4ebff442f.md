
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

$$
\mathrm{P}_{n, \Psi}: \left\{ \Phi = (\Phi_1, \dots, \Phi_n) \in \mathbb{N}^n: \; \forall j \in \{1, 2, \dots, n\}: \mathcal{O}(\Phi_j) = \mathcal{I}(\Psi_j) \right\} \to \mathbb{N} \tag{2.105}
$$

表示满足以下条件的函数：对于所有满足 $\forall j \in \{1, 2, \dots, n\}$: $\mathcal{O}(\Phi_j) = \mathcal{I}(\Psi_j)$ 的 $\Phi = (\Phi_1, \dots, \Phi_n) \in \mathbb{N}^n$，

$$
\mathrm{P}_{n, \Psi}(\Phi) = \mathrm{P}\big(\mathcal{E}_{\mathrm{max}_{k \in \{1, \dots, n\}} \mathcal{L}(\Psi_k)}, \Psi_1(\Phi_1), \dots, \mathcal{E}_{\mathrm{max}_{k \in \{1, \dots, n\}} \mathcal{L}(\Psi_k)}, \Psi_n(\Phi_n)\big) \tag{2.106}
$$

（参见定义 2.2.1 和 2.2.8 以及引理 2.2.9）。

**引理 2.2.13**（不同长度全连接前馈 ANNs 并行化的实现）。设 $a \in C(\mathbb{R}, \mathbb{R})$，$n \in \mathbb{N}$，$\mathbb{I} = (\mathbb{I}_1, \dots, \mathbb{I}_n)$，$\Phi = (\Phi_1, \dots, \Phi_n) \in \mathbb{N}^n$ 满足对于所有 $j \in \{1, 2, \dots, n\}$ 和 $x \in \mathbb{R}^{\mathcal{O}(\Phi_j)}$ 有 $\mathcal{H}(\mathbb{I}_j) = 1$，$\mathcal{I}(\mathbb{I}_j) = \mathcal{O}(\mathbb{I}_j) = \mathcal{O}(\Phi_j)$，且 $(\mathcal{R}_a^{\mathbb{N}}(\mathbb{I}_j))(x) = x$（参见定义 1.3.1 和 1.3.4）。则

- (i) 成立
$$
\mathcal{R}_a^{\mathbb{N}}\big(\mathrm{P}_{n, \mathbb{I}}(\Phi)\big) \in C\big(\mathbb{R}^{[\sum_{j=1}^n \mathcal{I}(\Phi_j)]}, \mathbb{R}^{[\sum_{j=1}^n \mathcal{O}(\Phi_j)]}\big) \tag{2.107}
$$
- (ii) 对于所有 $x_1 \in \mathbb{R}^{\mathcal{I}(\Phi_1)}$，$x_2 \in \mathbb{R}^{\mathcal{I}(\Phi_2)}$，$\dots$，$x_n \in \mathbb{R}^{\mathcal{I}(\Phi_n)}$ 成立
$$
\begin{aligned}
& \big(\mathcal{R}_a^{\mathbb{N}}(\mathrm{P}_{n, \mathbb{I}}(\Phi))\big)(x_1, x_2, \dots, x_n) \\
& \qquad = \big((\mathcal{R}_a^{\mathbb{N}}(\Phi_1))(x_1), (\mathcal{R}_a^{\mathbb{N}}(\Phi_2))(x_2), \dots, (\mathcal{R}_a^{\mathbb{N}}(\Phi_n))(x_n)\big) \in \mathbb{R}^{[\sum_{j=1}^n \mathcal{O}(\Phi_j)]}
\end{aligned}
\tag{2.108}
$$

（参见定义 2.2.12）。

**引理 2.2.13 的证明。** 在整个证明过程中，设 $L \in \mathbb{N}$ 满足 $L = \mathrm{max}_{j \in \{1, \dots, n\}} \mathcal{L}(\Phi_j)$。注意引理 2.2.9 中的第 (ii) 项、假设对于所有 $j \in \{1, 2, \dots, n\}$ 成立 $\mathcal{H}(\mathbb{I}_j) = 1$、(2.79)、(2.4) 以及引理 2.2.10 中的第 (ii) 项表明

- (I) 对于所有 $j \in \{1, 2, \dots, n\}$，成立 $\mathcal{L}(\mathcal{E}_{L, \mathbb{I}_j}(\Phi_j)) = L$ 且 $\mathcal{R}_a^{\mathbb{N}}(\mathcal{E}_{L, \mathbb{I}_j}(\Phi_j)) \in C(\mathbb{R}^{\mathcal{I}(\Phi_j)}, \mathbb{R}^{\mathcal{O}(\Phi_j)})$
- (II) 对于所有 $j \in \{1, 2, \dots, n\}$ 和 $x \in \mathbb{R}^{\mathcal{I}(\Phi_j)}$，成立
$$
\big(\mathcal{R}_a^{\mathbb{N}}(\mathcal{E}_{L, \mathbb{I}_j}(\Phi_j))\big)(x) = \big(\mathcal{R}_a^{\mathbb{N}}(\Phi_j)\big)(x)
\tag{2.109}
$$

（参见定义 2.2.8。命题 2.2.3 中的第 (i) 项和第 (ii) 项因此意味着

- (A)
$$
\mathcal{R}_{a}^{\mathbf{N}}\big(\mathbf{P}_{n}(\mathcal{E}_{L, \mathbb{I}_{1}}(\Phi_{1}), \mathcal{E}_{L, \mathbb{I}_{2}}(\Phi_{2}), \ldots, \mathcal{E}_{L, \mathbb{I}_{n}}(\Phi_{n}))\big) \in C\big(\mathbb{R}^{[\sum_{j=1}^{n} \mathcal{I}(\Phi_{j})]}, \mathbb{R}^{[\sum_{j=1}^{n} \mathcal{O}(\Phi_{j})]}\big)
\tag{2.110}
$$
- (B) 对于所有 $x_{1} \in \mathbb{R}^{\mathcal{I}(\Phi_{1})}, x_{2} \in \mathbb{R}^{\mathcal{I}(\Phi_{2})}, \ldots, x_{n} \in \mathbb{R}^{\mathcal{I}(\Phi_{n})}$，成立
$$
\begin{aligned}
& \left(\mathcal{R}_{a}^{\mathbf{N}}\left(\mathbf{P}_{n}\left(\mathcal{E}_{L, \mathbb{I}_{1}}\left(\Phi_{1}\right), \mathcal{E}_{L, \mathbb{I}_{2}}\left(\Phi_{2}\right), \ldots, \mathcal{E}_{L, \mathbb{I}_{n}}\left(\Phi_{n}\right)\right)\right)\right)\left(x_{1}, x_{2}, \ldots, x_{n}\right) \\
& \quad=\left(\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\mathcal{E}_{L, \mathbb{I}_{1}}\left(\Phi_{1}\right)\right)\right)\left(x_{1}\right),\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\mathcal{E}_{L, \mathbb{I}_{2}}\left(\Phi_{2}\right)\right)\right)\left(x_{2}\right), \ldots,\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\mathcal{E}_{L, \mathbb{I}_{n}}\left(\Phi_{n}\right)\right)\right)\left(x_{n}\right)\right) \\
& \quad=\left(\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\Phi_{1}\right)\right)\left(x_{1}\right),\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\Phi_{2}\right)\right)\left(x_{2}\right), \ldots,\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\Phi_{n}\right)\right)\left(x_{n}\right)\right)
\end{aligned}
\tag{2.111}
$$
（参见定义 2.2.1）。将此与 (2.106) 及事实 $L=\max _{j \in\{1, \ldots, n\}} \mathcal{L}(\Phi_{j})$ 结合，确保

- (C)
$$
\mathcal{R}_{a}^{\mathbf{N}}\left(\mathbf{P}_{n, \mathbb{I}}(\Phi)\right) \in C\big(\mathbb{R}^{[\sum_{j=1}^{n} \mathcal{I}(\Phi_{j})]}, \mathbb{R}^{[\sum_{j=1}^{n} \mathcal{O}(\Phi_{j})]}\big)
\tag{2.112}
$$
- (D) 对于所有 $x_{1} \in \mathbb{R}^{\mathcal{I}(\Phi_{1})}, x_{2} \in \mathbb{R}^{\mathcal{I}(\Phi_{2})}, \ldots, x_{n} \in \mathbb{R}^{\mathcal{I}(\Phi_{n})}$，成立
$$
\begin{aligned}
& \left(\mathcal{R}_{a}^{\mathbf{N}}\left(\mathbf{P}_{n, \mathbb{I}}(\Phi)\right)\right)\left(x_{1}, x_{2}, \ldots, x_{n}\right) \\
& \quad=\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\mathbf{P}_{n}\left(\mathcal{E}_{L, \mathbb{I}_{1}}\left(\Phi_{1}\right), \mathcal{E}_{L, \mathbb{I}_{2}}\left(\Phi_{2}\right), \ldots, \mathcal{E}_{L, \mathbb{I}_{n}}\left(\Phi_{n}\right)\right)\right)\right)\left(x_{1}, x_{2}, \ldots, x_{n}\right) \\
& \quad=\left(\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\Phi_{1}\right)\right)\left(x_{1}\right),\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\Phi_{2}\right)\right)\left(x_{2}\right), \ldots,\left(\mathcal{R}_{a}^{\mathbf{N}}\left(\Phi_{n}\right)\right)\left(x_{n}\right)\right).
\end{aligned}
\tag{2.113}
$$

这就建立了第 (i) 项和第 (ii) 项。引理 2.2.13 的证明至此完成。

**练习 2.2.3**。对于每个 $d \in \mathbb{N}$，设 $F_{d}: \mathbb{R}^{d} \rightarrow \mathbb{R}^{d}$ 满足对于所有 $x=(x_{1}, \ldots, x_{d}) \in \mathbb{R}^{d}$ 有
$$
F_{d}(x)=\left(\max \left\{\left|x_{1}\right|\right\}, \max \left\{\left|x_{1}\right|,\left|x_{2}\right|\right\}, \ldots, \max \left\{\left|x_{1}\right|,\left|x_{2}\right|, \ldots,\left|x_{d}\right|\right\}\right)
\tag{2.114}
$$
证明或反驳以下陈述：对于所有 $d \in \mathbb{N}$，存在 $\Phi \in \mathbb{N}$ 使得
$$
\mathcal{R}_{\mathbf{r}}^{\mathbf{N}}(\Phi)=F_{d}
\tag{2.115}
$$
（参见定义 1.2.4、1.3.1 和 1.3.4）。
