# 298 DATA SCIENCE

The generalised least squares (GLS) estimator of y is:

```
$\hat{y} = [R'(ZZ'\Sigma_{u}^{-1})R]^{-1}R'(Z\Sigma_{u}^{-1})y$.
```

The variance-covariance matrix of the residual $\Sigma_{u}$ is unknown and can be estimated by OLS. Given the residuals $\hat{u} = \text{vec}(\hat{y})=y-(Z \otimes I_{k})R$, the estimated generalised least squares (EGLS) estimator of y becomes:

```
$\hat{y} = [R'(ZZ'\Sigma_{u}^{-1})R]^{-1}R'(Z\Sigma_{u}^{-1})y$.
```

with $\Sigma_{u} = UU'/T$.

# 14.3.2 Code

The implementation of the VARX(p,q) model closely follows the structure of the VAR(p) process. The function .quantQ.ts.varX provides the unbiased estimate of the VARX(p,q) model. It uses an extension of the vectorisations $Y$ and $Z$ of the VAR(p). Below is a defined set of functions:

```
.quantQ.ts.zt::[y;t;p;flag]
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
.quantQ.ts.Z::[y;p;flag]
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
.quantQ.ts.ZX::[x;y;p]
// x -- historical data of the exogenous variable (list of floating numbers)
// y -- historical data of the endogenous variable (list of floating numbers)
// q -- order of exogenous process
// p -- order of the VAR(p) process
  :.quantQ.ts.Z[y;p;1b],quantQ.ts.Z[x;q;0b],x[q+til(count x[0])-q
```

```
;
```

![](bbox=[0.107, 0.933, 0.894, 0.966])