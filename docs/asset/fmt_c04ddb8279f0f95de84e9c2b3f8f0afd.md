
$\hat{\sigma}_{p,p}^2 = \hat{\sigma}_{p-1}^2(1-\hat{\sigma}_{p,p}^2),$

# 时间序列计量学

Yule-Walker 和 Durbin-Levinson 算法的直接实现由该部分描述的函数 `.quantQ.ts.YuleWalker[p;data]` 和 `.quantQ.ts.DurbinLevinson[data;p]` 提供。最小二乘法产生与 Yule-Walker 相同的 AR(p) 参数，但比迭代方法慢得多。Durbin Levinson 算法的速度与转转 Toeplitz 矩阵 $R_p^{-1}r_p$ 一样。

| 方法 | 时间 (ms) |
| :--- | :--- |
| Yule-Walker | 913 |
| Durbin-Levinson | 26 |
| 迭代 | 12 |

## 4.1.3 MA(q) 过程

回归过程是长记忆模型。它们通常具有随时间衰减的无限非零相关性。回归过程无法表示短记忆，序列的当前值 $X_t$ 只与少数过去值 $X_{t-1}$ 相关。本节介绍了移动平均过程，它们通常是阶为 $q$ 的短记忆过程，定义为：

$X_t = c + \epsilon_t + \alpha_1\epsilon_{t-1} + \alpha_2\epsilon_{t-2} + \dots + \alpha_q\epsilon_{t-q}$,

其中 $\alpha_1, \alpha_2,\dots, \alpha_q$ 是过程的系数，$c$ 和 $\epsilon$ 是白噪声，$\epsilon_i \sim N(0,\sigma^2)$。MA(q) 过程构造上是平稳的。它的期望为 $E[X_t]$，方差为 $Var[X_t] = \gamma(0) = \sigma^2(1 + \alpha_1^2 + \alpha_2^2 + \dots + \alpha_q^2)$。

相关系数 $\gamma(s) = \frac{1}{\gamma(0)}\sigma^2(\alpha_s + \alpha_{s+1}\alpha_1 + \alpha_{s+2}\alpha_2 + \dots + \alpha_q\alpha_{q-s})$ 对于 $s \leq q$，使得 $X_t$ 是每个 $t$ 均为均值为有限方差的过程，且 $E[X_tX_j] = \gamma(i,j)$，其中 $|i-j|=n$ 对于 $n=1,2,\dots$ 非奇异的。

# 数据科学

MA(q) 过程的单步预测器给出：

$$\hat{X}_{n+1} = \begin{cases} 0 & n=0 \\ \sum_{j=1}^{n} \hat{\alpha}_j(X_{n+1-j} - \hat{X}_{n+1-j}) & n \ge 1 \end{cases}$$

单步预测器 $\hat{X}_1, \hat{X}_2, ...$ 可以通过创新算法（14.14）确定的系数 $\hat{\alpha}_{ij}$ 递归计算。

## 4.1.3.1 MA(q) 参数估计

当 Durbin-Levinson 算法给出表示形式中的系数估计时：

$$\hat{X}_t = \sum_{j=1}^{p} \hat{\alpha}_{pj}X_{t-j}$$

其中 $\hat{\alpha}_{pj}, j=1, ..., p$ 是模型的参数，用于估计 MA(q) 过程参数的创新算法 (14.13) 考虑表示：

$$\hat{X}_t = \sum_{j=1}^{m} \hat{\alpha}_{mj}(X_{t-j} - \hat{X}_{t-j})$$

对于 AR(p) 过程，我们带双后缀重写 MA(q) 过程 $X_t = \epsilon_t + \alpha_{q,1}\epsilon_{t-1} + \dots + \alpha_{q,q}\epsilon_{t-q}$。从 $\hat{\sigma}_0^2 = \hat{Y}(0)$ 开始，$\alpha$ 的估计器递归求解：

$$\hat{\alpha}_{q,k} = \frac{\hat{\sigma}_q(k) - \sum_{j=0}^{k-1} \hat{\alpha}_{q,j}\hat{\sigma}_q(k-j)}{\sigma^2} \quad (14.14)$$

对于 $q=1, 2, ...$ 且 $\hat{\sigma}_q^2 = \hat{Y}(0) - \sum_{j=0}^{q-1} \hat{\alpha}_{q,j}^2$。

## 4.1.3.2 模拟

阶为 1 的移动平均过程的模拟如下：

$X_1 = \epsilon_1 + \alpha_1\epsilon_0$
$X_2 = \epsilon_2 + \alpha_1\epsilon_1$
...
$X_n = \epsilon_n + \alpha_1\epsilon_{n-1}$

给定一组 5 个随机数 $\epsilon_0, ... \epsilon_4$：

```
eps:-0.153913 2.22843 -0.324018 0.37141 0.57357
```

对于 $\alpha = 0.9$，函数显示花费 913 毫秒来估计 100,000 个遵循 ARMA(1,1) 模型 $X_t = 0.4X_{t-1} + 0.3\epsilon_t + \epsilon_t$ 的随机数的参数，通过求解 SLS 估计器转转 Toeplitz 矩阵需要 26 毫秒，而 Durbin-Levinson 算法仅需 12 毫秒：

## 4.1.3 示例

图 14.3 展示了 MA(2) 过程的 100 条路径：

$X_t = \epsilon_t + 0.5\epsilon_{t-1} + 0.3\epsilon_{t-2}$

通过函数生成：

```
> 通用的 MA(q) 模型可以使用递归函数 .quantQ.ts.simMA[q;alpha;eps].
>
```

![](img/97f758128bd0bdf5683d4c69d242_297.png)

**图 14.3** 模拟的 MA(2) 过程 $X_t = \epsilon_t + 0.5\epsilon_{t-1} + 0.3\epsilon$

## 4.1.4 ARMA(p, q) 过程

长记忆 AR(p) 模型可以与短记忆 MA(q) 过程结合，产生一个新的易处理且灵活的平稳过程族，自回归平均 ARMA(p,q) 指具有 $p$ 个自回归项和 $q$ 个移动平均项的模型：

```
$X_t = c + \sum_{i=1}^{p} \Phi_i X_{t-i} + \sum_{i=1}^{q} \alpha_i \epsilon_{t-i}, \quad (14.15)$
```

# 274 数据科学

使用滞后算子 L 表示的 ARMA(p,q) 过程为：

```
$$(1 - \sum_{i=1}^{p} \Phi_i L)X_t = c + (1 + \sum_{i=1}^{q} \alpha_i L^i)\epsilon_t$$
```

或者更简洁的形式

```
$$\Phi(L)X_t = c + \alpha(L)\epsilon_t. \quad (14.16)$$
```

### 14.1.4.1 ARMA(p, q) 过程的可逆性

记 $\pi(L) \equiv \frac{\Phi(L)}{\alpha(L)}$只要 $\sum_{j=0}^{\infty} |\pi_j| < \infty$ 且 $\pi_0=1$，ARMA(p,q) 过程可以表示为 (14.1) 所示 AR($\infty$) 模型：

```
$$\epsilon_t = \frac{1}{\alpha(L)}(\Phi(L)X_t - c)
= \pi(L)X_t - c
= \sum_{j=0}^{\infty} \pi_j L^j X_t - c
= \sum_{j=0}^{\infty} \pi_j X_{t-j} - c$$
```

### 14.1.4.2 Hannan-Riesenen 算法：两步回归估计

ARMA(p,q) 过程是自回归 AR(p) 和移动平均 MA(q) 过程的结合。$p+q$ 参数 $\mathbf{\Phi} = (\Phi_1, ..., \Phi_p)$、$\alpha = (\alpha_1, ..., \alpha_q)$ 和 $\sigma^2$可以通过两步回归进行估计：

- 将 $x_t$ 对其过去值 $x_{t-1}, ..., x_{t-m}$，$m > \max[p,q]$ 进行回归，并导出 $\hat{\pi}_i, i=1, ..., m$ 的 OLS 估计值。
- 第二步：将 $\hat{x}_t$ 对 $x_{t-1}, ..., x_{t-p}$ 以及 $\hat{\epsilon}_{t-1} = x_t - \sum_{i=1}^m \hat{\pi}_i x_{t-i}$ 进行回归。

### 14.1.4.3 Yule-Walker 估计

遵循 AR(p) 过程相同的原理，ARMA(p,q) 过程的广义 Yule-Walker 方程为：

$$ \left[\begin{array}{c} r(q+1) \\ r(q+2) \\ \vdots \\ r(q+p) \end{array}\right] = \left[\begin{array}{cccc} r(q) & r(q-1) & ... & r(q-p) \\ r(q+1) & r(q) & ... & r(q-p+1) \\ \vdots & \vdots & \ddots & \vdots \\ r(q+p-1) & r(q+p-2) & ... & r(q) \end{array}\right] \begin{pmatrix}\Phi_1 \\ \Phi_2 \\ \vdots \\ \Phi_p\end{pmatrix}$$

在给定自相关函数 $r(i)$ 的情况下， Yule-Walker 方程组可用于求解 $\Phi_i$。

# 时间序列计量学

### 14.4.4.4 极大似然估计

令 $\theta = (\Phi_1, \dots, \Phi_p, \alpha_1, \dots, \alpha_q, \sigma^2)$ 表示 ARMA(p, q) 过程的参数，令 $x = (x_1, \dots, x_T)$ 为大小为 $T$ 的观测样本。给定参数 $\theta$ 下，数据的联合概率密度函数为 $f(x|X_{T-1}, \dots, x_1|\theta)$。给定 $x$ 下，参数 $\theta$ 的似然函数为 $L(\theta|x) = f(x_{T-1}, \dots, x_1|\theta)$。极大似然估计为：

```
$\hat{\theta}_{MLE} = \max_{\theta \in \Theta} L(\theta|x) = \max_{\theta \in \Theta} \log L(\theta|x)$
```

假设 ARMA(p, q) 过程的误差服从高斯分布，$\epsilon_t \sim N(0,\sigma^2)$，则似然为：

```
$L(\theta|x) = (2\pi)^{-T/2}|\Gamma(\theta)|^{-1/2} \exp(-\frac{1}{2}x'\Gamma(\theta)^{-1}x)$
```

其中 $x$ 的 $T \times T$ 协方差矩阵为 $\Gamma(\theta) = E[xx']$。需要优化的对数似然为：

```
$l(\theta|x) = \log L(\theta|x) = -\frac{1}{2}(T\log(2\pi) + \log |\Gamma(\theta)| + x'\Gamma(\theta)^{-1}x)$
```

### 14.4.4.5 模拟

ARMA(p,q) 过程使用函数 `simARMA(alpha, eps)` 进行模拟。图 14.4 展示了 ARMA(1,1) 过程的 100 条模拟路径：

```
$X_t = \epsilon_t - 0.4\epsilon_{t-1} + 0.99X_{t-1}$
```

![](img/97f758128bd0df85683d4c942299.png)

**图 14.4** 模拟 ARMA(1,1) 过程 $X_t = \epsilon_t - 0.4\epsilon_{t-1} + 0.99X_{t-1}$

### 14.1.4.6 预测

用于估计和预测 MA(q) 过程的创新算法 (14.14) 可用于预测 ARMA(p, q) 模型。单步预测器为：

```
$$\hat{X}_{n+1} = \begin{cases} \sum_{j=1}^p \Phi_j X_{n-j+1} + \sum_{j=1}^q \alpha_j \hat{\epsilon}_{n-j+1} & n < m \\ \sum_{j=1}^p \Phi_j X_{n-j+1} + \sum_{j=1}^q \alpha_j \hat{\epsilon}_{n-j+1} & n \geq m \end{cases}$$
```

$\alpha_j$ 由创新算法 (14.14) 给出：

```
$$\hat{y}(i) = \begin{cases} \sum_{j=1}^p \Phi_j y_{i-j+1} + \sum_{j=1}^q \alpha_j \hat{\epsilon}_{i-j+1} & i < m \\ \sum_{j=1}^p \Phi_j y_{i-j+1} + \sum_{j=1}^q \alpha_j \hat{\epsilon}_{i-j+1} & \text{其他} \end{cases}$$
```

## 14.1.5 ARIMA(p, d, q) 过程

自回归移动平均过程是 ARMA(p,q) 过程的推广。由三个参数定义：与 ARMA 过程一样，$p$ 是自回归阶，$q$ 是积分阶。定义 $d$ 阶滞后差分算子 $V_d$ 为 $V_d X_t = X_t - X_{t-d} = (1 - L^d)X_t$。如果 $V_d X_t$ 是因果 ARMA(p,q) 过程，则过程 $[X_t, t \in \mathbb{Z}]$ 为 ARIMA(p,d,q) 过程。因果 ARIMA(p,d,q) 过程满足：

```
$$\Phi(L)Y_t = \Phi^*(1-L^d)X_t = \alpha(L)\varepsilon_t$$
```

其中 $[\varepsilon_t \sim N(0, \sigma^2)]$ 且 $\Phi^* \neq 0 \leq 1$。过程 $V_d X_t = (I - L^d)X_t$ 满足：

```
$$\Phi^*(L)Y_t = \alpha(L)\varepsilon_t. \quad (14.18)$$
```

## 14.1.6 代码

本节介绍了用于模拟、估计和预测 AR(p)、MA(q) 以及 ARMA(p,q) 过程算法实现。使用了三个通用函数对所有模型进行模拟、估计和预测：

- `quantQ.ts.simulate[process; params; eps]`
- `quantQ.ts.estimate[data; process; lags]`
- `quantQ.ts.forecast[data; period; lags]`.

### 14.1.6.1 模拟

通用函数 `quantQ.ts.simulate` 模拟了章节涵盖的自回归、移动平均和 ARMA 过程。该函数接受三个参数：第一个参数是过程，第二个是模型参数，第三个是白噪声 $\epsilon$。

```
.quantQ.ts.simulate(process, params, eps)
```

# 时间序列计量经济学

```
:.quantQ.ts.DurbinLevinson[data;first lags];
  "参数 lags 的类型错误"
```

```
[$process=MA;
  $7h = type lags;
    :.quantQ.ts.innovations[data;lags];
    [$7h = type lags;
      :.quantQ.ts.innovations[data;first lags];
      "参数 lags 的类型错误"
];
[$process=ARMA;
  $7h = type lags;
    :.quantQ.ts.HannanRissanen[data;lags[1]];
    "ARMA(p,q) 过程的估计需要一个包含两个整数的滞后参数列表"
];
"未知的过程类型。接受值：AR, MA 和 ARMA
]
];
```

自回归过程 AR(p) 默认使用 Durbin-Levinson 算法进行估计，该过程比求解 Yule-Walker 算法或求逆矩阵 (14.6) 来计算 OLS 估计量更快。Durbin-Levinson 算法的实现方式如下：

```
quantQ.ts.DurbinLevinson:[data;p]

// 用于估计 AR(p) 过程的历史数据（浮点数列表）
// p -- AR(p) 阶数
p:p+1;
phi:(p:p)=0f;
v:w=0f;
phi[1:1]:.quantQ.ts.gamma[1;data]*.quantQ.ts.gamma[0];data;
v[0]:.quantQ.ts.gamma[0];data;
s:0f;
while[n<p]
  j:1;
  while[j<n]
    s:s+phi[n-1;j]*quantQ.ts.gamma[n-j];data;
    j:j+1;
phi[n:n]:(.quantQ.ts.gamma[n;data]-s)%v[n-1];
s:0f;
v[n]:v(n-1)*(1-phi[n] xexp 2));
  j:1;
  while[j<n]
    phi[n;j]:phi[n-1;j]-phi[n];phi[n-1;n-j];
    j:j+1;
n:n+1;
```
