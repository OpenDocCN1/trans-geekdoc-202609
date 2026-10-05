

其中容许集 `Ω` 由归一化条件 (5.21) 和经验平衡约束 (5.24) 给出。

### 5.2.2 RPM-Rel 模型的估计算法

在 RPM-Rel 模型中，随机参数包括非负相对参数 `u` 和测量噪声 `{ \overline{\eta}^{(1)},\ldots,\overline{\eta}^{(s)} }`。根据 (5.13)，RPM-Rel 模型在时刻 *t*[*j*] 的可观测输出由

$$
\begin{aligned} \left. \mathbf{f}(t_{j}) = \mathbf{z}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack \right. & {+ \overline{\xi}_{-}^{(j)} + K_{j}\overline{\eta}^{(j)}\lbrack G_{j}(\overline{\eta}^{(j)})\rbrack,} \\ \left. \mathbf{z}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack = \mathcal{D}\lbrack\mathbf{x}(t_{j},\tau), \right. & {\mathbf{a}^{-} + A\,\mathbf{u},\, W(\mathbf{u});(t_{j},\tau) \in \mathcal{T}\rbrack,} \\ & {j = \overline{1,s}.} \\ \end{aligned}
$$

(5.26)

描述。

这里，`𝒟` 表示维数为 (*m* × *n*) 的矩阵泛函，它表征了模型输出 `z(t[j])` 与由输入向量 `x(t[j], τ[1])`，…，`x(t[j], τ[(j − 1)])` 组成的数组之间存在的关系。RPM-Rel 模型输出 (5.2.2) 依赖于具有 PDF `W(u)` 的随机相对参数 `u`，也依赖于具有 PDF `G_{j}(\overline{\eta}^{(j)})` 的随机相对噪声向量 `\overline{\eta}^{(j)}`；参见 (5.2.2)。关于这些 PDF 的可用先验信息（如有）以先验 PDF `W[0](u)` 和 `G_{j}^{0}(\overline{\eta}^{(j)})` 的形式表示。根据假设，PDF 属于所有连续可微函数类 `ℂ¹`。

*对于 RPM-Rel 模型 (5.1)，其参数和测量噪声的 PDF 的熵鲁棒估计问题* 制定如下：

* 最大化广义玻尔兹曼信息熵泛函

$$
\begin{aligned} & {\quad\mathcal{H}\lbrack W(\mathbf{u}),\overline{G}(\eta)\rbrack = - {\int_{\mathcal{U}}W}(\mathbf{u})\,\ln\frac{W(\mathbf{u})}{W_{0}(\mathbf{u})}\, d\,\mathbf{u} -} \\ & \left. - {\sum\limits_{j = 1}^{s}\,}{\int_{\mathcal{E}_{j}}G_{j}}(\overline{\eta}^{(j)})\,\ln\frac{G_{j}(\overline{\eta}^{(j)})}{G_{j}^{0}(\overline{\eta}^{(j)})}d\overline{\eta}^{(j)}\Rightarrow\min_{W,\overline{G}} \right. \\ \end{aligned}
$$

(5.27)

* 约束条件为：

  * –PDF 的归一化条件，即

$$
\begin{array}{r} {{\int_{\mathcal{U}}W}(\mathbf{u})d\mathbf{u} = 1,\text{\quad\quad}{\int_{\mathcal{E}_{j}}G_{j}}(\overline{\eta}^{(j)})\, d\overline{\eta}^{(j)} = 1,\quad j = \overline{1,s},} \\ \end{array}
$$

(5.28)

和

  * –RPM-Rel 模型 (5.15) 输出的 *k*-均值与物体输出测量值之间的平衡约束，即

$$
\begin{array}{r} {\mathbf{n}^{(k)}\lbrack W(\mathbf{u}),G_{j}(\overline{\eta}^{(j)}),j\rbrack = \mathbf{y}(t_{j}),\text{\quad\quad}j = \overline{1,s}.} \\ \end{array}
$$

(5.29)

由于 (5.15)，这些等式约束中的向量 `\mathbf{n}^{(k)}\lbrack W(\mathbf{u}),G_{j}(\overline{\eta}^{(j)}),j\rbrack` 的分量为

$$
\begin{aligned} {n_{i}^{(k)}\lbrack j\rbrack} & {\left[\int_{\mathcal{U}}W}(\mathbf{u})z_{i}^{k}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack\, d\mathbf{u} \right]^{1/k} +} \\ & {\left[\int_{\mathcal{E}_{j}}\,}{G_{j}(\overline{\eta}^{(j)})\,{\lbrack\eta_{i}^{(j)}\rbrack}^{k}\, d\eta_{i}^{(j)}} \right]^{1/k},} \\ & {\text{\quad\quad}\quad i = \overline{1,m},\, j = \overline{1,s}.} \\ \end{aligned}
$$

(5.30)

考虑平衡约束涉及 RPM-Rel 模型输出的 1-均值的情况：

$$
\begin{aligned} {\left[\int_{\mathcal{U}}W}(\mathbf{u})\mathbf{z}\lbrack t_{j}\, \middle| \, W(\mathbf{u})\rbrack\, d\mathbf{u} \right] +} & {\left[\int_{\mathcal{E}_{j}}\,}{G_{j}(\overline{\eta}^{(j)})\,{\overline{\eta}}^{(j)}\, d\overline{\eta}^{(j)}} \right] = \mathbf{y}(t_{j}),} \\ & {j = \overline{1,s}.} \\ \end{aligned}
$$

(5.31)

与上述优化问题一样，泛函约束从类 `ℂ¹` 中提取所有容许函数子集 `\Psi\lbrack W(\mathbf{u}),G(\overline{\eta})\rbrack`，其中 `G(\overline{\eta}) = \{ G_{1}(\overline{\eta}^{(1)}),\ldots,G_{s}(\overline{\eta}^{(s)}) \}`。问题 (5.27-5.31) 也是 Lyapunov 型。

*对于 RPM-Rel 模型，熵鲁棒 RML 算法* 的形式为

$$
\begin{array}{r} {\left[\,W(\mathbf{u}),\overline{G}(\overline{\eta}) \right]^{*} = \arg\max_{\lbrack W(\mathbf{u}),\overline{G}(\overline{\eta})\rbrack}\left\{ \mathcal{H},\, \middle| \,\lbrack W(\mathbf{u}),G(\overline{\eta})\rbrack \in \Psi \right\},} \\ \end{array}
$$

(5.32)

其中容许集 `Ψ` 由归一化条件 (5.28) 和经验平衡约束 (5.31) 给出。

### 5.2.3 具有输入和输出测量误差的 RPM-F 模型的估计算法

前几节研究了仅在输出中出现的测量误差情况。然而，在许多应用中，输入数据集合也包含误差。因此，一般的 RML 过程应相应地修改。

如果输入数据中存在误差，RPM-F 模型的观测输出采用以下形式：

$$
\begin{array}{r} \left. \mathbf{v}(t_{j}) = \mathbf{y}\lbrack t_{j}\, \middle| \, F(\mathbf{a},\overline{\mu}^{(j)})\rbrack + \overline{\xi}\lbrack Q_{j}(\overline{\xi}^{(j)})\rbrack, \right. \\ \left. \mathbf{y}\lbrack t_{j}\, \middle| \, F(\mathbf{a},\overline{\mu}^{(t_{j})})\rbrack = \mathcal{B}\lbrack\mathbf{x}(t_{j},\tau) + \overline{\mu}^{(t_{j})}\rbrack. \right. \\ \end{array}
$$

(5.33)

这里 `\overline{\mu}^{(j)}` 表示在时刻 *t*[*j*] 的输入噪声向量，它们是区间型：

$$
\begin{array}{r} {{\overline{\mu}}^{(j)} \in \mathcal{M} = \lbrack\mu^{-},\mu^{+}\rbrack\quad\text{for~all}\, t_{j}.} \\ \end{array}
$$

(5.34)

由 RPM-F 模型方程 (5.33) 可知，随机元素是参数 `a` 和输入噪声 `\overline{\mu}.` 它们的概率特性由联合概率密度函数 `F(a,\overline{\mu}^{(t_{j})})` 表征。如果对该函数存在某些信息，则以先验 PDF `F_{0}(a,\overline{\mu}^{(t_{j})})` 的形式表示。

*对于 RPM-F 模型 (5.33)，其参数以及输入和输出测量噪声的 PDF 的熵鲁棒估计问题* 制定如下：

* 最大化广义玻尔兹曼信息熵泛函

$$
\begin{aligned} {\mathcal{H}\lbrack F(\mathbf{a},\overline{\mu}),\overline{Q}(\overline{\xi})\rbrack} & {= - \int_{\mathcal{R}}F(\mathbf{a},\overline{\mu})\,\ln\frac{F(\mathbf{a},\overline{\mu})}{F_{0}(\mathbf{a},\overline{\mu})}\, d\,\mathbf{a}\, d\,\overline{\mu} -} \\ {- \sum_{j = 1}^{s}\,\int_{\Xi_{j}}} & \left. Q_{j}(\overline{\xi}^{(j)})\,\ln\frac{Q_{j}(\overline{\xi}^{(j)})}{Q_{j}^{0}(\overline{\xi}^{(j)})}d\overline{\xi}^{(j)}\Rightarrow\max_{F,\overline{Q}} \right. \\ \end{aligned}
$$

(5.35)

* 约束条件为：

  * —PDF 的归一化条件，即

