

## Vega 章节 | A.6 305

对于欧式跌式期权，我们有：

$$\rho_p = \frac{\partial p}{\partial r}=\frac{\partial}{\partial r}\{E\exp(-r(T-t))(1-N_1(d_2)) - S\exp(-q(T-t))(1-N_1(d_2))\} = -E(T-t)(1-N_1(d_2)) - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial r} + S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial r} = -E(T-t)N_1(-d_2) - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial r} + S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial r}$$

代入 $n(d_2)$ 和 $\partial d_2/\partial r$，我们得到

$$\rho_p = -E(T-t)N_1(-d_2) \quad (A.5.2)$$

## A.6 VEGA

Vega 是期权价值随波动率变化的速率。对于看涨式期权，我们有：

$$\mathcal{V}_c = \frac{\partial c}{\partial \sigma} \quad (A.6.1) = \frac{S\exp(-q(T-t))N_1(d_1) - E\exp(-r(T-t))N_1(d_2)}{\partial \sigma} = S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial \sigma} - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial \sigma}$$

代入 $n(d_2)$ 和 $\partial d_1/\partial \sigma$，我们得到

$$\mathcal{V}_c = S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial \sigma} - E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial \sigma} = \sqrt{T-t}$$

因此，

$$\mathcal{V}_c = S\exp(-q(T-t))n(d_1)\sqrt{T-t} \quad (A.6.2)$$

对于欧式跌式期权，我们有：

$$\mathcal{V}_p = \frac{\partial p}{\partial \sigma} \quad (A.6.3) = \frac{\partial}{\partial \sigma}\{E\exp(-r(T-t))(1-N_1(d_2)) - S\exp(-q(T-t))(1-N_1(d_2))\} = -E(T-t)n(d_2)\frac{\partial d_2}{\partial \sigma} + S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial \sigma}$$

代入 $n(d_2)$ 和 $\partial d_1/\partial \sigma$，我们得到

$$\mathcal{V}_p = S\exp(-q(T-t))n(d_1)\sqrt{T-t} \quad (A.6.4)$$

这与看涨式期权相同。

## 附录 B 障碍期权积分

### B.1 下触出看涨期权

我们现在推导股息收益率为 $q$ 的欧式下触出期权价值价值 $c_{do}$ 公式，当执行价格 $E$ 满足 $E > B$ 时：

$$c_{do} = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{S\exp(X) - E\}f(X > B)dX \quad (B.1.1)$$

代入 $f(X > B)$，得到 $c_{do} = I_A + I_B$，其中：

$$I_A = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{S\exp(X) - E\}\exp\left(-\frac{X - (r - q - \sigma^2/2)\tau}{\sigma^2}\right)dX$$

$$I_B = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{S\exp(X) - E\}\exp\left(-\frac{X - (r - q - \sigma^2/2)\tau}{\sigma^2}\right)\exp\left(-\frac{2\log(B/S)(X - \log(B/S))}{\sigma^2}\right)dX$$

现在将 $I_A$ 与方程 (4.4.54) 对比，可以将 $I_A$ 识别为 $c$，即欧式看涨期权的价格：

$$I_A = S\exp(-q\tau)N_1(d_1) - E\exp(-r\tau)N_1(d_2) \quad (B.1.2)$$

其中：

$$d_1 = \frac{\log(S/E) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$$
$$d_2 = \frac{\log(S/E) + (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$$

现在考虑项 $I_B$，并令 $I_B = I_C + I_D$：

$$I_C = -\frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} S\exp(X)\exp\left(-\frac{X - (r - q - \sigma^2/2)\tau}{\sigma^2}\right)\exp\left(-\frac{2\log(B/S)(X - \log(B/S))}{\sigma^2}\right)dX$$

$$I_D = \frac{E \exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{-\infty}^{\infty} X\log(E/S)\exp\left(\frac{(X-(r-q-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)dX$$

我们将先考虑 $I_D$ 并对被积函数分解：

$$-\exp\left(\frac{(X-(r-q-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)\exp\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2}\right) = \exp\left(\frac{(X-(r-q-\sigma^2/2)\tau)^2 - 2\sigma^2\tau\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2}}{2\sigma^2\tau}\right) \dots$$

实际上，这意味着 $I_D$ 可以表示为：

$$I_D = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{-\infty}^{\infty} X\log(E/S)\exp\left(\frac{(X-(r-q-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)dX$$

令 $u = \frac{X-(r-q-\sigma^2/2)\tau-2\log(B/S)}{\sigma\sqrt{\tau}}$，得到：

$$I_D = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{k_3}^{\infty} \dots$$

