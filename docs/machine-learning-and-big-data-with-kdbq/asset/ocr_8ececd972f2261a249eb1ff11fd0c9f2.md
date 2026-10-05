Given the function .quantQ.ts.toeplitz to build the Toeplitz matrix (14.12) of sample autocovrelation .quantQ.ts.r, first, we define the sample autocovariance function of order h:

```
.quantQ.ts.gamma[[h;data]
// order of autocovrelation
// data -- data
// :neg[h]_data cov (h _data);
;
```

then the sample autocorrelation function of order h:

```
.quantQ.ts.r[[data;h]
// order of autocovrelation
// data -- data
// :quantQ.ts.data]%.quantQ.ts.gamma[0;data];
;
```

and, finally, the Toeplitz matrix:

```
.quantQ.ts.toeplitz::[data;p]
// data -- historical data (list of floating numbers)
// p -- order of the AR(p) process
tabs (p;p)="[x;data](til p);\quantQ.ts.r[data;x]][data] raze t;
;
```

The Yule-Walker equations can be solved as:

```
.quantQ.ts.yuleWalker::[data;p]
// data -- historical data (list of floating numbers)
// p -- order of the AR(p) model
inv[.quantQ.ts.toeplitz[data;p]] mmu {.quantQ.r[data;data]] each 1+til p
~;
```

Finally, the OLS estimator (14.6) can be implemented as:

```
.quantQ.ts.estAR::[data;p]
// data -- historical data (list of floating numbers) used to estimate
// p -- order of the AR(p) model
n:count_data;
dim:(n-p,p+1);
x:dim=0f;
i:0;j:1;
while i<(n-p);
x[i:0]:1f;
while j<p+1;
$0<=i-j;
x[i;j]:data[i-j];nx[i;j]:0f;
j:j+1;
```