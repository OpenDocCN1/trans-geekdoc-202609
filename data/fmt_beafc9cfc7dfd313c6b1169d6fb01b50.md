
* the vectors `${\overline{\theta}}^{(j)} = \left\{ \theta_{1}^{(j)},\ldots,\theta_{m}^{(j)} \right\},\, j = \overline{1,s},$` composed of the Lagrange multipliers for the constraints (5.22), writing them in the form

$$\begin{aligned} & {\text{\quad\quad}\mathbf{h}^{(j)}\lbrack W(\mathbf{u}),G_{j}({\overline{\eta}}^{(j)})\rbrack = \mathbf{y}(t_{j}) -} \\\\ & \left. - {\int_{\mathcal{U}}W}(\mathbf{u})\mathbf{D}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{h}),\, \middle| \, h = \overline{1,(j-1)}),\mathbf{a}^{-} + A\,\mathbf{u}\rbrack\, d\mathbf{u} - \right. \\\\ & {+ {\int_{\mathcal{E}_{j}}}\,G_{j}({\overline{\eta}}^{(j)})\,{\overline{\eta}}^{(j)}\, d{\overline{\eta}}^{(j)},\quad j = \overline{1,s}.} \\\\ \end{aligned}$$

(5.68)

Using these notations, define the Lagrange functional

$$\begin{aligned} {\mathcal{L}\lbrack W(\mathbf{u}),G(\overline{\eta})\rbrack} & {\mathcal{H}\lbrack W(\mathbf{u}),G(\overline{\eta})\rbrack + \lambda w\lbrack W(\mathbf{u})\rbrack + \left\langle \overline{\mu},\mathbf{g}\lbrack G(\overline{\eta})\rbrack \right\rangle +} \\\\ & {\left. + {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{(j)},\mathbf{h}^{(j)}\lbrack W(\mathbf{u}),G_{j}( \right.}{\overline{\eta}}^{(j)})\rbrack \right\rangle.} \\\\ \end{aligned}$$

(5.69)

To get optimality conditions for the Lagrange functional, we will again employ the Gateaux derivative-based method; see (5.60, 5.4.1). The corresponding first-order optimality conditions have the form

$$\begin{aligned} {\ln\frac{W^{\*}(\mathbf{u})}{W_{0}(\mathbf{u})}} & {+ 1 + \lambda +} \\\\ \left. + {\sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{j},\mathbf{D}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{h}) \right.},\, \middle| \, h = \right. & {\left. \overline{1,(j-1)}),\mathbf{a}^{-} + A\,\mathbf{u}\rbrack \right\rangle = 0,} \\\\ {\ln\frac{G_{j}^{\*}({\overline{\eta}}^{(j)})}{G_{j}^{0}({\overline{\eta}}^{(j)})} + 1 + \mu_{j}} & {+ \left\langle {\overline{\theta}}^{(j)},{\overline{\eta}}^{(j)} \right\rangle = 0,} \\\\ {j =} & {\overline{1,s}.} \\\\ \end{aligned}$$

(5.70)

The solution of these equations within the Lagrange multipliers `λ`, `μ[1]`, …, `μ[s]`, and `${\overline{\theta}}^{(1)},\ldots,{\overline{\theta}}^{(s)}$` is given by

$$\begin{aligned} {W^{\*}(\mathbf{u}) = W_{0}} & {(\mathbf{u})\exp\lbrack - 1 - \lambda -} \\\\ {{ \sum\limits_{j = 1}^{s}\left\langle {\overline{\theta}}^{j},\mathbf{D}^{(j)}\lbrack\mathbf{x}((t_{j},\tau_{h}) \right.},} & {\, \left| \, r = \overline{1,(j-1)}),\mathbf{a}^{-} + A\,\mathbf{u}\rbrack \right\rangle\rbrack,} \\\\ {G_{j}^{\*}({\overline{\eta}}^{(j)}) = G_{j}^{0}({\overline{\eta}}^{(j)})} & {\exp\left\lbrack {- 1 - \mu_{j} - \left\langle {\overline{\theta}}^{(j)},{\overline{\eta}}^{(j)} \right\rangle} \right\rbrack,} \\\\ & {j = \overline{1,s}.} \\\\ \end{aligned}$$

(5.71)

The Lagrange multipliers `λ` and `μ[1]`, …, `μ[s]` can be eliminated using the normalization conditions (5.28). Then formulas (5.4.2) yield the following entropy-optimal estimates for the PDFs of the RPM-Rel model parameters and measurement noises:

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

![](img/math5_252.jpg)

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
