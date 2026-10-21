
上述抛物线型方程的解由以下公式给出

```
$f(t,x|x_0)=\frac{b}{a(e^{-bt}-1)}\left(\frac{e^{-bt}x}{x_0}\right)^{(h-a)/2a}\exp\left\{\frac{-b(x+x_0e^{bt})}{a(e^{bt}-1)}\right\}
\times I_{1-h/a}\left(\frac{2b}{a(1-e^{-bt})}(e^{-bt}x x_0)^{1/2}\right),\tag{109.6}$
```

其中 $I_k(x)$ 为第一类 $k$ 阶修正贝塞尔函数，定义为

```
$I_k(x)=\sum_{r=0}^{\infty}\frac{(x/2)^{2r+k}}{r!\Gamma(r+1+k)}.\tag{109.7}$
```

证明：见附录109A。

在进一步探讨之前，我们首先考虑 $\beta = 1$ 的特例，即 Cox 和 Ross (1976) 所考虑的模型。在此情形下，我们有

```
$dS = \mu(S,t)dt + \sigma(S,t)dZ,\tag{109.8}$
```

其中 $\sigma(S,t)=\sigma\sqrt{S}$。

现在进一步假设每股股票以连续股息流 $b(S,t)$ 支付股息，使得所需均值变为 $\mu(S,t)=rS-b(S,t)=rS-(aS+h)$，其中 $b(S,t)=aS+h$，$r$ 为无风险利率。则 $dS=[(r-a)S-h]dt+\sigma\sqrt{S}dz$，期权价格的微分方程变为

```
$\frac12\sigma^2 S\frac{\partial^2 P}{\partial S^2}+[(r-a)S-h]\frac{\partial P}{\partial S}+\frac{\partial P}{\partial t}=rP,\tag{109.9}$
```

对应的扩散过程（方程(109.8)）的柯尔莫哥洛夫正向方程为

```
$\frac12\frac{\partial^2}{\partial S_T^2}(\sigma^2 S_T P)+\frac{\partial}{\partial S_T}[(r-a)S-h]P]-\frac{\partial P}{\partial t}=0,\tag{109.10}$
```

该方程通过将 $\mu(x_t,t)=(r-a)S-h$ 代入 (109.4) 得到。

与方程(109.6)比较，我们设 $a=\sigma^2/2$，$x=S_T$，$x_0=S_t$，$b=r-\sigma^2/2$，$h=-h$，$t=\tau=(T-t)$。由此，我们得到如下转移关系

则 f(S_T|S_t, T > t) = f(Y_t|yt, T > t)|J|，其中 J = (2 - β)S^{1-β}。根据费勒引理，令 a = ½σ²(2 - β)²，b = (r - a)(2 - β)，h = ½σ²(β - 2)(1 - β)，x = 1/τ，x0 = 1，t = τ = (T - t)，我们有

f(S_T|S_t, T > t) = (2 - β)k^{1/(2-β)}(x z^{1-β})^{1/(2(2-β))}e^{-x z} I_{1/(2-β)}(2(x z)^{1/2})，

(109.18)

其中

k^* = 2(r - a) / [σ²(2 - β)[e^{(r-a)(2-β)τ} - 1]]，x = k^*S_t^{-β} e^{(r-a)(2-β)τ}，z = k^*S_T^{2-β}

Cox (1975) 得到了如下期权定价公式：

C = S_t e^{-rτ} ∑_{n=0}^∞ e^{-x} x^n G(n + 1 + 1/(2-β), k^* K^{2-β}) / Γ(n+1) - K e^{-rτ} ∑_{n=0}^∞ e^{-x} x^{n+1/(2-β)} G(n + 1, k^* K^{2-β}) / Γ(n + 1 + 1/(2-β))，

(109.19)

其中 G(m, v) = [Γ(m)]^{-1} ∫_v^∞ e^{-u} u^{m-1} du 为标准互补伽马分布函数。

上述公式的证明见 Chen 和 Lee (1993)。接下来，我们将详细介绍 Schröder (1989) 对期权定价公式的推导过程。由于期权定价公式以非中心卡方互补分布函数的形式表达，下一节将简要回顾非中心卡方分布。

## 109.3 非中心卡方分布回顾

如果 Z_1, …, Z_v 是标准正态随机变量，δ_1, …, δ_v 是常数，则

Y = ∑_{i=1}^v (Z_i + δ_i)^2

(109.20)

为具有 v 个自由度和非中心参数 λ = ∑_{j=1}^v δ_j² 的非中心卡方分布，记为 χ_v'²(λ)。当所有 δ_j = 0 时，Y 服从具有 v 个自由度的中心卡方分布，记为 χ_v²。χ_v'²(λ) 的累积分布

函数为

$$F(x; v, \lambda) = P(\chi_v'^2(\lambda) \le x)$$

$$= e^{-\lambda/2} \sum_{j=0}^{\infty} \frac{(\lambda/2)^j}{j! 2^{v/2} \Gamma(v/2 + j)} \times \int_0^x y^{v/2 + j -1} e^{-\frac{y}{2}} dy, \quad x > 0.$$

(109.21)

$F(x; v, \lambda)$ 的另一种表达式为

$$F(x; v, \lambda) = \sum_{j=0}^{\infty} \left( \frac{(\lambda/2)^j e^{-\lambda/2}}{j!} \right) P(\chi_{v+2j}^2 \le x).$$

(109.22)

χ_v'²(λ) 的互补分布函数为

$$Q(x; v, \lambda) = 1 - F(x; v, \lambda),$$

(109.23)

其中 $F(x; v, \lambda)$ 由方程 (109.21) 或方程 (109.22) 给出。

χ_v'²(λ) 的概率密度函数可以表示为中心卡方概率密度函数的混合：

$$P_{\chi_v'^2(\lambda)}(x) = e^{-\lambda/2} \sum_{j=0}^{\infty} \frac{(\frac{1}{2}\lambda)^j}{j!} p_{\chi_{v+2j}^2}(x) = \frac{e^{-(x+\lambda)/2}}{2^{v/2}} \sum_{j=0}^{\infty} \frac{x^{v/2 + j -1} \lambda^j}{\Gamma(v/2 + j) 2^{2j} j!}.$$

(109.24)

χ_v'²(λ) 的概率密度函数的另一种表达式为

$$P_{\chi_v'^2(\lambda)}(x) = \frac{1}{2} \left( \frac{x}{\lambda} \right)^{(v-2)/4} \exp\left\{ -\frac{1}{2}(\lambda + x) \right\} \times I_{(v-2)/2}(\sqrt{\lambda x}), \quad x > 0,$$

(109.25)

其中 $I_k$ 为第一类 $k$ 阶修正贝塞尔函数，定义为

$$I_k(z) = \left( \frac{1}{2} z \right)^k \sum_{j=0}^{\infty} \frac{(z^2/4)^j}{j! \Gamma(k + j + 1)}.$$

(109.26)

需要指出的是，对于整数 $k$，

$$I_k(z) = \frac{1}{\pi} \int_0^{\pi} e^{z \cos(k\theta)} \cos(k\theta) d\theta = I_{-k}(z).$$

(109.27)

非中心卡方分布关于 $n$ 和 $\lambda$ 具有可再现性。如果 $X_1, \dots, X_k$ 是独立随机变量，且 $X_t$ 服从 $\chi_{n_i}'^2(\lambda_i)$ 分布，则

$$Y = \sum_{i=1}^{k} X_i \sim \chi_{\sum_{i=1}^{k} n_i}'^2 \left( \sum_{i=1}^{k} \lambda_i \right).$$

(109.28)

## 109.4 期权定价模型的非中心卡方方法

参照 Schroder (1989)，给定 (109.18) 中的转移概率密度函数，CEV 模型下的期权定价公式为

```
C = E(max(0, S_T - K)) \qquad \tau = T - t
= e^{-r\tau} \int_K^\infty f(S_T|S_t, T > t)(S_T - K) dS_T
= e^{-r\tau} \int_K^\infty S_T f(S_T|S_t, T > t) dS_T
\quad - e^{-r\tau} K \int_K^\infty f(S_T|S_t, T > t) dS_T
= C_1 - C_2. \tag{109.29}
```

### 109.4.1 C1 和 C2 的详细推导

进行变量替换 w = k* S_T^{2-β}，我们有

```
dS_T = (2 - \beta)^{-1} k^{*-1/(2-\beta)} w^{(\beta-1)/(2-\beta)} dw
```

因此，令 y = k* K^{2-β}，我们有

```
C_1 = e^{-r\tau} \int_y^\infty e^{-x-w} (x/w)^{1/(4-2\beta)} \times I_{\frac{1}{2-\beta}} (2\sqrt{xw}) (w/k^*)^{1/(2-\beta)} dw
= e^{-r\tau} \int_y^\infty e^{-x-w} (x/w)^{1/(4-2\beta)} \times I_{\frac{1}{2-\beta}} (2\sqrt{xw}) (w/x)^{1/(2-\beta)} \times (x/k^*)^{1/(2-\beta)} dw
= e^{-r\tau} (x/k^*)^{1/(2-\beta)} \int_y^\infty e^{-x-w} (x/w)^{-1/(4-2\beta)} I_{\frac{1}{2-\beta}} (2\sqrt{xw}) dw
= e^{-r\tau} S_t e^{(r-a)\tau} \int_y^\infty e^{-x-w} (w/x)^{1/(4-2\beta)} I_{\frac{1}{2-\beta}} (2\sqrt{xw}) dw
= e^{-a\tau} S_t \int_y^\infty e^{-x-w} (w/x)^{1/(4-2\beta)} I_{\frac{1}{2-\beta}} (2\sqrt{xw}) dw, \tag{109.30}
```

以及

C₂ = K e^{-rτ} ∫_y^∞ (2 - β) k^{*1/(2-β)} (x w^{1-2β})^{1/(4-2β)} e^{-x-w} I_{1/(2-β)}(2√(x w)) w^{β-1} dw

= K e^{-rτ} ∫_y^∞ x^{1-2β} w^{(1-2β+2β-2)/(4-2β)} e^{-x-w} I_{1/(2-β)}(2√(x w)) dw

= K e^{-rτ} ∫_y^∞ e^{-x-w} (x/w)^{1/(4-β)} I_{1/(2-β)}(2√(x w)) dw. (109.31)

回顾非中心参数为 λ、自由度为 v 的非中心卡方分布的概率密度函数为

P_{χ_v²(λ)}(x) = ½ (x/λ)^{(v-2)/4} I_{(v-2)/2}(√(λ x)) e^{-(λ+x)/2} = P(x; v, λ)。

令 Q(x; v, λ) = ∫_x^∞ P_{χ_v²(λ)}(y) dy。则令 w' = 2w，x' = 2x，我们有

C₁ = S_t e^{-rτ} ∫_y^∞ e^{-(x+w)/2} (w/x)^{1/(4-2β)} I_{1/(2-β)}(2√(x w)) dw

= S_t e^{-rτ} ∫_y^∞ e^{-(x'+w')/2} (w'/x')^{1/(4-2β)} I_{1/(2-β)}(2√(x' w')) dw'

= S_t e^{-rτ} Q(2y; v, x')

= S_t e^{-rτ} Q(2y; 2 + 2/(2-β), 2x)， (109.32)

上式通过注意到 (v - 2)/2 = 1/(2 - β) 得出，即 v = 2 + 2/(2 - β)。类似地，令 w' = 2w，x' = 2x，并利用 I_n(z) = I_{-n}(z)，我们有

C₂ = K e^{-rτ} ∫_y^∞ e^{-x-w} (x/w)^{1/(4-2β)} I_{1/(2-β)}(2√(x w)) dw

= K e^{-rτ} ∫_y^∞ e^{-(x'+w')/2} (x'/w')^{1/(4-2β)} × I_{1/(2-β)}(2√(x' w')) dw'

= Q(2y; 2 - 2/(2-β), 2x)， (109.33)

上式通过注意到 $(v^* - 2)/2 = -1/(2 - \beta)$ 得出，即 $v^* = 2 - 2/(2 - \beta)$。因此，

$$C = S_t e^{-a\tau} Q\left(2y; 2 + \frac{2}{2 - \beta}, 2x\right) - K e^{-r\tau} Q\left(2y; 2 + \frac{2}{2 - \beta}, 2x\right). \tag{109.34}$$

需要指出的是，当 $\beta < 2$ 时，$2 - 2/(2 - \beta)$ 可能为负。因此需要进一步处理。利用单调收敛定理和分部积分，我们有

$$\int_y^{\infty} P(2y,2v,2k)\,dk = \int_y^{\infty} e^{-z - k}\left(\frac{z}{k}\right)^{v-1}\sqrt{kz}^{\,v-1} \times \sum_{n=0}^{\infty} \frac{(zk)^n}{n!\Gamma(n+v-1+1)}\,dk$$
$$= \int_y^{\infty} \frac{e^{-z}z^{n+v-1}}{\Gamma(n+v)} \int_y^{\infty} \frac{e^{-k}k^{n}}{\Gamma(n+1)}\,dk$$
$$= \sum_{n=0}^{\infty} g(n+v,z)G(n+1,y)$$
$$= \sum_{n=0}^{\infty} g(n+v-1,z)\sum_{i=1}^{\infty} g(i,y). \tag{109.35}$$

现在我们还有结果 $G(n,y)=\sum_{i=1}^{\infty} g(i,y)$，这可以通过观察以下推导得出：

$$G(n,y)=\int_y^{\infty} \frac{e^{-k}k^{n-1}}{\Gamma(n)}\,dk = -\int_y^{\infty} \frac{k^{n-1}}{\Gamma(n)}d e^{-k}$$
$$= \frac{y^{n-1}e^{-y}}{\Gamma(n)} + \int_y^{\infty} \frac{k^{n-2}e^{-k}}{\Gamma(n-1)}\,dk$$
$$= \sum_{i=1}^{n} \frac{y^{i-1}e^{-y}}{\Gamma(i)} = \sum_{i=1}^{n} g(i,y).$$

上述结果也可以表示为

$$G(m + 1, t) = G(m + 1, t) + G(m, t). \tag{109.36}$$

