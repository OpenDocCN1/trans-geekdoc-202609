
将其代入(7.11)，得到

$$
\sum_{i=1}^{n} \frac{1}{\sqrt{u}}\,\mathbb{E}\,X_i\,\frac{\partial f}{\partial x_i}(Z(u)) = \sum_{i,j=1}^{n} \Sigma_{ij}^{X}\,\mathbb{E}\,\frac{\partial^2 f}{\partial x_i\,\partial x_j}(Z(u)).
$$

对两边关于\(Y\)取期望，我们消去对\(Y\)的条件。

类似地，我们可以计算(7.10)中另一个和式，即包含\(Y_i\)的项。将这两个和式合并，即完成证明。

## 7.2.2 Slepian不等式的证明

我们准备建立Slepian不等式的一个初步的、泛函形式。

**引理7.2.6（Slepian不等式，泛函形式）。** *考虑\(\mathbb{R}^n\)中的两个零均值高斯随机向量\(X\)和\(Y\)。假设对所有\(i,j=1,\ldots,n\)，有*

$$
\mathbb{E}X_i^2 = \mathbb{E}Y_i^2 \quad\text{且}\quad \mathbb{E}(X_i-X_j)^2 \leq \mathbb{E}(Y_i-Y_j)^2.
$$

*考虑一个二次可微函数\(f:\mathbb{R}^n\to\mathbb{R}\)，使得*

$$
\frac{\partial^2 f}{\partial x_i\,\partial x_j} \geq 0 \quad\text{对所有 } i\ne j.
$$

*则*

$$
\mathbb{E}f(X) \geq \mathbb{E}f(Y),
$$

*假设两个期望都存在且有限。*

*证明。* 这些假设意味着\(X\)和\(Y\)的协方差矩阵\(\Sigma^X\)和\(\Sigma^Y\)的元素满足

$$
\Sigma_{ii}^{X}=\Sigma_{ii}^{Y} \quad\text{且}\quad \Sigma_{ij}^{X}\geq\Sigma_{ij}^{Y}
$$

对所有\(i,j=1,\ldots,n\)成立。我们可以假设\(X\)和\(Y\)独立。（为什么？）应用引理7.2.5并利用我们的假设，我们得出

$$
\frac{d}{du}\,\mathbb{E}f(Z(u)) \geq 0,
$$

所以\(\mathbb{E}f(Z(u))\)随\(u\)递增。因此\(\mathbb{E}f(Z(1))=\mathbb{E}f(X)\)至少与\(\mathbb{E}f(Z(0))=\mathbb{E}f(Y)\)一样大。这就完成了证明。

现在我们准备证明Slepian不等式，即定理7.2.2。让我们用高斯随机向量的等价形式来陈述并证明它。

**定理7.2.7（Slepian不等式）。** *设\(X\)和\(Y\)是如引理7.2.6中的高斯随机向量。则对每个\(\tau\geq 0\)，有*

$$
\mathbb{P}\{\max_{i\leq n}X_i\geq\tau\}\leq\mathbb{P}\{\max_{i\leq n}Y_i\geq\tau\}.
$$

因此，

$$
\mathbb{E}\max_{i\le n} X_i \le \mathbb{E}\max_{i\le n} Y_i.
$$

*证明。* 设\(h:\mathbb{R}\to[0,1]\)是区间\((-\infty,\tau)\)的指示函数的一个二次可微、非增的近似：

$$
h(x)\approx \mathbf{1}_{(-\infty,\tau)},
$$

如图7.2所示。定义函数\(f:\mathbb{R}^n\to\mathbb{R}\)为

![](img/b122213aed28c1888de83a894123323e_208_0.png)

**图7.2** 函数\(h(x)\)是指示函数\(\mathbf{1}_{(-\infty,\tau)}\)的一个光滑、非增的近似。

$$
f(x)=h(x_1)\cdots h(x_n).
$$

则\(f(x)\)是指示函数

$$
f(x)\approx \mathbf{1}_{\{\max_i x_i<\tau\}}.
$$

我们想对\(f(x)\)应用Slepian不等式的泛函形式，即引理7.2.6。为了检验该结果的假设，注意到对\(i\ne j\)，有

$$
\frac{\partial^2 f}{\partial x_i\,\partial x_j}=h'(x_i)h'(x_j)\cdot\prod_{k\notin\{i,j\}}h(x_k).
$$

根据假设，前两个因子非正，其余因子非负。因此二阶导数非负，符合要求。

由此可得

$$
\mathbb{E}f(X)\ge\mathbb{E}f(Y).
$$

通过近似，这意味着

$$
\mathbb{P}\left\{\max_{i\le n}X_i<\tau\right\}\ge\mathbb{P}\left\{\max_{i\le n}Y_i<\tau\right\}.
$$

这就证明了结论的第一部分。第二部分可通过练习1.15(b)中的积分尾公式得到（请验证！）

## 7.2.3 Sudakov–Fernique和Gordon不等式

Slepian不等式对(7.3)中的过程\((X_t)\)和\((Y_t)\)有两个假设：方差相等和增量占优。我们现在去掉方差相等的假设，仍然能够得到(7.5)。

**定理7.2.8（Sudakov-Fernique不等式）。** 设\((X_t)_{t\in T}\)和\((Y_t)_{t\in T}\)是两个*零均值高斯过程*。假设对所有\(t,s\in T\)，有

$$
\mathbb{E}(X_t-X_s)^2 \leq \mathbb{E}(Y_t-Y_s)^2.
$$

*则*

$$
\mathbb{E}\sup_{t\in T}X_t \leq \mathbb{E}\sup_{t\in T}Y_t.
$$

*证明。* 与定理7.2.7中证明Slepian不等式一样，只需对\(\mathbb{R}^n\)中的高斯随机向量\(X\)和\(Y\)证明此定理即可。我们同样从高斯插值引理7.2.5推出结论。但这次，我们不再选择近似指示函数\(\{\max_i x_i<\tau\}\)的\(f(x)\)，而是希望\(f(x)\)近似\(\max_i x_i\)。

为此，令\(\beta>0\)为一个参数，定义函数⁴

$$
f(x):=\frac{1}{\beta}\log\sum_{i=1}^{n}e^{\beta x_i}.
$$

快速检验可知

$$
f(x)\to\max_{i\leq n}x_i\quad\text{当 }\beta\to\infty.
$$

（请自行验证！）将\(f(x)\)代入高斯插值公式(7.9)并化简表达式，可得

$$
\frac{d}{du}\,\mathbb{E}\,f(Z(u))\leq 0\quad\text{对所有 }u\in[0,1].
$$

（请在练习7.7中仔细完成这一步！）然后我们可以像Slepian不等式那样完成证明。

某些应用需要随机过程的*极小极大*界。例如，由(4.14)，一个所有元素为独立\(N(0,1)\)的\(m\times n\)高斯矩阵\(A\)的最小奇异值可以写成

$$
s_n(A)=\min_{u\in S^{n-1}}\|Au\|_2=\min_{u\in S^{n-1}}\max_{v\in S^{m-1}}X_{uv},
$$

其中\(X_{uv}=\langle Au,v\rangle\)是正态随机变量。处理这类问题的一个便捷工具是Gordon不等式，它将Slepian和Sudakov-Fernique不等式推广到极小极大情形：

**定理7.2.9（Gordon不等式）。** 设\((X_{ut})_{u\in U,t\in T}\)和\((Y_{ut})_{u\in U,t\in T}\)是以乘积集\(U\times T\)中的点对\((u,t)\)为索引的两个*零均值高斯过程*。假设

$$
\mathbb{E}(X_{ut}-X_{vs})^2\leq\mathbb{E}(Y_{ut}-Y_{vs})^2\quad\text{对所有 }u,v,t,s;
$$

$$
\mathbb{E}(X_{ut}-X_{vs})^2\geq\mathbb{E}(Y_{ut}-Y_{vs})^2\quad\text{对所有 }u\neq v\text{ 和所有 }t,s.
$$

⁴ 考虑这种\(f(x)\)形式的动机来自统计力学，其中(7.12)的右边可以解释为*对数配分函数*，而\(\beta\)为*逆温度*。

其中\(g\sim N(0,I_n)\)和\(h\sim N(0,I_m)\)是独立的高斯向量。这个过程的增量为

$$
\begin{aligned}
\mathbb{E}(Y_{uv}-Y_{wz})^2
&=\mathbb{E}\left(\langle g,u-w\rangle+\langle h,v-z\rangle\right)^2\\
&=\mathbb{E}\langle g,u-w\rangle^2+\mathbb{E}\langle h,v-z\rangle^2\quad\text{（由独立性，均值为0）}\\
&=\|u-w\|_2^2+\|v-z\|_2^2\quad\text{（因为$g,h$为标准正态）。}
\end{aligned}
$$

比较两个过程的增量，我们看到

$$
\mathbb{E}(X_{uv}-X_{wz})^2\leq\mathbb{E}(Y_{uv}-Y_{wz})^2\quad\text{对所有 }(u,v),(w,z)\in T,
$$

正如Sudakov-Fernique不等式所要求的那样。应用定理7.2.8，我们得到

$$
\begin{aligned}
\mathbb{E}\|A\|&=\mathbb{E}\sup_{(u,v)\in T}X_{uv}\leq\mathbb{E}\sup_{(u,v)\in T}Y_{uv}\\
&=\mathbb{E}\sup_{u\in S^{n-1}}\langle g,u\rangle+\mathbb{E}\sup_{v\in S^{m-1}}\langle h,v\rangle\\
&=\mathbb{E}\|g\|_2+\mathbb{E}\|h\|_2\\
&\leq\left(\mathbb{E}\|g\|_2^2\right)^{1/2}+\left(\mathbb{E}\|h\|_2^2\right)^{1/2}\quad\text{（回忆练习1.11）}\\
&=\sqrt n+\sqrt m\quad\text{（见命题3.2.1(b)）。}
\end{aligned}
$$

定理7.3.1只给出了期望界，但我们可以利用5.2节的集中工具将其提升为高概率界：

**推论7.3.2（高斯随机矩阵的范数：尾部）。**

*设\(A\)是一个具有独立\(N(0,1)\)元素的\(m\times n\)矩阵。则对每个\(t\geq 0\)，有*

$$
\mathbb{P}\{\|A\|\geq\sqrt m+\sqrt n+t\}\leq 2\exp(-ct^2).
$$

**证明。** 我们将期望界（定理7.3.1）与高斯集中性（定理5.2.3）结合起来。将\(A\)的行拼接起来，将其视为\(\mathbb{R}^{m\times n}\)中的一个长随机向量。这使\(A\)成为一个标准正态随机向量：\(A\sim N(0,I_{nm})\)。考虑函数

$$
f(A):=\|A\|
$$

它将向量化的矩阵映射为矩阵的算子范数。由于算子范数以Frobenius范数为上界，而Frobenius范数正是\(\mathbb{R}^{m\times n}\)上的欧几里得范数，所以\(f\)是\(\mathbb{R}^{m\times n}\)上的Lipschitz函数，其Lipschitz范数以1为界。（为什么？）于是定理5.2.3给出

$$
\mathbb{P}\{\|A\|\geq\mathbb{E}\|A\|+t\}\leq 2\exp(-ct^2).
$$

由定理7.3.1给出的\(\mathbb{E}\|A\|\)的界完成了证明。

现在尝试练习7.11来证明一个*对称高斯矩阵*满足

$$
\mathbb{E}\|A\|\leq 2\sqrt n,
$$

并尝试练习7.13来证明一个\(m\times n\)高斯矩阵\(A\)的*最小奇异值*满足

$$
\mathbb{E}\,s_n(A)\geq\sqrt m-\sqrt n.
$$

