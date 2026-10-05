

$$
\begin{aligned} & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}W^{*}\mathbf{u}) = W_{0}\mathbf{u}) \times} \\ & {\times \frac{\exp\left\lbrack \left. - {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{j},\mathbf{D}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{r}) \right.},\, \middle| \, r = \overline{1,(j-1)}),\mathbf{a}^{-} + \Delta\,\mathbf{u}\rbrack \right\rangle \right\rbrack}{\mathcal{W}({\overline{\theta}}^{(1)},\ldots,{\overline{\theta}}^{(s)})},} \\ & {\text{\quad\quad}\quad\quad G_{j}^{*}({\overline{\eta}}^{(j)}) = G_{j}^{0}({\overline{\eta}}^{(j)})\frac{\exp\left\lbrack {- {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{(j)},{\overline{\eta}}^{(j)} \right\rangle}} \right\rbrack}{\mathcal{G}_{j}({\overline{\theta}}^{(j)})},} \\ & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}j = \overline{1,s},} \\ \end{aligned}
$$

(5.72)

where

$$
\begin{aligned} & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\mathcal{W}({\overline{\theta}}^{(1)},\ldots,{\overline{\theta}}^{(s)}) = {\int_{\mathcal{U}}W_{0}}(\mathbf{u}) \times} \\ & {\times \exp\left\lbrack \left. - {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{(j)},\mathbf{D}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{r}) \right.},\, \middle| \, r = \overline{1,(j-1)}),\mathbf{a}^{-} + \Delta\,\mathbf{u}\rbrack \right\rangle \right\rbrack d\mathbf{u},} \\ & {\text{\quad\quad}\text{\quad\quad}\quad\mathcal{G}_{j}({\overline{\theta}}^{(j)}) = {\int_{\mathcal{E}}G_{j}^{0}}({\overline{\eta}}^{(j)})\exp\left\lbrack {- \left\langle {\overline{\theta}}^{(j)},{\overline{\eta}}^{(j)} \right\rangle} \right\rbrack d{\overline{\eta}}^{(j)},} \\ & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\quad\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}j = \overline{1,s}.} \\ \end{aligned}
$$

(5.73)

与 RPM-Orig 类的随机化模型类似（参见 (5.4.1)），熵最优 PDF 由拉格朗日乘子参数化并表示为指数函数。

### 5.4.3 具有输入和输出误差的 RPM-Orig 类随机化模型

考虑问题 (5.2.3, 5.36, 5.2.3) 并写出拉格朗日泛函：

$$
\begin{aligned} {\mathcal{L}\lbrack F(\mathbf{a},\mu),\overline{Q}(\overline{\xi})\rbrack} & {\mathcal{H}\lbrack F(\mathbf{a},\mu),\overline{Q}(\overline{\xi})\rbrack + \lambda w\lbrack F(\mathbf{a},\mu)\rbrack + \left\langle \overline{\eta},\mathbf{q}\lbrack\overline{Q}(\overline{\xi}\rbrack \right\rangle +} \\ & {+ \left\langle {\overline{\theta}}^{(j)},\mathbf{c}^{(j)}\lbrack F(\mathbf{a},\mu),\overline{Q}(\overline{\xi})\rbrack \right\rangle,} \\ \end{aligned}
$$

(5.74)

其中 $\lambda;\overline{\eta};\overline{\theta}$ — 对应约束的拉格朗日乘子：

$$
\begin{array}{r} {w\lbrack P(\mathbf{a})\rbrack = 1 - {\int_{\mathcal{R}}F}(\mathbf{a},\mu)d\mathbf{a}d\mu = 0,} \\ \end{array}
$$

(5.75)

![](images/math5_252.jpg)

$$
\begin{aligned} & {\mathbf{c}^{(j)}\lbrack F(\mathbf{a},\mu),\overline{Q}(\overline{\xi})\rbrack = \mathbf{y}^{(j)} - \left\lbrack {{\int_{\mathcal{R}}F}(\mathbf{a},\mu)\hat{\mathbf{y}}(t_{j},\mathbf{a},\mu)\, d\mathbf{a}\, d\mu} \right\rbrack +} \\ & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad} + {\int_{\Xi_{j}}\,}Q_{j}({\overline{\xi}}^{(j)})\,{\overline{\xi}}^{(j)}\, d{\overline{\xi}}^{(j)} = 0,} \\ & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\quad\text{\quad\quad}\text{\quad\quad}j = \overline{1,s}.} \\ \end{aligned}
$$

(5.77)

为了得到拉格朗日泛函的最优性条件，我们再次采用基于 Gâteaux 导数的方法。相应的一阶最优性条件具有如下形式

$$
\begin{aligned} & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\quad\text{\quad\quad}F^{*}(\mathbf{a},\mu) = F_{0}(\mathbf{a},\mu) \times} \\ & {\times \frac{\left. \exp\lbrack - {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{(j)},\mathbf{B}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{h}) \right.} + \mu(t_{j},\tau_{h}),\, \middle| \, h = \overline{1,(j-1)}),\mathbf{a}\rbrack \right\rangle\rbrack}{\mathcal{F}({\overline{\theta}}^{(1)},\ldots,{\overline{\theta}}^{(s)})},} \\ & {\text{\quad\quad}\text{\quad\quad}Q_{j}^{*}({\overline{\xi}}^{(j)}) = Q_{j}^{0}({\overline{\xi}}^{(j)})\frac{\exp\lbrack - \left\langle {\overline{\theta}}^{(j)},{\overline{\xi}}^{(j)} \right\rangle\rbrack}{\mathcal{Q}_{j}({\overline{\theta}}^{(j)})},\quad j = \overline{1,s}.} \\ \end{aligned}
$$

(5.78)

其中

$$
\begin{aligned} & {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\mathcal{F}({\overline{\theta}}^{(1)},\ldots,{\overline{\theta}}^{(s)}) = {\int_{\mathcal{R}}F_{0}}(\mathbf{a},\mu) \times} \\ & {\exp\left\lbrack \left. - {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{(j)},\mathbf{B}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{h}) \right.} + \mu(t_{j},\tau_{h}),\, \middle| \, h = \overline{1,(j-1)}),\mathbf{a}\rbrack \right\rangle \right\rbrack d\mathbf{a},} \\ & {\quad\text{\quad\quad}\text{\quad\quad}\mathcal{Q}_{j}({\overline{\theta}}^{(j)}) = {\int_{\Xi}Q_{j}^{0}}({\overline{\xi}}^{(j)})\exp\left\lbrack {- \left\langle {\overline{\theta}}^{(j)},{\overline{\xi}}^{(j)} \right\rangle} \right\rbrack d{\overline{\xi}}^{(j)},} \\ & {\text{\quad\quad}\text{\quad\quad}\quad\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}j = \overline{1,s}.} \\ \end{aligned}
$$

(5.79)

得到的 PDF 函数由拉格朗日乘子 $\overline{\theta}$ 参数化，$\overline{\theta}$ 由平衡方程确定。

## 5.5 拉格朗日乘子的方程

所有熵最优 PDF 都属于由拉格朗日乘子 ${\overline{\theta}}^{1},\ldots,{\overline{\theta}}^{s}$ 参数化的指数函数类；参见上一节推导的公式。为了计算拉格朗日乘子，我们需要求解由平衡约束 (5.24, 5.31) 与熵最优 PDF (5.64, 5.4.2) 得到的方程。

**1. 具有输出误差的 RPM-Orig 模型**

为了形成相应的方程，引入以下辅助记号。

* 具有熵最优随机参数的模型的平均输出

$$
\begin{aligned} & {\text{\quad\quad}\mathbb{Y}_{j}(\overline{\theta}) = \mathcal{P}^{( - 1)}(\overline{\theta}){\int_{\mathcal{A}}P_{0}}(\mathbf{a}) \times} \\ {\times \exp} & {\left\lbrack \left. - {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{(j)},\mathcal{B}\lbrack\mathbf{x}((t_{j},\tau_{h}) \right.}\\, \middle| \, h = \overline{1,(j-1)}),\mathbf{a}\rbrack \right\rangle \right\rbrack \times} \\ & \left. \quad \times \mathcal{B}\lbrack\mathbf{x}((t_{j},\tau_{h})\, \middle| \, h = \overline{1,(j-1)}),\mathbf{a}\rbrack d\mathbf{a}; \right. \\ \end{aligned}
$$

(5.80)

* 平均熵-“最差”测量噪声

