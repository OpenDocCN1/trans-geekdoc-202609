
Monte Carlo simulation: 3 dimensional Black-Scholes, The results are compared with those_
George Levy: 2007

```c
* long_seed,num_simulations,iflag;
double time_step,sqrt_time_step,rho = 0.0,half = 0.5;
double r_opt,val_opt,call;
double sum_max_put,ST0, ST2, ST3, ST4, S1, S2, S3, S4;
double sum_min_put,sum_min_call;
double v = (double)1.0;
double rho_12,rho_13,rho_23;
double c3 = "c", "s", "std",
ndouble tmp2,tmp3,tmp4,sigma1,sigma2,sigma3,sigma4;
long is_fcall=0;
```

```c
#define MEANS(I) means[I-1]
#define XBAR(I) xbar[I-1]
#define Z(I) z[I-1]
#define STD(I) std[I-1]
#define C(I,J) c[(I-1) * 3 + ((J)-1)]

seed = 11;
r = 0.1;

signal = 0.2;
sigma2 = 0.2;
sigma3 = 0.2;
S1 = 100.0;
S2 = 100.0;
S3 = 100.0;
X = 100.0;

rho_12 = 0.5;
rho_13 = 0.5;
rho_23 = 0.5;

time_step = 1.0;
sqrt_time_step = sqrt(time_step);
disc = exp(-r*time_step);

c3 = ALLOCATE(3*3, double);
means = ALLOCATE(3, double);
z = ALLOCATE(3, double);
std = ALLOCATE(3, double);

if (!(means(I)) || !(std(I)) || !(z(I))) {
printf("Allocation error\n");
}

tmp1 = signal*time_step;
tmp2 = sigma2*time_step;
tmp3 = sigma3*time_step;

C(1,1) = tmp1;
C(2,2) = tmp2;
C(3,3) = tmp3;
C(1,2) = signal*time_step*rho_12;
C(2,3) = sigma3*time_step*rho_23;
C(1,3) = signal*time_step*rho_13;
C(2,1) = C(1,2);
C(3,1) = C(1,3);
C(3,2) = C(2,3);

tmp1 = (r - signal*half)*time_step;
tmp2 = (r - sigma2*half)*time_step;
tmp3 = (r - sigma3*half)*time_step;

MEANS(1) = tmp1;
MEANS(2) = tmp2;
MEANS(3) = tmp3;
```

**Code 6.1** A Monte Carlo simulation program, using pseudo-random numbers, for estimating the value of European put and call options on the maximum and minimum of three underlying assets. The results are presented in Tables 6.1 and 6.2.

## Multiaset options

```c
sumit_max_put = zero;
sumit_max_call = zero;
sumit_min_put = zero;
sumit_min_call = zero;

tol = 1.0e-8;

srand(seed);
if_call = 1; /* initialization call to the random number generator */
multivariate_normal(1,fMEANS(1),3,C3(1),3,tol,&rvec,&Z(1),iflag);

num_simulations = 6000;
if_call = 0;
for (int i = 0; i < num_simulations; i++) {

    /* continuation call to the random number generator */
    multivariate_normal(1,fMEANS(1),3,C3(1),3,tol,&rvec,&Z(1),iflag);

ST1 = exp(Z(1));
ST2 = exp(Z(2));
ST3 = exp(Z(3));
}
// options on the maximum
tmp2 = MAX(ST1,ST2);
tmp_max = MAX(tmp2,ST3);
tmpl = max-X;
opt_val = MAX(tmpl, zero);
sumit_max_call += opt_val*disc;

tmpl = X-min;
opt_val = MAX(tmpl, zero);
sumit_min_put += opt_val*disc;
//// options on the minimum
tmp2 = MIN(ST1,ST2);
tmp_min = MIN(tmp2,ST3);
tmpl = min-X;
opt_val = MAX(tmpl, zero);
sumit_min_call += opt_val*disc;

}
```

opt_val = sumit_max_put/(double)num_simulations; /* put option value on the maximum
of three assets */
opt_val = sumit_max_call/(double)num_simulations; /* call option value on the maximum
of three assets */
opt_val = sumit_min_put/(double)num_simulations; /* put option value on the minimum
of three assets */
opt_val = sumit_min_call/(double)num_simulations; /* call option value on the minimum
of three assets */

## Code example 6.1 (Continued).

If $S_t$ is the price of the asset at time $t$, and $S_{t+\Delta t}$ is the price at $t+\Delta t$, then we define the following equations:

$log(S_{t+\Delta t}) = log(S_t) + \epsilon_t, \quad \epsilon_t \sim N(\mu\Delta t, \sigma^2\Delta t)$

or equivalently

$$\log\left(\frac{S_{t+\Delta t}}{S_t}\right) \sim N(\mu\Delta t, \sigma^2\Delta t)$$

where $\epsilon_t$ represents a random variable as usual $N(\mu\Delta t, \sigma^2\Delta t)$ with mean $\mu\Delta t$ and variance $\sigma^2\Delta t$.

We will now consider the situation when $\epsilon_t$ either jumps up or down by an amount $u = \sigma\Delta t$. For an up jump:

$$\log\left(\frac{S_{t+\Delta t}}{S_t}\right) = \sigma\Delta t$$

and therefore $S_{t+\Delta t} = S_t \exp(\sigma\Delta t)$. While a down jump we have

$$\log\left(\frac{S_{t+\Delta t}}{S_t}\right) = -\sigma\Delta t$$

and therefore $S_{t+\Delta t} = S_t \exp(-\sigma\Delta t)$. The reader will notice that these expressions are the same as for Chapter 5. For an up jump $S_{t+\Delta t} = S_t u$, for a down jump $S_{t+\Delta t} = S_t d$, and $u/d = \exp(\sigma\Delta t)$.

The probability of undergoing an up or down jump can be found by matching the mean and variance of $\epsilon_t$. From the:

$E[\epsilon_t] = u(p_u - p_d) = \mu\Delta t$ (6.4.1)

and the variance:

$Var[\epsilon_t] = u^2(p_u + p_d) = \sigma^2\Delta t$ (6.4.2)

So combining Eqs. (6.4.1) and (6.4.2) we obtain:

$\mu\Delta t + \sigma^2\Delta t = 2u^2p_u$

so

$p_u = \frac{1}{2}\left(\frac{\sigma^2\Delta t}{u^2} + \frac{\mu\Delta t}{u}\right)$

Substituting $u = \sigma\Delta t$ we obtain:

$p_u = \frac{1}{2}\left(1 + \frac{\mu\Delta t}{\sigma}\right)$ (6.4.3)

and using the fact that $p_d = 1 - p_u$ gives:

$p_d = \frac{1}{2}\left(1 - \frac{\mu\Delta t}{\sigma}\right)$ (6.4.4)

We shall now show that this is equivalent to the Cox-Rubinstein–Ross binomial model. For the CRR model (Chapter 5, Eq. (5.3.19)) we have:

$p_u = \frac{\exp(r\Delta t) - d}{u - d}$

expanding $\exp(r\Delta t)$, $u$ and $d$ to order $\Delta t$ we obtain:

$\exp(r\Delta t) \sim 1 + r\Delta t$
$u = \exp(\sigma\Delta t) \sim 1 + \sigma\sqrt{\Delta t} + \frac{\sigma^2}{2}\Delta t$
$d = \exp(-\sigma\Delta t) \sim 1 - \sigma\sqrt{\Delta t} + \frac{\sigma^2}{2}\Delta t$

so

$\exp(r\Delta t) - d \sim r\Delta t + \sigma\Delta t - \frac{\sigma^2}{2}\Delta t$

and

$u - d \sim 2\sigma\sqrt{\Delta t}$

So

$p_u = \frac{\exp(r\Delta t)}{u - d} \sim \frac{r\Delta t + \sigma - \sigma^2/2\Delta t}{2\sigma\sqrt{\Delta t}}$

which simplifies to

$p_u = \frac{1}{2} \left[1 + \frac{\mu\sqrt{\Delta t}}{\sigma}\right]$

and therefore

$p_d = 1 - p_u = \frac{1}{2} \left[1 - \frac{\mu\sqrt{\Delta t}}{\sigma}\right]$

where the expressions for $p_u$ and $p_d$ given in Eqs. (6.4.1) and (6.4.2), respectively. So we have shown, that to first order in $\Delta t$, both the size of the jump and the probability of the jump are the same as the CRR binomial model.

The attractive feature of the BEGKR binomial lattice model is that it can easily be generalized to describe a model consisting of $k assets. Here we will merely quote the results in Kamrad and Ritchen (1991). As before it is assumed that the asset prices follow a multivariate lognormal distribution. Let $\mu_i = r - \sigma_i^2/2$, and $\sigma_i$ be the instantaneous mean and variance, respectively ($i = 1, 2, \dots, k$) and let $\rho_{ij}$ be the correlation between asset $i$ and asset $j$. The binomial model requires $2^k$ possible jumps in the time interval $\Delta t$. The binomial model requires $2^k$ possible jumps in the time interval $\Delta t$.

## 6.5 Asset options

In this section we consider the case of two assets, $S_1$ and $S_2$. We use analytic formulas to price European options on the maximum and minimum of the two assets.
