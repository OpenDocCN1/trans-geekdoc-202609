# 180 CHAPTER | 6 Multi-asset Options

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
tol = 1.0-8;
sndseed(1);
if (!is_call) { /* initialisation to the random number generator */
multivariate_normal(is_call,MEAN,3,C(1,3),tol,&Arvec(i),&flag);
num_simulations = 6666;
if (!is_call) {
for (i = 1; i < num_simulations; i++) {
/* calls to the random number generator */
multivariate_normal(is_call,MEAN, 
ST1 = exp(1);
ST2 = exp(2);
ST3 = exp(3);
// options on the maximum
tmp2 = MIN(ST1,ST2);
the_max = MAX(tmp2,0);
opt_call = MAX(tmp1,zero);
sum_max_call += opt_call*disc;
tmp1 = X-the_max;
opt_val = MAX(tmp1,zero);
sum_min_put += opt_val*disc;
// options on the minimum
tmp2 = MAX(ST1,ST2);
the_min = MIN(tmp2,0);
tmp1 = X-the_min;
opt_val = MIN(tmp1,zero);
sum_min_call += opt_val*disc;
tmp1 = X-the_min;
opt_val = MIN(tmp1,zero);
sum_min_put += opt_val*disc;
}
}
opt_val = sum_max_put(double)/num_simulations;/* put option value on the maximum of three assets */
opt_val = sum_max_call(double)/num_simulations;/* call option value on the maximum of three assets */

opt_val = sum_min_put(double)/num_simulations;/* put option value on the minimum of three assets */
opt_val = sum_min_call(double)/num_simulations;/* call option value on the minimum of three assets */
}
```

**Code 6.1 (Continued).**

# 6.4 INTRODUCTION TO MULTIDIMENSIONAL LATTICE METHODS

Finite difference lattices can be used to value options on about four assets before they require increasingly large amounts of computer memory. The main advantage of finite difference method is that they are easily cater for