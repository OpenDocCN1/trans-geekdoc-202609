

## 第 5 章 单资产美式期权

因此，美式看跌权的迭代算法为：

```
$S_{i}^{**} = \frac{E - RHS(S_{i}^{**}, E, \tau)}{1 + b_i} + b_i S_{i}^{**} \quad (5.2.37)
```

其中我们可以使用 $S_{0}^{**} = E$ 作为临界资产值的初始估计（参见下文计算机代码）。

## $b_i$ 的表达式

在这里，我们推导出用于方程 (5.2.37) 的项 $b_i$ 的表达式。由于

```
$b_i = \frac{\partial}{\partial S_{i}^{**}} p(S_{i}^{**}, E, \tau) - \frac{S_{i}^{**}}{\gamma_1} (1 - \exp(-q\tau)) + N_1(d_1(S_{i}^{**})) \exp(-q\tau))$
```

我们得到：

```
$b_i = \frac{\partial p(S_{i}^{**}, E, \tau)}{\partial S_{i}^{**}} - \frac{1}{\gamma_1} \{1 - \exp(-q\tau)\} - \frac{1}{\gamma_1} \exp(-q\tau) N_1(d_1(S_{i}^{**})) \\ \frac{\exp(-q\tau) N_1(d_1(S_{i}^{**}))}{\partial d_1(S_{i}^{**})}{\gamma_1} \frac{\partial d_1(S_{i}^{**})}{\partial S_{i}^{**}}$
```

我们现在引用附录 A 中推出的以下结果：

- 附录 A，方程 (A.1.3): $\frac{N(d_1(S_{i}^{**}))}{\partial d_1(S_{i}^{**})} = n(d_1(S_{i}^{**}))$
- 附录 A，方程 (A.1.6): $\frac{1}{\partial S_{i}^{**}} = \frac{1}{S_{i}^{**}} \sigma \sqrt{\tau}$
- 附录 A，方程 (A.3.4): $\Delta_p = \frac{\partial p(S_{i}^{**}, E, \tau)}{\partial S_{i}^{**}} = \exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\}$

将这些结果代入上述表达式，我们得到：

```
$b_i = \exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\} - \frac{1}{\gamma_1} \{\exp(-q\tau) + N_1(d_1(S_{i}^{**})) \exp(-q\tau)\} \\ \frac{\exp(-q\tau) N_1(d_1(S_{i}^{**}))}{\partial d_1(S_{i}^{**})}{\gamma_1} \frac{\partial d_1(S_{i}^{**})}{\partial S_{i}^{**}}$
```

```
$=\exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\} - \frac{1}{\gamma_1} \{\exp(-q\tau) + N_1(d_1(S_{i}^{**})) \exp(-q\tau)\}
```

```
$-\frac{S_{i}^{**} \exp(-q\tau) n(d_1(S_{i}^{**}))}{\gamma_1 \sigma \sqrt{\tau}},
```

可以重新整理可以得到：

```
$b_i = \exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\} \frac{1}{\gamma_1} + \frac{1}{\gamma_1} \{\exp(-q\tau) - 1 - \frac{\exp(-q\tau) n(d_1(S_{i}^{**}))}{\sigma \sqrt{\tau}}\} \exp(-q\tau)\}quad (5.2.38)$
```

## 欧式期权的近似

在代码段 5.4 中，我们提供了实现 Macmillan、Baronei 和 Whaley 方法的计算机代码。

```cpp
void MMW_approx(double opt_value, double critical_value, double s_0, double x, double sigma, double t, double r, double q, long iflag) {
    输入参数:
    S               - 标的资产当前值
    X               - 执行价格
    sigma           - 波动率
    t               - 到期时间
    r               - 利率
    q               - 连续股息率
    put             - 如果 put 为 0 为看涨期权，否则为看跌期权
    输出参数:
    opt_value       - 期权价值
    critical_value  - 临界值
    error           - 指示
}
    double a_1, gamma_2, gamma_1;
    double di1, alpha, h2, temp1;
    double pi, bs, val, tol, err;
    long iter;
    pi = PI;
    beta = 2.0 * (r - q) / (sigma * sigma);
    alpha = 2.0 * r / (sigma * sigma);
    temp = 1.0 * exp(-t);
    sol = 0.0;
    iter = 0;
    tol = 1e-6;
    if (put) { // 美式看涨
        gamma_2 = sqrt(temp + (4.0/alpha));
        gamma_2 = 2.0 / gamma_2;
    } else { // 美式看跌
        while (iter < 5) { // 迭代
            di = log(S/x) + (r - q-sigma/2.0)*t / (sigma*sqrt(t));
            di1 = di + sigma*sqrt(t);
            pdf = (1.0*exp(-di1*di1/2.0))/sqrt(2*PI);
            temp = (temp*temp)*(1.0 - (1/gamma_2));
            temp = (1.0 - (exp/pdf(sigma*sqrt(temp))))/gamma_1;
            // 计算看涨权的 Black-Scholes 价值
            black_scholes(&err, s_star,sigma, T,r,q,put);
            rhs = s_star*exp(-q*t)-exp(-r*t)*cum_norm(di1)*s_star/gamma_1;
            s_star = x*exp(-r*t)*rhs;
            err = fabs(s_star-x);
            if (err < tol) break;
            iter++;
        }
        A_2 = (s_star/gamma_2)*exp(-temp)*cum_norm(di1);
        if (s_0 > s_star) { // 美式看涨
            temp = 1.0;
            black_scholes(&err, s_0,sigma, T,r,q,put);
            opt_value = s_0 + pow(temp,gamma_2);
        } else { // 美式看跌
            gamma_1 = sqrt(temp + (4.0/alpha));
            gamma_1 = 2.0 / gamma_1;
            iter = 0;
            while (iter < 5) { // 计算 S
                di = log(S/x) + (r - q-sigma/2.0)*t / (sigma*sqrt(t));
                di1 = di + sigma*sqrt(t);
                pdf = (1.0*exp(-di1*di1/2.0))/sqrt(2*PI);
                temp = (temp*temp)*(1.0 - (1/gamma_1));
                temp = (1.0 - (exp/pdf(sigma*sqrt(temp))))/gamma_1;
                h2 = temp;
            }
            // 计算看跌权的 Black-Scholes 价值
            black_scholes(&err, s_star,sigma, T,r,q,put);
            rhs = s_star*(1.0-exp(-q*t))-cum_norm(di1)*s_star/gamma_1;
            s_star = x*exp(-r*t)*rhs;
            err = fabs(s_star-x);
            if (err < tol) break;
            iter++;
        }
        opt_value = -s_star;
} 代码段 5.4 用于 Macmillan、Baronei 和 Whaley 的美式期权近似。*注意。*

```cpp
A_1 = -(S*gamma_1)*(1.0 - exp(-q*T))*cum_norm(-di1)
if (S < s_star) {
    temp_i = s_star;
    black_scholes(&temp_i,S,sigma, T,r,q,put);
    opt_value = A_1*pow(temp_i,gamma_i);
} else {
    opt_value = S;
}
``` 代码段 5.4（续）。表 5.2 和 5.3 是使用上述计算机代码获得。

## 5.3 欧式期权的格子方法

### 5.3.1 二叉格

在本节中，我们将推导出描述资产价格 GBM 运动的二叉格方程。我们将采用 MBW_approx 程序。

| 表 5.2 | 使用 Macmillan、Baronei 和 Whaley 方法。使用的参数为 r = 0.5, X = 100.0, q = 0.1, \sigma = 0.06, 和 \sigma = 0.2。使用标准网格 2000 步计算出的精确值，减去 Macmillan、Baronei 和 Whaley 的估计值。 |
| 股票价格 | 精确值 | 误差 | 精确值 | 误差 |
|---|---|---|---|---|
| 86.0 | 1.2064 | 5.54 × 10⁻⁴ | 14.0987 | -3.66 × 10⁻² |
| 89.0 | 1.8838 | 1.95 × 10⁻⁴ | 11.5120 | -4.85 × 10⁻² |
| 92.0 | 2.7890 | 7.03 × 10⁻⁴ | 9.2478 | -3.58 × 10⁻² |
| 95.0 | 3.9427 | 1.16 × 10⁻³ | 7.3031 | -3.66 × 10⁻² |
| 98.0 | 5.3522 | 1.15 × 10⁻³ | 5.6674 | -4.85 × 10⁻² |
| 101.0 | 7.0119 | 2.21 × 10⁻³ | 4.3209 | -3.58 × 10⁻² |
| 104.0 | 8.9043 | 2.63 × 10⁻³ | 3.2362 | -3.66 × 10⁻² |
| 107.0 | 11.0072 | 4.20 × 10⁻³ | 2.2215 | -4.85 × 10⁻² |
| 110.0 | 13.2905 | 4.77 × 10⁻³ | 1.7235 | -3.66 × 10⁻² |
| 113.0 | 15.7264 | 5.20 × 10⁻³ | 1.3501 | -3.66 × 10⁻² |

| 表 5.3 | 美式看跌权早期行权的 Macmillan、Barone-Adesi 和 Whaley 方法。使用的参数为 r = 0.5, X = 100.0, q = 0.1, \sigma = 0.06, 和 \sigma = 0.2 |
| 到期时间, $\tau$ | 临界资产值, $S^{**}$ | 到期时间, $\tau$ | 临界资产值, $S^{**}$ |
|---|---|---|---|
| 1.0 | 82.1510 | 0.75 | 88.0333 |
| 0.95 | 82.3751 | 0.70 | 88.8959 |
| 0.90 | 82.6115 | 0.65 | 89.9568 |
| 0.85 | 82.2618 | 0.60 | 91.3469 |
| 0.80 | 83.1273 | 0.55 | 93.4260 |
| 0.75 | 83.4098 | 0.50 | 95.1701 |
| 0.70 | 83.7115 | 0.45 | 96.6199 |
| 0.65 | 84.0439 | 0.40 | 98.1176 |
| 0.60 | 84.3830 | 0.35 | 99.6740 |
| 0.55 | 84.7598 | 0.30 | 101.3469 |

