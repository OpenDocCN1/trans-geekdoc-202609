
## 引理 2.4.4

设 $n \in \mathbb{N}$，$a \in C(\mathbb{R}, \mathbb{R})$，$\mathbf{\Phi} \in \mathbf{N}$（参见定义 1.3.1）。则

- (i) 有 $\mathcal{R}_a^\mathbf{N}(\mathbf{\Phi} \bullet \mathbb{S}_{I(\mathbf{\Phi}, n)}) \in C(\mathbb{R}^{n I(\mathbf{\Phi})}, \mathbb{R}^{O(\mathbf{\Phi})})$ 成立，且
- (ii) 对所有 $x_1, x_2, \ldots, x_n \in \mathbb{R}^{I(\mathbf{\Phi})}$，有

$$
(\mathcal{R}_a^\mathbf{N}(\mathbf{\Phi} \bullet \mathbb{S}_{I(\mathbf{\Phi}, n)})(x_1, x_2, \ldots, x_n) = (\mathcal{R}_a^\mathbf{N}(\mathbf{\Phi}))\big(\sum_{k=1}^n x_k\big) \quad (2.140)
$$

（参见定义 1.3.4、2.1.1 和 2.4.1）。

**引理 2.4.4 的证明。** 注意，引理 2.4.2 保证了对所有 $m \in \mathbb{N}$ 和 $x_1, x_2, \ldots, x_n \in \mathbb{R}^m$，有 $\mathcal{R}_a^\mathbf{N}(\mathbb{S}_{m, n}) \in C(\mathbb{R}^{mn}, \mathbb{R}^m)$ 成立，且

$$
(\mathcal{R}_a^\mathbf{N}(\mathbb{S}_{m, n})(x_1, x_2, \ldots, x_n) = \sum_{k=1}^n x_k \quad (2.141)
$$

（参见定义 1.3.4 和 2.4.1）。结合此结论以及命题 2.1.2 中的第 **(v)** 项，可证得第 **(i)** 项和第 **(ii)** 项。引理 2.4.4 的证明由此完成。 $\square$

## 2.4.2 向量作为全连接前馈人工神经网络的串联

**定义 2.4.5** *（矩阵的转置）。* 设 $m, n \in \mathbb{N}$，$A \in \mathbb{R}^{m \times n}$。则我们用 $A^* \in \mathbb{R}^{n \times m}$ 表示 $A$ 的转置。

**定义 2.4.6** *（向量作为全连接前馈人工神经网络的串联）。* 设 $m, n \in \mathbb{N}$。则我们用

$$
\mathbb{T}_{m, n} \in (\mathbb{R}^{(mn) \times m} \times \mathbb{R}^{mn}) \subseteq \mathbf{N} \quad (2.142)
$$

表示由下式给出的全连接前馈人工神经网络

$$
\mathbb{T}_{m, n} = \mathbf{A}_{(I_{m}\ \ I_m\ \ldots\ \ I_m)^*, 0} \quad (2.143)
$$

（参见定义 1.3.1、1.3.2、1.5.5、2.3.1 和 2.4.5）。

**引理 2.4.7.** 设 $m, n \in \mathbb{N}$。则

- (i) 有 $\mathcal{D}(\mathbb{T}_{m, n}) = (m, mn) \in \mathbb{N}^2$ 成立，
- (ii) 对所有 $a \in C(\mathbb{R}, \mathbb{R})$，有 $\mathcal{R}_a^\mathbf{N}(\mathbb{T}_{m, n}) \in C(\mathbb{R}^m, \mathbb{R}^{mn})$ 成立，且
- (iii) 对所有 $a \in C(\mathbb{R}, \mathbb{R})$ 和 $x \in \mathbb{R}^m$，有

$$
(\mathcal{R}_a^\mathbf{N}(\mathbb{T}_{m, n})(x) = (x, x, \ldots, x) \quad (2.144)
$$

（参见定义 1.3.1、1.3.4 和 2.4.6）。

**引理 2.4.7 的证明。** 观察到 $\mathbb{T}_{m,n} \in (\mathbb{R}^{(mn) \times m} \times \mathbb{R}^{mn})$ 这一事实意味着

$$
\mathcal{D}(\mathbb{T}_{m,n}) = (m,mn) \in \mathbb{N}^2 \quad (2.145)
$$

（参见定义 1.3.1 和 2.4.6）。这确立了第 **(i)** 项。注意，引理 2.3.2 中的第 **(iii)** 项表明，对所有 $a \in \mathcal{C}(\mathbb{R}, \mathbb{R})$ 和 $x \in \mathbb{R}^m$，有 $\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{m,n}) \in \mathcal{C}(\mathbb{R}^m, \mathbb{R}^{mn})$ 成立，且

$$
\begin{align*}
(\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{m,n}))(x) &= (\mathcal{R}_a^{\mathbb{N}}(\mathbf{A}_{(\mathbf{l}_m \ \ \ \mathbf{l}_m \ \ldots \ \mathbf{l}_m)^*,\mathbf{0}}))(x) \\
&= (\mathbf{l}_m \ \ \ \mathbf{l}_m \ \ \ldots \ \ \mathbf{l}_m)^*x = (x,x,\ldots,x) \quad (2.146)
\end{align*}
$$

（参见定义 1.3.4、1.5.5、2.3.1 和 2.4.5）。这证明了第 **(ii)** 项和第 **(iii)** 项。引理 2.4.7 的证明由此完成。

**引理 2.4.8.** *设 $n \in \mathbb{N}$，$a \in \mathcal{C}(\mathbb{R}, \mathbb{R})$，$\Phi \in \mathbb{N}$（参见定义 1.3.1）。则*

- (i) *有* $\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{\mathcal{O}(\Phi),n} \bullet \Phi) \in \mathcal{C}(\mathbb{R}^{\mathcal{I}(\Phi)}, \mathbb{R}^{\mathcal{N} \circ \mathcal{I}(\Phi)})$ *成立，且*
- (ii) *对所有* $x \in \mathbb{R}^{\mathcal{I}(\Phi)}$ *，有*

$$
\begin{align*}
(\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{\mathcal{O}(\Phi),n} \bullet \Phi))(x) &= ((\mathcal{R}_a^{\mathbb{N}}(\Phi))(x), (\mathcal{R}_a^{\mathbb{N}}(\Phi))(x), \ldots, (\mathcal{R}_a^{\mathbb{N}}(\Phi))(x)) \quad (2.147)
\end{align*}
$$

（参见定义 1.3.4、2.1.1 和 2.4.6）。

**引理 2.4.8 的证明。** *观察到引理 2.4.7 表明，对所有* $m \in \mathbb{N}$ *和* $x \in \mathbb{R}^m$ *，有* $\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{m,n}) \in \mathcal{C}(\mathbb{R}^m, \mathbb{R}^{mn})$ *成立，且*

$$
(\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{m,n}))(x) = (x,x,\ldots,x) \quad (2.148)
$$

（参见定义 1.3.4 和 2.4.6）。*结合此结论以及命题 2.1.2 中的第* **(v)** *项，可确立第* **(i)** *项和* **(ii)** *项。引理 2.4.8 的证明由此完成。*

**引理 2.4.9.** *设* $m, n \in \mathbb{N}$，$a \in \mathcal{C}(\mathbb{R}, \mathbb{R})$，$\Phi \in \mathbb{N}$ *满足* $\mathcal{I}(\Phi) = mn$ *（参见定义 1.3.1）。则*

- (i) *有* $\mathcal{R}_a^{\mathbb{N}}(\Phi \bullet \mathbb{T}_{m,n}) \in \mathcal{C}(\mathbb{R}^m, \mathbb{R}^{\mathcal{O}(\Phi)})$ *成立，且*
- (ii) *对所有* $x \in \mathbb{R}^m$ *，有*

$$
\begin{align*}
(\mathcal{R}_a^{\mathbb{N}}(\Phi \bullet \mathbb{T}_{m,n}))(x) &= (\mathcal{R}_a^{\mathbb{N}}(\Phi))(x,x,\ldots,x) \quad (2.149)
\end{align*}
$$

（参见定义 1.3.4、2.1.1 和 2.4.6）。

**引理 2.4.9 的证明。** *注意，引理 2.4.7 保证了对所有* $x \in \mathbb{R}^m$ *，有* $\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{m,n}) \in \mathcal{C}(\mathbb{R}^m, \mathbb{R}^{mn})$ *成立，且*

$$
\begin{align*}
(\mathcal{R}_a^{\mathbb{N}}(\mathbb{T}_{m,n}))(x) &= (x,x,\ldots,x) \quad (2.150)
\end{align*}
$$

（参见定义 1.3.4 和 2.4.6）。*结合此结论以及命题 2.1.2 中的第* **(v)** *项，可证得第* **(i)** *项和* **(ii)** *项。引理 2.4.9 的证明由此完成。*

## 2.4.3 全连接前馈人工神经网络的和

**定义 2.4.10** （相同长度全连接前馈 $ANNs$ 的和）。设 $m \in \mathbb{Z}$，$n \in \{m, m+1, \ldots\}$，$\Phi_m, \Phi_{m+1}, \ldots, \Phi_n \in \mathbf{N}$ 且满足对所有 $k \in \{m, m+1, \ldots, n\}$ 有

$$
\mathcal{L}(\Phi_k) = \mathcal{L}(\Phi_m), \qquad \mathcal{I}(\Phi_k) = \mathcal{I}(\Phi_m), \qquad \text{以及} \qquad \mathcal{O}(\Phi_k) = \mathcal{O}(\Phi_m) \quad (2.151)
$$

（参见定义 1.3.1）。则我们用 $\bigoplus_{k=m}^n \Phi_k \in \mathbf{N}$ （记作 $\Phi_m \oplus \Phi_{m+1} \oplus \cdots \oplus \Phi_n \in \mathbf{N}$）表示由下式给出的 *全连接前馈人工神经网络*

$$
\bigoplus_{k=m}^n \Phi_k = \left( \mathcal{SO}_{\mathcal{O}(\Phi_m), n-m+1} \bullet \left[ \mathbf{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \ldots, \Phi_n) \right] \bullet \mathbb{T}_{\mathcal{I}(\Phi_m), n-m+1} \right) \in \mathbf{N} \quad (2.152)
$$

（参见定义 1.3.2、2.1.1、2.2.1、2.4.1 和 2.4.6）。

**引理 2.4.11** （全连接前馈 $ANNs$ 的和的实现）。设 $m \in \mathbb{Z}$，$n \in \{m, m+1, \ldots\}$，$\Phi_m, \Phi_{m+1}, \ldots, \Phi_n \in \mathbf{N}$ 且满足对所有 $k \in \{m, m+1, \ldots, n\}$ 有

$$
\mathcal{L}(\Phi_k) = \mathcal{L}(\Phi_m), \qquad \mathcal{I}(\Phi_k) = \mathcal{I}(\Phi_m), \qquad \text{以及} \qquad \mathcal{O}(\Phi_k) = \mathcal{O}(\Phi_m) \quad (2.153)
$$

（参见定义 1.3.1）。*则*

- (i) 有 $\mathcal{L}\left(\bigoplus_{k=m}^n \Phi_k\right) = \mathcal{L}(\Phi_m)$ 成立，
- (ii) 有
$$
\mathcal{D}\left( \bigoplus_{k=m}^n \Phi_k \right) = \left( \mathcal{I}(\Phi_m), \sum_{k=m}^n \mathbb{D}_1(\Phi_k), \sum_{k=m}^n \mathbb{D}_2(\Phi_k), \ldots, \sum_{k=m}^n \mathbb{D}_{\mathcal{H}(\Phi_m)}(\Phi_k), \mathcal{O}(\Phi_m) \right) \quad (2.154)
$$
成立，且
- (iii) 对所有 $a \in \mathcal{C}(\mathbb{R}^\mathbb{R}, \mathbb{R})$，有
$$
\mathcal{R}_a^\mathbf{N}\left( \bigoplus_{k=m}^n \Phi_k \right) = \sum_{k=m}^n \left( \mathcal{R}_a^\mathbf{N}(\Phi_k) \right) \quad (2.155)
$$
成立
（参见定义 1.3.4 和 2.4.10）。

*引理 2.4.11 的证明*。首先，观察到引理 2.2.2 意味着

$$
\begin{aligned}
&\mathcal{D}(\mathbf{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \ldots, \Phi_n)) \\
= & \left( \sum_{k=m}^n \mathbb{D}_0(\Phi_k), \sum_{k=m}^n \mathbb{D}_1(\Phi_k), \ldots, \sum_{k=m}^n \mathbb{D}_{\mathcal{L}(\Phi_m)-1}(\Phi_k), \sum_{k=m}^n \mathbb{D}_{\mathcal{L}(\Phi_m)}(\Phi_k) \right) \\
= & \left( (n-m+1) \mathcal{I}(\Phi_m), \sum_{k=m}^n \mathbb{D}_1(\Phi_k), \sum_{k=m}^n \mathbb{D}_2(\Phi_k), \ldots, \sum_{k=m}^n \mathbb{D}_{\mathcal{L}(\Phi_m)-1}(\Phi_k), \right. \\
& \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \left. (n-m+1) \mathcal{O}(\Phi_m) \right) \quad (2.156)
\end{aligned}
$$
