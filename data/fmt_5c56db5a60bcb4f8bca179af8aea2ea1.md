
$E[\epsilon_{1,t}] = v_1(P_{uu} + P_{ud} - P_{du}) = \mu_1\Delta t$,

$E[\epsilon_{2,t}] = v_2(P_{uu} + P_{ud} - P_{du}) = \mu_2\Delta t$，

以及方差/协方差得出：

$Var[\epsilon_{1,t}] = v_1^2(P_{uu} + P_{ud} + P_{du}) = \sigma_1^2\Delta t$,

$Var[\epsilon_{2,t}] = v_2^2(P_{uu} + P_{ud} + P_{du}) = \sigma_2^2\Delta t$，

$E[\epsilon_{1,t}\epsilon_{2,t}] = v_1v_2(P_{uu} + P_{ud} - P_{du}) = \rho\sigma_1\sigma_2\Delta t$，

其中 $\rho$ 是 $\epsilon_{1,t}$ 和 $\epsilon_{2,t}$ 之间的相关系数。我们得到

$P_{uu} + P_{ud} - P_{du} = \frac{\mu_1}{\sigma_1}$

## 6.5 双资产期权

**表格 6.4** 两个资产最小值的欧式看跌和看涨期权的计算值与绝对误差。结果采用二项树和解析公式（Johnson (1987) 和 Stulz (1982)）。期权期限在 0.1 到 0.8 年之间变化。参数为 $E = 44.0, S_1 = 40.0, S_2 = 50.0, r = 0.1, \sigma_1 = 0.2, \sigma_2 = 0.2, q_1 = q_2 = 0.0, \rho = 0.5$， 以及 $n_{steps} = 50$。

| 时间 | 解析法 | 误差 | 解析法 | 误差 |
|---|---|---|---|---|
| 0.1 | 0.10810 | 0.10753 | $5.7048 \times 10^{-4}$ | 0.36704 | 0.36693 | $5.0955 \times 10^{-4}$ |
| 0.2 | 0.40862 | 0.40781 | $8.1047 \times 10^{-4}$ | 3.54551 | 3.54514 | $6.9961 \times 10^{-4}$ |
| 0.3 | 0.74162 | 0.73418 | $7.4339 \times 10^{-3}$ | 3.47882 | 3.42706 | $6.7643 \times 10^{-3}$ |
| 0.4 | 1.06989 | 1.07299 | $3.1076 \times 10^{-3}$ | 3.43823 | 3.43715 | $4.3214 \times 10^{-3}$ |
| 0.5 | 1.38675 | 1.38909 | $2.3414 \times 10^{-3}$ | 3.39540 | 3.40159 | $6.1826 \times 10^{-3}$ |
| 0.6 | 1.69203 | 1.69025 | $1.7757 \times 10^{-3}$ | 3.36145 | 3.35779 | $3.6964 \times 10^{-3}$ |
| 0.7 | 1.98691 | 1.96939 | $1.5520 \times 10^{-3}$ | 3.32859 | 3.31517 | $1.3417 \times 10^{-2}$ |
| 0.8 | 2.27276 | 2.26274 | $1.0018 \times 10^{-2}$ | 3.29566 | 3.29157 | $4.0885 \times 10^{-3}$ |

$P_{uu} - P_{ud} + P_{du} = \frac{\mu_2}{\sigma_2}$,

$P_{uu} + P_{ud} + P_{du} = 1$，

$P_{uu} - P_{ud} - P_{du} = \rho$。

这些方程导致了以下跃概率：

$P_{uu} = \frac{1}{4} \left\{1 + \sqrt{\Delta t} \left(\frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} \right) + \rho \right\}$,

$P_{ud} = \frac{1}{4} \left\{1 + \sqrt{\Delta t} \left(\frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} \right) - \rho \right\}$,

$P_{dd} = \frac{1}{4} \left\{1 - \sqrt{\Delta t} \left(\frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} \right) + \rho \right\}$,

$P_{du} = \frac{1}{4} \left\{1 + \sqrt{\Delta t} \left(\frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} \right) - \rho \right\}$。

在代码段 6.4 中，我们提供了一个标准的二项树代码，用于对两个资产的最大值和最小值期权进行定价。参数 $M$ 是使用的步数，且该树在 $M$ 为偶数的假设下构建。

```c
void standard_2D_binomial(double value, double s1, double s2, double X,
double sigma, double sigma2, double rho, double T,
double r, double q1, double q2, long,
long M, long opt_type, long is_american, int iflag)
{
    /* 输入参数:
    s1 // 基础资产 1 的当前价格
    s2 // 基础资产 2 的当前价格
    // 行权价
    sigma1 // 资产 1 的波动率
    sigma2 // 资产 2 的波动率
    rho // 资产 1 和资产 2 之间的相关系数
    t // 到期时间
    r // 利率
    q1 // 资产 1 的连续收益率
    q2 // 资产 2 的连续收益率
    put // 如果 put 为看涨期权，否则为看跌期权
    // 步数，零步是树的根
    opt_type // 如果 opt_type 是两个资产最大值的期权
          // 否则是最小值的期权
    is_american // 如果 is_american 是美式期权，否则是欧式期权
    /* 输出参数:
    value // 期权价值
    iflag // 指示符
}
```

## 6.6 三资产期权

对于三资产期权（代码段 6.5 和表 6.5–6.8 中的结果），我们有以下跃概率：

```c
if (opt_type == 0) { /* 两个资产的最大值 */
    if (put) {
        V(i,j) = MAX(X-MAX(S1,S2),0);
    } else {
        V(i,j) = MAX(MAX(S1,S2)-X,0);
    }
} else { /* 两个资产的最小值 */
    if (put) {
        V(i,j) = MAX(X-MIN(S1,S2),0);
    } else {
        V(i,j) = MAX(MIN(S1,S2)-X,0);
    }
}
```

# 194 章 | 多资产期权

$P_{udd} = \frac{1}{8} \left\{ 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} \right) - \rho_{12} - \rho_{13} - \rho_{23} \right\}$

$P_{dud} = \frac{1}{8} \left\{ 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} \right) + \rho_{12} - \rho_{13} - \rho_{23} \right\}$

$P_{ddl} = \frac{1}{8} \left\{ 1 - \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} - \frac{\mu_3}{\sigma_3} \right) + \rho_{12} + \rho_{13} + \rho_{23} \right\}$

```cpp
void standard_d3_binomial_double(double s1, double s2, double s3, double x,
double signal1, double signal2, double signal3, double rho_12, double rho_13, double rho_23,
 double T, double r, long m, long type, long is_american, int *flag)
{
// 输入参数：
s1 // 标的资产 1 的当前价格
s2 // 标的资产 2 的当前价格
s3 // 标的资产 3 的当前价格
sigma1 // 资产 1 的波动率
sigma2 // 资产 2 的波动率
sigma3 // 资产 3 的波动率
rho_12 // 资产 1 和 资产 2 之间的相关系数
rho_13 // 资产 1 和 资产 3 之间的相关系数
rho_23 // 资产 2 和 资产 3 之间的相关系数
 T // 到到期的时间
put // 如果 put 为 1 则为看涨期权，否则为看跌期权
opt_type // 如果 opt_type 为 1 则为执行期权，否则为欧式期权
is_american // 如果 is_american 为 1 则为欧式期权，否则为美式期权

value // 期权价值
iflag // 错误指示

double double_count, dt1, dt2, dt3, d1, d2, u3;
long i, j, k; flags = 0;
double price = 0.0;
double dsv1, dsv2, dsv3, bvh, tmp1, tmp1, tmp2, tmp3;
long P1, P2, P3, tdv, mu1, mu2, mu3, jp1, jp2, jp3;
double one = 1.0, half = 0.625;
hall = 0;

if ((m/2) != (m/2)) printf("THE ERROR OF TIME STEPS IS NOT EVEN\n");
tdv = T/m;
tdv2 = sqrt(tdv);
#define V(i,j,k) v(i) * tdv + (j) * (k)
#define U0 0
#define U1 1
#define U2 2
#define U3 3
#define U4 4
#define U5 5
#define U6 6
#define U7 7
dt = sqrt(tdv);
pj1 = sigma1*sqrt(tdv);
pj2 = sigma2*sqrt(tdv);
pj3 = sigma3*sqrt(tdv);
mu1 = r - sigma1*half;
mu2 = r - sigma2*half;
mu3 = r - sigma3*half;
u1 = exp(mu1); // 分配跳转大小 *
nu2 = exp(mu2);
u3 = exp(mu3);
d1 = exp(-jp1);
d2 = exp(-jp2);
d3 = exp(-jp3);
// 设置跳跃概率 /
pU[0] = eighth(one + sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
pU[1] = eighth(one - sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
pU[2] = eighth(one + sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
pU[3] = eighth(one + sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
```

代码示例 6.5 标准三维二项树格。

# 三资产期权章节 | 6 195

```cpp
d[DUD] = eighth(one + sqrt_dt * (-mu1/sigma1) + (mu2/sigma2) - (mu3/sigma3)) - rho_12 + rho_13 - rho_23);
p[dUD] = eighth(one + sqrt_dt * (-mu1/sigma1) - (mu2/sigma2) + (mu3/sigma3)) + rho_12 - rho_13 + rho_23);
p[dD] = eighth(one + sqrt_dt * (-mu1/sigma1) - (mu2/sigma2) + (mu3/sigma3)) + rho_12 - rho_13 + rho_23;
for (i = 0; i < 8; i++) {
    if (g[i] < 0 || g[i] > 1.0) printf("P error %d: %.1f out of range %s", i, g[i]);
}for (i = 0; i < 8; i++) {
    p[i] = discount[i];
}
// 分配数组 (V(M+1)), M[i], s2(M+1), 以及 s3(M+1))
s[M];
for (i = 0; i < M; i++) {
    s1[i] = u*M; // s1 的 M+1 价值
    s1[i] = d/M;
}
s2[M+1];
for (i = 0; i < M; i++) {
    s2[i] = u*M; // s2 的 M+1 价值
    s2[i] = d/M;
}
s3[M+1];
for (i = 0; i < M; i++) {
    s3[i] = u*M; // s3 的 M+1 价值
    s3[i] = d/M;
}
/* 计算到期日的期权价值 */
P1[M];
for (i = 0; i < M; i++) {
P2[M];
for (j = 0; j < M; j++) {
P3[M];
for (k = 0; k < M; k++) {
    if (put) { 三资产的最大值 */
        tmp = MAX(s1[i], s2[j], s3[k]);
        V(i,j,k) = MAX(tmp, p3[k]);
    } else if (opt_type == 1) { 三资产的最小值 */
        tmp = MIN(s1[i], s2[j], s3[k]);
        V(i,j,k) = MIN(tmp, p3[k]);
    } else { /* 看涨期权 */
        ** 使用提供的期权代码作为模板插入看权代码 **
P3 = P3 + P2;
P2 = P2 + P1;
P1[M];
for (i = M-1; i >= 0; i--) { /* 反向遍历网格计算期权价值 */
P2[M];
for (j = 0; j < M; j++) {
P3[M];
for (k = 0; k < M; k++) {
    V(i,j,k) = p[DUD](i,j,k) + p[DUD](i,j+1,k) + p[DUD](i,j,k+1) + p[DUD](i+1,j+1,k+1);
    if (is_american) {
        if (opt_type == 0) { 三资产的最大值 */
            tmp = MAX(s1[i], s2[j], s3[k]);
            tmp1 = MAX(tmp, p1[i]);
            tmp2 = MAX(tmp1, p2[j]);
            V(i,j,k) = MAX(tmp2, zero);
        } else if (opt_type == 1) { 三资产的最小值 */
            tmp = MIN(s1[i], s2[j], s3[k]);
            tmp1 = MIN(tmp, p1[i]);
            tmp2 = MIN(tmp1, p2[j]);
            V(i,j,k) = MIN(tmp2, zero);
        } else { /* 看涨期权 */
        ** 使用提供的期权代码作为模板插入看权代码 **
    }
    } else { /* 欧式期权 */
        V(i,j,k) = ...;
    }
}}
```

代码 6.5（续）。**注意**

# 196 章 | 多资产期权

```cpp
P1 = P3 + 2;
P2 = P2 + 2;
P1 = P1 + 2;
}
value = V(9,0);
```

代码 6.5（续）。

## 6.7 四资产期权

四资产的结果如表 6.9 和 6.10 所示。我们有以下跳跃概率：
