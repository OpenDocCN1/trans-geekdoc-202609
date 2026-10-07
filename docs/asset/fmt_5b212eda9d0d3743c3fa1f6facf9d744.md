
$$
\begin{aligned}
& {{\int_{\mathcal{B}\cap \mathcal{M}}}W}(\mathbf{b},\mu)\, d\mathbf{b}d\mu = 1,\quad{\int_{\mathcal{E}_{n}}E_{n}}(\eta\lbrack n\rbrack)\, d\,\eta\lbrack n\rbrack = 1,}
\\
& {\text{\quad\quad}{\int_{\mathcal{B}\cap \mathcal{M}}}\,}W(\mathbf{b},\mu)\left\lbrack {T_{(n - p)}^{(r)}\mathbf{b} + \mu\lbrack n\rbrack} \right\rbrack\, d\,\mathbf{b}\, d\,\mu\lbrack n\rbrack +}
\\
& {\text{\quad\quad}\quad + {\int_{\mathcal{E}_{n}}E_{n}}(\eta\lbrack n\rbrack)\eta\lbrack n\rbrack\, d\,\eta\lbrack n\rbrack = T^{(r)}\lbrack n\rbrack,}
\\
& {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}n = \overline{p,24}.}
\\
\end{aligned}
$$

(11.72)

表达式 (11.4.5.2, 11.4.5.2) 包含了向量 *μ* = {*μ*\[*p*\],…,*μ*\[24\]}。

令 *ϑ* = {*ϑ*[*p*],…,*ϑ*[7 + *p*]} 为该问题的拉格朗日乘子。该线性模型具有随机参数和输入上的辅助随机序列。因此该问题的解，表示最优 PDF，可写为

$$
\begin{aligned}
{W^{*}\mathbf{b},\mu,\vartheta) =} & {L^{*}\mathbf{b},\vartheta)\, M^{*}\mu,\vartheta),\quad M^{*}\mu,\vartheta) = {\prod\limits_{n = p}^{24}M_{n}^{*}\mu\lbrack n\rbrack,\vartheta_{n})}
\\
& {\quad L^{*}\mathbf{b},\vartheta) = \frac{\exp\left( {- \left\langle \vartheta,T_{(n - p)}^{(r)}\,\mathbf{b} \right\rangle} \right)}{\mathcal{L}\vartheta)},}
\\
& {\quad\mathcal{L}\vartheta) = {\int_{\mathcal{B}}\exp}\left( {- \left\langle \vartheta,T_{(n - p)}^{(r)}\,\mathbf{b} \right\rangle} \right)\, d\,\mathbf{b},}
\\
& {\quad M_{n}^{*}\mu\lbrack n\rbrack,\,\vartheta_{n}) = \mathbb{M}_{n}^{- 1}\vartheta_{n})\exp\left( {- \vartheta_{n}\mu\lbrack n\rbrack} \right),}
\\
& {\quad\mathbb{M}_{n}\vartheta_{n}) = {\int_{\mathcal{M}_{n}}}\,}\exp\left( {- \vartheta_{n}\mu\lbrack n\rbrack} \right)d\,\mu\lbrack n\rbrack,}
\\
& {\quad E_{n}^{*}\eta\lbrack n\rbrack,\vartheta_{n}) = \mathbb{E}_{n}^{- 1}\vartheta_{n})\exp\left( {- \eta\lbrack n\rbrack\,\vartheta_{n}} \right),}
\\
& {\quad\mathbb{E}_{n}\vartheta_{n}) = {\int_{\mathcal{E}_{n}}\exp}\left( {- \eta\lbrack n\rbrack\,\vartheta_{n}} \right)d\,\eta\lbrack n\rbrack,}
\\
\end{aligned}
$$

(11.73)

其中拉格朗日乘子 *ϑ* 满足方程组

$$
\begin{aligned}
& {\text{\quad\quad}\mathcal{L}^{- 1}\vartheta)\,{{\int_{\mathcal{B}}}\,}\exp\left( {- \left\langle \vartheta,T_{(n - p)}^{(r)}\,\mathbf{b} \right\rangle} \right)T_{(n - p)}^{(r)}\,\mathbf{b}\, d\mathbf{b} +}
\\
& {\quad\text{\quad\quad} + \mathbb{M}_{n}^{- 1}\vartheta_{n}){{\int_{\mathcal{M}_{n}}M_{n}^{*}\mu\lbrack n\rbrack,\,\vartheta_{n})\,}\mu\lbrack n\rbrack d\mu\lbrack n\rbrack +}
\\
& {+ \mathbb{E}_{n}^{- 1}\vartheta_{n}){{\int_{\mathcal{E}_{n}}E_{n}^{*}\eta\lbrack n\rbrack,\vartheta_{n})\,}\eta\lbrack n\rbrack d\eta\lbrack n\rbrack = T^{(r)}\lbrack n\rbrack,}
\\
& {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}n = \overline{p,24}.}
\\
\end{aligned}
$$

(11.74)

对于 `LDRR-P`，`RML` 算法的形式类似于 (11.4.5.2, 11.4.5.2)：

$$
\begin{aligned}
{F^{*}\mathbf{c},\zeta,\lambda) =} & {V^{*}\mathbf{c},\lambda)\, Z^{*}\zeta,\lambda),\quad Z^{*}\zeta,\lambda) = {\prod\limits_{n = p}^{24}Z_{n}^{*}\zeta\lbrack n\rbrack,\lambda_{n})}
\\
& {V^{*}\mathbf{c},\lambda) = \frac{\exp\left( {- \left\langle \lambda,R_{(n - p)}^{(r)}\,\mathbf{c} \right\rangle} \right)}{\mathcal{V}\lambda)},}
\\
& {\mathcal{V}\lambda) = {\int_{\mathcal{C}}\exp}\left( {- \left\langle \lambda,R_{(n - p)}^{(r)}\,\mathbf{c} \right\rangle} \right)\, d\,\mathbf{c},}
\\
& {Z_{n}^{*}\zeta\lbrack n\rbrack,\lambda_{n}) = {\mathbb{Z}}_{n}^{- 1}\lambda_{n})\exp\left( {- \lambda_{n}\,\zeta\lbrack n\rbrack} \right),}
\\
& {{\mathbb{Z}}_{n}\lambda_{n}) = {\int_{\mathcal{Z}_{n}}}\,}\exp\left( {- \lambda_{n}\,\zeta\lbrack n\rbrack} \right)d\,\zeta\lbrack n\rbrack,}
\\
& {G_{n}^{*}\chi\lbrack n\rbrack,\lambda_{n}) = \mathbb{G}_{n}^{- 1}\lambda)\exp\left( {- \chi\lbrack n\rbrack\lambda_{n}} \right),}
\\
\end{aligned}
$$

(11.75)

$$
\begin{aligned}
& {{\mathbb{G}}_{n}\lambda_{n}) = {\int_{\mathcal{G}_{n}}\exp}\left( {- \chi\lbrack n\rbrack\,\lambda_{n}} \right)d\,\chi\lbrack n\rbrack,}
\\
\end{aligned}
$$

(11.76)

其中拉格朗日乘子 *λ* = {*λ*[*p*],…,*λ*[24]} 由方程组确定

$$
\begin{array}{r}
{\text{\quad\quad}\mathcal{V}^{- 1}\lambda)\,{{\int_{\mathcal{C}}}\,}\exp\left( {- \left\langle \lambda,R_{(n - p)}^{(r)}\,\mathbf{c} \right\rangle} \right)\, R_{(n - p)}^{(r)}\,\mathbf{c}\, d\mathbf{c} +}
\\
{\text{\quad\quad}\text{\quad\quad}{{\mathbb{Z}}}_{n}^{- 1}\lambda_{n}){{\int_{\mathcal{Z}_{n}}Z_{n}^{*}\zeta\lbrack n\rbrack,\lambda_{n})\,}\zeta\lbrack n\rbrack d\zeta\lbrack n\rbrack +}
\\
{+ \mathbb{G}_{n}^{- 1}\lambda_{n}){{\int_{\mathcal{G}_{n}}G_{n}^{*}\chi\lbrack n\rbrack,\lambda_{n})\,}\chi\lbrack n\rbrack\, d\chi\lbrack n\rbrack = R^{(r)}\lbrack n\rbrack,}
\\
{\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}n = \overline{p,24}.}
\\
\end{array}
$$

(11.77)

根据 (11.4.5.2, 11.4.5.2, 11.4.5.2, 11.4.5.2)，熵最优 PDF 属于由相应拉格朗日乘子参数化的指数类，这些乘子由平衡方程 (11.4.5.2, 11.4.5.2, 11.4.5.2) 给出。

算法 2 和 3 旨在计算平衡方程的残差并恢复熵最优 PDF。

![Algorithm 2 Residual for balance equations.](img/comp11_2.jpg)

Algorithm 2 Residual for balance equations.

![Algorithm 3 Restoration of entropy-optimal PDFs.](img/comp11_3.jpg)

Algorithm 3 Restoration of entropy-optimal PDFs.

### 11.4.6 Testing procedure, data and accuracy estimates

测试程序应用于以下训练模型的组合：

* `LDRR-LA`，测试集合 ℭ[*t**s*]\[*n*\]、 𝔇[*t**s*]\[*n*\]、 ℑ[*t**s*]\[*n*\]；

* `LDRR-T`，使用测试集合中的 `T`^((*r*))\[*n*\]；

* `LDRR-P`，使用测试集合中的 `R`^((*r*))\[*n*\]。

测试 `LDRR-LA` 时，使用测试集合的所有分量，模型通过采样其参数和测量噪声的熵最优 PDF 生成输出集合（湖泊面积的值）。

![Algorithm 4 Sampling algorithm for PDFs.](img/comp11_4.jpg)

Algorithm 4 Sampling algorithm for PDFs.

测试训练好的 `LDRR-T` 和 `LDRR-P` 模型时，仅使用测试集合中的温度和降水数据。这些模型通过采样其参数和输入序列的熵最优 PDF 生成相应输出的集合，用于温度和降水。

测试的准确性由以下指标表征：

* —绝对均方误差（以自然单位计）

$$
\begin{array}{r}
{AbsErr = \Delta = \sqrt{\frac{1}{10}{\sum\limits_{n = 25}^{34}\left( {\bullet^{(r)}\lbrack n\rbrack - \hat{\bullet}\lbrack n\rbrack} \right)^{2}}};}
\\
\end{array}
$$

(11.78)

* —相对均方误差

$$
\begin{aligned}
{RelErr =} & {\frac{\Delta}{\Delta_{1} + \Delta_{2}},}
\\
{\Delta_{1} = \sqrt{\frac{1}{10}{\sum\limits_{n = 25}^{34}{( \bullet^{(r)}\lbrack n\rbrack)}^{2}}},} & {\Delta_{2} = \sqrt{\frac{1}{10}{\sum\limits_{n = 25}^{34}{(\hat{\bullet}\lbrack n\rbrack)}^{2}}}.}
\\
\end{aligned}
$$

(11.79)

### 11.4.7 热喀斯特湖面积演化的随机化预测

热喀斯特湖面积的时间演化在超过可用面积和气候参数数据的时间间隔的时间间隔上进行预测。在所考虑的情况下，每个预测间隔的开始都指 2008 年。我们考虑以下三个时间间隔：

* —短期，2008 年至 2013 年之间（$n = \overline{35,40}$）；

* —中期，2008 年至 2018 年之间（$n = \overline{35,45}$）；

* —长期，2008 年至 2023 年之间（$n = \overline{35,50}$）。

热喀斯特湖面积的时间演化使用训练好的随机化模型的组合（见 Fig. 11.13）在上述指定的预测间隔上进行预测。该组合中的模型以其参数的熵最优 PDF、辅助随机序列和测量噪声为特征。测量噪声的 PDF 在训练间隔上的时间瞬间是不同的：它们取决于时间瞬间和相应的拉格朗日乘子。例如，*LDRR-LA* 的测量噪声具有 PDF $Q_{n}^{\*}(\xi\lbrack n\rbrack,\theta_{n}),\, n = \overline{0,34}.$ 对于预测过程，我们应用对拉格朗日乘子取平均的 PDF。

好吧，复合模型的块由以下 PDF 表征：

* 对于 *LDRR-LA*，$P^{*}(a)$ 和 $Q^{*}(\xi,\overline{\theta}),\,\,\overline{\theta} = \frac{1}{34 - p}{\sum\limits_{n = p}^{34}\theta_{n}}$；

* 对于 *LDRR-T*，$L^{*}(b)$，$M^{*}(\mu,\overline{\vartheta})$，和 $E^{*}(\eta,\overline{\vartheta}),\,\overline{\vartheta} = \frac{1}{34 - p}{\sum\limits_{n = p}^{34}\vartheta_{n}}$；

* 对于 *LDRR-P*，$V^{*}(c)$，$Z^{*}(\zeta,\overline{\lambda})$，和 $G^{*}(\chi,\overline{\lambda}),\,\overline{\lambda} = \frac{1}{34 - p}{\sum\limits_{n = p}^{34}\lambda_{n}}.$

这些 PDF 在相应的预测间隔上采样，并且通过蒙特卡洛模拟生成轨迹（湖泊面积变化）的预测集合。

### 11.4.8 西西伯利亚热喀斯特湖面积时间演化训练、测试和预测的结果

#### 11.4.8.1 随机化训练（1973–1997）
