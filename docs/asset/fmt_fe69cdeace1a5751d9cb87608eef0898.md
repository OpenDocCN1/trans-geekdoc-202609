
:1_phi[p-1];

```
给定函数 `.quantQ.ts.toeplitz` 用于构建样本自协方差 `.quantQ.ts.r` 的 Toeplitz 矩阵 (14.12)，首先，我们定义阶数为 h 的阶样本自协方差函数：
```
.quantQ.ts.gamma[[h;data]
// 自相关阶数
// data -- 数据
// :neg[h]_data cov (h _data);
;
```
然后是阶数为 h 的阶样本自相关函数：
```
.quantQ.ts.r[[data;h]
// 自相关阶数
// data -- 数据
// :quantQ.ts.data]%.quantQ.ts.gamma[0;data];
;
```
最后，是 Toeplitz 矩阵：
```
.quantQ.ts.toeplitz::[data;p]
// data -- 历史数据（浮点数列表）
// p -- AR(p) 过程阶数
tabs (p;p)="[x;data](til p);\quantQ.ts.r[data;x]][data] raze t;
;
```
Yule-Walker 方程可以这样求解：
```
.quantQ.ts.yuleWalker::[data;p]
// data -- 历史数据（浮点数列表）
// p -- AR(p) 模型阶数
inv[.quantQ.ts.toeplitz[data;p]] mmu {.quantQ.r[data;data]] each p
;
```
最后，OLS 估计量 (14.6) 可以实现为：
```
.quantQ.ts.estAR::[data;p]
// 用于估计 AR(p) 模型的历史数据（浮点数列表）
// p -- AR(p) 模型阶数
n:count_data;
dim:(n-p,p+1);
x:dim=0f;
i:0;j:1;
while i<(n-p);
x[i:0]:1f;
while j<p;
0<=i-j;
x[i;j]:data[i-j];
j:j+1;
i:i+1;
y:neg[p]-inv([flip x);
;
```
估计 MA(q) 过程系数的创新算法 (14) 实现如下：
```
.quantQ.ts.innovations:[data;q]
// 用于估计 MA(q) 过程的历史数据（浮点数列表）
// q -- MA(q) 过程阶数
p:1:q 直收敛
v:(p+1)*0f;
alpha:(p+1;p+1)*0f;
v[0]:.quantQ.ts.gamma[0;data];
n:1;
k:0;
while[n<=p>
  k:0;
  while[k<n]
    j:0; s:0f;
    while[j<k]
      s:s+(alpha[k-j]+alpha[n-j]+v[j]);
      j:j+1;
    ];
    alpha[n-k]:(quantQ.ts.gamma[n;data] - s)*v[k];
    k:k+1;
    s:0f; j:0;
    while[j<n]
      s:s+(alpha[n-j] xexp 2)*v[j];
      j:j+1;
    ];
    v[n]:.quantQ.ts.gamma[0;data]-s;
  n:n+1;
alpha[p-1;p+1];
```
算法算法收敛比移动平均过程的滞后数慢。因此，我们将滞后数 q 改进估计量并选择 alpha 矩阵的前 q 个元素。ARMA(p,q) 的参数通过双步回归求解 Hannan-Rissanen 算法来估计：
```
.quantQ.ts.HannanRissanen:[data;p;q]
// 用于估计 ARMA(p,q) 过程的历史数据（浮点数列表）
// p -- AR(p) 过程阶数
// q -- MA(q) 过程阶数
```
```
// 步骤 1 - 估计 AR(max(p+q))
lags:1+(p+q)
arest:quantQ.ts.DurbinLevinson[data; lags]
res:.quantQ.ts.residuals[arest;data];
es:(lags+0),res;
// 步骤 2 - 对 (data[t-1],...,data[p],res[t-1],...,res 回归 data[t]
// 对于 t = lag,q，通过 OLS
t:(lags+q) -- 数据计数
x:(reverse each quantQ.ts.matrix[t;p;data]),(reverse each .quantQ.ts.matrix[t;q]); mmu flip x mmu data[t]);
```
递归函数 `.quantQ.ts.matrix` 将序列 d 堆叠到矩阵中计算 [d-q];d[t-q];...d[t-1]：
```
.quantQ.ts.matrix:{t;q}
// t 索引
// q MA(q) 过程阶数
// d 序列
$[q=1]; d[t-q].quantQ.ts.matrix[t-q;d];d[t-1];
```
ARMA(p,q) 过程估计量的实现留给读者作为练习。可以通过 ARMA(p,q) 过程的 Yule-Walker 选择或通过调整 Hannan-Rissanen 算法来估计。

## 14.6.3 预测

通用函数 `.quantQ.ts.forecast[data;period;process;lags]` 根据数据集 `data` 预测阶数为 `lags` 的过程未来 `period` 步。参数 `data` 是浮点数列表。参数 `process` 是一个正整数。变量包含自回归过程的 AR 值、移动平均过程的 MA 值或自回归移动平均的 AR 值。第四个参数是正整数或 ARMA(p,q) 模型的两个整数列表。
```
.quantQ.ts.forecast:{data;period;process;lags}
// data 用于预测过程的历史数据（数字列表）
// period -- 过程未来预测步数，其中 period 为正整数。
// process -- 要模拟的过程类型。接受值：AR, MA 或 ARMA
// lags -- 过程阶数。AR 和 MA 过程为整数。ARMA 的
-- 两个整数列表。
$[process=AR;
$[(period=type period) & (period > 0);
$[(lags = type lags;
::quantQ.ts.forecastAR[data;
];[lags = type lags];
```
预测 MA(q) 过程，我们假设真实模型是。以 MA(2) 过程为例：

![https://images.example.com/97f512880c5f8d94c22307png](https://images.example.com/97f512880c5f8d94c22307png)

一步预测：
$X_{n+1} = c + \varepsilon_{n+1}$

两步预测：
$X_{n+2} = c + \alpha_1\varepsilon_{n+1} + \alpha_2\varepsilon_n$

三步预测：
$X_{n+3} = c + \alpha_1\varepsilon_{n+2} + \alpha_2\varepsilon_{n+1}$ 且误差方差为 $\sigma^2(1-\alpha_1^2-\alpha_2^2)$。

因此，MA(q) 预测代码可以实现为：
```
quantQ.ts.forecastMA:{data;q};
// 用于预测 AR
// lags 模型的历史数据（浮点列表）
// q -- MA 数
est:(q+2)#0f;
v:(q+1);q+1)#0f;
alpha:(q+1;q+1)*0f;
v[0]:.quantQ.ts.gamma[0;data];
n:1;
k:0;
while[n<=q]; {
  k:0;
  while[k<n]; {
    j:0; s:0f;
    while[j<k] {
      s:s+(alpha[k-j]*alpha[n-j]*v[j]);
      j:j+1;
    }
    ];
    alpha[n-k]:..quantQ.ts.gamma[n-k;data] - s)%v[k];
  k:k+1;
  s:0f; j:0;
  while[j<n] {
    s:s+(alpha[n-j] xexp 2)*v[j]);
    j:j+1;
  }
  ];
  v[n]:..quantQ.ts.gamma[0;data]-s;
}
n:n+1;
alpha[p-1;p+1];
```

# 时间序列计量经济学
# 285
```cpp
// MA(q) 的一步预测器
n;
while[n <= q] {
  j=1;s=0;
  while[j <= n] {
    s=s+(alpha[n]*(data[j]-est[j]));
    j=j+1;
  }
  est[n+1]=s;
  n=n+1;
  s=0;
}
_est;
```
ARMA 过程的预测遵循相同的原理。给定 ARMA 过程
$X_t = \Phi_1 X_{t-1} + ... + \Phi_p X_{t-p} + \epsilon_t + \alpha_1 \epsilon_{t-1} + ... + \alpha_q \epsilon_{t-q}$，
一步前预测为 $X_{n+1} = \Phi_1 X_n + ... + \Phi_p X_{n-p+1} + (\epsilon_{n+1} = 0) + \alpha_1 \epsilon_n + ... + \alpha_q \epsilon_{n-q+1}$。两步前预测为 $X_{n+2} = \Phi_1 X_{n+1} + ... + \Phi_p X_{n-p+2} + (\epsilon_{n+2} = 0) + \alpha_1(\epsilon_{n+1} = 0) + ... + \alpha_q \epsilon_{n-q+2}$。三步前预测为 $X_{n+3} = \Phi_1 X_{n+2} + ... + \Phi_p X_{n-p+3} + (\epsilon_{n+3} = 0) + \alpha_1(\epsilon_{n+2} = 0) + \alpha_2(\epsilon_{n+1} = 0) + ... + \alpha_q \epsilon_{n-q+3}$。$q+1$ 步前预测为 $X_{n+q+1} = \Phi_1 X_{n+q} + ... + \Phi_p X_{n-p+q+1} + (\epsilon_{n+q+1} = 0) + \alpha_1(\epsilon_n = 0) + ... + \alpha_q(\epsilon_{n+1} = 0)$。我们清楚看到移动平均项是依赖的。该函数的实现留给读者作为进阶练习题。函数 `.quantQ.ts.forecastARMA` 需要修改以处理 ARMA 情况。

## 14.2 平稳性与格兰杰因果

### 14.2.1 平稳性

如果一个随机过程的统计特性不随时间变化，则称该过程是平稳的。形式上，时间序列 $X_t, t \in \mathbb{Z}$ 是弱平稳或宽平稳的，当：
- 它具有有限方差 $Var(X_t) < \infty$ $\forall t \in \mathbb{Z}$。
- 均值为常数：$\mu_X(t) = \mu$，$\forall t \in \mathbb{Z}$。
- 自协方差不依赖于 $t$：$Cov(X_t, X_{t+h}) = Cov(X_{t+r}, X_{t+r+h})$，$\forall r \in \mathbb{Z}$。

如果对于任何 $k \geq 1$ 和 $(n_1, ..., n_k, t) \in \mathbb{Z}$，任何有限集合 $(X_{n_1}, ..., X_{n_k})$ 与 $(X_{n_1+t}, ..., X_{n_k+t})$ 具有相同的分布，则称该过程是严格平稳的。

## 平稳性检验 – Dickey-Fuller 和广义 Dickey-Fuller 检验

Dickey-Fuller (DF) 检验自回归模型中存在单位根的假设。该检验估计了三个模型：
- 第一模型是不带常数项 AR(1) 过程：$y_t = \rho_1 y_{t-1} + \epsilon_t$。
- 第二模型是带常数项 AR(1) 过程：$y_t = \beta_2 + \rho_1 y_{t-1} + \epsilon_t$。
- 第三模型在 AR(1) 中添加趋势项：$y_t = \mu_1 + \beta_3 t + \rho_1 y_{t-1} + \epsilon_t$。

第一模型可以重写为 $\Delta y_t = (\rho_1 - 1)y_{t-1} + \epsilon_t$，第二模型为 $\Delta y_t = \mu_1 + \Phi_2 y_{t-1} + \epsilon_t$，第三模型为 $\Delta y_t = \mu_2 + \beta_3 t + \Phi_1 y_{t-1} + \epsilon_t$。

ADF 检验检验 AR(1) 过程的稳定性。该检验可以扩展以检测 AR(p) 的单位根，即广义 Dickey-Fuller (ADF) 检验。ADF 估计三个模型：
- 不带常数项 AR(p) 模型：$\Delta y_t = \Phi_1 y_{t-1} + \sum_{j=2}^p \beta_j y_{t-j} + \epsilon_t$。
- 带常数项 AR(p) 模型：$\Delta y_t = \mu_1 + \Phi_1 y_{t-1} + \sum_{j=2}^p \beta_j y_{t-j} + \epsilon_t$。
- 带常数项和趋势的 AR(p) 模型：$\Delta y_t = \mu_2 + \beta_3 t + \Phi_1 y_{t-1} + \sum_{j=2}^p \beta_j y_{t-j} + \epsilon_t$。

ADF 检验的零假设是变量 $y_t$ 非平稳（单位根），即 $\phi=0$。ADF 检验使用 MacKinnon (1996) 给出的统计量。如果 $t_{obs} < ADF_{critical}$，则拒绝非平稳假设。AR(p) 的最优阶数通过线性回归确定并用 `.quantQ.ols AIC` 实现：为了确定是否保留带常数的单位根假设，与常数项 $\mu_i$ 相关的 t 统计与表值进行比较。对于第三模型，ADF 检验检查与常数项 ($\mu_2$) 和趋势 ($\beta_3$) 相关的系数是否显著异于零，零假设为 $H_0: \mu_2=0$ 和 $H_0: \beta=0$。

时间序列的 $\Delta$ 仅为差分。它们的自回归模型可以用 `.quantQ.ols` 估计。MacKinnon 给出的统计量表值可以存储在字典中，并用 `.quantQ.fit` 实现的 t 统计量 $t_{obs}$ 计算。

为止介绍的模型是局限的。它们只使用随机变量的观测值来解释其当前和未来值。除了使用过去值，可以通过添加外部因子（也称为外生变量）来改进模型。带有外生变量的 p 自回归过程记为 ARX(p)，由给出：
```math
Y_t = a_0 + a_1Y_{t-1} + ... + a_pY_{t-p} + b_1X_{t-1} + ... + b_pX_{t-p} + \epsilon_t. (14.19)
```
同样，ARX(p,q) 过程定义为：
```math
Y_t = a_0 + \sum_{i=1}^p a_iY_{i-i} + \sum_{i=1}^p b_iX_{t-i} + \sum_{j=1}^q c_j\epsilon_{t-j}. (14.20)
```
这两个带有外生变量的模型参数可以使用与其基础模型相同的方法进行估计。为了确定外生变量的滞后值是否解释随机变量的当前和未来值，我们引入了格兰杰因果检验。格兰杰因果检验是一种统计假设检验，用于确定外部序列 $X(t)$ 对预测另一个 $Y(t)$ 是否有用。如果通过对 $X$ 的滞后值运行 t 检验或 F 检验，显示 $X$ 的历史值提供了关于 $Y$ 未来值的统计显著信息，则称时间序列 $X$ 是 $Y$ 的 Granger。要找出 X 是否导致 Y，我们将 AR(p) 模型与相应的 ARX(p) 模型比较，并在零假设 $H_0, b_1 = ... = b_p = 0$ 下对单个系数进行 t 检验，对应备择假设 $H_1$（即至少有一个系数非零）。

我们可以运行 F 检验：
```math
F = \frac{\frac{(R^2_{fullModel} - R^2_{restrictedModel})}{nbAdditionalVariables}}{\frac{1}{nObs - nParamsFullModel}}.
```
并与 $F^*(nbAddedParams, nObs - nParamsFullModels)$ 比较。如果 $F > F'$，则拒绝不存在格兰杰因果的零假设。注意，格兰杰因果存在以下局限性：
- 格兰杰因果并不一定成立
- 当 $X$ 影响 $Y$ 时，格兰杰因果并不总是真实的
- F 检验在之前的章节中介绍过。

## 14.3 向量回归

本章将单变量自回归过程推广到捕捉多个序列之间的线性依赖关系。简单来说，向量回归模型是 AR(p) 过程的泛化，其中 $X_t$ 被替换为向量。

### 14.3.1 VAR(p) 过程

p 阶自回归过程给出：
```math
Y_t = \nu + A_1Y_{t-1} + ... + A_pY_{t-p} + \epsilon_t, (14.21)
```
