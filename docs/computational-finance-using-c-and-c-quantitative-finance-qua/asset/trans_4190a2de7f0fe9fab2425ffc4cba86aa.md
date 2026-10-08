
这意味着 $\widetilde{X} \sim N(0, \sigma_B^2 \, dt + \sigma_A^2 \, dt - 2\sigma_B\sigma_A\rho_{AB} \, dt)$，且变量 $(\sigma_B^2 - 2\sigma_B\sigma_A\rho_{AB})dW^P$ 与 $\widetilde{X}$ 具有相同的分布。
我们可以写为：

```
$$d\left(\frac{S_B^B}{S_A^B}\right) = \left(\frac{S_B^B}{S_A^B}\right)\hat{\mu} \, dt + \left(\frac{S_B^B}{S_A^B}\right)\sigma \, dW^P$$quad (6.5.2)$$
```

其中

```
$$\widetilde{\sigma} = \sqrt{\sigma_B^2 + \sigma_A^2 - 2\sigma_B\sigma_A}$$
```

以及

```
$$\hat{\mu} = \mu_B - \mu_A + \sigma_A^2 - \sigma_B\sigma_A\rho_{AB}$$
```

遵循第 4.4.3 节选择概率测度 $\mathbb{Q}$使得方程 (6.5.2) 中的漂移项为零。我们有

```
$$dW^P = dW^Q - \left(\frac{\mu}{\sigma}\right)dt$$
```

将此代入方程 (6.5.2)得到

```
$$d\left(\frac{S_B^B}{S_A^B}\right) = \left(\frac{S_B^B}{S_A^B}\right)\sigma \, dW^Q$$quad (6.5.3)$$
```

可以看出方程 (6.5.3) 与方程 (4.4.31) 相同，但映射关系为

```
$$S_t \to \frac{S_B^B}{S_A^B}, \quad \sigma \to \widetilde{\sigma}, \quad r \to 0$$quad (6.5.4)$$
```

现在结合方程 (4.4.3) 和 (4.4.37)，我们得到

```
$$\exp(-r\tau)E^Q[\max(S_t - E, 0)] = SN_1(d_1) - E\exp(-r\tau)N_1(d_2)$$
```

其中 $d_1$ 和 $d_2$ 已在第 4.4.3 节中定义。

因此，

```
$$\mathbb{E}^Q[\max(S_t - E)] = \exp(r\tau)SN_1(d_1) - N_1(d_2)$$
```

使用方程 (6.5.4) 中定义的映射，且在 Black-Scholes 公式中取 $E = 1$，我们得到：

```
$$\mathbb{E}^Q\left[\left(\frac{S_B^B}{S_A^B}\right) - 1\right] = \left(\frac{S_B^0}{S_A^0}\right)N_1(d_1) - N_1(d_2)$$
```

根据方程 (6.5.1)：

```
$$\mathcal{V}(t_0) = S_A^0\frac{S_B^0}{S_A^0}N_1(d_1) - N_1(d_2)$$
```

这意味着在时间 $t_0$ 时的交换期权价值为：

```
$$\mathcal{V}(t_0) = S_B^0N_1(d_1) - S_A^0N_1(d_2)$$
```

其中

```
$d_1 = \frac{\log(S_0^A/S_0^B) + \frac{1}{2}\sigma^2(T-t_0)}{\sigma\sqrt{T-t_0}}, \quad d_2 = d_1 - \sigma\sqrt{T-t_0}$
```

## 192 使用 C 语言计算金融

## 6.5.1 多资产期权

### 6.5.2 最大值或最小值的欧式期权

这里给出了 Stulz (1982) 和 Johnson (1987) 关于两种资产最大值和最小值的欧式看跌和看涨期权价值的结果，参见表 6.3 和 6.4。

```c
void rainbow_bs_2d(double *opt_value, double S1, double S2, double X, double signal, double sigma2, double rho, double opt_mat, double r, long is_max, long flag) {
    /* 输入参数:
    S1                  -- 资产 1 的当前价格，
    S2                  -- 资产 2 的当前价格，
    X                   -- 行权价，
    signal             -- 资产 1 的波动率，
    sigma2               -- 资产 2 的波动率，
    rho                 -- 资产 1 和资产 2 之间的相关系数，
    opt_mat             -- 到期时间，
    r                  -- 利率，
    is_max              -- 如果为 max 则期权是两个资产的看涨期权，
                        否则期权是两个资产的看涨期权。
    输出参数:
    opt_value           -- 期权价值，
    flag                -- 错误指示器。
    */
    double one=1.0, two=1.0, zero=0.0;
    double a,d1, d2,d1_d2,temp1,temp2,np;
    double rho_h,d1_prime;
    double sigma,term2;
    long lax = 0;

    if(X < EPS) { /* 行权价太小 */
        flag = 2;
        return;
    }
    if(signal < EPS) { /* 波动率太小 */
        flag = 3;
        return;
    }
    if(sigma2 < EPS) { /* 波动率太小 */
        flag = 3;
        return;
    }
    if(opt_mat < EPS) { /* 到期时间太小 */
        flag = 3;
        return;
    }
    sigma = sqrt(signal*signal + sigma2*sigma2 - signal*sigma2*rho); // 使用 Johnson (1987) 和 Stulz (1982) 的结果计算两个资产最大值或最小值的欧式看涨期权价值。
```c
    if (is_max == 1) { /* 两个资产的最大值
        /* 计算 term1 */
        temp = log(S1/X);
        d1 = temp+(r-sigma/2)*opt_mat;
        d2 = d1-sigma*sqrt(opt_mat);
        d1_prime = temp+(r-sigma/2)*opt_mat; // 注意：此处原文逻辑似乎存在重复赋值或错误，按样翻译
        d1_prime = d1-sigma*sqrt(opt_mat);   // 此处保持原代码逻辑
```
（注：原文代码的逻辑翻译如下：
```c
        temp = log(S1/X);
        d1 = temp+(r-sigma_2)*opt_mat;
        d2 = d1-sigma*sqrt(opt_mat);
        d1_prime = temp+(r-sigma/2)*opt_mat;
        d1_prime = d1-sigma*sqrt(opt_mat);
```
由于，，代码，，，代码代码注释翻译如下：

```c
    } else { /* 两个资产的最小

        /* 计算 term1 */
        temp = log(S1/X);
        d1 = temp+(r-sigma/2)*opt_mat;
        d2 = d1-sigma*sqrt(opt_mat);
        d1_prime = temp+(r-sigma/2)*opt_mat;
        d1_prime = d1-sigma*sqrt(opt_mat);
        rho12 = sigma*sigma2;
        term1 = cum_norm2(d1,d1_prime,rho12,flag);
        /* 计算 term2 */
        temp = log(S2/X);
        d2 = temp+(r-sigma/2)*opt_mat;
        d2 = d2-sigma*sqrt(opt_mat);
        d2_prime = temp+(r-sigma/2)*opt_mat;
        d2_prime = d2-sigma*sqrt(opt_mat);
        term2 = cum_norm2(d2,d2_prime,rho12,flag);
        /* 计算 term3 */
        temp = log(S1/X);
        d2_1 = temp+(r-sigma/2)*opt_mat;
        d2_1 = d1-sigma*sqrt(opt_mat);
        d2_2 = temp+(r-sigma/2)*opt_mat;
        d2_2 = d2-sigma*sqrt(opt_mat);
        term3 = cum_norm2(d2_1,d2_2,rho,flag);
        opt_value = term1+term2-X*exp(-r*opt_mat)*term3;
    }
    return;
}
```

表 6.3 欧式看跌和看涨期权的计算值和绝对误差

| 时间 | 看涨分析值 | 看涨误差 | 看跌分析值 | 看跌误差 |
|---|---|---|---|---|
| 0.1 | 6.45320 | 7.492 × 10⁻⁴ | 6.4524 | 7.334 × 10⁻⁴ |
| 0.2 | 6.96192 | 2.3845 × 10⁻³ | 6.95953 | 2.0172 × 10⁻ | |
| 0.3 | 7.49587 | 2.1084 × 10⁻³ | 7.49376 | 2.1572 × 10⁻ | |
| 0. | | ..0371 | | ..2600 10⁻³ | 0.22362 | 3.168 × 10⁻³ |
| 0.5 | 8.57808 | 1.037 × 10⁻³ | 8.59156 | 7.886 × 10⁻⁴ |
| 0.6 | 9.11529 | 7.206 × 10⁻³ | 9.10809 | 2.438 × 10⁻³ |
| 0.7 | 9.64700 | 1.3826 × 10⁻³ | 9.64838 | 1.154 × 10⁻³ |
| 0.8 | 10.17238 | 4.251 × 10⁻³ | 10.17663 | 3.389 × 10⁻³ |
