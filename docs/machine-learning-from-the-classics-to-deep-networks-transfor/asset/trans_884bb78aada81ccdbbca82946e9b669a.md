

$$
\Sigma_{u} = \begin{bmatrix} 
1.25\sigma_{s}^{2} + \sigma_{\eta}^{2} & 0.5\sigma_{s}^{2} & 0 \\ 
0.5\sigma_{s}^{2} & 1.25\sigma_{s}^{2} + \sigma_{\eta}^{2} & 0.5\sigma_{s}^{2} \\ 
0 & 0.5\sigma_{s}^{2} & 1.25\sigma_{s}^{2} + \sigma_{\eta}^{2} 
\end{bmatrix},\quad \mathbf{p} = \begin{bmatrix} 
\sigma_{s}^{2} \\ 
0.5\sigma_{s}^{2} \\ 
0 
\end{bmatrix}.
$$

![Equation](images/B978044329238500010X/si253.png)

求解正规方程，

$$\Sigma_{u}\mathbf{w}^{*} = \mathbf{p},$$

![Equation](images/B978044329238500010X/si254.png)

当 $\sigma_{s}^{2} = 1$ 和 $\sigma_{\eta}^{2} = 0.01$ 时，结果为

$$\mathbf{w}^{*} = [0.7462,\ 0.1195,\ -0.0474]^{T}.$$

![Equation](images/B978044329238500010X/si257.png)

[图 4.15](#Chp004_119-175_B978044329238500010X.xhtml#f0080)C 显示了均衡器恢复的序列（$\mathbf{w}^{*T}\mathbf{u}_{n}$），经过适当的阈值处理后。它与发送的序列完全相同：无错误。[图 4.15](#Chp004_119-175_B978044329238500010X.xhtml#f0080)D 显示了噪声方差增加到 $\sigma_{\eta}^{2} = 1$ 时恢复的序列。相应的 MSE 最优均衡器等于

$$\mathbf{w}^{*} = [0.4132,\ 0.1369,\ -0.0304]^{T}.$$

![Equation](images/B978044329238500010X/si260.png)

这一次，均衡器重构的序列相对于发送序列存在错误（灰线）。

获得 $\Sigma_{u}$ 的一种略有不同的替代公式，而不是单独计算其每个元素，如下所示。验证时刻 $n$ 送入均衡器（三抽头）的输入向量由下式给出

