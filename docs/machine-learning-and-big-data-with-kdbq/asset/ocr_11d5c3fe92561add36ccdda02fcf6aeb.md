# 294

# DATA SCIENCE

The estimator of the variance-covariance matrix of residual (14.23) is implemented as follows:

```
quantQ.ts.covarianceResidual:[{y;p}
// y -- historical data (list of floating numbers)
// p -- order of the VAR(p) process
T:(count y[0]-p);
K:count y;
coef:1F%(T-K+p)-1f);
:coef.(quantQ.ts.Y[y;p] - mmu flip quantQ.ts.Z[y;p]) - 
(quantQ.ts.Y[y;p] mmu flip quantQ.ts.Z[y;p]) mmu
inv.(quantQ.ts.Y[y;p] mmu flip quantQ.ts.Z[y;p]) mmu
(quantQ.ts.Z[y;p] mmu flip quantQ.ts.Y[y;p]);
;
```

The Likelihood Ratio test statistic used to determine the optimal order of the VAR(p) model is implemented in quantQ.varOrder[y;m] as a function of the least square or the maximum likelihood estimator of (14.26). The function returns a three of columns. The first column p returns the order of the VAR(p) model, the second column $\lambda_{LR}(p)$ as given in (14.25) and the third p-value of $\lambda_{LR}(p).

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