
在最近的一项工作 [\[69\]](#c10.xhtml#c10-bib-0069) 中，已知源（如某些正常脑节律）的位置被用作先验，以便利用约束 BSS 找到异常或其他脑源信号的位置。BSS 算法的代价函数受此信息约束，且已知源被迭代计算。

考虑 $\tilde{\mathbf{A}} = [\mathbf{A}_k \vdots \mathbf{A}_{uk}]$ 为混合矩阵，包含关于已知源 $\mathbf{A}_k$ 和未知源 $\mathbf{A}_{uk}$ 的几何信息。$\mathbf{A}_k$ 是 $n_e \times k$ 矩阵，$\mathbf{A}_{uk}$ 是 $n_e \times (m - k)$ 矩阵。给定 $\mathbf{A}_k$，$\mathbf{A}_{uk}$ 可按如下方式估计：

(10.46)
```
\mathbf{A}_{uk_{n+1}} = \mathbf{A}_{uk_n} - \xi \nabla_{\mathbf{A}_{uk}} J_c
```

其中

(10.47)
```
\nabla_{\mathbf{A}_{uk}} J_c = 2 \left( [\mathbf{A}_k \vdots \mathbf{A}_{uk}] - \mathbf{R}_{n+1} \mathbf{W}_{n+1}^{-1} \right)
```

(10.48)
```
\mathbf{R}_{n+1} = \mathbf{R}_n - \gamma \nabla_{\mathbf{R}} (J_c)
```

以及

(10.49)
```
J_c = \left\| \tilde{\mathbf{A}}_n - \mathbf{R}_{n+1} \mathbf{W}_{n+1}^{-1} \right\|_F^2
```

(10.50)
```
\nabla_{\mathbf{R}} (J_c) = 2 \left( \mathbf{W}_{n+1}^{-1} \mathbf{A}_{k_n} + \mathbf{R}_n \mathbf{W}_{n+1}^{-1} (\mathbf{W}_{n+1}^{-1})^T - \mathbf{W}_{n+1}^{-1} \mathbf{A}_{u_{k_n}} \right)
```

其中

(10.51)
```
\mathbf{W}_{n+1} = \mathbf{W}_n - \mu \nabla_{\mathbf{W}} J
```

这里 $J(\mathbf{W}) = J_m(\mathbf{W}) + \lambda J_c(\mathbf{W})$；$J_m$ 为主要 BSS 代价函数。参数 $\mu$、$\gamma$ 和 $\zeta$ 可经验设定或迭代调整；当收敛误差减小时它们也随之减小。回顾 $\mathbf{A}_k$ 是已知且保持常数的。

### 10.5.2 用于 P3a 和 P3b 定位的约束最小二乘法

通常，关于源形状的某些信息有助于其定位。ERP 在 EEG 信号中表现为正负波峰。此类波峰可用高斯或拉普拉斯函数近似。可采用一种基于 LS 的方法 [\[70\]](#c10.xhtml#c10-bib-0070)。利用该方法，可估计头皮图（前向矩阵 $\mathbf{H}$ 的列向量）。考虑：

(10.52)
```
\mathbf{R} = \mathbf{X} \mathbf{Y}^T = \mathbf{H} \mathbf{S} \mathbf{Y}^T
```

其中 $\mathbf{Y}$ 为行等于 $\mathbf{y}[c]$ 的矩阵，且 $\mathbf{Y} = \mathbf{D} \mathbf{S}$，$\mathbf{D}$ 为对角缩放矩阵：

(10.53)
```
\mathbf{D} = \begin{bmatrix}
d_1 & 0 & \dots & 0 \\
0 & d_2 & \dots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \dots & d_m
\end{bmatrix}
```

右乘 $\mathbf{R}$ 以 $\mathbf{R}_y^{-1} = \mathbf{Y} \mathbf{Y}^{-1}$：
