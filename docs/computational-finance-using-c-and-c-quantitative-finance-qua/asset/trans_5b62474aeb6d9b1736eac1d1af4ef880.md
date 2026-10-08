

# 使用 C 和 C# 进行计算金融学

```
$$d_2 = \log(S/E) + (r-q-\sigma^2/2)(T-t) = d_1 - \sigma\sqrt{T-t} \quad (A.1.5)$$
```

我们有：

$$
$$\frac{\partial d_2}{\partial S} = \frac{\partial d_1}{\partial S}\frac{1}{S\sqrt{T-t}} \quad (A.1.6)$$
```

$$
$$\frac{\partial d_2}{\partial \sigma} = \frac{\partial d_1}{\partial \sigma}-\sqrt{T-t} \quad (A.1.7)$$
```

$$
$$\frac{\partial d_1}{\partial r} = \frac{\partial d_2}{\partial r}\frac{\sqrt{T-t}}{\sigma} \quad (A.1.8)$$
```

$$
$$\frac{\partial d_1}{\partial t} = \frac{\partial d_1}{\partial t}\frac{-2(T-t)}{\sigma} \quad (A.1.9)$$
```

同时：

$$
$$n(d_2) = \frac{1}{\sqrt{2\pi}}exp(-\frac{d_2^2}{2})$$
$$= \frac{1}{\sqrt{2\pi}}exp(-\sigma d_1\sqrt{T-t}-\frac{\sigma^2(T-t)}{2})$$
$$= n(d_1)exp(-\log(\frac{S}{E})+(r-q+\frac{\sigma^2}{2})(T-t)-2{\frac{\sigma^2(T-t)}{2}))$$
$$

所以

$$
$$n(d_2) = \frac{S}{E}exp(r(T-t))exp(-q(T-t)) \quad (A.1.10)$$
$$

我们注意到：

$$
$$\frac{\partial N_1(d_1)}{\partial S} = \frac{\partial N_1(d_1)}{\partial d_1}\frac{\partial d_1}{\partial S} = n(d_1)\frac{1}{S\sqrt{T-t}}$$
$$

这种技术将用于计算希腊字母（Greeks）。

# A.2 Gamma

Gamma 定义为期权价值相对于标的股票价格的二阶导数。这意味着（参见 A.3 节）它是 Delta 随标的股票价格的变化率。

对于欧式看涨期权，gamma 的值为：

$$
$$\Gamma_c = \frac{\partial^2 \Delta_c}{\partial S^2} = \frac{\partial \Delta_c}{\partial S}\frac{\partial \Delta_c}{\partial S}\{N_1(d_1)exp(-q(T-t))\}$
$$

其中 $\Delta_c$ 的值在 A.3 节给出。所以

$$
$$\Gamma_c = exp(-q(T-t))\frac{\partial d_1}{\partial S} = exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial S}$$
$$

# 附录 A：标准欧式期权的希腊字母

因此：

$$
$\Gamma_c = \frac{n(d_1)}{S\sqrt{T-t}} \exp(-q(T-t)) \quad (A.2.1)$
$$

欧式看跌期权的 gamma 值可以类似地计算：

$$
$\Gamma_p = \frac{\partial^2 p}{\partial S^2} = \frac{\partial \Delta_p}{\partial S} = \frac{\partial}{\partial S}\{(N_1(d_1)-1) \exp(-q(T-t))\}$
$$

这里我们使用了 A.3 节中推出的 $\Delta_p$ 的值。因此：

$$
$\Gamma_p = \exp(-q(T-t))\frac{\partial(N_1(d_1)-1)}{\partial S} = \exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial S}$
$$

所以

$$
$\Gamma_p = \Gamma_c = \frac{n(d_1)}{S\sqrt{T-t}} \exp(-q(T-t)) \quad (A.2.2)$
$$

看跌和看涨期权的 gamma 值是相同的。

# A.3 Delta

Delta 定义为期权价值随标的股票价格的变化率。

对于欧式看涨期权：

$$
$\Delta_c = \frac{\partial c}{\partial S} = \frac{\partial}{\partial S}\{S\exp(-q(T-t))N_1(d_1)-E \exp(-r(T-t))N_1(d_2)\}$
$$

所以

$$
$\Delta_c = \exp(-q(T-t))\{N_1(d_1)+Sn(d_1)\}\frac{\partial d_1}{\partial S} - E \exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial S} \quad (A.3.1)$
$$

代入 $n(d_2)$ 和 $\frac{\partial d_2}{\partial S}$，我们得到：

$$
$\Delta_c = \exp(-q(T-t))N_1(d_1) \quad (A.3.2)$
$$

以相同的方式，欧式看跌期权有：

$$
$\Delta_p = \frac{\partial p}{\partial S} = \frac{\partial}{\partial S}\{E \exp(-r(T-t))(1-N_1(d_2))-S \exp(-q(T-t))(1-N_1(d_1))\}$
$$

所以

$$
$\Delta_p = -E \exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial S} - \exp(-q(T-t))\{(1-N_1(d_1))+Sn(d_1)\}\frac{\partial d_1}{\partial S} \quad (A.3.3)$
$$

代入 $n(d_2)$ 和 $\frac{\partial d_2}{\partial t}$，我们得到：

# 附录 A：标准欧式期权的希腊字母

$$
$$\Theta_p=rE\exp(-r(T-t))N_1(-d_2)-qS\exp(-q(T-t))N_1(-d_2)$$
$$-E\exp(-r(T-t))\times\exp(-q(T-t))n(d_1)S\left\{\frac{\partial d_1}{\partial t}+\frac{\sigma}{2(T-t)}\right\}$$
$$

所以

$$
$$\Theta_p=-\exp(-q(T-t))\left\{SN_1(-d_1)+\frac{Sn(d_1)\sigma}{2(T-t)}\right\}$$
$$-rE\exp(-r(T-t))N_1(-d_2) \quad (A.4.2)$$


# A.5 Rho

Rho 是期权价值随利率的变化率。

对于看涨期权，有：

$$
$$\rho_c=\frac{\partial c}{\partial r}=\frac{\partial}{\partial r}\left\{S\exp(-q(T-t))N_1(d_1)-E\exp(-r(T-t))N_1(d_2)\right\}$$
$$+S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial r}+E(T-t)N_1(d_2)-E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial r}$$
$$

代入 $n(d_2)$ 和 $\frac{\partial d_2}{\partial r}$，得到：

$$
$$\rho_c=E(T-t)N_1(d_2) \quad (A.5.1)$$
$$

对于看跌期权，有：

$$
$$\rho_p=\frac{\partial p}{\partial r}$$
$$-\frac{\partial}{\partial r}\left\{E\exp(-r(T-t))(1-N_1(d_2))-S\exp(-q(T-t))(1-N_1(d_1))\right\}$$
$$+E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial r}+S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial r}$$
$$（此处逻辑推导）

代入 $n(d_2)$ 和 $\frac{\partial d_2}{\partial r}$，得到：

$$
$$\rho_p=-E(T-t)N_1(d_2) \quad (A.5.2)$$
$$

# A.6 Vega

Vega 是期权价值随波动率的变化率。对于看涨期权，有：

$$
$$\mathcal{V}_c=\frac{\partial c}{\partial\sigma}=\frac{\partial}{\partial\sigma}\left\{S\exp(-q(T-t))N_1(d_1)-E\exp(-r(T-t))N_1(d_2)\right\}$$
$$=S\exp(-q(T-t))n(d_1)\frac{\partial d_1}{\partial \sigma}-E\exp(-r(T-t))n(d_2)\frac{\partial d_2}{\partial \sigma} \quad (A.6.1)$$
$$

代入 $n(d_2)$ 和 $\frac{\partial d_2}{\partial \sigma}$，得到：

$$
$$\mathcal{V}_c=S\exp(-q(T-t))n(d_1)\left(\frac{\partial d_1}{\partial \sigma}-\sqrt{T-t}\right)$$
$$

因此

$$
$$\mathcal{V}_c=S\exp(-q(T-t))n(d_1)\sqrt{T-t} \quad (A.6.2)$$
$$

对于看跌期权，有：

代入 $n(d_2)$ 和 $\frac{\partial d_2}{\partial \sigma}$，得到：

$$
$$\mathcal{V}_p=S\exp(-q(T-t))n(d_1)\sqrt{T-t} \quad (A.6.3)$$
$$

这与看涨期权相同。

# 附录 B：障碍期权积分

# B.1 下触碰失效看涨期权

现在我们为股息收益率为 $q$ 且执行价 $E$ 满足 $E > B$ 的欧式下触碰期权价值 $c_{do}$ 推导公式：

$$
$c_{do} = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}f(X > B)dX \quad (B.1.1)$$
$$

代入 $f(X > B)$，得到 $c_{do} = I_A + I_B$，其中：

$$
$I_A = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}$
\times \exp\left(\{X - (r-q-\sigma^2/2)\tau)^2 / 2\sigma^2\tau\right)dX
$$

以及

$$
$I_B = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}$
\times \exp\left(\{X - (r-q-\sigma^2/2)\tau)^2 / 2\sigma^2\tau\right)\
\times \exp\left(\{2\log(B/S)(X - \log(B/S)) / \sigma^2\tau\right)dX
$$

现在将 $I_A$ 与公式 (4.454) 比较，我们可以将 $I_A$ 识别为 $c$，即欧式看涨期权的价格。即：

$$
$I_A = S\exp(-q\tau)N_1(d_1) - E\exp(-r\tau)N_1(d_2) \quad (B.1.2)$
$$

其中：

$$
$d_1 = \frac{\log(S/E)+(r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
$$
$d_2 = d_1 - \sigma\sqrt{\tau}$
$$

我们现在考虑 $I_B$，令 $I_B = I_C + I_D$，其中：

$$
$I_C = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}\exp\left(\{X - (r-q-\sigma^2/2)\tau)^2 / 2\sigma^2\tau\right)dX
$$

以及

$$
$I_D = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}\exp\left(\{X - (r-q-\sigma^2/2)\tau)^2 / 2\sigma^2\tau\right)\exp\left(\{2\log(B/S)(X - \log(B/S)) / \sigma^2\tau\right)dX
$$

这是评估障碍期权积分的标准方法。

