
## TABLE 6.2 The Computed Values and Absolute Errors, in Brackets, for European Options on the Minimum of Three Assets. Monte Carlo Simulation was used with Quasi (Sobol) Sequences and Pseudorandom Sequences. The Number of Paths Used from 500 to 3000. The Parameters were $E = 100.0, S_1 = S_2 = S_3 = 100.0, r = 0.1, t = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = 0.2, \rho_{12} = \rho_{23} = 0.5,$ and $q_1 = q_2 = q_3 = 0.0$. The Accurate Values were 7403 for a Put and 5249 for a Call, See Table 6.8 and Table 2 of Boyle Evnin and Gibbs (1989)

| nsim | Quasi | Pseudo | Quasi | Pseudo |
|---|---|---|---|---|
| 500 | 7.365 ($3.8122 \times 10^{-2}$) | 7.7670 ($2.7298 \times 10^{-1}$) | 5.312 ($6.3431 \times 10^{-2}$) | 5.3086 ($5.9591 \times 10^{-2}$) |
| 1000 | 7.425 ($2.1554 \times 10^{-2}$) | 7.7607 ($3.5772 \times 10^{-3}$) | 5.293 ($4.3958 \times 10^{-2}$) | 5.4376 ($1.8887 \times 10^{-1}$) |
| 1500 | 7.408 ($5.1232 \times 10^{-3}$) | 7.5654 ($1.6240 \times 10^{-3}$) | 5.253 ($4.0761 \times 10^{-3}$) | 5.4121 ($1.6307 \times 10^{-3}$) |
| 2000 | 7.399 ($3.6364 \times 10^{-3}$) | 7.4820 ($7.8995 \times 10^{-2}$) | 5.266 ($1.7726 \times 10^{-2}$) | 5.4029 ($1.5390 \times 10^{-1}$) |
| 2500 | 7.407 ($4.1463 \times 10^{-3}$) | 7.3592 ($4.3574 \times 10^{-2}$) | 5.267 ($1.7707 \times 10^{-2}$) | 5.4690 ($2.2005 \times 10^{-1}$) |
| 3000 | 7.400 ($2.7166 \times 10^{-3}$) | 7.3997 ($3.3236 \times 10^{-3}$) | 5.245 ($3.5024 \times 10^{-3}$) | 5.4331 ($1.8407 \times 10^{-1}$) |

requires hundreds of thousands of simulations to ensure an accuracy of $10^{-1}$ or $10^{-2}$ in the estimated option price. It is because that various Monte Carlo variance reduction techniques are used to increase the accuracy of the computed integral.

In this section, we show how to price a three-asset basket option using Monte Carlo simulation; the accuracy of the results obtained with quasirandom numbers and pseudorandom numbers is compared.

We consider European put and call options on the maximum and minimum of three assets. All the options have a maturity of one year, and the model parameters used are given in Tables 6.1 and 6.2.

In Code 6.1, most of the work is given by the routine multivariate_normal generates a vector of multivariate pseudorandom numbers with a particular covariance matrix. In the program the values of the assets at current time, $S_1 = S_2 = S_3 = 100$, and the option motions in year.

The asset process follows

```
$dY_i = \log(S_{i,t+dt}) - \log(S_{i,t}) \ dt + \sigma_i dW_i, \quad i = 1, \dots, m,$
```

where have used the notation $S_{i,t}$ to denote the value of the $i$th asset at current time t, and $S_{i,t+dt}$ to denote the value of the asset at the future time $t+dt$. Simple rearrangement of the above equations gives

```
log\left(\frac{S_{i,t+dt}}{S_{i,t}}\right) = (r - \sigma_i^2/2) dt + \sigma_i dW_i, \quad i = 1, \dots, m.
```

Taking exponentials of both sides, we obtain

```
$S_{i,t+dt} = \exp\{(r - \sigma_i^2/2) dt + \sigma_i dW_i\}, \quad i = 1, \dots, m.$
```

which is equivalent to

```
$S_{i,t+dt} = S_{i,t} \exp\{(r - \sigma_i^2/2) dt + \sigma_i dW_i\}. \quad (6.3.1)
```

**Code 6.1** A Monte Carlo simulation program, using pseudorandom numbers, for estimating the value of European put and call options on the maximum and minimum of three assets. The results are presented in Tables 6.1 and 6.2.

```
C(2,2) = tmp1;
C(3,1) = tmp3;
C(1,2) = signal1*signal2*time_step*rho_12;
C(2,3) = signal2*signal3*time_step*rho_23;
C(1,3) = signal1*signal3*time_step*rho_13;
C(2,1) = C(1,2);
C(3,1) = C(1,3);
C(3,2) = C(2,3);
tmp = (r - signal1*half)*time_step;
tmp2 = (r - signal2*half)*time_step;
tmp3 = (r - signal3*half)*time_step;
MEAN(1) = tmp1;
MEAN(2) = tmp2;
MEAN(3) = tmp3;
sum_max_put = zero;
sum_max_call = zero;
sum_min_put = zero;
sum_min_call = zero;
tol = 1.0;
seed(1);
if (!is_call) { /* initialization to the random number generator */
multivariate_normal(is_call,MEAN,C(1,3),tol,&Arvec(i),&flag);
num_simulations = 6666;
if (!is_call) {
for (i = 1; i < num_simulations; i++) {
/* calls to random generator */
multivariate_normal(is_call,MEAN,
  ST1 = exp(1);
  ST2 = exp(2);
  ST3 = exp(3);
  // options on the maximum
  tmp2 = MIN(ST1,ST2);
  the_max = MAX(tmp2,0);
  opt_call = MAX(tmp1,zero);
  sum_max_call += opt_call*disc;
  tmp1 = the_max;
  opt_val = MAX(tmp1,zero);
  sum_max_put += opt_val*disc;
  // options on the minimum
  tmp2 = MAX(ST1,ST2);
  the_min = MIN(tmp2,0);
  tmp1 = the_min;
  opt_call = MIN(tmp1,zero);
  sum_min_call += opt_call*disc;
  tmp1 = the_min;
  opt_val = MIN(tmp1,zero);
  sum_min_put += opt_val*disc;
}
opt_val = sum_max_put/num_simulations;
opt_val = sum_max_call/num_simulations;
opt_val = sum_min_put/num_simulations;
opt_val = sum_min_call/num_simulations;
}
```

## 6.4 INTRODUCTION TO MULTIDIMENSIONAL LATTICE METHODS

Finite difference lattices can be used to value options on four assets before they require increasingly large amounts of computer memory. The advantage of finite difference method is that they easily cater for American style early exercise. This is not true of Monte Carlo methods. They can easily model complex European options but have difficulty modelling American style.

In this section, we use the approach of Kamrad and Reiche (1991), and Boyle and Gibbs (1989), which we will call the BEGR method, for multi-asset options. We first derive expressions for the jump size and jump probabilities for a single asset and show that these are equivalent to those of the CRR lattice discussed in Chapter 5. We will then give expressions for the jump sizes and jump probabilities of a general multi-asset option.

To derive the BEGR equations for one asset, we first assume that the asset follows a lognormal process with drift $\mu=r-\sigma^2/2$, where $r$ is the riskless interest rate and $\sigma$ is the instantaneous volatility.

Therefore, if $S_t$ is the price of the asset at time $t$, and $S_{t+\Delta t}$ is the price at time $t+\Delta t$, we have the following:

```
log(S_{t+\Delta t}) = log(S_t) + \epsilon_t, \quad \epsilon_t \sim N(\mu\Delta t, \sigma^2\Delta t),
```

or equivalently

```
log\left(\frac{S_{t+\Delta t}}{S_t}\right) \sim N(\mu\Delta t, \sigma^2\Delta t),
```

where $\epsilon_t$ represents a random variable and as $N(\mu\Delta t, \sigma^2\Delta t)$ denotes a Gaussian with mean $\mu\Delta t$ and variance $\sigma^2\Delta t$.

We will now consider the situation when $\epsilon_t$ either jumps up or down by an amount $\nu = \sigma\sqrt{\Delta t}$. For an up-jump,

```
log\left(\frac{S_{t+\Delta t}}{S_t}\right) = \sigma\sqrt{\Delta t},
```

and therefore, $S_{t+\Delta t} = S_t\exp(\sigma\sqrt{\Delta t})$.
For a down-jump, we have

```
log\left(\frac{S_{t+\Delta t}}{S_t}\right) = -\sigma\sqrt{\Delta t},
```

and therefore, $S_{t+\Delta t} = S_t\exp(-\sigma\sqrt{\Delta t})$.
The reader will notice that these expressions are the same as for the CRR lattice of Chapter 5. That is for an up-jump, $S_{t+\Delta t} = S_tu$, and for a down-jump, $S_{t+\Delta t} = S_td$ and $u = 1/d = \exp(\sigma\sqrt{\Delta t})$.

The probability undergoing either an up- or down-jump occurring by finding the mean and variance of $\epsilon_t$.

From the mean,

```
E[\epsilon_t] = v(p_u - p_d) = \mu\Delta t,
```

and from the variance,

```
Var[\epsilon_t] = v^2(p_u + p_d) = \sigma^2\Delta t.
```
