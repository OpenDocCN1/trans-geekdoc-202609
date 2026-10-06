

# 第186 页 | 6 多种资产期权

当 $x_1$ 和 $x_2$ 的相关系数为 $\rho$ 时，$x_1$ 和 $x_2$ 满足 $x_1 \leq a$ 和 $x_2 \leq b$ —— 该值使用 $cum\norm2$ 程序进行计算。其他符号定义如下：

```
$\sigma_0^2 = \sigma_1^2 - 2\rho\sigma_1\sigma_2 + \sigma_2^2$,
$d_1(S_i, E, \sigma_2) = \frac{\log(S_i/E) + (r + \sigma_2^2)/2)\tau}{\sigma_i\sqrt{\tau}}, i=1, 2$，
$d_2(S_i, E, \sigma_2) = \frac{\log(S_i/E) + (r - \sigma_2^2)/2)\tau}{\sigma_i\sqrt{\tau}}, i=1, 2$，
$d_1'(S_i, S_j, \sigma_2^2) = \frac{\log(S_i/S_j) + (\sigma_j^2)/2)\tau}{\sigma_*\sqrt{\tau}}, for $i=1, j=2$ or $i=2, j=1$，
$d\rho_1 = \frac{\sigma_1 - \rho\sigma_2}{\sigma_*}, \rho_2 = \frac{\sigma_2 - \rho\sigma_1}{\sigma_*}$
```

并且

> $c_{max}(S_1, S_2, \tau) + c_{min}(S_1, S_2, \tau) = c(S_1, E, \tau) + c(S_1, S_2, E),$ (6.5.7)

也可以证明，其中 $c(S, E, \tau)$ 是标准欧式看涨期权的价值。
我们现在推导出相应的欧式看跌期权的价值表达式。

# 资产最小值的看跌期权

已知两种资产最小值的欧式看跌期权价格 $p_{min}(S_1, S_2, E)$

> $p_{min}(S_1, S_2, E) = E\exp(-r\tau) - c_{min}(S_1, S_2, 0, \tau) + c_{min}(S_1, S_2, E, \tau),$ (6.5.8)

其中符号的含义之前已经定义。该结果可以通过考虑以下两种投资来证明：

- 组合 A：
买入一个关于 $S_1$ 和 $S_2$ 最小值的期权，执行价格为 $E$。

- 组合 B：
买入一个在到期时支付 $E$ 的贴现债券。卖出（即建立）一个关于 $S_1$ 和 $S_2$ 最小值的执行价格为零的期权。买入一个关于 $S_1$ 和 $S_2$ 最小值的执行价格为 $E$ 的期权。

我们现在考虑这些组合在期权到期日 $\tau$ 的价值。

如果 $min(S, S_2) \geq E$：

- 组合 A：支付 0。
组合 B：支付 $E - min(S_1, S_2) + min(S_1, S_2) - E = 0$。

如果 $min(S_1, S_2) < E$：

- 组合 A：支付 $E - S_1$。
组合 B：支付 $E - S_1 + 0 = E - S_1$。

如果 $min(S_1, S_2) = S_2 < E$：
组合 A：支付 $E - S_2$。
组合 B：支付 $E - S_2 + 0 = E - S_2$。

因此我们已经证明，在所有可能的情况下，组合 A 的价值与组合 B 相同。这意味着方程 (6.5.8) 是正确的。

# 资产最大值的看跌期权

现在将证明两种资产最大值的欧式看跌期权价格 $p_{max}(S_1, S_2, E, \tau)$ 为：

```
$p_{max}(S_1, S_2, E, \tau) = E \exp(-r\tau) - c_{max}(S_1, S_2, \tau) + c_{max}(S_1, S_2, E, \tau), \quad (6.5.9)$
```

其中，如前，符号的含义已经定义。该结果可以通过考虑以下两种投资来证明：

- 组合 A：
买入一个关于 $S_1$ 和 $S_2$ 最大值的期权，执行价格为 $E$。

- 组合 B：
买入一个在到期时支付 $E$ 的贴现债券。卖出（即建立）一个关于 $S_1$ 和 $S_2$ 最大值的执行价格为零的期权。买入一个关于 $S_1$ 和 $S_2$ 最大值的执行价格为 $E$ 的期权。

我们现在考虑这些组合在期权到期日的价值：

如果 $max(S_1, S_2) \geq E$：

- 组合 A：支付 0。
组合 B：支付 $-max(S_1, S_2) + max(S_1, S_2) - E = 0$。

如果 $max(S_1, S_2) < E$：

- 组合 A：支付 $E - S_1$。
组合 B：支付 $E - S_1 + 0 = E - S_1$。

如果 $max(S_1, S_2) = S_2 < E$：
（注：此处原文逻辑似乎有误，但按要求翻译）

由此可知，在所有可能的情况下，组合 A 的价值与组合 B 相同。

```cpp
void rainbow_bs2d(double opt_value, double s1, double s2, double x, double signal);
    double rho, double opt_mat, double r, long is_max, long putcall, long flag) {
    
    s1               // 基础资产 1 的当前价格；
    s2               // 基础资产 2 的当前价格；
    x                // 执行价格
    sigma1           // 资产 1 的波动率；
    sigma2           // 资产 2 的波动率；
    rho              // 资产 1 和资产 2 之间的相关系数；
    opt_mat          // 到期时间；
    r                // 利率，
    is_max           // 如果 is_max 则期权是关于两种资产最大值的，否则是关于最小值的。
    putcall          // 如果 putcall 则期权是看跌期权，否则是看涨期权。
    // 输出参数：
    opt_value        // 期权的价值；
    flag             // 错误指示器。

    double temp;
    double temp2;
    double double = 1e-6; // 防止 rainbow_bs2d 溢出的近似值
    if (putcall) { // 看跌期权
        temp = x*exp(-r*opt_mat)-(s1, s2, sigma1, sigma2, rho, opt_mat, flag);
        temp2 = bs2d(s1, s2, sigma1, sigma2, rho, opt_mat, flag);
        opt_value = temp-temp2;
    } else { // 看涨期权
        rainbow_bs2d(s1, s2, sigma1, sigma2, rho, opt_mat, flag);
        opt_value = temp-temp2+temp3*exp(-r*T);
    }
}
```

**代码片段 6.2** 使用 Johnson (1987) 和 Schulz (1982) 的解析结果计算两种资产最大值或最小值的欧式看涨期权的价值。

```cpp
temp = log(S2/S1);
d2_ = temp-(sigma(signal)/2)*opt_mat;
d1 = d2_+sigma(opt_mat);
term = term_cov(d1,d2,Alfalls);
opt_value = term-term2-X*exp(-r*opt_mat);

return;
```

**代码示例 6.2（续）。**

