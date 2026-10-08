

## 欧式期权

$f(b \le X^{\min}, X)$

$=-\Omega \sqrt{\frac{2}{\pi}} \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)\exp\left(\frac{X-(r-q-\sigma^2/2)\tau}{2\sigma^2\tau}\right) \quad (4.5.6)$

$r$ 是无风险利率，$q$ 是连续股息率。到期期限为 $\tau$ 障碍位在 $X=B$ 的欧式下行触出障碍期权如果在时间 $X_s \le B$（对于 $t \le s \le T$）将会失效（变得无价值）。因此，如果终点为 $X$，该障碍期权在时间 $T$ 继续存的概率密度函数为：

$f(X > B) =-\sqrt{\frac{2}{\pi}} \int_{b=S\exp(b)}^{b=X} \Omega \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)\times \exp\left(\frac{X-(r-q-\sigma^2/2)\tau}{2\sigma^2\tau}\right)db \quad \quad (4.5.7)$

或者

$f(X > B) =-\sqrt{\frac{2}{\pi}} \exp\left(\frac{X-(r-q-\sigma^2/2)\tau}{2\sigma^2\tau}\right)\times \int_{b=\log(B/S)}^{b=X} \Omega \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)db \quad (4.5.8)$

其中我们对所有使期权存活的 $b$ 取值 $B < b < X$ 进行了积分。回想起：

> $-\int_{b=\log(B/S)}^{b=X} \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)db$
> $-\int_{b=\log(B/S)}^{b=X} \exp\left(\frac{(X-2b)}{\sigma^3\tau^{3/2}}\right)\exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)db$

并注意到：

> $$\frac{\partial}{\partial b} \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)=\exp\left(\frac{2(X-2b)}{\sigma^2\tau}\right)\exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)$$

我们得到：

> $-\int_{b=\log(B/S)}^{b=X} \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)db$
> $-\exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)\times_{b=\log(B/S)}^{b=X} = 1-\exp\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right)$

所以我们：

> $f(X > B) =-\frac{1}{\sigma\tau\sqrt{\frac{2}{\pi}}}} \exp\left(\frac{X-(r-q-\sigma^2/2)\tau}{2\sigma^2\tau}\right)\times \left\{1-\exp\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right)\right\}$

执行价为 $E$ 且满足 $E > B$ 的欧式下行触出看涨期价值 $c_{do}$ 给出：

$c_{do} = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{X=\log(E/S)}^{\infty} {\exp(X) - E\f(X > B) dX \quad (4.5.9)}$

该积分在附录 B.1 中计算，下行触出看涨权的价值 $c_{do}$ 为：

$c_{do} = c - c_{di} \quad (4.5.10)$

其中

$c = S\exp(-q\tau)N_1(d_1) - E\exp(-r\tau)N_1(d_2)$

$c_{di} = S\exp(-q\tau)N_1(d_1) (\frac{B}{S})^{\frac{2(r-q)}{\sigma^2}} - E\exp(-r\tau)N_1(d_3) (\frac{B}{S})^{\frac{2(r-q)-1}{\sigma^2}}$

$d_1 = \frac{\log(S/E) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$

$d_2 = \frac{\log(S/E) + (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$

$d_3 = \frac{\log(B^2/SE) + (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$

以及

$d_4 = \frac{\log(B/ES) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$

在代码段 4.7 中，我们提供了函数 `bs_opt_barrier_downout_call`，它使用公式 (4.5.10) 为下行触出看涨期权定价。该程序将在第 5 章用于衡量使用有限差分网格求解 Black-Scholes 方程的精度。

## 4.5.3 上行触出期权的解析定价

在这里我们将获得连续股息率 $q$ 的上行触出看涨权的表达式，方法类似于 4.5.2 节中下行触出期权的方法。到期期限为 $\tau$ 障碍位在 $X=B$ 的欧式上行障碍期如果在如果在时间 $X_t \geq B$，将会失效（变得无价值）。如果终点为 $X$，该障碍期权在时间 $T$ 继续存的概率密度函数为：

$f(X < B) = \sqrt{\frac{2}{\pi}} \int_{b=B}^{\infty} \Omega \exp\left(\frac{2b(X-b)}{\sigma^2\tau}\right)\times \exp\left([X - (r - q - \sigma^2/2)\tau]^2\right) db \quad (4.5.11)$

## 欧式期权

```c
void bs_opt_barrier_downcall(double *value, double barrier_level,
double s0, double x, double sigma, double t, double r,
double q, long *iflag)
{
    /* 输入参数:
       ===================
       barrier_level    - 障碍水平
       s0               - 层资产当前价格
       x               - 行权价
       sigma           - 波动率
       t               - 到期时间
       r               - 无风险利率
       q               - 股息率
       输出参数:
       ===================
       value            - 期权价值
       iflag            - 错误指示
    */
    double one=1.0,two=2.0,zero=0.0;
    double temp,temp1,temp2,a,b,c,d1,d2,d3,d4,d5;
    
    if (t <= zero) {
        *value = zero;
        *iflag = 1;
        return;
    }
    if (sigma <= zero) {
        *value = zero;
        *iflag = 1;
        return;
    }
    if (s0 >= barrier_level) {
        *value = zero;
        *iflag = 1;
        return;
    }
    // ... (剩余实现)
}
```

