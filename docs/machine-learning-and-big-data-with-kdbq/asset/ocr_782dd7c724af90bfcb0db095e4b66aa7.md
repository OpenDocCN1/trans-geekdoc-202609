# 284

# DATA SCIENCE

The one-step forecast is:

$X_{n+1} = c + \varepsilon_{n+1} + \alpha_1\varepsilon_n + \alpha_2\varepsilon_{n-1}$
$\hat{X}_{n+1} = c + \alpha_1\varepsilon_n + \alpha_2\varepsilon_{n-1}$,

with $e_{n+1} = X_{n+1} - \hat{X}_{n+1}$ and $Var(X_{n+1} - \hat{X}_{n+1}) = \sigma$. The two-step forecast solves:

$X_{n+2} = c + \varepsilon_{n+2} + \alpha_1\varepsilon_{n+1} + \alpha_2\varepsilon_n$
$\hat{X}_{n+2} = c + 0 + \alpha_1 \cdot 0 + \alpha_2\varepsilon_n$.

The forecasted error is $X_{n+2} - \hat{X}_{n+2} = \varepsilon_{n+2} + \alpha_1\varepsilon_{n+1}$. The variance of $Var(X_{n+2} - \hat{X}_{n+2}) = \sigma^2(1-\\alpha_1^2)$. The three-step forecast:

$X_{n+3} = c + \varepsilon_{n+3} + \alpha_1\varepsilon_{n+2} + \alpha_2\varepsilon_{n+1}$
$\hat{X}_{n+3} = c$.

The forecasted error $Var(X_{n+3} - \hat{X}_{n+3}) = \varepsilon_{n+3} + \alpha_1\varepsilon_{n+2} + \alpha_2\varepsilon_{n+1}$ and the variance of the error is $\sigma^2(1-\\alpha_1^2-\alpha_2^2)$.

The code to forecast $MA(q)$ model can, therefore, be implemented as:

```
quantQ.ts.forecastMA: {[data;q];
// historical data (list of floating) used to forecast the AR(
// lags model
// q -- degree of MA
est:(q+2)#0f;
v:(q+1);q+1)#0f;
alpha:(q+1);q+1)#0f;
v[0]:..quantQ.ts.gamma[0;data];
n:1;
k:0;
while[n<=q]; {
  k:0;
  while[k<n]; {
    j:0; s:0f;
    while[j<k]; {
      s:s+(alpha[k-j]*alpha[n-j]*v[j]);
      j:j+1;
    }
    ];
    alpha[n-k]:..quantQ.ts.gamma[n-k;data] - s)%v[k];
  k:k+1;
  s:0f; j:0;
  while[j<n]; {
    s:s+(alpha[n-j]*xexp 2)*v[j]);
    j:j+1;
  }
  ];
  v[n]:..quantQ.ts.gamma[0;data]-s;
}
n:n+1;
```