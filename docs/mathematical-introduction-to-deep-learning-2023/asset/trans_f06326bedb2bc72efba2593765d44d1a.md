
## 4.4. 多维函数的精化 ANN 近似结果

因此，我们得出，对于所有 $x_{0}\in\mathbb{R}^{l_0}$，$x_{1}\in\mathbb{R}^{\mathrm{l}_{1}}, \ldots, x_{L-1}\in\mathbb{R}^{l_{L-1}}$，以及 $k\in\mathbb{N}\cap(0,L)$ 满足 $\forall m\in\mathbb{N}\cap(0,L)$ 时：$x_m = \mathfrak{M}_{a,l_m}(\mathfrak{M}_{m \times m-1} + \mathfrak{B}_m)$，均有

$$
\pi_k(x_k) = \mathfrak{M}_{a,l_k}(\pi_k(\mathcal{M}_{k,k-1} + \mathfrak{B}_k)) = \mathfrak{M}_{a,l_k}(W_k \pi_{k-1}(x_{k-1}) + B_k) \quad (4.142)
$$

（参见定义 1.2.1）。基于归纳法，假设 $l_0 = \mathrm{l}_0$ 且 $l_L = \mathrm{l}_L$，以及 (4.141)，由此可得，对于所有 $x_{0}\in\mathbb{R}^{l_0}$，$x_{1}\in\mathbb{R}^{\mathrm{l}_{1}}, \ldots, x_{L-1}\in\mathbb{R}^{l_{L-1}}$ 满足 $\forall k\in\mathbb{N}\cap(0,L)$ 时：$x_k = \mathfrak{M}_{a,l_k}(\mathcal{M}_{k}x_{k-1} + \mathfrak{B}_k)$，均有

$$
\begin{aligned}
&(\mathcal{R}_{a}^{\mathrm{N}}(((W_{1},B_{1}),(W_{2},B_{2}),\ldots,(W_{L},B_{L}))))(x_{0}) \\
&\quad = \mathcal{R}_{a}^{\mathrm{N}}(((\mathcal{M}_{1},B_{1}),(W_{2},B_{2}),\ldots,(W_{L},B_{L})))((\pi_{0})(x_{0})) \\
&\quad = W_{L}\pi_{L-1}(x_{L-1}) + B_{L} \\
&\quad = \pi_{L}(\mathcal{M}_{L}x_{L-1} + \mathfrak{B}_{L}) = \mathcal{M}_{L}x_{L-1} + \mathfrak{B}_{L} \\
&\quad = (\mathcal{R}_{a}^{\mathrm{N}}(((\mathcal{M}_{1},\mathfrak{B}_{1}),(\mathcal{M}_{2},\mathfrak{B}_{2}),\ldots,(\mathcal{M}_{L},\mathfrak{B}_{L})))((x_{0})
\end{aligned} \quad (4.143)
$$

因此，引理 4.4.3 的证明完成。

### 引理 4.4.4

设 $a\in C(\mathbb{R},\mathbb{R})$，$L\in\mathbb{N}$，$\mathrm{l}_0, \mathrm{l}_1, \ldots, \mathrm{l}_L$，$l_0, \mathrm{l}_1, \ldots, l_L\in\mathbb{N}$ 满足对于所有 $k\in\{1,2,\ldots,L\}$ 有

$$
\mathrm{l}_0 = l_0, \quad \mathrm{l}_L = l_L, \quad \text{且} \quad \mathrm{l}_k \geq l_k \quad (4.144)
$$

并设 $\Phi\in\mathbb{N}$ 满足 $\mathcal{D}(\Phi) = (l_0, l_1, \ldots, l_L)$（参见定义 1.3.1）。则存在 $\Psi\in\mathbb{N}$ 使得

$$
\mathcal{D}(\Psi) = (\mathrm{l}_0, \mathrm{l}_1, \ldots, \mathrm{l}_L), \quad \|\mathcal{T}(\Psi)\|_\infty = \|\mathcal{T}(\Phi)\|_\infty, \quad \text{且} \quad \mathcal{R}_{a}^{\mathrm{N}}(\Psi) = \mathcal{R}_{a}^{\mathrm{N}}(\Phi) \quad (4.145)
$$

（参见定义 1.3.4、1.3.5 和 3.3.4）。

**引理 4.4.4 的证明。** 在整个证明过程中，设 $B_k = (B_{k,i})_{i\in\{1,2,\ldots,l_k\}}\in\mathbb{R}^{l_k}$，$k\in\{1,2,\ldots,L\}$，且 $W_k = (W_{k,i,j})_{(i,j)\in\{1,2,\ldots,l_k\}\times\{1,2,\ldots,l_{k-1}\}}\in\mathbb{R}^{l_k\times l_{k-1}}$，$k\in\{1,2,\ldots,L\}$，满足

$$
\Phi = ((W_1, B_1), (W_2, B_2), \ldots, (W_L, B_L)) \quad (4.146)
$$

并设 $\mathfrak{M}_k = (\mathfrak{M}_{k,i,j})_{(i,j)\in\{1,2,\ldots,l_k\}\times\{1,2,\ldots,l_{k-1}\}}\in\mathbb{R}^{\mathrm{l}_k\times\mathrm{l}_{k-1}}$，$k\in\{1,2,\ldots,L\}$，且 $\mathfrak{B}_k = (\mathfrak{B}_{k,i})_{i\in\{1,2,\ldots,\mathrm{l}_k\}}\in\mathbb{R}^{\mathrm{l}_k}$，$k\in\{1,2,\ldots,L\}$，满足对于所有 $k\in\{1,2,\ldots,L\}$，$i\in\{1,2,\ldots,\mathrm{l}_k\}$，$j\in\{1,2,\ldots,\mathrm{l}_{k-1}\}$ 有

$$
\mathfrak{M}_{k,i,j} = \begin{cases} 
W_{k,i,j} & : i \leq l_k \land (j \leq l_{k-1}) 
\end{cases}
\quad \text{且} \quad 
\mathfrak{B}_{k,i} = \begin{cases} 
B_{k,i} & : i \leq l_k \\ 
0 & : i > l_k 
\end{cases}
\quad (4.147)
$$

注意，(1.77) 建立了 $((\mathfrak{M}_1, \mathfrak{B}_1), (\mathfrak{M}_2, \mathfrak{B}_2), \ldots, (\mathfrak{M}_L, \mathfrak{B}_L)) \in (\prod_{i=1}^{L}(\mathbb{R}^{\mathrm{l}_i\times\mathrm{l}_{i-1}} \times \mathbb{R}^{\mathrm{l}_i})) \subseteq \mathbb{N}$ 以及

$$
\mathcal{D}(((\mathfrak{M}_1, \mathfrak{B}_1), (\mathfrak{M}_2, \mathfrak{B}_2), \ldots, (\mathfrak{M}_L, \mathfrak{B}_L))) = (\mathrm{l}_0, \mathrm{l}_1, \ldots, \mathrm{l}_L). \quad (4.148)
$$

此外，观察到引理 1.3.8 和 (4.147) 表明

$$
\|\boldsymbol{T}\left(\left(\mathfrak{W}_{1}, \mathfrak{B}_{1}\right),\left(\mathfrak{W}_{2}, \mathfrak{B}_{2}\right), \ldots,\left(\mathfrak{W}_{L}, \mathfrak{B}_{L}\right)\right)\|_{\infty}=\|\boldsymbol{T}(\Phi)\|_{\infty} \quad (4.149)
$$

（参见定义 1.3.5 和 3.3.4）。再者，注意引理 4.4.3 证明了

$$
\begin{aligned}
\mathcal{R}_{a}^{\mathbf{N}}(\Phi) &=\mathcal{R}_{a}^{\mathbf{N}}\left(\left(\left(W_{1}, B_{1}\right),\left(W_{2}, B_{2}\right), \ldots,\left(W_{L}, B_{L}\right)\right)\right) \\
&=\mathcal{R}_{a}^{\mathbf{N}}\left(\left(\mathfrak{W}_{1}, \mathfrak{B}_{1}\right),\left(\mathfrak{W}_{2}, \mathfrak{B}_{2}\right), \ldots,\left(\mathfrak{W}_{L}, \mathfrak{B}_{L}\right)\right)
\end{aligned} \quad (4.150)
$$

（参见定义 1.3.4）。因此，引理 4.4.4 的证明完成。$\square$

### 引理 4.4.5

设 $L, \mathfrak{L} \in \mathbb{N}, l_{0}, l_{1}, \ldots, l_{L}, l_{0}, l_{1}, \ldots, l_{\mathfrak{L}} \in \mathbb{N}, \Phi_{1} = \left(\left(W_{1}, B_{1}\right),\left(W_{2}, B_{2}\right), \ldots,\left(W_{L}, B_{L}\right)\right) \in \left(\prod_{k=1}^{L}\left(\mathbb{R}^{l_{k} \times l_{k-1}} \times \mathbb{R}^{l_{k}}\right)\right), \Phi_{2} = \left(\left(\mathfrak{W}_{1}, \mathfrak{B}_{1}\right),\left(\mathfrak{W}_{2}, \mathfrak{B}_{2}\right), \ldots,\left(\mathfrak{W}_{\mathfrak{L}}, \mathfrak{B}_{\mathfrak{L}}\right)\right) \in \left(\prod_{k=1}^{\mathfrak{L}}\left(\mathbb{R}^{l_{k} \times l_{k-1}} \times \mathbb{R}^{l_{k}}\right)\right)$。则

$$
\left\|\boldsymbol{T}\left(\Phi_{1} \bullet \Phi_{2}\right)\right\|_{\infty} \leq \max \left\{\left\|\boldsymbol{T}\left(\Phi_{1}\right)\right\|_{\infty},\left\|\boldsymbol{T}\left(\Phi_{2}\right)\right\|_{\infty},\left\|\boldsymbol{T}\left(\left(\left(W_{1} \mathfrak{W}_{2}, W_{1} \mathfrak{B}_{2}+B_{1}\right)\right)\right)\right\|_{\infty}\right\} \quad (4.151)
$$

（参见定义 1.3.5、2.1.1 和 3.3.4）。

**引理 4.4.5 的证明。** 观察到 (2.2) 和引理 1.3.8 确立了 (4.151)。因此，引理 4.4.5 的证明完成。$\square$

### 引理 4.4.6

设 $d, L \in \mathbb{N}, \Phi \in \mathbf{N}$ 满足 $L \geq \mathcal{L}(\Phi)$ 且 $d = \mathcal{O}(\Phi)$（参见定义 1.3.1）。则

$$
\left\|\boldsymbol{T}\left(\mathcal{E}_{L, d}\left(\Phi\right)\right)\right\|_{\infty} \leq \max \left\{1,\left\|\boldsymbol{T}(\Phi)\right\|_{\infty}\right\} \quad (4.152)
$$

（参见定义 1.3.5、2.2.6、2.2.8 和 3.3.4）。

**引理 4.4.6 的证明。** 在整个证明过程中，不失一般性地假设 $L > \mathcal{L}(\Phi)$，并设 $l_{0}, l_{1}, \ldots, l_{L-\mathcal{L}(\Phi)+1} \in \mathbb{N}$ 满足

$$
\left(l_{0}, l_{1}, \ldots, l_{L-\mathcal{L}(\Phi)+1}\right)=(d, 2 d, 2 d, \ldots, 2 d, d). \quad (4.153)
$$

注意，引理 2.2.7 表明 $\mathcal{D}\left(\mathfrak{I}_{d}\right)=(d, 2 d, d) \in \mathbb{N}^{3}$（参见定义 2.2.6）。因此，引理 2.2.9 中的条目 (i) 确保

$$
\begin{aligned}
\mathcal{L}\left(\left(\mathfrak{I}_{d}\right)^{\bullet(L-\mathcal{L}(\Phi))}\right) &=L-\mathcal{L}(\Phi)+1 \\
\text{且} \quad \mathcal{D}\left(\left(\mathfrak{I}_{d}\right)^{\bullet(L-\mathcal{L}(\Phi))}\right) &=\left(l_{0}, l_{1}, \ldots, l_{L-\mathcal{L}(\Phi)+1}\right) \in \mathbb{N}^{L-\mathcal{L}(\Phi)+2}
\end{aligned} \quad (4.154)
$$

（参见定义 2.1.1）。这意味着存在 $W_{k} \in \mathbb{R}^{l_{k} \times l_{k-1}}, k \in \{1,2, \ldots, L-\mathcal{L}(\Phi)+1\}$ 以及 $B_{k} \in \mathbb{R}^{l_{k}}, k \in \{1,2, \ldots, L-\mathcal{L}(\Phi)+1\}$，满足

$$
\left(\mathfrak{I}_{d}\right)^{\bullet(L-\mathcal{L}(\Phi))}=\left(\left(W_{1}, B_{1}\right),\left(W_{2}, B_{2}\right), \ldots,\left(W_{L-\mathcal{L}(\Phi)+1}, B_{L-\mathcal{L}(\Phi)+1}\right)\right). \quad (4.155)
$$

