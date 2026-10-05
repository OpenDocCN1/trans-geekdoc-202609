

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
:1_phi[p-1];
```

给定函数 .quantQ.ts.toeplitz 用于构建样本自协方差 .quantQ.ts.r 的 Toeplitz 矩阵 (14.12)，首先，我们定义阶数为 h 的阶样本自协方差函数：

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

递归函数 .quantQ.ts.matrix 将序列 d 堆叠到矩阵中计算 [d-q];d[t-q];...d[t-1]：

```
.quantQ.ts.matrix:{t;q}
// t 索引
// q MA(q) 过程阶数
// d 序列
$[q=1]; d[t-q].quantQ.ts.matrix[t-q;d];d[t-1];
```

ARMA(p,q) 过程估计量的实现留给读者作为练习。可以通过 ARMA(p,q) 过程的 Yule-Walker 选择或通过调整 Hannan-Rissanen 算法来估计。

## 14.6.3 预测

通用函数 .quantQ.ts.forecast[data;period;process;lags] 根据数据集 data 预测阶数为 lags 的过程未来 period 步。参数 data 是浮点数列表。参数 process 是一个正整数。变量包含自回归过程的 AR 值、移动平均过程的 MA 值或自回归移动平均的 AR 值。第四个参数是正整数或 ARMA(p,q) 模型的两个整数列表。

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
quantQ.ts.forecastMA:{data;q];
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

