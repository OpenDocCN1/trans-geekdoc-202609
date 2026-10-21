
with those of ours. 由于有限维分布决定了过程的规律，我们对 X 的定义是充分的。

根据假设 (41.15) 和定理 41.B.2，(41.5) 中的特征指数 ψ 给出为

ψ(ξ) = D ξ² + c ξ + λ ψ₁(ξ) − λ, ξ ∈ iR, (41.17)

其中 ψ₁(ξ) = ∫ e^{−ξ y} f(y) dy 的形式为

ψ₁(ξ) = p α₊ (ξ I − B₊)^{−1} b₊^T + q α₋ (−ξ I − B₋)^{−1} b₋^T. (41.18)

由于 (41.18) 的右端在 C 上关于 ξ 是有理函数（见定理 41.B.2），(41.17) 的右端实际上在 C 上是有理函数，在 C\iR 中只有有限个极点。因此，我们将 ψ 和 ψ₁ 在 C 上视为除 C\iR 中的极点外的解析函数。

设 P₀(ζ) 为首项系数为 1 的“最小”多项式，使得 P₀(ζ) 的零点与 ψ₁(ζ) 的极点重合，计入其重数。写

P₁(ξ) = P₀(ξ)(ψ(ξ) − r). (41.19)

则 ψ(ξ) − r 的零点与多项式 P₁(ξ) 的零点重合，计入其重数。

另一方面，过程 X 的无穷小生成元具有形式

Lh(x) = D h''(x) + c h'(x) + λ p α₊ T_{B₊}^+ h(x) b₊^T + λ q α₋ T_{B₋}^- h(x) b₋^T − λ h(x), (41.20)

对所有 h ∈ C₀²(R)。这里，对于非奇异次强度矩阵 B，矩阵值算子 T_B^± 在有界可测函数 h 的集合上定义为

## 命题 41.3.3: 假设跳跃密度 f 如 (41.15) 中所述，且 E[X₁] > 0，r = 0。则 φ 属于 C₀,b^∞(R₊₊)，且对 k ≥ 0，有递推公式

$$\phi^{(k+2)}(x) = -\frac{c}{D}\phi^{(k+1)}(x) + \frac{\lambda + r}{D}\phi^{k}(x) - \frac{\lambda}{D}E_{k}(x),\qquad (41.22)$$

其中

$$E_{k}(x)=p\alpha_{+}\left(B_{+}^{k}T_{B_{+}}^{+} \phi(x)+\sum_{j=0}^{k-1}B_{+}^{j}\phi^{(k-1-j)}(x)\right)b_{+}^{T}
\quad +q\alpha_{-}\left((-B_{-})^{k}T_{B_{-}}^{-}\phi(x)
\quad +\sum_{j=0}^{k-1}(-1)^{j+1}B_{-}^{j}\phi^{(k-j-1)}(x)\right)b_{-}^{T}\qquad (41.23)$$

这里 $\phi^{(0)}(x)=\phi(x)$。

**证明。** 请参阅附录 41A。

接下来，当跳跃分布的两侧均为相位型分布时，我们将积分-微分方程转化为常微分方程。在给出一般结果之前，我们通过直接计算处理一个简单情形。

## 示例 41.3.4: 我们考虑模型 (41.6)，其跳跃分布为 $dF(y)=\eta e^{-\eta y}1_{y>0}dy$，其中 $\eta>0$。则

$$\psi(\xi)=D\xi^{2}+c\xi+\lambda\frac{\eta}{\eta+\xi}-\lambda$$

且

$$Lh(x)=Dh''(x)+ch'(x)+\lambda\int_{0}^{\infty}h(x-y)\eta e^{-\eta y}dy-\lambda h(x).$$

另一方面，我们有 $P_0(\xi)=\eta+\xi$ 且

$P_1(\xi)=D\xi^2(\xi+\eta)+c\xi(\xi+\eta)+\lambda\eta-(\lambda+r)(\xi+\eta)$
$=D\xi^3+(D\eta+c)\xi^2+(c\eta-\lambda-r)\xi-r\eta.$

因此 φ 满足以 $P_1$ 为特征多项式的常微分方程。

## 定理 41.3.5: 设 $D_1$ 为具有特征多项式的微分算子

$P_1$ 由 (41.19) 给出。则 $D_1\Phi\equiv0$ 在 $R_{++}$ 上。

证明。设 $L_2=L_2(R)$ 为定义在 $R$ 上的平方可积函数空间，并设 $(f_1,f_2)=\int f_1(x)f_2(x)dx$。对于 $L_2$ 上的算子 $A$，记 $A^*$ 为其伴随算子（即对所有 $k$、$h$ 在 $L_2$ 中，$\langle Ak,h\rangle=\langle kA^*h\rangle$）。通过分部积分，我们有 $\langle k',h\rangle=-\langle k h'\rangle$，当 $k$ 或 $h$ 具有紧支集时。记 $Th(x)=\int h(x-y)f(y)dy$。通过变量替换和 Fubini 定理，我们有

$\langle Th,k\rangle=\int k(x)\int h(x-y)f(y)dydx=\int h(z)\int k(z-y)f(-y)dydz=\langle h,T^*k\rangle$

其中 $T^*k(x)\equiv\int k(x-y)f(-y)dy$。

设 $D_0$ 为具有特征多项式 $P_0$ 的微分算子，$\phi\in C_c^\infty(R_{++})$ 为一个检验函数。回想一下，根据定理 41.2.4，$(L-r)\phi\equiv0$ 在 $R_{++}$ 上。因此，我们有

$0=\langle D_0(L-r)\phi,\phi\rangle=\langle\phi(L^*-r)D_0^*\phi\rangle.\quad(41.24)$

这里 $L^*$ 给出为

$L^*h(x)=D h''(x)-c h'(x)+\lambda T^*h(x)-\lambda h(x).$

设 $L_D=L-r-\lambda T$。则 $(L^*-r)D_0^*\phi=\lambda T^*D_0^*\phi+L_D^*D_0^*\phi=\lambda T^*D_0^*\phi+(D_0L_D)^*\phi.\quad(41.25)$

记 $D_2$ 为对应于多项式 $P_2(\xi)=P_0(\xi)\psi(\xi)$ 的微分算子。我们通过证明 $T^*D_0^*\phi$ 和 $D_2^*\phi$ 均属于 $L_2\cap L_1$ 且具有相同的傅里叶变换，来证明 $T^*D_0^*\phi=D_2\phi$ 几乎处处成立。（这里 $L_1=L_1(R)$ 为 $R$ 上可积函数空间。）

首先，我们证明 $T^*D_0^*\phi$ 和 $D_2^*\phi$ 属于 $L_1\cap L_2$。由于 $\phi\in C_c^\infty(R_{++})$，我们得到 $D_2^*\phi\in L_1\cap L_2$。此外，$\int|T^*D_0^*\phi(x)|dx\le\iint|D_0^*\phi(x-y)|dx f(-y)dy\le\|D_0^*\phi\|_{L_1}\|f\|_{L_1}<\infty.$

因此 $T^* D_0^* \phi \in L_1$。我们证明 $T^* D_0^* \phi \in L_2$。由于 $D_0^* \phi \in C_c^\infty(R_{++})$ 且 $T^* h(x) = \int h(x-y)f(-y)dy$，只需证明对任意 $k \in C_c^\infty(R_{++})$，有 $T k \in L_2$。注意，根据定理 41.B.1，$f$ 的尾部呈指数衰减，因此 $\int f^2 dx < \infty$。设 $k \in C_c^\infty(R_{++})$，并记 $H$ 为 $k$ 的紧支集。由 Cauchy–Schwarz 不等式可得

$$\int [T k(x)]^2 dx = \int \left( \int k(x-y)f(y)dy \right)^2 dx = \int \left( \int_H k(Y)f(x-y)dy \right)^2 dx \le \int \left( \int k(y)^2 dy \right) \left( \int_H f(x-y)^2 dy \right) dx \le \|k\|_{L_2}^2 \|f\|_{L_2}^2 \int_H dx < \infty.$$

接下来，我们证明傅里叶变换 $F(T^* D_0^* \phi)$ 和 $F(D_2^* \phi)$ 相等，其中 $Fh(\theta) = \int e^{-2\pi i \theta x} h(x)dx$。回想 $\psi_1(\xi) = \int e^{-\xi y} f(y)dy$，并注意到 $F(D_0^* \phi)(\theta) = P_0(-2\pi i \theta)F(\phi)(\theta)$（见 Stein and Shakarchi (2005)，第 5.3 节）。由于 $T^* D_0^* \phi \in L_1 \cap L_2$，我们有，对所有 $\theta \in R$，

$$F(T^* D_0^* \phi)(\theta) = \int e^{-2\pi i \theta x} \left( \int D_0^* \phi(x-y)f(-y)dy \right) dx = \int \left( \int D_0^* \phi(x-y)e^{-2\pi i \theta (x-y)}dx \right) e^{-2\pi i \theta y} f(-y)dy = \psi_1(-2\pi i \theta)P_0(-2\pi i \theta)F(\phi)(\theta) = P_2(-2\pi i \theta)F(\phi)(\theta) = F(D_2^* \phi)(\theta).$$

由傅里叶反演公式，我们推得 $T^* D_0^* \phi = D_2^* \phi$ 几乎处处成立。

由 (41.25) 及 $T^* D_0^* \phi = D_2^* \phi$ 几乎处处成立，可得 $(L^* - r)D_0^* \phi = \lambda D_2^* \phi + (D_0 L_D)^* \phi = D_1^* \phi$ 几乎处处成立。因此，由 (3.11)，我们有 $$0 = \langle \Phi, (L^* - r)D_0^* \phi \rangle = \langle \Phi, D_0^* \phi \rangle = \langle D_1 \Phi, \phi \rangle.$$ 由于 $\phi \in C_c^\infty(R_{++})$ 是任意的，我们有 $D_1 \Phi = 0$ a.s. 在 $(0,\infty)$ 上。由于 $\Phi \in C_c^\infty(R_{++})$，$D_1 \Phi \equiv 0$ 在 $R_{++}$ 上。本证明完成。

从现在起假设 $r > 0$。我们用 $Z^r_{(-)} = (\rho_i^r)_{i=1}^S$ 表示 $\psi(\xi)-1$ 的零点（计入其重数）的集合，其实部严格为负。我们称 $Z^r_{(-)}$ 为可分离的，如果其成员互不相同。若无混淆，我们记 $Z_{(-)}$ 为 $Z^r_{(-)}$，$\rho_i$ 为 $\rho_i^r$。

作为定理 41.3.7 的一个应用，我们考虑 Hieberink 和 Rogers 对 Leland 模型的推广。我们首先回顾 Leland 模型的基本设定，然后以显式形式得到最优违约边界。此外，我们提供计算债券、公司和股权价值的程序。

## 示例 41.3.9 (最优资本结构)。

我们假设在风险中性测度 $Q$ 下，公司资产的价值由 $V_t = V e^{c t + \sigma W_t - Z_t}$ 给出。债务发行和息票支付的设定遵循 Leland and Toft (1996) 中的惯例。在时间区间 $(t, t + dt)$ 内，公司发行面值为 $a dt$ 的新债务，其到期期限分布为 $k(t) = m e^{-m t}$。由于指数到期期限分布，$(t, t + dt)$ 内到期的债务面值与新发行的债务面值相同。因此，所有未决债务的面值等于常数 $A = a \int_0^\infty e^{-m t} dt = a / m$。所有债券持有人在违约前按 $b$ 的利率收取息票。所有债务具有同等优先权，一旦违约发生，债券持有人在破产成本 $(1 - \beta) V_\tau$ 后获得剩余价值 $\beta V_\tau$。我们假设存在企业税率 $\delta$，且支付的息票可以抵扣税款。我们进一步假设违约发生在时间 $\tau = \inf\{t \ge 0; V_t \le L\}$，其中 $L$ 将在以后最优确定。如 Hieberink and Rogers (2002) 中所述，我们假设市场具有无风险利率 $r > 0$，且 $\mu > 0$ 为利润按比例分配给投资者的速率。则所有债务在时间 0 的总价值为

$$D(V, L) = \frac{bA + mA}{m + r} E_Q\left[1 - e^{-(m+r)\tau}\right] + \beta E_Q\left[V_\tau e^{-(m+r)\tau}\right] \qquad (41.29)$$

而公司的价值为

$$v(V, L) = V + \frac{bA\delta}{r} E_Q\left[1 - e^{-r\tau}\right] - (1 - \beta)E_Q\left[V_\tau e^{-r\tau}\right]. \qquad (41.30)$$

公司的股权价值由下式给出

$$S(V, L) = v(V, L) - D(V, L), \qquad (41.31)$$

（见 Hieberink and Rogers (2002) 或 备注 41.4.8）。通过施加光滑粘贴条件，我们计算使公司股权价值最大化的最优违约触发水平 $L^*$。

设 $X_t = \log \frac{V_t}{L}$ 且 $x = \log \frac{V}{L}$。注意 $\tau = \inf\{t \ge 0; V_t \le L\} = \inf\{t \ge 0; X_t \le 0\}$，并且在风险中性测度 $Q$ 下，$X$ 是
