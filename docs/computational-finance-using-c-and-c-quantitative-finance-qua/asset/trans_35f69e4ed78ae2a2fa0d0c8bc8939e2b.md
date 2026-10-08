
## 附录 B：障碍期权积分

令 $d_3=-k_3$，我们有：

```
$d_3 = \frac{\log(B^2/SE) + (r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

以及

```
$I_D = \left(\frac{B}{S}\right)^{2(r-\sigma^2-1)} E\exp(-r\tau)N_1(d_3) \quad (B.1.5)$
```

现在考虑项：

```
$I_C = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{X=\log(E/S)}^{\infty} \exp(X) \exp(\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) \times \exp(\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right))dX$
```

现在我们得到

```
$\exp(X)\exp(\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)\exp(\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right)) = \exp(-\{{(X-(r-\sigma^2/2)\tau)^2-2\sigma^2\tau X\} -4\log(B/S)X+4(\log(B/S))^2)/(2\sigma^2\tau)) = \exp(((\sigma^2)\tau+2(r-q-\sigma^2/2)\tau^2\sigma^2 +4(r-q-\sigma^2/2)\log(B/S)+4\sigma^2\log(B/S))/(2\sigma^2\tau) \times \exp(-\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/2\sigma^2\tau)) = \exp((r-q)\tau)\exp(\left(\frac{2(r-q)}{\sigma^2}+1\right)\log(\left(\frac{B}{S}\right)) \times \exp(-\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/2\sigma^2\tau)) = \exp((r-q)\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1} \times \exp(-\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/2\sigma^2\tau))$
```

所以我们：

```
$I_C = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1} \frac{S\exp(-q\tau)}{\sigma\sqrt{2\pi}} \times \int_{X=\log(E/S)}^{\infty} \exp(-\\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/(2\sigma^2\tau)^{-1})dX$
```

## 令

$u = \frac{X - (r - q - \sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}}$

我们有 $dX = \sigma\sqrt{\tau} du$ 和

```
$I_C = -S\exp(-q\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1}N_1(-k_4) \quad (B.1.6)$
```

其中

```
$k_4 = \frac{\log(E/S) - (r - q - \sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}} = \frac{\log(ES/B^2) - (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

或者令 $d_4 = -k_4$，我们有

```
$d_4 = \frac{\log(B^2/ES) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

```
$I_C = -S\exp(-q\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1}N_1(d_4) \quad (B.1.7)$
```

下碰期（down out option）的价格为：

$c_{do} = I_A + I_C$

由于 $c_{do} + c_{di} = c$，其中 $c$ 是普通看权的价格，$c_{di}$ 是下碰看权的价格，我们可以写成：

$c_{do} = c - c_{di}$

其中

$c_{di} = S\exp(-q\tau)N_1(d_3)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2}$

## B.2 上碰看权（up out call）

我们现在为股息收益率为 $q$ 的欧式上碰看权推导公式，当执行价 $E$ 满足 $B > E$ 时。

```
$c_{uo} = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}}\int_{E}^{B}\{\exp(X)-E\}f(X < B)dX \quad (B.2.1)$
```

## 附录 B：障碍期权积分

替换 $f(X < B)$ 得 $c_{uo} = I_A + I_B$，其中：

```
$I_A = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\log(B/S)} \{S\exp(X) - E \times \exp\left(\frac{(X-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)\}dX$
```

以及

```
$I_B = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \times \int_{\log(E/S)}^{\log(B/S)} \{S\exp(X) - E\}\exp\left(\frac{(X-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) \times \exp\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right)dX$
```

令 $I = I_1 + I_2$，其中

```
$I_1 = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\log(B/S)} \exp(X)\exp\left(\frac{(X-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)dX$
```

以及

```
$I_2 = \frac{-E\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\log(B/S)} \exp\left(\frac{(X-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)dX$
```

根据我们在第 4 章对 Black-Scholes 公式的推导，我们有：

```
$I_1 = \frac{S\exp(-q\tau)}{\sigma\sqrt{2\pi}} \int_{k_1}^{k_2} \exp\left(-\frac{u^2}{2}\right)du = S\exp(-q\tau)\{N_1(k_2)-N_1(k_1)\}$
```

其中

```
$k_1 = \frac{\log(E/S)-(r-q+\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

以及

```
$k_2 = \frac{\log(B/S)-(r-q+\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

```
$I_2 = \frac{-E\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{k_3}^{k_4} \exp\left(-\frac{u^2}{2}\right)du = -E\exp(-r\tau)\{N_1(k_4)-N_1(k_3)\}$
```

其中

```
$k_3 = \frac{\log(E/S)-(r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

以及

```
$k_4 = \frac{\log(B/S)-(r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

因此，

$I_A = S \exp(-q\tau)N_1(k_2) - N_1(k_1) - E \exp(-r\tau)N_1(k_4)$

由于 $N_1(-x) = 1 - N_1(x)$，我们有 $N_1(k_2) - N_1(k_1) = N_1(d_2) - N_1(d_1)$，所以 $I_A = S \exp(-q\tau)N_1(d_2) - E \exp(-r\tau)N_1(d_3)$

与 B.1 节的方法相似，我们有：

```
$I_D = \frac{B^{2(r-q)/\sigma^2/2}}{S} \frac{E\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\log(B/S)} \exp\left(\frac{(X-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)dX
```

令 $u = \frac{X - (r - q - \sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}}$，我们有 $dX = \sigma\sqrt{\tau} du$ 和

```
$I_D = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2/2} E \exp(-r\tau) \int_{u=k_5}^{k_6} \exp\left(-\frac{u^2}{2}\right) du \quad (B.2.3)$
```

其中

```
$k_5 = \frac{\log(E/S) - (r-q-\sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}} = \frac{\log(ES/B^2) - (r-q+\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

以及

```
$k_6 = \frac{\log(B/S) - (r-q-\sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}} = \frac{\log(S/B) - (r-q+\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

所以

$I_D = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2-1} \exp(-r\tau)\{N_1(k_6) - N_1(k_5)\}$

这可以重新表示为：

```
$I_D = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2} \exp(-r\tau)\{N_1(d_5) - N_1(d_6)\} \quad (B.2.4)$
```
