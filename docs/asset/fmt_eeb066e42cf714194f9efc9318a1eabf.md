
在本节中，我们将展示如何使用蒙特卡洛模拟来为下触即出障碍期权定价。我们将描述一种基本的蒙特卡洛方法以及一种可以提供更准确结果的布朗桥接方法（见第 8 章）。

资产价格 `$S$` 假设服从几何布朗运动（GBM），因此资产价格 `$X$` 的对数遵循布朗运动过程：

```
$\Delta X = \nu\Delta t + \sigma\Delta W_t \quad (4.5.18)$
```

其中 `$\nu$` 是漂移率，`$\sigma$` 是波动率。

如果障碍水平为 `B`，当 `S \le B` 时（或等价于 `log(S) \le log(B)`），期权将失效（knocked out）。这可以表示为 `X \le b`，其中 `b = log(B)`。

模拟下触即出期权的基本方法是首先确定许多场景，并确定每个场景包含多少个时间步（`TimeSteps`）。每个时间步的大小为 `time_step = TimeTimeToExpiry/TimeSteps`。对于每个场景，使用公式 `(4.5.18)` 将 `X_t` 的路径从时间 `t` 推进到 `t + \Delta t`，其中 `dr = time_step`，并从高斯随机数生成器获取 `W_t` 的值。如果达到期权到期时间或期权在此之前失效（即 `X \le b`），则停止路径构建。如果期权在在该场景产生收益之前失效，则该场景的收益为零。我们将从第 `i` 个场景获得的期权值为 `DO_i`，其中 `i=1, \dots`。场景：期权值为所有场景下 `DO_i` 的平均值；更多细节请参见代码段 4.8。

该方法的一个问题是，它没有考虑到尽管 `X_t > b` 且 `X_{t+\Delta t} > b`，但仍存在 `X_T \le b, t < \tau < t + \Delta t` 的可能性。在这种情况下，期权将会失效，因为 `X` 在时间 `$\tau$` 触及（或穿过）了障碍 `b`，但在时间 `t + \Delta t` 又增加到了 `X_{t+\Delta t}` 的值。

我们现在讨论布朗桥方法如何处理这种情况情况。我们选取两个时间点 `t_1` 和 `t_2 = t_1 + \Delta t`，并假设 `X_{t_1}` 和 `X_{t_2}` 都在（对数）障碍水平 `b` 之上。我们想要找到时间区间 `[t_1, t_2]` 内资产价格低于 `B` 的概率，并以此获得更准确的下触即出期权值。因此，所要求的障碍穿越概率为：

`$P(m_{t_1}^{t_2} \le b|X_{t_1}, X_{t_2}) =$`

其中 `m_{t_1}^{t_2}` 表示 `X` 在时间间隔 `[t_1, t_2]` 上的最小值。在给定 `X_{t_1}, X_{t_2}` 的情况下，`m_{t_1}^{t_2}` 的概率密度为：

```cpp
}
sum_opt_vals += total_probability_above * opt_val * disc;
else
    // 不使用布尔桥
    sum_opt_vals += opt_val * disc;
}
double temp = sum_opt_vals / (double)fNumberScenarios;
return temp;
}
```

代码片段 4.8（续）。

# 5 单资产美式期权

## 5.1 引言

在第4章中，我们讨论了单资产欧式期权以及用于定价的解析公式。在这里，我们将使用数值方法和解析公式考虑单资产美式期权的定价；此外，我们还讨论了使用数值技术对某些欧式期权定价。本章的内容如下：

- 用于美式期权定价的解析近似技术
- 用于美式和欧式期权定价的二项树格技术
- 使用有限差分格对美式和欧式普通及障碍期权进行定价
- 通过蒙特卡洛模拟对美式期权进行定价

需要提到，尽管这里的大部分讨论涉及普通欧式和美式看跌及看涨期权的定价，但所使用的技术可以较容易地修改，以包含具有自定义收益和早期行权特性的奇异期权。

## 5.2 普通美式期权的近似

### 5.2.1 带现金股息的美式看涨期权

在本节中，我们将考虑带现金股息的普通美式看涨期权的定价，并讨论 Roll、Geske、Whaley 和 Black 方法。我们将首先考虑 Roll–Geske–Whaley 方法。

### Roll–Geske–Whaley 近似法

该方法利用了 Roll (1977)、Geske (1979) 和 Whaley (1981) 的工作。设 `S` 为资产的当前 (`t`) 价格，该资产在除权日 `t_1` 支付单笔现金股息 `D_1`，资产的价值将从 `S_{t_1}` 下降到 `S_{t_1}-D_1`。扣除预留股息后的当前资产价格为：

```
$S_D = S - D_1 \exp(-r(t_1 - t)) \quad (5.2.1)$
```

* Whaley

其中 `r` 是无风险利率。

现在考虑一种在该资产上的、行权价为 `E`、到期时间为 `T` 的美式看涨期权。在 `t_1` 将有一个除权后资产价格 `S^*`，期权将在该处提前行权。该值可以通过求解以下方程找到：

```
$$c(S^*, E, \tau_1) = S^* + D_1 - E \quad (5.2.2)$$
```

其中 `c(S^*, E, \tau_1)` 是行权价为 `E`、到期时间为 `$\tau_1 = T - t_1$` 的欧式看涨期权在 `t_1` 时当前价值为 `S^*` 的 Black-Scholes 价值。如果在除权日之前 `S_t > S^*`，则美式期权将被行权并实现 `S_{t_1} + D_1 - E` 的收益。相反，如果 `S_{t_1} \le S^*`，则期权更有可能不行权，并将持有到时间 `T` 的期权到期。

我们可以将方程 `(5.2.2)` 重写为 `S^*` 是以下方程的根：

```
$K(S^*) = c(S^*, E, \tau_1) - S^* - D_1 + E = 0 \quad (5.2.3)$
```

其中 `K(S^*)` 表示单变量 `S^*` 的函数。求解方程 `(5.2.3)` 的一种常用技术是牛顿法，我们在此例中使用了它：

```
$S_{i+1}^* = S_i^* - \frac{K(S_i^*)}{K'(S_i^*)} \quad (5.2.4)$
```

其中 `S_i^*` 是 `S^*` 的第 `i` 次近似值，`S_{i+1}^*` 是改进后的第 `(i+1)` 次近似值。如果我们考虑方程 `(5.2.4)` 中的情况，根据方程 `(5.2.2)` 和 `(5.2.3)`，我们得到：

```
$K(S^*) = c(S^*, E, \tau_1) - S^* - D_1 + E$
```

以及

```
$K'(S^*) = \frac{\partial K(S_i^*)}{\partial S_i^*} = \frac{\partial c(S_i^*, E, \tau_1)}{\partial S_i^*} - 1$
```

此外，根据附录 A.3 中的方程 `(A.3.2)`：

```
$\frac{\partial c(S_i^*, E, \tau_1)}{\partial S_i^*} = N_1(d_1(S_i^*))$
```

我们注意到连续股息率 `q = 0`。因此：

```
$K'(S^*) = \frac{\partial K(S_i^*)}{\partial S_i^*} = N_1(d_1(S_i^*)) - 1$
```

```
$d_1 = \frac{\log(S_i^*/E) + (r + \sigma^2/2)\tau_1}{\sigma\sqrt{\tau_1}}$
```

将这些结果代入方程 `(5.2.4)` 得到：

```
$S_{i+1}^* = S_i^* - \frac{c(S^*, E, \tau_1) - (S^* + D_1)}{N_1(d_1(S^*))}$
```

单资产美式期权通过重组得到：

```
$S_{i+1}^* = \frac{c(S^*, E, \tau_1) + D_1 - E}{N_1(d_1(S^*))}$
```

对于 `i = 0, \dots, max` `(5.2.5)`，一个方便的初始近似是考虑 `S_0^* = E，$max$` 是迭代次数。现在使用 Roll、Geske 和 Whaley 公式来计算在时间 `t_1` 支付单笔股息 `D_1` 的美式看涨期权价值：

```
$C(S, E, \tau) = S_D \left\{ N_1(b_1) + N_2(a_1, -b_1, \frac{t_1-t}{\tau}) + D_1 \exp(-r(t_1-t))N_1(b_2) - E \exp(-r\tau)N_1(b_2)\exp(r\tau) + N_2(a_2, -b_2, \frac{t_1-t}{\tau}) \right\}$ (5.2.6)
```

其中 `S_D` 由方程 `(5.2.1)`给出，`E` 是行权价，`T` 是期权到期日，`t` 代表当前时间，`$\tau$` 是剩余期限，`N_1(a)` 是上限为 `a` 的单变量累积密度，`N_2(a,b,\rho)` 是上限为 `a, b` 相关系数为 `$\rho$` 的二变量累积密度。方程 `(5.2.6)` 中的其他符号定义为：

```
a_1 = \frac{\log(S/E) + (r + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}, \quad a_2 = a_1 - \sigma\sqrt{\tau}$
$b_2 = \frac{\log(S/S^*) + (r + \sigma^2/2)(t_1-t)}{\sigma\sqrt{\tau}}, \quad b_2 = b_1 - \sigma\sqrt{t_1}$
```

且 `S` 是当前 (`t`) 价格，`S^*` 使用方程 `(5.2.5)` 找到，`r` 是无风险利率，`$\sigma$` 是资产波动率，`$\tau = T-t$` 且 `$\tau_1 = T-t_1$`。为了计算在时间 `t_i, i=1,...,n` 支付 `n` 笔现金股息 `D_i` 的美式看涨期权价值，我们可以利用最优行权发生在最后一个除权日 `t_n` 的事实；例如，对于美式看涨期权，`t_1` 应设置为 `t_n，$D_1$` 应设置为 `D_n`，且 `S_D` 由下给出：

```
$S_D = S - \sum_{i=1}^n D_i \exp(-r(t_i-t))$ (5.2.7)
```

代码片段 5.1 提供了一个计算带有多个股息的美式看涨期权 Roll-Geske-Whaley 近似的程序。在这里，使用 `cum_norm` 和 `cum_norm2` 函数分别计算 `N_1(a)` 和 `N_2(a,b,\rho)` 的值。代码片段 5.3 用于计算值

```cpp
voidGM_approx(double *opt_value, double *critical_value, long n_divs, double dividends[],
    double Divs_T[],
{
    /* 输入参数:
    n_divs              = 股息数量
    dividends[]         = dividends[0] 包含第一笔股息, dividend[1]
                        = 第二笔等等
    Divs_T[]            = 支付时间: Divs_T[0] 是
                        Divs_T[1] 是支付第二笔股息的时间，等等
    S0                  = 基础资产的当前价值
    X                   = 行权价
    sigma               = 波动率
    T                   = 到期时间
    r                   = 利率
    输出参数:
    opt_value           = 期权价值
    critical_value      = 临值
    iflag               = 错误指示
*/
    double A1,A2,S_star,alpha1,alpha2,nt1,nt2;
    double b1,b2,di1,di2,sqrt,temp,temp1,temp2,temp3;
    double pdf,f,eur,var,fac,tol,loc_q,error=0;
    long iterate,flag=0;
    temp=0.0;
    for (i=0; i<n_divs; i++) { /* 检查 Divs_T 数组 */
        if (Divs_T[i] < 0 || Divs_T[i] > T) {
            flag=2;
            return;
        }
    }
    temp=Divs_T[i];
    /* 计算股息的现值（排除最后一笔） */
    temp=0.0;
    for (i=0; i<n_divs-1; i++) {
        temp += dividends[i] * exp(-r*Divs_T[i]);
    }
    /* 用所有股息的现值降低价格 */
    div=dividends[n_divs-1];
    S=S*exp(-r*div);
    iterate=0;
    tol=0.000001;
    S_star=S;
    while (iterate) /* 计算欧式看涨期权的 Black-Scholes 价值 */
        d1=(log(S/X) + (r+sigma*sigma/2.0)*(T-t1))/(sigma*sqrt(T-t1));
        d2=d1-sigma*sqrt(T-t1));
        put=S*norm_n(d2)-X*exp(-r*(T-t1))*norm_n(d1);
        loc_q=0.0;
        S_star=S*(S*norm_n(d1)-X*exp(-r*(T-t1))*norm_n(d2)-1.0);
        error=fabs(S_star-S);
        if (error<tol) break;
        iterate++;
    }
    a1=(log(S/X) + (r+sigma*sigma/2.0)*T)/(sigma*sqrt(T));
    a2=a1-sigma*sqrt(T);
    b1=(log(S/X) + (r+sigma*sigma/2.0)*(T-t1))/(sigma*sqrt(t1));
    b2=b1-sigma*sqrt(t1);
    nt1=sqrt(t1);
    temp1=S*(num_n(b1)-num_n(a2)-nt1,nt1+iflag))*exp(-r*t1)*(X-div)*exp(-r*t1)*num_n(b2);
    opt_value=temp1+temp2;
    critical_value=S_star;
}
```

## 单资产美式期权

**表 5.1** 使用了 Roll–Geske–Whaley 近似和 Black 近似计算的带股息美式看涨期权值对比

| 股票价格 | 临界价格, S* | RGW 近似 | Black 近似 |
| :--- | :--- | :--- | :--- |
| 80.0 | 123.582 | 3.212 | 3.208 |
| 85.0 | 123.582 | 4.818 | 4.808 |
| 90.0 | 123.582 | 6.839 | 6.820 |
| 95.0 | 123.582 | 9.276 | 9.239 |
| 100.0 | 123.582 | 12.111 | 12.048 |
| 105.0 | 123.582 | 15.316 | 15.215 |
| 110.0 | 123.582 | 18.851 | 18.703 |
| 115.0 | 123.582 | 22.676 | 22.470 |
| 120.0 | 123.582 | 26.748 | 26.476 |

使用的参数为：`E = 100.0, r = 0.04, \sigma, \tau = 2.0`，且在时间 `t = 1.0` 时有一笔 5.0 的现金股息。当前股票价格 `S` 从 80.0 变化到 120.0。结果与 Whaley (1981) 表 1 中给出的结果一致。

表 5.1 所示。这些结果将 Roll–Geske–Whaley 近似与 Black 近似进行了对比，我们现在将进行简要讨论。现在我们考虑 Black 近似。

## Black 近似

Black (1973) 对带现金股息的美式看涨期权的近似比我们刚刚描述的 Roll–Geske–Whaley 方法更简单。对于在时间 `T` 到期的美式看涨期权，其 `n` 个离散现金股息 `D_i, i = 1, \dots, n`，分别在时间 `t_i, i = 1, \dots, n` 支付，涉及计算在时间 `T` 和 `t_n` 到期的欧式期权价格，然后将期权价格设定为这两个值中的较大者，参见 Hull (2003)。

Black 近似 `C_{BL}` 可以用我们之前定义的符号更简洁地表示为：

```
$C_{BL}(S, \tau) = \max(v_1, v_2)$
```

其中 `v_1` 和 `v_2` 是以下欧式看涨期权：

`v_1 = c(S_D, E, \tau)` 且 `v_2 = c(S_D^+, E, \tau), \tau = T - t, \tau_1 = T - t_n`

```
$S_D = S - \sum_{i=1}^n D_i \quad \text{and} \quad S_D^+ = S - \sum_{i=1}^{n-1} D_i$
```

代码段 5.2 计算了 Black 近似。

代码段 5.3 使用与 Whaley (1981) 相同的值，并将 Roll–Geske–Whaley 近似与 Black 近似进行对比；结果如表 5.1 所示。

## 102 使用 C 和 C# 计算金融
