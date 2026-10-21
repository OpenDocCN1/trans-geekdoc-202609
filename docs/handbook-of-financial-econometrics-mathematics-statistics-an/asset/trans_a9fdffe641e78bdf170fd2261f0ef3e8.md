
下一步，应用单调收敛定理，我们有

$$Q(z; v, k) = \int_z^{\infty} \frac{1}{2} \left(\frac{y}{k}\right)^{(v-2)/4} I_{\frac{v-2}{2}}(\sqrt{k y}) e^{-(k+y)/2} dy$$
$$= \int_z^{\infty} \frac{1}{2} \left(\frac{y}{k}\right)^{(v-2)/4} \left(\frac{1}{2}\sqrt{k y}\right)^{(v-2)/2} \times \sum_{n=0}^{\infty} \frac{(k y/4)^n}{n! \Gamma\left(\frac{v+2n}{2}\right)} e^{-(k+y)/2} dy$$
$$= \sum_{n=0}^{\infty} e^{-k/2} \frac{k^n (1/2)^n}{\Gamma(n+1)} \times \int_z^{\infty} \frac{(1/2)^{(v+2n)/2}}{(1/2)^{-(v+2n)/2} \Gamma\left(\frac{v+2n}{2}\right)} dy$$
$$= \sum_{n=0}^{\infty} e^{-k/2} \frac{(k/2)^n}{\Gamma(n+1)} \times \int_z^{\infty} \frac{(1/2)^{(v+2n)/2}}{\Gamma\left(\frac{v+2n}{2}\right)} e^{-y/2} y^{\frac{v+2n}{2}-1} dy$$
$$= \sum_{n=0}^{\infty} e^{-k/2} \frac{(k/2)^n}{\Gamma(n+1)} Q(z; v+2n, 0), \qquad (109.37)$$

其中

$$Q(x; v+2n, 0) = \int_z^{\infty} \frac{(1/2)^{(v+2n)/2}}{\Gamma\left(\frac{v+2n}{2}\right)} e^{-y/2} y^{\frac{v+2n}{2}-1} dy$$
$$= \int_{z/2}^{\infty} \frac{1}{\Gamma\left(\frac{v+2n}{2}\right)} e^{-y} y^{\frac{v+2n}{2}-1} dy$$
$$= G\left(n + v/2, z/2\right).$$

此外，根据式 (109.36) 中所示的 $G(\cdot, \cdot)$ 的性质，我们有

$$Q(z; v, k) = \sum_{n=0}^{\infty} g(n+1, k/2) G(n + v/2, z/2)$$
$$= \sum_{n=0}^{\infty} g(n, k/2) G\left(n + \frac{v-2}{2}, z/2\right). \qquad (109.38)$$

因此

$$Q(2z; 2v, 2k) = \sum_{n=0}^{\infty} g(n, k) G(n + v - 1, z).$$

再根据式 (109.36) 给出的 $G(\cdot,\cdot)$ 的性质，我们有

$Q(2z;2v,2k)=g(1,k)G(v,z)+g(2,k)G(v+1,z)+g(3,k)G(v+2,z)+\cdots$
$=g(1,k)[G(v-1,z)+g(v,z)]$
$+g(2,k)[G(v-1,z)+g(v+1,z)]+g(3,k)[G(v-1,z)$
$+g(v,z)+g(v+1,z)+g(v+2,z)]+\cdots$
$=[G(v-1,z)+g(v,z)]\sum_{n=1}^{\infty}g(n,k)+g(v+1,z)$
$\times\sum_{n=2}^{\infty}g(n,k)+g(v+2,z)\sum_{n=3}^{\infty}g(n,k)+\cdots$
$=G(v-1,z)+g(v,z)+g(v+1,z)[1-g(1,k)]$
$+g(v+2,z)[1-g(1,k)-g(2,k)]+\cdots$
$=G(v-1,z)+\sum_{n=0}^{\infty}g(v+n,z)-g(v+1,z)[g(1,k)]$
$-g(v+2,z)[g(1,k)+g(2,k)]+\cdots$
$=1-g(v+1,z)[g(1,k)]-g(v+2,z)[g(1,k)+g(2,k)]-\cdots.$

我们得出结论

$Q(2z;2v,2k)=1-\sum_{n=1}^{\infty}g(n+v,z)\sum_{i=1}^{n}g(i,k). \tag{109.39}$

由式 (109.35) 和式 (109.39) 可知

$\int_{y}^{\infty}P(2z;2v,2k)dk=1-Q(2z;2(v-1),2y). \tag{109.40}$

因此，我们可以将 $C_2$ 写为

$C_2=Ke^{-r\tau}\int_{y}^{\infty}P\left(2x;2+\frac{2}{2-\beta},2w\right)dw$

$=Ke^{-r\tau}Q\left(2y;2-\frac{2}{2-\beta},2x\right)$

$=Ke^{-r\tau}\left(1-Q\left(2x;\frac{2}{2-\beta},2y\right)\right). \tag{109.41}$

由式 (109.41) 可立即得到

$Q\left(2y;2-\frac{2}{2-\beta},2x\right)+Q\left(2x;\frac{2}{2-\beta},2y\right)=1, \tag{109.42}$

## 常弹性方差期权定价模型

意味着

Q(z;2n, k) + Q(k; 2 - 2n, z) = 1, (109.43)

其中 $Q(k;2 - 2n, z)$ 的自由度 $2 - 2n$ 可以是非整数。

由式 (109.42)，我们可以得到自由度为 $2 - 2/(2-β)$、非中心参数为 $2x$ 的非中心卡方 $Q(2y; 2 - 2/(2-β),2x)$ 可由自由度为 $2/(2 - β)$、非中心参数为 $2y$ 的另一非中心卡方分布 $1 - Q(2x; 2/(2 - β),2y)$ 表示。第 109.3 节中非中心卡方分布的标准定义具有整数自由度。如果自由度不是整数，我们可以使用式 (109.43) 将原始非中心卡方分布转化为另一个非中心卡方分布。因此，我们得到了以补非中心卡方分布函数 $Q(z;u,k)$ 表示的 CEV 模型的期权定价公式，该公式对模型要求的任何小于 2 的 β 值均有效。

将式 (109.41) 代入式 (109.34)，我们得到

C = S_t e^{-aτ} Q (2y; 2 + 2/(2 - β),2x) - K e^{-rτ} (1 - Q (2x; 2/(2 - β),2y)), (109.44)

其中 $y = k^* K^{2-β}$，$x = k^* S_t^{2-β} e^{(r-a)(2-β)τ}$，$k^* = 2(r - a)/(σ²(2 - β)) (e^{(r-a)(2-β)τ} - 1)$，且 $a$ 为连续比例股息率。β > 2 时对应的 CEV 期权定价公式可通过类似方式推导。

当 β > 2 时（参见 Emanuel and Macbeth 1982, Chen and Lee 1993），看涨期权公式如下：

C = S_t e^{-aτ} Q (2x; 2/(β-2),2y) - K e^{-rτ} (1 - Q (2y; 2/(β-2),2x)). (109.45)

我们注意到，由式 (109.34) 给出的期权定价公式 C 的评估，特别是 $C_2$，我们有

2k* S_T^{2-β} ~ χ²_v (λ), (109.46)

其中

v = 2 - 2/(2 - β),

λ = 2k* S_t^{2-β} e^{(r-a)(2-β)τ},

且 $a$ 为连续比例股息率。

因此，如式 (109.44) 所示的 CEV 模型的期权定价公式可直接由收益函数

max(S_T - K, 0) = { S_T - K, if S_T > K, 0, otherwise, }

(109.47)

通过取式 (109.47) 的期望得到，其中 $S_T$ 的分布由式 (109.46) 给出。

在结束本小节之前，我们考虑当 β 趋于 2 时，非中心卡方分布将趋近于对数正态。因为当 λ 或 v 中的任一个趋于无穷时，标准化变量

χ²_v(λ) - (v + λ) / √(2(v + 2λ))

趋于 $N(0,1)$，当 $v → ∞$ 或 $\lambda → ∞$ 时。利用 $(x^a - 1)/a$ 当 $a → ∞$ 时趋于 $\ln x$ 这一事实，可以验证

χ²_v(λ) - (v + λ) / √(2(v + 2λ)) = 2k* S_T^{2-β} - (v + λ) / √(2(v + 2λ)) = [2r* S_T^{2-β} - (1 - β)σ²(e^{r*τ(2-β)} - 1) - 2r* S_t^{2-β} e^{r*τ(2-β)} ] / σ²(e^{r*τ(2-β)} - 1) × √[ σ²(e^{r*τ(2-β)} - 1)/(2 - β) / ((1 - β)σ²(e^{r*τ(2-β)} - 1) + 4r* S_t^{2-β} e^{r*τ(2-β)}) ] = ln S_T - [ln S_t + (r* - σ²/2)τ ] / σ√τ ,

其中 $r^* = r - a$。因此，

ln S_T ~ N ( ln S_t + (r - a - σ²/2)τ , σ²τ ),

(109.48)

当 $\beta → 2^-$ 时。类似地，式 (109.48) 在 $\beta → 2^+$ 时也成立。由式 (109.45)，我们有 $2k^* S_T^{2-β} ~ χ²_v(λ)$，其中若 $\beta > 2$ 则 $v = 2 + 2/(β - 2)$。因此，我们澄清了式 (109.48) 的结果。

## 109.5 一些计算考虑

如 Schröder (1989) 所指出的，式 (109.39) 允许在 $z$ 和 $k$ 不大时使用以下迭代算法来计算无穷和。首先初始化以下四个变量（取 $n = 1$）

gA = \frac{e^{-z} z^{v}}{\Gamma(1+v)} = g(1+v, z),

gB = e^{-k} = g(1,k),

Sg = gB,

R = 1 - (gA)(Sg).

然后从 $n = 2$ 开始重复以下循环，并在每次迭代后将 $n$ 增加一。当对和的贡献 $R$ 下降且非常小时，循环终止。

gA = gA\left(\frac{z}{n+v-1}\right) = g(n+v, z),

gB = gB\left(\frac{k}{n-1}\right) = g(n,k),

Sg = Sg + gB = g(1,k) + g(n,k),

R = R - (gA)(Sg) = the nth partial sum.

在每次迭代中，$gA$ 等于 $g(n+v,z)$，$gB$ 等于 $g(n,k)$，而 $Sg$ 等于 $g(1,k)+⋯+g(n,k)$。计算很容易完成。

关于近似，Sankaran (1963) 表明 $(\chi'^2_v/(v+k))^h$ 的分布近似为正态，其期望值为 $\mu = 1 + h(h−1)P − h(2−h)mP^2/2$，方差为 $\sigma^2 = h^2P(1+mP)$，其中 $h = 1 − 2/3(v+k)(v+3k)(v+2k)^{-2}$，$P = (v+2k)/(v+k)^2$ 且 $m = (h−1)(1−3h)$。利用该近似，我们近似有

Q(z,v,k) = Pr(χ′2 > z)

= Pr\left(\frac{χ′2}{v+k} > \frac{z}{v+k}\right)

= Pr\left(\left(\frac{χ′2}{v+k}\right)^h > \left(\frac{z}{v+k}\right)^h\right)

= Φ\left(\frac{1 - hP[1 - h + 0.5(2 - h)mP] - \left(\frac{z}{v+k}\right)^h}{h\sqrt{2P(1+mP)}}\right).

## 109.6 结论

CEV 模型下的期权定价公式相当复杂，因为它涉及非中心卡方分布 $Q(z, v, k)$ 的累积分布函数。本章给出了一些计算考虑，有助于计算 CEV 期权定价公式。因此，实际计算不会是一个困难的问题。

## 致谢

我们衷心感谢编辑和一位匿名审稿人对本文提出的富有洞见的评论和建议。本研究部分得到 NSC 资助项目 95-2118-M-005-003 的支持。

## 参考文献

Brandt, M.W. and Kang, Q. (2004). On the Relationship Between the Conditional Mean and Volatility of Stock Returns: A Latent VAR Approach. Journal of Financial Economics 72, 217–257.
Campbell, J. (1987). Stock Returns and the Term Structure. Journal of Financial Economics 18, 373–399.
Chen, R.R. and Lee, C.F. (1993). A Constant Elasticity of Variance (CEV) Family of Stock Price Distributions in Option Pricing: Review and Integration. Journal of Financial Studies 1, 29–51.
Cox, J. (1975). Notes on option pricing I : constant elasticity of variance diffusion, Unpublished Note, Stanford University, Graduate School of Business. Also, Journal of Portfolio Management (1996) 23, 5–17.
Cox, J. and Ross, S.A. (1976). The Valuation of Options for Alternative Stochastic Processes. Journal of Financial Economics 3, 145–166.
Emanuel, D. and MacBeth, J. (1982). Further Results on the Constant Elasticity of Variance Call Option Pricing Formula. Journal of Financial and Quantitative Analysis 17, 533–554.
Feller, W. (1951). Two Singular Diffusion Problems. Annals of Mathematics 54, 173–182.
Glosten, L., Jagannathan, R. and Runkle, D. (1993). On the Relation Between the Expected Value and the Volatility of the Nominal Excess Returns on Stocks. Journal of Finance 48, 1779–1802.
Sankaran, M. (1963). Approximations to the Non-central Chi-square Distribution. Biometrika 50, 199–204.
Schröder, M. (1989). Computing the Constant Elasticity of Variance Option Pricing Formula. Journal of Finance 44, 211–219.
