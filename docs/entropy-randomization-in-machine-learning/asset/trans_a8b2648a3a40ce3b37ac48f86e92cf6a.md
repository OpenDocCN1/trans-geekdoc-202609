

## 4.4 随机参数和系综的概率特性

RML 程序中使用的模型具有 *随机化参数* 的实现，它们在这些模型的输出处生成随机对象（向量、轨迹、事件）的 *系综*。两者均以适当的概率特性来描述。

### 1. 随机化参数的概率特性

所研究的 RPM 涉及具有期望概率特性的随机化区间型参数。我们将区分

* *原始* 参数 `a` = {`a[1]`,…,`a[n]`}，其取值在具有任意大小面的 *n* 维平行六面体 `𝒜` 内，即

```
\begin{array}{r} {\mathcal{A} = \lbrack\mathbf{a}^{-},\mathbf{a}^{+}\rbrack = \otimes_{i = 1}^{n}\mathcal{A}_{i} = \lbrack a_{i}^{-},a_{i}^{+}\rbrack,\quad\quad\text{and}} \\ \end{array}
```
(4.95)

* *相对非负* 参数 `u` = {`u[1]`,…,`u[n]`}，其取值在具有单位面的 *n* 维非负平行六面体 `𝒰` 内，即

```
\begin{array}{r} {\mathcal{U} = \lbrack\mathbf{0},\mathbf{1}\rbrack.} \\ \end{array}
```
(4.96)

相对非负参数与原始参数的关系为

```
\begin{aligned} a_{i} & {= a_{i}^{-} + u_{i}\delta_{i},\quad\delta_{i} = a_{i}^{+} - a_{i}^{-},\quad\quad i = \overline{1,n},} \\ \mathbf{a} & {= \mathbf{a}^{-} + \Delta\mathbf{u},\quad\quad\Delta = \text{diag}\lbrack(a_{i}^{+} - a_{i}^{-})\,,\, i = \overline{1,n}\rbrack.} \\ \end{aligned}
```
(4.97)

这些类型的模型参数根据期望的概率特性进行随机化，更具体地说，根据原始参数 `a` 的 PDF `P(a)` 和相对非负参数 `u` 的 PDF `W(u)` 进行随机化。一般情况下，向量 `a` 和 `u` 的元素可以相互关联。它们的 PDF 表示一般形式的多个变量函数。如果参数是独立的，则相应的 PDF 具有乘性结构：

```
\begin{array}{r} {P(\mathbf{a}) = {\prod\limits_{i = 1}^{n}P_{i}}(a_{i}),\quad\quad W(\mathbf{u}) = {\prod\limits_{i = 1}^{n}w_{i}}(u_{i}).} \\ \end{array}
```
(4.98)

为了使表述简洁，让我们引入以下术语缩写：

* `RPM-Orig` 表示具有原始参数 `a` 和 *PDF* `P(a)` 的随机化参数模型；
* `RPM-Rel` 表示具有相对非负参数 `u` 和 *PDF* `W(u)` 的随机化参数模型。

### 2. 系综的经验概率特性

随机化模型输出随机向量（静态模型）的系综、时变函数即轨迹（动态模型）的系综，或随机事件的系综。对于每个模型，这些系综都是通过生成其随机化参数而出现的。系综可以用数理统计的众所周知的概率特性以定量方式描述。

考虑在有限时间区间 `𝒯` = `[0, T]` 上的一组任意轨迹 `${\hat{\mathcal{Y}}}_{T}$` `ŷ(t)`，即由具有给定 PDF 的一维 `RPM-Orig` 模型生成的。这样的系综的示例在 [Fig. 4.23](#chapter4.xhtml#f4_23) 中给出。假设它包含 `N` 条轨迹。用 `ŷ(t*)` 表示其在固定值 `t` = `t*` 下的截集。该截集形成随机变量 `ŷ(t*)` 的值（实现）的集合，将用于经验估计。

![Figure 4.23](images/fig4_24.jpg)

[Figure 4.23](#chapter4.xhtml#f4_23b)

*A) 均值轨迹的演化*。随机变量 `ŷ(t*)` 的均值由下式给出

```
\begin{array}{r} {\overline{y}(t^{\*}) = \frac{1}{N}{\sum\limits_{k = 1}^{N}{\hat{y}}^{(k)}}(t^{\*}),} \\ \end{array}
```
(4.99)

其中 `ŷ^{(k)}(t*)` 表示随机变量 `ŷ(t*)` 的实现。

对不同的时间 `t*` ∈ `𝒯` 计算这些均值，我们得到经验估计 `\overline{y}(t_u^*), u ∈ \overline{1,U}.` 的集合。它们可以用连续曲线 `\overline{y}(t),` 来近似，该曲线形成均值轨迹 [[104](#refbib.xhtml#r104)]。

*B) 经验方差管的演化*。取 [Fig. 4.23](#chapter4.xhtml#f4_23) 中所示的系综 `${\hat{\mathcal{Y}}}_{T}$`，并考虑其截集 `ŷ(t*)`。定义随机变量

```
\begin{array}{r} {D(t^{\*}) = {\lbrack\hat{y}(t^{\*}) - \overline{y}(t^{\*})\rbrack}^{2}.} \\ \end{array}
```
(4.100)

该随机变量的均值（即随机变量 `ŷ(t*)` 的方差）由下式给出

```
\begin{array}{r} {\overline{D}(t^{\*}) = \frac{1}{N - 1}{\sum\limits_{k = 1}^{N}D^{(k)}}(t^{\*}),} \\ \end{array}
```
(4.101)

其中 `D^{(k)}(t*)` 表示随机变量 `D(t*)` (4.100) 的实现。

引入随机变量 `ŷ(t*)` 相对于其均值 `\overline{y}(t*)` 的标准差：

```
\begin{array}{r} {\sigma(t^{\*}) = \sqrt{\overline{D}(t^{\*})}.} \\ \end{array}
```
(4.102)

在假设 `t*` 取值于区间 `𝒯` 内的条件下，让我们用连续曲线——标准差轨迹 `σ(t)` 来近似得到的结果点。

定义两条轨迹，`δ_± = \overline{y}(t) ± σ(t).` 域

```
\begin{array}{r} {\mathcal{D} = \left\{ \hat{y}:\delta_{-}(t) \leq \hat{y}(t) \leq \delta_{+}(t) \right\}} \\ \end{array}
```
(4.103)

将被称作 *标准差管*。 [Figure 4.23](#chapter4.xhtml#f4_23) 展示了关于均值轨迹 `\overline{y}(t).` 的标准差管 `𝒟`。

*C) 经验概率密度函数的演化*。经验 PDF 的估计值可以用固定时间 `t*` 下随机变量实现 `ŷ(t*)` 构造。

经验 PDF，即直方图 `p[ŷ(t*)]`，是根据众所周知的规则 [104] 构造的。用 `ŷ^-(t*)` 和 `ŷ^+(t*)` 分别表示随机变量 `ŷ(t*)` 的左、右极限。接下来，将区间 `[ŷ^-(t*), ŷ^+(t*)]` 分成 `J` 个子区间 `η_j, (j = \overline{1,J})`，其长度为 (`ŷ^+(t*)` − `ŷ^-(t*)`) / `J`。经验概率密度函数是随机变量 `ŷ(t*)` 的值落入子区间 `η_j, (j = \overline{1,J}),` 的频率，即

```
\begin{array}{r} {p_{j} = \frac{M_{j}}{M},} \\ \end{array}
```
(4.104)

其中 `M[j]` 给出子区间 `η[j]` 内 `ŷ(t*)` 的值的数量，`M` 是系综中轨迹的总数量。 [Figure 4.24](#chapter4.xhtml#f4_24) 提供了直方图 `p[ŷ(t*)]` 的示例。通过改变时间 `t*` 可以观察到直方图的演化。通常，系综包含非常多的轨迹。因此，直方图可以用连续曲线 `\hat{P}[ŷ(t*)]` 以良好的精度近似。

![Figure 4.24](images/fig4_24.jpg)

[Figure 4.24](#chapter4.xhtml#f4_24b)

*D). 经验中位轨迹的演化*。通常经验 PDF 没有对称性。在这种情况下，中位轨迹似乎更有信息量。考虑 PDF `\hat{P}[ŷ(t*)]`，并定义值 `z(t*)` 使得

```
\begin{array}{r} {{\int_{\hat{y}^{-}(t^{\*})}^{z(t^{\*})}\hat{P}}(x)dx = {\int_{z(t^{\*})}^{\hat{y}^{-}(t^{\*})}\hat{P}}(x)dx.} \\ \end{array}
```
(4.105)

