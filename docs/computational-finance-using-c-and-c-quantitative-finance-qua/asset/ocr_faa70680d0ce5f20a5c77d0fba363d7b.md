# Single American Options

```
void dko_call(double lower_barrier, double upper_barrier, double theta_m,
double S0, double sigma_array[], double sigma_times[], long n_sigma, double r,\ouble opt_mat, double X, double option_value, double geeks[], double q,
long n_lower_s0, long n_above_s0, long nt, int iflag)
```

```
// Input parameters
lower_barrier      // the asset price corresponding to the lower barrier
uper_barrier      // the asset price corresponding to the upper barrier
theta_m            // the value used for the finite difference method
s0                // the price of the underlying asset
sigma_array[]      // an array containing the volatility: sigma_array[0] is the
sigma_times[]      // the first volatility and value of the volatility,..
                   // an array containing the time for different volatilities;
sigma_times[0] is the time corresponding to
                   // the second volatility, times[1] is the time corresponding to
n_sigma            // the number of elements in sigma_array[], and sigma_times[];
r                // the interest rate
opt_mat           // the time to maturity
X                // the strike price
q                // the continuous dividend yield
n_lower_s0       // the number of asset intervals between the current price S0,
n_above_s0       // the number of asset intervals above the current price S0,
tnt                // the number of time intervals.
```

```
// Output parameters
option_value      // the value of the option
geeks[]           // the hedges output as follows: geeks[0] is gamma,geeks[1] is delta, and geeks[2] is theta
iflag             // an error indicator
```

```
double a, *b, *c, *vals, *b1, *c1, *opt_vals, *rhs, *z,gamma,work,*u;
double dz,dt,dz1,dz2,zmax,long
double temp2,t4,dt2;
double in,n1,n2,n5;
double log_s2,sigma2,val2,b_fac,temp[4];ndouble double = 0.0;
lower_barrier_index,ind2;
double shift_time,step_log_barrier_level1,log_barrier_level2;
double temp2, ds,plus_ds, min_bb, b; double
double curr_time;
```

```
if (S0 > upper_barrier) printf("ERROR asset price is greater than\nupper_barrier\n");
if (S0 < lower_barrier) printf("ERROR lower price is greater than current asset price\n");
if (S0 <= 0) printf("ERROR price is not > 0\n");
if (upper_barrier < lower_barrier) printf("ERROR upper_barrier must be >\nlower_barrier\n");
log_s0 = log(S0);
log_barrier_level1 = log(lower_barrier);
log_barrier_level2 = log(upper_barrier);
double log_s2_log_barrier_level1/(double)n_lower_s0;
n_level1 = n_lower_s0;
```

```
// Include 5 points above the asset price so that don't get discontinuity in
grid space //
n2 = above_S0;
d_shift = dz1/5; // shift by 5 grid points
d2 = (log_barrier_level2-ds_shift)/(double)n_above_S0;
opt_mat=(double)dt; // time interval size /
time_step=dt;
--n2=n1+2;
```

```
// Set up the RHS and LHS coefficients, a[], b[] and c[] are the LHS coefficients for the
unknown option
time_step j; a[j], b[] and c[] are the values of the RHS coefficients for the
known option prices
(time_step j). Note: a1, bl and c1 are used to form the RHS vector rhs[]_
time_system j; /
// Allocate the required arrays of size (n1) a,b,c,a1,bl1,c1,opt_vals,vals,
rhs,z,delta,gamma,work,u /
```

# Code example 5.20.