
证明了第 **iii** 项。接下来注意，**(4.23)** 意味着第 **iv** 项。此外，注意到 $\mathcal{W}_{2, \underline{\mathbf{L}}_1} = (1 \ 1)$ 这一事实，以及 $\underline{\mathbf{L}}_d = \mathbf{S}_{1, d} \bullet \mathbf{P}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1)$ 这一事实，表明

$$
\begin{align*}
\mathcal{W}_{2, \mathbf{L}_d} &= \mathcal{W}_{1, \mathbf{S}_{1, d}} \mathcal{W}_{2, \underline{\mathbf{L}}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1)} \\
&= \underbrace{\begin{pmatrix} 1 & 1 & \cdots & 1 \end{pmatrix}}_{\in \mathbb{R}^{1 \times d}} \underbrace{\begin{pmatrix} \mathcal{W}_{2, \underline{\mathbf{L}}_1} & 0 & \cdots & 0 \\ 0 & \mathcal{W}_{2, \underline{\mathbf{L}}_1} & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & \mathcal{W}_{2, \underline{\mathbf{L}}_1} \end{pmatrix}}_{\in \mathbb{R}^{d \times (2d)}} \\
&= \begin{pmatrix} 1 & 1 & \cdots & 1 \end{pmatrix} \in \mathbb{R}^{1 \times (2d)}.
\end{align*}
$$

这确立了第 **v** 项。引理 **4.2.3** 的证明由此完成。$\square$

*练习* **4.2.1**。令 $d = 9$，$S = \{ (1, 3), (3, 5) \}$，$V = (V_{r, k})_{(r, k) \in S} \in \prod_{(r, k) \in S} \mathbb{R}^{d \times d}$ 满足 $V_{1, 3} = V_{3, 5} = \mathbf{I}_d$，令 $\Psi \in \mathbb{N}$ 满足

$$
\Psi = \mathbf{J}_d \bullet \mathbf{P}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1) \bullet \mathbf{J}_d \bullet \mathbf{P}_d(\underline{\mathbf{L}}_1, \underline{\mathbf{L}}_1, \dots, \underline{\mathbf{L}}_1),
$$

并令 $\Phi \in \mathbf{R}$ 满足

$$
\Phi = (\Psi, (V_{r, k})_{(r, k) \in S})
$$

(参见定义 **1.3.1, 1.5.1, 1.5.5, 2.1.1, 2.2.1, 2.2.6** 和 **4.2.1**)。对于每个 $x \in \mathbb{R}^d$，明确写出

$$
\mathcal{R}_t^\mathbf{R}(\Phi)(x)
$$

并证明你的结果是正确的（参见定义 **1.2.4** 和 **1.5.4**）。

### 4.2.2 最大值的ANN表示

**引理 4.2.4**（全连接前馈最大值 **ANN** 的唯一存在性）。*存在唯一的* $(\phi_d)_{d \in \mathbb{N}} \subseteq \mathbb{N}$ *满足以下性质*

- (i) 对于所有 $d \in \mathbb{N}$，有 $\mathcal{I}(\phi_d) = d$，
- (ii) 对于所有 $d \in \mathbb{N}$，有 $\mathcal{O}(\phi_d) = 1$，
- (iii) 有 $\phi_1 = \mathbf{A}_{1, 0} \in \mathbb{R}^{1 \times 1} \times \mathbb{R}^1$，
- (iv) 有

$$
\phi_2 = \left(
\begin{pmatrix}
1 & -1 \\
0 & 1 \\
0 & -1
\end{pmatrix},
\begin{pmatrix}
0 \\
0
\end{pmatrix}
\right),
\left(
\begin{pmatrix}
1 & 1 & -1
\end{pmatrix},
\begin{pmatrix}
0
\end{pmatrix}
\right)
\in \left(\mathbb{R}^{3 \times 2} \times \mathbb{R}^3\right) \times \left(\mathbb{R}^{1 \times 3} \times \mathbb{R}^1\right),
$$

- (v) 对于所有 $d \in \{2,3,4, \ldots\}$，有 $\phi_{2d} = \phi_{d} \bullet (\mathbf{P}_{d}(\phi_{2}, \phi_{2}, \ldots, \phi_{2}))$，且
- (vi) 对于所有 $d \in \{2,3,4, \ldots\}$，有 $\phi_{2d-1} = \phi_{d} \bullet (\mathbf{P}_{d}(\phi_{2}, \phi_{2}, \ldots, \phi_{2}, \mathbf{J}_{1}))$

(参见定义 1.3.1, 2.1.1, 2.2.1, 2.2.6 和 2.3.1)。

引理 4.2.4 的证明。在整个证明过程中，令 $\psi \in \mathbf{N}$ 满足

$$
\psi = \left( \left( \begin{pmatrix} 1 & -1 \\ 0 & 1 \\ 0 & -1 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \right), \left( (1 \quad 1 \quad -1), (0) \right) \right) \in (\mathbb{R}^{3 \times 2} \times \mathbb{R}^{3}) \times (\mathbb{R}^{1 \times 3} \times \mathbb{R}^{1}) \tag{4.29}
$$

(参见定义 1.3.1)。观察到 (4.29) 和引理 2.2.7 表明

$$
\mathcal{I}(\psi) = 2, \quad \mathcal{O}(\psi) = \mathcal{I}(\mathbf{J}_{1}) = \mathcal{O}(\mathbf{J}_{1}) = 1, \quad \text{且} \quad \mathcal{L}(\psi) = \mathcal{L}(\mathbf{J}_{1}) = 2. \tag{4.30}
$$

因此，引理 2.2.2 和引理 2.2.7 证明了对于所有 $d \in \mathbf{N} \cap (1, \infty)$，有

$$
\mathcal{I}(\mathbf{P}_{d}(\psi, \psi, \ldots, \psi)) = 2d, \quad \mathcal{O}(\mathbf{P}_{d}(\psi, \psi, \ldots, \psi)) = d, \tag{4.31}
$$

$$
\mathcal{I}(\mathbf{P}_{d}(\psi, \psi, \ldots, \psi, \mathbf{J}_{1})) = 2d-1, \quad \text{且} \quad \mathcal{O}(\mathbf{P}_{d}(\psi, \psi, \ldots, \psi, \mathbf{J}_{1})) = d \tag{4.32}
$$

(参见定义 2.2.1 和 2.2.6)。结合 (4.30)、命题 2.1.2 以及归纳法，可知存在唯一的 $\phi_{d} \in \mathbf{N}$，$d \in \mathbf{N}$，使得对于所有 $d \in \mathbf{N}$，有 $\mathcal{I}(\phi_{d}) = d$，$\mathcal{O}(\phi_{d}) = 1$，且

$$
\phi_{d} = \begin{cases} 
\mathbf{A}_{1,0} & : d=1 \\ 
\psi & : d=2 \\ 
\phi_{d/2} \bullet (\mathbf{P}_{d/2}(\psi, \psi, \ldots, \psi)) & : d \in \{4,6,8,\ldots\} \\ 
\phi_{(d+1)/2} \bullet (\mathbf{P}_{(d+1)/2}(\psi, \psi, \ldots, \psi, \mathbf{J}_{1})) & : d \in \{3,5,7,\ldots\}. 
\end{cases} \tag{4.33}
$$

引理 4.2.4 的证明由此完成。$\square$

# 定义 4.2.5 (最大值ANN表示)。我们将满足以下性质的全连接前馈 $ANN$ 记为 $(\mathbb{M}_{d})_{d \in \mathbf{N}} \subseteq \mathbf{N}$

- (i) 对于所有 $d \in \mathbf{N}$，有 $\mathcal{I}(\mathbb{M}_{d}) = d$，
- (ii) 对于所有 $d \in \mathbf{N}$，有 $\mathcal{O}(\mathbb{M}_{d}) = 1$，
- (iii) 有 $\mathbb{M}_{1} = \mathbf{A}_{1,0} \in \mathbb{R}^{1 \times 1} \times \mathbb{R}^{1}$，
- (iv) 有

$$
\mathbb{M}_{2} = \left( \left( \begin{pmatrix} 1 & -1 \\ 0 & 1 \\ 0 & -1 \end{pmatrix}, \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \right), \left( (1 \quad 1 \quad -1), (0) \right) \right) \in (\mathbb{R}^{3 \times 2} \times \mathbb{R}^{3}) \times (\mathbb{R}^{1 \times 3} \times \mathbb{R}^{1}). \tag{4.34}
$$

- (v) 对于所有 $d \in \{2,3,4, \ldots\}$，有 $\mathbb{M}_{2d} = \mathbb{M}_d \bullet \left(\mathbf{P}_d(\mathbb{M}_2, \mathbb{M}_2, \ldots, \mathbb{M}_2)\right)$，且
- (vi) 对于所有 $d \in \{2,3,4, \ldots\}$，有 $\mathbb{M}_{2d-1} = \mathbb{M}_d \bullet \left(\mathbf{P}_d(\mathbb{M}_2, \mathbb{M}_2, \ldots, \mathbb{M}_2, \mathbf{J}_1)\right)$

(参见定义 1.3.1, 2.1.1, 2.2.1, 2.2.6 和 2.3.1 以及引理 4.2.4)。

# 定义 4.2.6 (实数的下取整和上取整)。我们将满足对于所有 $x \in \mathbb{R}$ 以下性质的函数 $\lceil \cdot \rceil : \mathbb{R} \rightarrow \mathbb{Z}$ 和 $\lfloor \cdot \rfloor : \mathbb{R} \rightarrow \mathbb{Z}$ 分别记为

$$
\lceil x \rceil = \min(\mathbb{Z} \cap [x, \infty)) \qquad \text{且} \qquad \lfloor x \rfloor = \max(\mathbb{Z} \cap (-\infty, x]).
$$

*练习* 4.2.2。证明或反驳以下陈述：对于所有 $n \in \{3,5,7, \ldots\}$，有 $\lceil \log_2(n+1) \rceil = \lceil \log_2(n) \rceil$。

# 命题 4.2.7 (全连接前馈最大值ANN的性质)。设 $d \in \mathbb{N}$。则

- (i) 有 $\mathcal{H}(\mathbb{M}_d) = \lceil \log_2(d) \rceil$，
- (ii) 对于所有 $i \in \mathbb{N}$，有 $\mathrm{D}_i(\mathbb{M}_d) \leq 3\lceil \frac{d}{2^i} \rceil$，
- (iii) 有 $\mathcal{R}_{\mathfrak{r}}^{\mathbb{N}}(\mathbb{M}_d) \in C(\mathbb{R}^d, \mathbb{R})$，且
- (iv) 对于所有 $x = (x_1, \ldots, x_d) \in \mathbb{R}^d$，有 $(\mathcal{R}_{\mathfrak{r}}^{\mathbb{N}}(\mathbb{M}_d))(x) = \max\{x_1, x_2, \ldots, x_d\}$

(参见定义 1.2.4, 1.3.1, 1.3.4, 4.2.5 和 4.2.6)。

命题 4.2.7 的$证明$。在整个证明过程中，不失一般性地假设 $d > 1$。注意到 (4.34) 保证了

$$
\mathcal{H}(\mathbb{M}_2) = 1 \tag{4.36}
$$

(参见定义 1.3.1 和 4.2.5)。结合 (2.44) 可知，对于所有 $\mathfrak{d} \in \{2,3,4, \ldots\}$，有

$$
\mathcal{H}(\mathbf{P}_\mathfrak{d}(\mathbb{M}_2, \mathbb{M}_2, \ldots, \mathbb{M}_2)) = \mathcal{H}(\mathbf{P}_\mathfrak{d}(\mathbb{M}_2, \mathbb{M}_2, \ldots, \mathbb{M}_2, \mathbf{J}_1)) = \mathcal{H}(\mathbb{M}_2) = 1 \tag{4.37}
$$

(参见定义 2.2.1 和 2.2.6)。将此结果与命题 2.1.2 结合，可建立对于所有 $\mathfrak{d} \in \{3,4,5, \ldots\}$，有

$$
\mathcal{H}(\mathbb{M}_\mathfrak{d}) = \mathcal{H}(\mathbb{M}_{\lceil \eta \rceil}) + 1 \tag{4.38}
$$

(参见定义 4.2.6)。这确保了对于所有 $\mathfrak{d} \in \{4,6,8, \ldots\}$ 且 $\mathcal{H}(\mathbb{M}_{\lceil \eta \rceil}) = \lceil \log_2(\eta / 2) \rceil$，有

$$
\mathcal{H}(\mathbb{M}_\mathfrak{d}) = \lceil \log_2(\eta / 2) \rceil + 1 = \lceil \log_2(\mathfrak{d}) - 1 \rceil + 1 = \lceil \log_2(\mathfrak{d}) \rceil. \tag{4.39}
$$

