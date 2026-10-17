
正如第 4.5 节所示，在大脑脸部区域系统中，特别是前额叶区域 `AL`，神经元被发现对感受野进行调谐。基于提取的深度旋转主成分的一种可能解释如下。令 `$R:\mathbb{R}^K \to \mathbb{R}^K$` 表示反射算子。`$R$` 的特征函数是奇函数和偶函数，特征值分别为 `$-1$` 和 `$1$`。我们证明与模板集合及其镜像对称性相关的协方差矩阵具有奇或偶特征函数。

## 附录

考虑一个仅包含一个模板 `$t$` 及其反射 `$R$`（酉变换）的集合。令 `$Z$` 表示取一个神经帧 `$T$` 并返回包含 `$t$` 及其反射的集的算子。

```
$Z = (1,R),\nZ(t) = T = \begin{pmatrix} t \\ Rt \end{pmatrix}$
```

我们证明 `$R$` 与 `$Z^\top Z$` 交换，它们具有共同的特征向量。我们有：

```
$Z^\top Z(Rt) = \begin{pmatrix} Rt+t \\ t+Rt \end{pmatrix} = R(Z^\top Z). (A.33)$
```

因此 `$R(Z^\top Z) = (Z^\top Z)R$`（交换），`$Z^\top Z$` 和 `$R$` 必须具有相同的特征函数。由于 `$R$` 的特征函数是偶函数和奇函数，`$T^\top T$` 的主成分也必须是偶函数和奇函数。

# A.6 来自模板组的类 Gabor 形状

### A.6.1 模板变换协方差算子的谱性质：皮层方程

本节侧重于描述模板变换协方差的谱性质。提出了一个皮层方程，其解提供了变换模板协方差的特征函数。我们考虑一层 `$2-D$` 孔径，以及与每个孔径相关的模板变换协方差，这些变换是通过这些孔径之一看到的图像变换产生的。这在平移情况下为第一层给出了显式解。

对于固定的 `$t$`，我们想要与集合 `$T_i = (g_0(t), g_1(t), \dots, g_i(t))^\top$` 相关的谱问题：

即我们想要找到特征值 `$\lambda_i$` 和特征函数 `$\psi_i$`，使得 `$T_i^\top T_i \psi_i = \lambda_i \psi_i. (A.34)$`

为了精确表述该问题，我们需要一些定义。我们从 `$1-D$` 问题开始。我们展示如何根据以下内容推导出视觉层细胞调性的解析表达式：

- **观测值。** 通过局部紧致群变换的图像，通过孔径看到；

- **赫布学习。** 视觉层中存在类似于赫布的突触。

我们固定对象：

- `$\mathcal{X}$` 信号空间：`$L^2(\mathbb{R}, dx)$`

- `$\mathcal{T} \subseteq \mathcal{X}$` 是模板集。

我们求解与等(A.34)连续版本相关的特征问题。在这种情况下，基本观测值由算子 `$T : \mathcal{X} \rightarrow \mathcal{X}$` 给出：

```
$(T I)(y) \equiv [t * M_I](y) = \int dx(y-x)a(x)I(x), \quad t \in \mathcal{T}, a, I \in \mathcal{X}, \quad (A.35)
```

其中：

```
$M_I(x) = a(x)I(x), \quad a \in \mathcal{X}$.
```

等(A.35) 是观测值 `$T$` 的数学表达式，即通过函数 `$a$`（称为孔径）看到的模板 `$t$` 的平移。

**备注 A.18** `$T$` 是线性的（根据卷积算子的性质）且有界的（根据 `$\|T\| = \|\Gamma(t)\| = \|a\|$`）。

**备注 A.19** `$M_a$` 是一个自伴算子。对伴算子 `$T^* : \mathcal{X} \rightarrow \mathcal{X}$` 给出：

```
$\langle T, I' \rangle = \int dy \dot{I}(y) \int dx (y-x)a(x)I(x) = \int dx I(x)a(x) \int dy (y-x)\dot{F}(y) = \langle I, T^*I \rangle$
```

意味着 `$T^* = M_a(t^* - I), t^*(x) = t(-x)$`。注意 `$\|t\| = \|t^*\| \rightarrow \|T\| = \|T^*\|$`，即 `$\|T^*\|$` 是有界的。

假设是赫布的，我们学习皮层细胞的调性由 `$T, T^* : \mathcal{X} \rightarrow \mathcal{X}$` 相关的协方差算子的谱问题给出：

```
$[T^* TI](y) = M_a[t^* * (M_I)](y) = M_a[(t)^* * (M_I)] = M_a(t^{(\otimes)} * (M_I)) = a(y) \int dx a(x)t^{(\otimes)}(y-x)I(x),
```

其中 `$t^{(\otimes)}$` 是 `$t$` 的自相关。这个表达式可以写为：

```
$[T^* TI](y) = \int dx K(x,y)I(x), K(x,y) = a(x)a(y)t^{(\otimes)}(y-x).
```

由于核 `$K$` 是希尔伯特-施密特的，

```
$Tr(K) = \int dx K(x,x) = \int dx a^2(x)t^{(\otimes)}(0) < \infty$,
```

我们有：

- 对应不同特征值的特征函数正正交；

- 特征值是实数且为正；

- 至少有一个特征值和特征函数（当 `$K$` 处处存在时），通常情况下是可计的。现在我们的目标是找到 `$\psi_n \in \mathcal{X}$` 和 `$\lambda_n \in \mathbb{R}$`，使得：

```
$a(y) \int dx t^{(\otimes)}(y-x)\psi_n = (A.36)$
```

并研究它们的性质。特别是，我们找到了近似解并证明它们是类 Gabor 的。精确解可以在 A.6 中找到。

### A.6.1 正方形孔径、循环与傅里

我们从最简单的情况开始，假设边界条件（在感受野），导致变换模板的循环结构。定义 `$T$` 为循环矩阵，其中每一列是上一列的平移。让我们在这个例子中使用通过正方形孔径看到的图像是一维的。使得对于 `$0 \leq x \leq a$`，`$a(x) = 1$`；否则 `$a(x) = 0，$t(x)$` 由 `$y$` 平移。这引导我们进入问题：找到对称矩阵 `$T^\top$` 的特征向量，其中 `$T$` 是循环矩阵（参见 [32]）。如果我们考虑该问题的连续版本，即特征值问题：

```
$\int dx \psi_n(x)t^{(\otimes)}(y-x) = \lambda_n\psi_n,$
```

其中 `$t^{(\otimes)}$` 是 `$t$` 的自相关，解为 `$\psi_n(x) = e^{-\alpha x}$`，位于 0 和 A。

### A.6.2 皮层孔径：推导与求解

假设 `$a(x) = e^{-\alpha x^2}$`。等(A.36) 可以写为：

```
$\lambda_n\psi_n(y) - e^{-\alpha y^2} \int dx e^{-\alpha x^2}t^{(\otimes)}(y-x) = 0,
```

或者等价于：

```
$\lambda_n\xi_n(y) - \int dx e^{-\alpha x^2} t^{\otimes} (y-x) \xi_n(x) = 0, \quad \xi_n(x) = e^{\alpha x}.$
```

在傅里基中分解 `$t^{\otimes}(x)$`：

```
$\lambda_n\xi_n(y) - \frac{1}{\sqrt{2\pi}} \int dx e^{-\alpha x^2} d\omega t^{\otimes}(\omega) e^{i\omega(y-x)} \xi_n(x) = 0.$
```

在 `$y$` 变量上推导并整理表达式：

```
$\lambda_n\xi_n'(y) + \frac{1}{\sqrt{2\pi}} \int d\omega t^{\otimes}(\omega) \int dx e^{-\alpha x^2} \psi_n(x) e^{-i\omega x} = 0. (A.37)$
```

这个表达式等于等(A.36) 中的原始特征问题，加上条件（例如 `$\xi_n(0) = c, \xi_n'(0) = c$`）。事实上，函数的导数决定了函数在某一点的值。因此，如果 `$\xi_n(0) = c$`，函数 `$\xi_n'(y)$` 唯一确定 `$\xi_n(y)$`；如果 `$\xi_n'(0) = c$`，函数 `$\xi_n(y)$` 唯一确定 `$\xi_n'(y)$`。

使用傅里叶算子 `$\mathcal{F}$`，我们可以将 (A.37) 重写为：

```
$\lambda_n\xi_n'(y) + 2\pi\delta^{-1}(t^{\otimes}(\omega)) \delta(e^{-2\alpha^2} \psi_n(x)) = 0.$
```

通过卷积定理：

```
$\lambda_n\xi_n'(y) + 2\pi\delta^{-1}(t^{\otimes}(\omega)) * (e^{-2\alpha^2} \xi_n(x)) = 0.$
```

将 `$\omega^2 t^{\otimes}(\omega)$` 展开为泰勒级数并回忆 `$\delta^{-1}(\omega^m) = i^m\delta^m(x)$`，得到了微分方程：

```
$\lambda_n\xi_n'(y) + \frac{1}{\sqrt{2\pi}} (c_0\delta + ic_1\delta^1 + \dots) * (e^{-2\alpha^2} \xi_n(x)) = 0. (A.38)$
```

其中 `$c_i$` 是 `$\omega^2 t^{\otimes}(\omega)$` 的泰勒级数展开系数。

### A.6.2.1 `$1/\omega$` 谱

在平均自然图像谱的情况下：

```
$t(\omega) = \frac{1}{\omega}$,
```

微分方程 (A.38) 假设：

```
$\lambda_n\xi_n'(y) + \sqrt{2\pi} e^{-2\alpha^2} \psi_n(y) = 0,$
```

其具有 Weber 方程（或谐振子的一维薛定谔方程）的形式。显式解给出：

```
$\xi_n(y) = D(-\frac{1}{2}, \sqrt{\alpha}}).
```

其中 `$D(\eta,y)$` 是圆柱函数。可以证明 [134] 解具有两种行为：指数增加和指数减少，当且仅当以下量子化成立时，我们具有指数减少：

```
$-\frac{1}{2} + \sqrt{\alpha\lambda_n} = n, n=0,1,\dots$
```

因此，考虑到 `$\alpha = 1/\sigma_{\alpha}^2$`，我们得到了谱量子化条件：

```
$\lambda_n = \sqrt{\frac{\pi}{2}}\frac{\sigma_{\alpha}^2}{2n+1}, n=0,1,\dots$ (A.40)
```

进一步，利用恒等式（当 `$n \in \mathbb{N}$` 时成立）：

```
$D(n,y) = 2^{-\frac{n}{2}}e^{-\frac{y^2}{2}}H_n(\frac{y}{\sqrt{2}}).
```

其中 `$H_n(y)$` 是米特多项式，我们有：

```
$\xi_n(y) = 2^{-\frac{n}{2}}e^{-\frac{(2n+1)y^2}{2\sigma_{\alpha}^2}}H_n(\frac{\sqrt{2n+1}}{\sigma_{\alpha}}).
```

或者参见图 A.4：

```
$\psi_n(y) = 2^{-\frac{n}{2}}e^{-\frac{(2n+1)y^2}{2\sigma_{\alpha}^2}}H_n(\frac{\sqrt{2n+1}}{\sigma_{\alpha}}).$ (A.41)
```

**备注 A.20** 等(A.41) 中的解也是任何满足以下谱的近似解：

```
$\omega(w) = const + O(\omega).$
```

![](img/24fc5dbf71f03b7f4f3dae6804e70aa2_105_0.png)

**图 A.4**

对于 `$\sigma_{\alpha}/\sqrt{\lambda}=C, C=10, \lambda=5, 20$`，解的小波行为。

92 附录

## A.6.2.2 向二维问题的扩展

假设模板 `$r$` 仅在 `$x$` 方向上移动。二维空间下的谱问题为：

```
$\lambda_n \xi_n(x, y) = - \int dx \ e^{-2\alpha(\eta^2+y^2)} \otimes (x-\eta, \gamma) \xi_n(\eta, \gamma) = 0,$
```

```
$\xi_n(x, y) = e^{+\alpha(x^2+y^2)} \psi_n(x, y)$.
```

应用算子 `$\nabla^2$` 并按照一维情况推导，我们得到：

```
$\lambda_n \nabla^2 \xi_n(x, y) + 2\pi \delta^{-1}(\omega_n^2 + \omega_y^2) \otimes (\omega_n, \omega_y) * (e^{-2\alpha(\eta^2+\gamma^2)}) \xi_n(\eta, y)|_{y=0} = 0$.
```

如果我们假设谱的形式为：

```
$t(\omega_x, \omega_y) = \frac{1}{\sqrt{\omega_x^2 + \omega_y^2}}$
```

则剩下的微分方程为：

```
$\nabla^2 \xi(x, y) + \frac{2\pi}{\lambda_n} e^{-2\alpha x} \xi_n(x, 0) = 0. (A.42)
```

在假设 `$\xi_n(x, y) = \xi_{1,n}(x)\xi_{2,n}(y)$` 下，我们可以立即看出，将解代入方程 (A.42），`$\xi_n(x, y)$` 是关于 `$y$` 独立的。因此，二维情况的解为：

```
$\psi_n(x, y) = 2^{-\frac{\alpha^2+2(n+1)x^2}{\alpha^2}} H_n(\frac{\sqrt{2(2n-1)}}{\sigma_\alpha}x), (A.43)
```

由此给出：

```
$\frac{\sigma_y}{\sigma_x} = \sqrt{2}(n+1).
```

## A.7 Gabor 小波

### A.7.1 从一维仿射群的不不变性论证推导

方程 (A.19) 中的等式一般情况下是不成立的。然而，如果我们认为变换群是尺度缩放和平移（见图 A.5a），这种情况显然是成立的。我们将详细讨论这种情况。

假设 `$G_0 = [0, a]$`。令：

```
$S = \{(T_{Ix},t) : x \in [0,a]\}, S_c = \{(T_{Ix},t) : x \in [c,a+c]\} (A.44)
```

![](img/24fc5dbf71f03b7f4f3dae6804e70aa2_107_0.png)

**图 A.5**

如果图像与模板之间点积的支撑包含在池化范围与群平移后(a)或缩放后(b)池化范围的交集内，则签名（signature）是不不变的。当频率条件 (b) 变为 (`$b'$`)：当缩放后的图像和模板的傅里叶支撑不相交时，它们的点积为零。

对于给定的 `$c$`，其中 `$T_x$` 是平移算子的酉表示，我们可以将 `$S_s, S_c$` 视为两个感受野对给定模板的简单表示集。令 `$S_0 = \{(T_{x,l} : x \in [0,a]\}$`（注：此处原文公式似乎有误，应为 `$T_x$`），使得 `$S_c \subset S_0$` 对于所有 `$c$` 均成立。我们假设 `$S_0, S_c$` 对于所有 `$c$` 都是闭区间。回想，如果一个双射函数在任何闭区间上是单调的，方程 (A.19) 中的积分差为零当且仅当 `$S = S_c$`。由于我们关注直到最大值 `$C$` 的所有 `$c$` 值，可以考虑：

```
$\langle T_x I, t\rangle = \langle T_a I, t\rangle, \forall x \in [0, c]. (A.45)$
```

该条件可以通过以下两种情况满足：(1) 两个积均为零，这是局部化条件；(2) `$T_a I = t$`，其中图像或模板是周期性的。在下一节中，我们将展示尺度变换的局部化条件如何意味着模板的特定形式。

94 附录

## A.7.2 来自不变性和海森堡原理的小波模板

在本节中，我们将 `$G_0$` 与仿射群的子集等同。特别是，我们分别研究尺度和平移（为了简单起见考虑一维）。假设所有图像 `$I$` 和模板 `$t$` 严格包含在平移或尺度的范围 `$P$` 内是有帮助的，因为范围之外未测量。我们考虑限制在 `$P$` 内的图像 `$I$`。对于平移，这意味着 `$I$` 的支撑在 `$P$` 内。对于缩放，`$g=f(sx)$` 和 `$I(x)=f(x/s)$`（其中 `$\sim$` 表示傅里叶变换），作为缩放范围 `$[s, M]$` 意味着频率 `$[\omega_m, \omega_M], [\omega_m', \omega_M']$`。因为定理 A.8 的不变性需要图像和模板的局部化，而尺度的不变性需要图像和模板带通。因此，假设图像在空间或频率上是局部化的。注意在我们的框架中，作为层次架构输入的图像是带通的。我们现在说明平移群和缩放群下定理 A.8 的结果。令 `$I, t \in L^2(\mathbb{R})$`, `$(\mathbb{R},+)$` 为平移的局部紧群，`$T_x : L^2(\mathbb{R}) \to L^2(\mathbb{R})$` 为平移算子的酉表示。例如，`$G_0 = [-b, b], b > 0$`，且假设 `$supp(t) \subseteq [-b, b]$`。进一步假设 `$supp(T_xI) \subseteq [-b, b]$`。我们有：

**推论 A.21** 空间域的局部化对于平移是充分的。对于固定的 `$t \in \mathcal{X}$`，我们有：
