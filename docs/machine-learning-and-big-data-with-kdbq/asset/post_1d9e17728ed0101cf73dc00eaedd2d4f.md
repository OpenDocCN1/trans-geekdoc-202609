
# 294
# DATA SCIENCE

The estimator of the variance-covariance matrix of residual (14.23) is implemented as follows:

```
quantQ.ts.covarianceResidual:[{y;p}
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
T:(count y[0]-p);
K:count y;
coef:1/(T-K+p)-1);
:coef.(quantQ.ts.Y[y;p] - mmu flip quantQ.ts.Z[y;p]) - 
(quantQ.ts.Y[y;p] mmu flip quantQ.ts.Z[y;p]) mmu
inv.(quantQ.ts.Y[y;p] mmu flip quantQ.ts.Z[y;p]) mmu
(quantQ.ts.Z[y;p] mmu flip quantQ.ts.Y[y;p]);
;
```

The Likelihood Ratio test statistic used to determine the optimal order of the VAR(p) model is implemented in quantQ.varOrder[y;m] as a function of the least square or the maximum likelihood estimator of (14.26). The function returns a three of columns. The first column p returns the order of the VAR(p) model, the second column $\lambda_{LR}(p)$ as given in (14.25) and the third p-value of $\lambda_{LR}(p)$.

First, we implement the identity of rank k:

```
quantQ.ts.eye:[k]
// k -- rank of matrix
//float$(til k)=:til k;
;
```

Then, we provide a definition of the least square estimator of the error:

```
quantQ.ts.beta:[{y;p}]
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
:coef(count(count y[0]-p)) - ((flip quantQ.ts.Z[y;p]) mmu
(quantQ.ts.eye[count y[0]-p]) mmu flip quantQ.ts.Z[y;p]) mmu
inv.(quantQ.ts.Z[y;p] mmu flip quantQ.ts.Z[y;p]) mmu
(quantQ.ts.Z[y;p]) mmu flip quantQ.ts.Y[y;p]);
;
```

The estimator of the optimal order of the VAR model returns:

```
quantQ.ts.varOrder:[{y;m}]
// y -- historical data (list of floating numbers)
// m -- maximum order of the VAR process
T:count y;
K:count y;
i:m;
k:v1:v2();
while(i>0)
	tr:1(log quantQ.ts.mat.det[quantQ.ts.beta[y-1]])-(log quantQ.mat.
		det[quantQ.ts.beta[y;i]]);
	k:(m-i);
v1:v1;
v2:v2.quantQ.ts.pValueChi[1lr;K*K];
i:i-1;
((p:k)v1:pvalue=v2);
;
```

The p-value of a $\chi^2$ distribution with $k$ degrees of freedom is approximated using the formula

$$\frac{e^{v-u}}{\sqrt{2\pi}} \left(\frac{u}{v}\right)^v \left(1-\frac{v-1}{p^2+2u}\right) \left(\frac{12v^{3/2}}{12v+1}\right), \quad (14.27)$$

with $u = \frac{x^2}{2}, 2k$ and $p = u-v+1$ described in Gray et al. (1969) and implemented

```
quantQ.ts.pValueChi2([[chi;nu]
// chi - instance of distribution (floating)
// nu - degrees of freedom of the Chi2 distribution
u:chi%%2f;
nu%%2f;
p:(u-v)+1f;
p:3.141592654;
term1:exp[-v]*p*sqrt([2*pi]);
term2:(u-v)*xexp v;
term3:1f-(v-1))*((p+2*u);
term4:(12*v*xexp 1.5f))*((12*v)+1);
term1+term2+term3+term4;
```
```

The matrix of t-ratio (14.24) indicating the statistical significance of the coefficients of the $VAR(p)$ model is implemented as a function of the t-statistic:

```
quantQ.ts.tstat:[y;p]
// y - historical data (list of floating numbers)
// p - order of the VAR(p) process
// quantQ.ts.kron[quantQ.ts.covarianceResidual[y;p]]; inv.[quantQ.ts.Z[y];
// p mmu
flip.quantQ.ts.Z[y;p]];
```

```
quantQ.ts.tRatios:[{y;p}
// y - historical data (list of floating numbers)
// p - order of the VAR(p) process
varp:quantQ.ts.varpest[y];
diag:(count varp[0])*sqrt[quantQ.ts.tstat[y;p]];
varp&diag;
```

where the Kronecker product and the diagonal of a matrix are:

```
quantQ.ts.kron:[a;b]
// a - matrix of floating numbers
// b - matrix of floating numbers
// calculating Kronecker product
nbcols:(count b[0])*(count a[0]);
nbrows:(count b[0])*(count a[0]);
:(nbrows,nbcols)*(raze) [[i;a;b]]/(flip (flip a[b];i\:b))[a;b]
```
quantQ.ts.diag:[m]
// m -- array of numbers to put on diagonal
:{i,m] each count m;

The 1-step and n-step forecasts estimate the coefficients B of VAR(p) model based on the data and predict its future values. First, the implementation of 1-step forecast reads:

```
quantQ.ts.estimate1:{y;p}
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
b..quantQ.ts.varpest[y;p];
v:[b];
k: count b
+sum(i;y;k)b[(1+k)]til k
// each p;
```

Further, we implement n-step forecast of VAR(p) model:

```
quantQ.ts.estimateN:{y;p}
// n -- positive integer indicating a n-step ahead forecast
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
output:quantQ.ts.estimat[y;p];[n];
.quantQ.ts.estimateN[n-1;y];output;
```

The accuracy of 1-step forecast is determined with the MSE function:

```
quantQ.ts.forecastMSE:{y;p}
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
T:(count y[0])-p;
k: count y;
coef:(T+p)+1
*.quantQ.ts.covarianceResidual[y;p];
```

The 95% confidence interval of 1-step forecast is:

```
quantQ.ts.confinterval:{y;p}
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
se:1.96*sqrt[quantQ.ts.diag[.quantQ.ts.forecastMSE[y;p]]];
forecast:.quantQ.ts.estimate1[d;2];
// flip ((forecast-mse);(forecast+mse));
```

# 2. VARX($p, q$) Process

The VAR model assumes that all stochastic variables of a system ($A_i$ in our case) have essentially the same status that they are all determined within the system. In practice, a VAR model only past its future values, the generation process may be affected by other observable variables which are determined outside the system of interest. Such variables are called exogenous or unmodel variables. In contrast, the variables determined within the system are called endogenous. A vector autoregressive process with exogenous variables VARX($p, q$) has the following form:

```
$Y_t = A_1Y_{t-1} + \dots + A_pY_{t-p} + B_0x_t + \dots + B_qx_{t-q} + u_t, \quad (14.28)$
```

where $A_i, i=1..p$ and $B_j=0..q, Y_t = (y_{1t}, \dots, y_{Kt})$ is a $K$-dimensional vector of endogenous variables, $x_t = (x_{1t}, \dots, x_{Mt})$ is an $M$-dimensional vector of exogenous variables and $u_t$ is white noise.

These types of models are also called transfer functions or distributed lag. In lag operator notation, the reduced form can be written as:

```
$A(L)y_t = B(L)x_t + u_t,$
```

where $A(L) := I_K - A_1L - \dots - A_pL^p$ and $B(L) := B_0 + B_1L + \dots + B_qL^q$. The final form of the system is given by:

```
$y_t = D(L)x_t + A(L)^{-1}u_t,$
```

where $D(L) := A(L)^{-1}B(L)$. The coefficient matrices $D_i$ of transfer operator contain the effects that in the exogenous variables have on the endogenous variables.

# 14.3.21 Estimator

The reduced form of a VARX($p, q$) model can be rewritten as:

```
$y_t = AY_{t-1} + Bx_{t-1} + B_0x_t, \quad (14.29)$
```

where $A = [A_1, \dots, A_p]$ and $B = [B_0, \dots, B_q]$.

# 298 DATA SCIENCE

The generalised least squares (GLS) estimator of y is:

# Code

The implementation of VARX(p,q) model closely follows the structure of the VAR(p) process. The function quantQ.ts.varX provides the unbiased estimate of VARX(p,q) model. It uses an extension of the vectorisations $Y$ and $Z$. Below is a defined set of functions:

```
quantQ.ts.zt::[y;t;p;flag]
// y0 -- vectorisation of y0
// t -- time (positive integer)
// p -- number of lags (positive integer)
// flag -- boolean value whether a leading 1 needs to be set
:$flag;
  if,quantQ.ts.vec[y;(t-1)-til p]];
    .quantQ.ts.vec[y;(t-1)-til p]];
```

```
;
```

```
quantQ.ts.Z::[y;p;flag]
// y -- historical data of the endogenous variable (list of floating numbers)
// p -- order of the VAR(p) process
// flag -- boolean value whether a leading 1 needs to be set
for z;
  flip [y;i;flag].quantQ.ts.Z[y;i;flag];y;p;flag] each p + til (
    count y[0]-q);
```

```
;
```

```
quantQ.ts.ZX::[x;y;p]
// x -- historical data of the exogenous variable (list of floating numbers)
// y -- historical data of the endogenous variable (list of floating numbers)
// q -- order of exogenous process
// p -- order of the VAR(p) process
  :.quantQ.ts.Z[y;p;1b],quantQ.ts.Z[x;q;0b],x[q+til(count x[0])-q
```

```
;
```
```

![](img/97f7581128bd0bdf85683d4c69d94242_322_0.png)
