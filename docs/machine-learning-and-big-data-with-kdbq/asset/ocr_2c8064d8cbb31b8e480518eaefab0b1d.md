# 278

# DATA SCIENCE

The simulation of moving average process (14.13) is computed recursively as follows:

```
.quantQ.ts.simMA:[q,alpha;eps]
// q -- order of the MA(q) process to simulate. q is an integer.
// alpha -- list of parameters of the MA process (alpha1,...,alphaq)
// eps -- list of random numbers
sum flip($q:1);
  ((q_eps,q0);((q-1) _alpha[q-1]*eps,(q-1)=0)),'.quantQ.ts.simMA
  -[q-1];alpha;eps);
  '((q_eps,0);((q-1)_alpha[q-1]*eps));
```

The ARMA(p,q) is given the white noise process ε and list of parameters for autoregressive coefficients ₙ, i ∈ [1,p] and moving average ⵐ, i ∈ [1,q].

```
.quantQ.ts.simARMA:[phi;alpha;eps]
// phi -- list of parameters of the AR(p) process.
// alpha -- list of parameters of the MA(q) process
// eps -- list of random numbers
p:count phi;
q:count alpha;
x:(count eps)#=0;
t:p;
while t:t((count eps);
  x[t]:((x[t-p]+p) mmu phi)+(eps((t-q)+til q mmu alpha);
  t:t+1];
nx;
```

# 14.6.2 Estimation

The generic function quantQ.ts.estimate estimates the coefficients of the autoregressive, moving average and ARMA processes. The function estimates the coefficients on the list of floating numbers provided in the first argument. The second parameter processes the value `AR`, MA or `ARMA` depending on the type of process to be estimated. The third parameter contains either an integer representing the order of the autoregressive or moving average process or a list of two integers for the lags of the ARMA(p,q) process.

```
.quantQ.ts.estimate:[data;process;lag]
// data historical data (list of floating numbers) used to estimate
// the process.
// process -- type of process to simulate. Accepted values: 'AR', 'MA' or
  - ARMA
// lags -- order of the process. integer for AR and MA process. List of
  - two integers for ARMA
$[process=AR];n  [-7h = type lags;
  .:quantQ.ts.DurbinLevinson[data;lags];
$[7h = type lags;
```