
表 8.2 各种算法在 IEEE 14 节点、57 节点、118 节点和 300 节点系统 [66] 上实现残差 log((1/m) \(\sum_{i=1}^m \mathbb{E}[\|y_i^t - y^*\|]\)) = -3 所需的迭代次数（缩写为 ‘N’）和收敛时间（秒，缩写为 ‘S’）。

| 节点 | 算法 1 S | 算法 1 N | 文献 [24] 方法 S | 文献 [24] 方法 N | 文献 [42] 方法 S | 文献 [42] 方法 N |
|---|---|---|---|---|---|---|
| 14 | 0.0295 | 375 | 0.0051 | 162 | 0.0031 | 131 |
| 57 | 0.0649 | 869 | 0.0065 | 212 | 0.0036 | 142 |
| 118 | 1.0844 | 2206 | 0.0425 | 1060 | 0.0056 | 765 |
| 300 | 2.1351 | 3510 | 0.0754 | 1440 | 0.0068 | 954 |

所提出的算法。在两个示例中，我们假设每个发电机 \(i\) 的初始功率生成 \(p_i\) 为 0，这间接导致波动增加。在实际场景中，如果算法的初始条件不设为 0 而是接近最优解，则波动将显著减小。其次，在实际场景中，智能电网在投入运行前必须进行必要的调试（算法迭代）。此调试过程会导致功率生成波动，进而导致发电成本波动。

## 8.6 结论

本章提出了一种用于在不平衡有向网络上求解 EDP 的新型隐私保护去中心化随机睡眠算法。所提算法将条件噪声纳入状态交换，有效保护敏感信息。此外，该算法将随机睡眠策略集成到带梯度重缩的去中心化不精确梯度方法中，提高了在不平衡有向网络上的计算效率。理论分析表明，所提算法可以实现 EDP 的最优解。此外，该算法的误差界和隐私特性已在理论上得到研究。已进行多个仿真示例来验证算法的性能。未来研究可以探索将基于异步广播的通信机制纳入算法。此外，研究更高效的计算智能算法以求解智能电网中的 EDP 是未来研究的一个有前途的方向。

## 附录 8.A 引理 8.4 的证明

考虑任意 \(i \in \mathcal{V}\)。如果 \(h_i^t = 1\)，则算法 1 意味着

\[
y_i^{t+1} = \sum_{j=1}^m b_{ij} y_j^t + \varepsilon_i^t - \gamma_i^t \frac{p_i^t - d_i}{[z_i^t]_i}.
\]

同样，如果对 \(i \in \mathcal{V}\) 有 \(h_i^t = 0\)，则可得

\[
y_i^{t+1} = \sum_{j=1}^m b_{ij} y_j^t + \varepsilon_i^t.
\] (8.A.2)

通过应用 (8.A.1) 和 (8.A.2)，并对 \(\mathcal{F}^t\) 取条件期望，我们得到对于任意 \(i \in \mathcal{V}\)、\(i \in \mathcal{V}\)，

\[
\mathbb{E} [y_i^{t+1} | \mathcal{F}^t] = \sum_{j=1}^m b_{ij} y_j^t + \varepsilon_i^t - \eta_i \gamma_i^t \frac{p_i^t - d_i}{[z_i^t]_i},
\] (8.A.3)

其中 \(\eta_i\) 表示 \(h_i^t = 1\) 的概率。基于 \(\varepsilon_i^t\) 和 \(\gamma_i^t\) 的定义，对于每个 \(i \in \mathcal{V}\)，有 \(\lim_{t \to \infty} \varepsilon_i^t = 0\) 且 \(\lim_{t \to \infty} \gamma_i^t = 0\)。考虑到对于所有 \(i \in \mathcal{V}\) 满足 \(0 \le \eta_i \le 1\)、\(|p_i^t - d_i| \le C\) 以及 \(\kappa^{-1} \le [z_i^t]_i \le 1\)，我们得出

\[
\lim_{t \to \infty} |\varepsilon_i^t - \eta_i \gamma_i^t \frac{p_i^t - d_i}{[z_i^t]_i}| \le \lim_{t \to \infty} (\varepsilon_i^t + \eta_i \kappa C \gamma_i^t) = 0.
\] (8.A.4)

因此，通过应用文献 [47] 中的引理 4，我们得到对于所有 \(i \in \mathcal{V}\)，\(\lim_{t \to \infty} |y_i^t - \bar{y}^t| = 0\) 几乎必然成立，证明完成。

## 附录 8.B 引理 8.5 的证明

对于任意 \(i \in \mathcal{V}\)，如果 \(h_i^t = 1\)，则对于任意 \(v \in \mathbb{R}\)，有

\[
|y_i^{t+1} - v|^2
= |v_i^t + \varepsilon_i^t - v|^2 + |\gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i}|^2 + 2(v_i^t + \varepsilon_i^t - v)\gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i}
\le \sum_{j=1}^m b_{ij} |y_j - v|^2 + 2\varepsilon_i^t (v_i^t - v) + |\varepsilon_i^t|^2 + |\gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i}|^2
+ 2\gamma_i^t (v_i^t - v) \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i} + 2\varepsilon_i^t \gamma_i^t \frac{\nabla Q_i(v_i^t)}{[z_i^t]_i},
\] (8.B.1)

该不等式源于 \(B\) 的行随机性以及对凸函数 \(|\cdot|^2\) 应用詹森不等式。我们可以进一步推断，对于所有 \(t \ge \hat{t}\)，

\[
2\gamma_i^t \nabla Q_i(v_i^t)(v_i^t - v)
= 2(\gamma_i^t - \frac{1}{t \eta_i})\nabla Q_i(v_i^t)(v_i^t - v) + \frac{2}{t \eta_i} \nabla Q_i(v_i^t)(v_i^t - v)
\le \phi^t |\nabla Q_i(v_i^t)|^2 + \phi^t |v_i^t - v|^2 + \frac{2}{t\eta_i}(Q_i(v_i^t) - Q_i(v))
\le \phi^t |\nabla Q_i(v_i^t)|^2 + \phi^t \sum_{j=1}^m b_{ij} |y_j^t - v|^2 + \frac{2C}{t\eta_i} \sum_{j=1}^m b_{ij} |y_j^t - \bar{y}^t|^2
+ \frac{2}{t\eta_i} (Q_i(\bar{y}^t) - Q_i(v)),
\] (8.B.2)

第一个和第二个不等式分别源于 \(-Q_i\) 的凸性以及对于所有 \(i \in \mathcal{V}\) 的 \(|\nabla Q_i| \le C\) 界。利用 (8.B.1)、(8.B.2)，结合对于所有 \(i \in \mathcal{V}\) 的 \(|\nabla Q_i| \le C\) 和 \(\kappa^{-1} \le [\xi_i^t]_i \le 1\) 条件，我们推导出对于所有 \(t \ge \hat{t}\)，

\[
|y_i^{t+1} - v|^2
\le (1 + \phi^t \kappa) \sum_{j=1}^m b_{ij} |y_j^t - v|^2 + \frac{2}{t\eta_i[z_i^t]_i} (Q_i(\bar{y}^t) - Q_i(v))
+ C^2 \kappa^2 |\gamma_i^t|^2 + 2\varepsilon_i^t \gamma_i^t C \kappa + 2|\varepsilon_i^t| |v_i^t - v| + |\varepsilon_i^t|^2
+ \phi^t \kappa C^2 + \frac{2C\kappa}{t\eta_i} \sum_{j=1}^m b_{ij} |y_j^t - \bar{y}^t|^2.
\] (8.B.3)

同样，如果对 \(i \in \mathcal{V}\) 有 \(h_i^t = 0\)，则可得

\[
|y_i^{t+1} - v|^2
\le (1 + \phi^t \kappa) \sum_{j=1}^m b_{ij} |y_j^t - v|^2 + |\varepsilon_i^t|^2 + 2|\varepsilon_i^t| |v_i^t - v|.
\] (8.B.4)

考虑两种情况 (8.B.3) 和 (8.B.4)，并对 \(\mathcal{F}^t\) 取条件期望，我们可以得出对于所有 \(i \in \mathcal{V}\) 和所有 \(t \ge \hat{t}\)，

\[
\mathbb{E} \left[ |y_i^{t+1} - v|^2 | \mathcal{F}^t \right]
\le (1 + \phi^t \kappa) \sum_{j=1}^m b_{ij} |y_j^t - v|^2 + \frac{2}{t[z_i^t]_i} (Q_i(\bar{y}^t) - Q_i(v))
+ C^2 \kappa^2 \eta_i |\gamma_i^t|^2 + 2C\kappa \eta_i \varepsilon_i^t \gamma_i^t + 2|\varepsilon_i^t| |v_i^t - v| + |\varepsilon_i^t|^2
+ \phi^t \kappa^2 \eta_i + \frac{2C\kappa}{t} \sum_{j=1}^m b_{ij} |y_j^t - \bar{y}^t|^2.
\] (8.B.5)

将两边乘以 \(c_i\) 并对 \(i=1\) 到 \(m\) 求和，我们得到对于所有 \(t \ge \hat{t}\)，

\[
\sum_{i=1}^m c_i \mathbb{E} \left[ |y_i^{t+1} - v|^2 | \mathcal{F}^t \right]
\le (1+\phi^t\kappa)\sum_{i=1}^m c_i|y_i^t-v|^2+\frac{2}{t}\sum_{i=1}^m\frac{c_i}{|z_i^t|_i}(Q_i(\bar{y}^t)-Q_i(v))
+C^2\kappa^2\hat{\eta}\sum_{i=1}^m|\gamma_i^t|^2+2C\kappa\hat{\eta}\sum_{i=1}^m\varepsilon_i^t\gamma_i^t+2\sum_{i=1}^m|\varepsilon_i^t||v_i^t-v|
+\sum_{i=1}^m|\varepsilon_i^t|^2+\phi^t\kappa C^2\hat{\eta}+\frac{2C\kappa}{t}\sum_{i=1}^m|y_i^t-\bar{y}|^2.
\]

利用 \(c^T B = c^T\) 以及对于 \(i \in \mathcal{V}\) 的 \(0 < c_i < 1\) 性质，我们还得到对于所有 \(t \ge \hat{t}\)，

\[
\frac{2}{t}\sum_{i=1}^m\frac{c_i}{|z_i^t|_i}(Q_i(\bar{y}^t)-Q_i(v))
\le\frac{2}{t}\sum_{i=1}^m(Q_i(\bar{y}^t)-Q_i(v))+\frac{2}{t}\sum_{i=1}^m|\frac{[z_i^t]_i-c_i}{[z_i^t]_i}||Q_i(\bar{y}^t)-Q_i(v)|
\le\frac{2}{t}\sum_{i=1}^m(Q_i(\bar{y}^t)-Q_i(v))+\frac{2}{t}m\kappa C W(\lambda^t)|\bar{y}^t-v|.
\]

因此，结合 (8.B.6) 和 (8.B.7) 使我们能够得出引理 8.5。证明完毕。\(\square\)

## 参考文献

- [1] Y. Liu, P. Zhou, L. Yang, Y. Wu, Z. Xu, K. Liu, X. Wang, 微电网能量调度中基于上下文的隐私保护电动汽车调度：一种在线学习方法, IEEE 计算智能新兴主题交易 6 (3) (2022 年 6 月) 462–478.
- [2] C. Li, X. Yu, T. Huang, X. He, 资源分配网络上的分布式最优一致及其在动态经济调度中的应用, IEEE 神经网络与学习系统交易 29 (6) (2018 年 6 月) 2407–2418.
- [3] B. Rajasekhar, W. Tushar, C. Lork, Y. Zhou, C. Yuen, N.M. Pindoriya, K.L. Wood, 空调能源管理的计算智能技术综述, IEEE 计算智能新兴主题交易 4 (4) (2020 年 8 月) 555–570.
- [4] L.-N. Liu, G.-H. Yang, 时变有向通信图上微电网分布式最优经济环境调度, IEEE 网络科学与工程交易 8 (2) (2021 年 4 月–6 月) 1913–1924.
- [5] K. Utkarsh, A. Trivedi, D. Srinivasan, T. Reindl, 基于一致性的智能配电网实时最优控制分布式计算智能技术, IEEE 计算智能新兴主题交易 1 (1) (2017 年 2 月) 51–60.
