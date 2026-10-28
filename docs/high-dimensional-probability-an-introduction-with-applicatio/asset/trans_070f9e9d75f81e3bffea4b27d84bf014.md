

## 7.4 苏达科夫不等式

让我们回到定义在任意指标集 $T$ 上的一般零均值高斯过程 $(X_t)_{t\in T}$。正如我们之前所看到的（注记 7.1.7），增量

$$d(t,s):=\|X_t-X_s\|_{L^2}=\bigl(\mathbb{E}(X_t-X_s)^2\bigr)^{1/2} \tag{7.13}$$

在 $T$ 上定义了一个度量，称为*典范度量*。这个度量决定了协方差函数 $\Sigma(t,s)$，而协方差函数又决定了过程 $(X_t)_{t\in T}$ 的分布（回顾注记 7.1.10）。因此，理论上，我们只需理解度量空间 $(T,d)$ 的几何结构，就能回答关于该过程分布的任何问题——换句话说，我们可以通过几何来研究概率。

这里有一个重要的具体问题：我们如何根据 $(T,d)$ 的几何结构来估计

$$\mathbb{E}\sup_{t\in T}X_t \tag{7.14}$$

这是一个困难的问题，我们现在开始研究它，并将在第8章继续。

我们将从(7.14)的一个下界开始，该下界用*度量熵*表示，度量熵在第4.2节中引入。回顾一下，对任意 $\varepsilon>0$，*覆盖数*

$$\mathcal{N}(T,d,\varepsilon)$$

是在度量 $d$ 下 $T$ 的 $\varepsilon$-网的最小基数，等价地，是能够覆盖 $T$ 的半径为 $\varepsilon$ 的闭球的最少个数。覆盖数的对数 $\log_2\mathcal{N}(T,d,\varepsilon)$ 称为 $T$ 的*度量熵*。

**定理 7.4.1**（苏达科夫不等式）。设 $(X_t)_{t\in T}$ 是一个*零均值高斯过程*。则对任意 $\varepsilon\ge 0$，有

$$\mathbb{E}\sup_{t\in T}X_t\ge c\varepsilon\sqrt{\log\mathcal{N}(T,d,\varepsilon)}.$$

其中 $d$ 是(7.13)中定义的典范度量。

*证明*  我们从苏达科夫-费尔尼克比较不等式（定理 7.2.8）来推导这个结果。假设

$$\mathcal{N}(T,d,\varepsilon)=:N$$

是有限的；无限情形留给你在习题7.4中处理。设 $\mathcal{N}$ 是 $T$ 的一个极大 $\varepsilon$-分离子集。则 $\mathcal{N}$ 是 $T$ 的一个 $\varepsilon$-网（回顾引理 4.2.6），因此

$$|\mathcal{N}|\ge N.$$

将过程限制在 $\mathcal{N}$ 上，我们看到只需证明

$$\mathbb{E}\sup_{t\in\mathcal{N}}X_t\ge c\varepsilon\sqrt{\log N}.$$

$^5$ 如果 $T$ 没有有限的 $\varepsilon$-网，我们令 $\mathcal{N}(T,d,\varepsilon)=\infty$。

我们通过将 $(X_t)_{t\in\mathcal N}$ 与一个更简单的高斯过程 $(Y_t)_{t\in\mathcal N}$ 进行比较来做到这一点，后者定义如下：

$$Y_t := \frac{\varepsilon}{\sqrt{2}}g_t,\qquad \text{其中 } g_t \text{ 是独立的 } N(0,1) \text{ 随机变量。}$$

为了使用苏达科夫-费尔尼克比较不等式（定理 7.2.8），我们需要比较这两个过程的增量。固定两个不同的点 $t,s\in\mathcal N$。根据定义，我们有

$$\mathbb E(X_t-X_s)^2=d(t,s)^2\geq\varepsilon^2$$

而

$$\mathbb E(Y_t-Y_s)^2=\frac{\varepsilon^2}{2}\,\mathbb E(g_t-g_s)^2=\varepsilon^2.$$

（在最后一行，我们使用了 $g_t-g_s\sim N(0,2)$。）这意味着

$$\mathbb E(X_t-X_s)^2\geq\mathbb E(Y_t-Y_s)^2\qquad\text{对任意 }t,s\in\mathcal N.$$

应用定理 7.2.8，我们得到

$$\mathbb E\sup_{t\in\mathcal N}X_t\geq\mathbb E\sup_{t\in\mathcal N}Y_t=\frac{\varepsilon}{\sqrt{2}}\,\mathbb E\max_{t\in\mathcal N}g_t\geq c\varepsilon\sqrt{\log N}.$$

在最后一步中，我们使用了 $N$ 个独立同分布 $N(0,1)$ 随机变量的期望最大值至少为 $c\sqrt{\log N}$，见习题2.38(b)。证明完成。□

### 7.4.1 在 $\mathbb R^n$ 中覆盖数的应用

苏达科夫不等式可用来界住任意集合 $T\subset\mathbb R^n$ 的覆盖数：

**推论 7.4.2**（$\mathbb R^n$ 中的苏达科夫不等式）。*设 $T\subset\mathbb R^n$。则对任意 $\varepsilon>0$，有*

$$\mathbb E\sup_{t\in T}\langle g,t\rangle\geq c\varepsilon\sqrt{\log\mathcal N(T,\varepsilon)}.$$

*这里 $\mathcal N(T,\varepsilon)$ 是覆盖 $T$ 的半径为 $\varepsilon$、圆心在 $T$ 中的欧氏球的最少个数，正如第4.2.1节中那样。*

*证明。* 考虑典范高斯过程 $X_t:=\langle g,t\rangle$，其中 $g\sim N(0,I_n)$。正如我们在第7.1.2节中指出的，该过程的典范距离就是 $\mathbb R^n$ 中的欧氏距离，即对任意 $t,s\in T$，$d(t,s)=\|X_t-X_s\|_{L^2}=\|t-s\|_2$。于是推论由苏达科夫不等式（定理 7.4.1）得出。□

在习题8.5中，你将证明推论7.4.2除一个对数因子外是精确的：

$$\mathbb E\sup_{t\in T}\langle g,t\rangle\leq C\log(n)\cdot\varepsilon\sqrt{\log\mathcal N(T,\varepsilon)}.$$

作为苏达科夫不等式的一个快速应用，让我们（粗略地）从推论0.0.3重新推导 $\mathbb R^n$ 中多胞体覆盖数的界：

*证明*  我们只证明 (f) 部分，其余留给你在习题7.15中完成。对于下界，固定任意 \(x,y\in T\)。由于 \(x-y\) 和 \(y-x\) 都在 \(T-T\) 中，性质 (e) 给出

\[w(T)\geq \frac{1}{2}\mathbb{E}\max\bigl(\langle x-y,g\rangle,\langle y-x,g\rangle\bigr)=\frac{1}{2}\mathbb{E}|\langle x-y,g\rangle|=\frac{1}{2}\sqrt{\frac{2}{\pi}}\,\|x-y\|_2.\]

最后一个等式成立是因为 \(\langle x-y,g\rangle\sim N(0,\|x-y\|_2^2)\)，且对 \(X\sim N(0,1)\) 有 \(\mathbb{E}|X|=\sqrt{2/\pi}\)。（请验证！）对所有 \(x,y\in T\) 取上确界即得结果。对于 (f) 中的上界，再次使用性质 (e) 得到

\[w(T)=\frac{1}{2}\mathbb{E}\sup_{x,y\in T}\langle g,x-y\rangle\leq \frac{1}{2}\mathbb{E}\sup_{x,y\in T}\|g\|_2\|x-y\|_2\leq \frac{1}{2}\mathbb{E}\|g\|_2\cdot\operatorname{diam}(T).\]

由于 \(\mathbb{E}\|g\|_2\leq (\mathbb{E}\|g\|_2^2)^{1/2}=\sqrt{n}\)，证毕。□

**注记 7.5.3**（宽度与直径）。(f) 中的上界和下界都是最优的，它们之间的 \(O(\sqrt{n})\) 差距无法改进（见习题7.16）。因此，用直径来刻画高斯宽度不是一个好方法。

### 7.5.1 宽度的几何意义

高斯宽度有一个很好的几何意义：它描述的是集合 \(T\subset\mathbb{R}^n\) 在随机方向上看去有多宽。\(T\) 在方向 \(\theta\in S^{n-1}\) 上的宽度，是包含 \(T\) 的最窄带状区域（位于正交于 \(\theta\) 的平行超平面之间）的宽度（见图7.3），它可以表示为 \(\sup_{x,y\in T}\langle\theta,x-y\rangle\)（请验证）！如果我们在所有单位方向 \(\theta\) 上对宽度取平均，就得到

\[\mathbb{E}\sup_{x,y\in T}\langle\theta,x-y\rangle=\mathbb{E}\sup_{z\in T-T}\langle\theta,z\rangle.\tag{7.16}\]

![](img/b122213aed28c1888de83a894123323e_215_0.png)

**图 7.3** 集合 \(T\subset\mathbb{R}^n\) 在单位向量 \(\theta\) 方向上的宽度。

**定义 7.5.4**（球面宽度）. 集合 \(T\subset\mathbb{R}^n\) 的*球面宽度*定义为

\[w_s(T):=\mathbb{E}\sup_{x\in T}\langle\theta,x\rangle\quad\text{其中}\quad\theta\sim\operatorname{Unif}(S^{n-1}).\]

高斯宽度与球面宽度之间的唯一区别在于我们取平均所依据的随机向量：\(g\sim N(0,I_n)\) 与 \(\theta\sim\operatorname{Unif}(S^{n-1})\)。两者都具有旋转不变性，但 \(g\) 的长度大约是 \(\theta\) 的 \(\sqrt{n}\) 倍。因此：

**引理 7.5.5**（高斯宽度与球面宽度）。*高斯宽度大约是球面宽度的* \(\sqrt{n}\) *倍：*

$$\left(\sqrt{n}-\frac{C}{\sqrt{n}}\right)w_s(T)\leq w(T)\leq \sqrt{n}\,w_s(T).$$

*证明。* 将高斯向量 \(g\) 用其长度和方向表示：\(g=r\theta\)，其中 \(r=\|g\|_2\)，\(\theta=g/\|g\|_2\)。这里 \(\theta\sim\operatorname{Unif}(S^{n-1})\) 与 \(r\) 独立（见习题 [3.22](#)）。因此

$$w(T)=\mathbb{E}\sup_{x\in T}\langle r\theta,x\rangle=\mathbb{E}[r]\cdot\mathbb{E}\sup_{x\in T}\langle\theta,x\rangle=\mathbb{E}\|g\|_2\cdot w_s(T).$$

剩下的只需使用范数的集中性（见习题 [3.2](#)），它给出 \(\sqrt{n}-C/\sqrt{n}\leq\mathbb{E}\|g\|_2\leq\sqrt{n}\)，从而完成证明。

### 7.5.2 例子

**例 7.5.6**（欧氏球与球面）。单位球和球面的高斯宽度为

$$w(S^{n-1})=w(B_2^n)=\mathbb{E}\|g\|_2=\sqrt{n}\pm\frac{C}{\sqrt{n}}, \tag{7.17}$$

其中最后一步我们使用了范数的集中性（习题 [3.2](#)）。这些集合的球面宽度当然等于1。

**例 7.5.7**（立方体）。\(\mathbb{R}^n\) 中 \(\ell^\infty\) 范数的单位球是立方体 \(B_\infty^n=[-1,1]^n\)。因此，利用对偶性（[1.6](#)），我们得到

$$w(B_\infty^n)=\mathbb{E}\|g\|_1=\mathbb{E}|g_1|\cdot n=\sqrt{\frac{2}{\pi}}\cdot n. \tag{7.18}$$

**例 7.5.8**（交叉多胞体）。\(\mathbb{R}^n\) 中 \(\ell^1\) 范数的单位球是*交叉多胞体* \(B_1^n=\{x\in\mathbb{R}^n:\|x\|_1\leq 1\}\)，见（[1.3](#)）。它的高斯宽度满足

$$w(B_1^n)\simeq\sqrt{\log n} \tag{7.19}$$

其中记号 \(\simeq\) 隐藏了绝对常数因子。这是因为

$$w(B_1^n)=\mathbb{E}\|g\|_\infty=\mathbb{E}\max_{i\leq n}|g_i|,$$

其中第一个等式使用了对偶性（[1.6](#)）。于是 (7.19) 由习题2.38(b)得出。

**例 7.5.9**（有限点集）。任意有限点集 \(T\subset\mathbb{R}^n\) 满足

$$w(T)\leq C\sqrt{\log|T|}\cdot\operatorname{diam}(T).$$

为了证明这一点，我们可以假设 \(\operatorname{diam}(T)=1/2\)（通过缩放），并且 \(T\) 位于单位欧氏球内（通过平移）。然后像 (7.15) 中那样论证（请自行完成！）。

