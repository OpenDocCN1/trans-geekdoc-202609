

(10.10)
$$
\hat{\mathbf{R}}_x = \mathbf{X}\mathbf{X}^T = \hat{\mathbf{\Phi}}_s \hat{\mathbf{\Lambda}}_s \hat{\mathbf{\Phi}}_s^T + \hat{\mathbf{\Phi}}_e \hat{\mathbf{\Lambda}}_e \hat{\mathbf{\Phi}}_e^T
$$

其中，分解的前 $m$ 个左奇异向量被指定为 $\hat{\mathbf{\Phi}}_s$，剩余的特征向量为 $\hat{\mathbf{\Phi}}_e$。相应地，对角矩阵 $\hat{\mathbf{\Lambda}}_s$ 包含前 $m$ 个特征值，而 $\hat{\mathbf{\Lambda}}_e$ 包含其余特征值。使用最小二乘（LS）拟合来估计上述参数的通用规则是：

(10.11)
$$
\{\hat{\mathbf{\rho}}, \hat{\mathbf{\theta}}, \hat{\mathbf{S}}\} = \arg\min_{\mathbf{\rho}, \mathbf{\theta}, \mathbf{S}} \|\mathbf{X} - \mathbf{A}(\mathbf{\rho}, \mathbf{\theta})\mathbf{S}^T\|_F^2
$$

其中 $\| \cdot \|_F$ 表示 Frobenius 范数。通过最优代入 [\[40\]](#c10.xhtml#c10-bib-0040)，我们得到：

(10.12)
$$
\{\hat{\mathbf{\rho}}, \hat{\mathbf{\theta}}\} = \arg\min_{\mathbf{\rho}, \mathbf{\theta}} \|\mathbf{X} - \mathbf{A}\mathbf{A}^\dagger\mathbf{X}\|_F^2
$$

其中 $\mathbf{A}^\dagger$ 是 $\mathbf{A}$ 的 Moore-Penrose 伪逆 [\[41\]](#c10.xhtml#c10-bib-0041)。鉴于 $\mathbf{A}(\mathbf{\rho}, \mathbf{\theta})$ 的秩为 $m$ 且 $\hat{\mathbf{\Phi}}_s$ 的秩至少为 $m$，最小子空间相关值 $C[m] = \text{subcorr}\{\mathbf{A}(\mathbf{\rho}, \mathbf{\theta}), \hat{\mathbf{\Phi}}_s\}[m]$，表示 $\mathbf{A}(\mathbf{\rho},\mathbf{\theta})$ 的列空间中的主向量与信号子空间 $\hat{\mathbf{\Phi}}_s$ 之间的最小子空间相关性（最大主角）。在 MUSIC 算法中，$\mathbf{A}(\mathbf{\rho}, \mathbf{\theta})$ 的任意单列，即 $\mathbf{a}(\mathbf{\rho}_i, \mathbf{\theta}_i)$ 与信号子空间的子空间相关性因此必须等于或超过此最小子空间相关性：

(10.13)
$$
C_i = \text{subcorr}\{\mathbf{a}(\mathbf{\rho}_i, \mathbf{\theta}_i), \hat{\mathbf{\Phi}}_s\} \ge C_m
$$

当样本数量增加或信噪比（SNR）变高时，$\hat{\mathbf{\Phi}}_s$ 趋近于 $\mathbf{\Phi}_s$。随后，当识别出正确的参数集时，最小相关性趋近于 1，使得 $m$ 组不同的参数 $(\mathbf{\rho}_i, \mathbf{\theta}_i)$ 具有趋近于 1 的子空间相关性。因此，采用搜索策略来寻找该度量的 $m$ 个峰值 [\[35\]](#c10.xhtml#c10-bib-0035)：

