# Multasset options

The parameter M is the number of time steps used, and the lattice is constructed under the assumption that M is even.

```
void standard_2D_binomial(double value, double s1, double s2, double X,
    double sigma1, double sigma2, double rho, double T,
    double r, double q1, double q2, long put,
    long M, long opt_type, long is_american, long *iflag)
{
/* Input parameters:
=====================================
s1 - the current price of the underlying asset 1
s2 - the current price of the underlying asset 2
T - the time to maturity
sigma1 - the volatility of asset 1
sigma2 - the volatility of asset 2
rho - the correlation coefficient between asset 1 and asset 2
r - the interest rate
q1 - the continuous dividend yield for asset 1
q2 - the continuous dividend yield for asset 2
put - if put is 0 a call option, otherwise a put option
M - the number of time steps, if the time step is the root_node,
    of the lattice
opt_type - if opt_type is 0 an option on the maximum of two assets else minimum of two assets
is_american - if is_american is 0 a European option, otherwise_
    an American option
Output parameters:
===================
value - the value of the option,
iflag - an error indicator.
*/
double count, dt, dt1, dt2, u1, u2,
long i, j, n, iflag, jj, nd;
double zero = 0.0;
double temp_dt, d1, dv1, dv2, h, temp;
double *s1, *s2;
double p[4];
long h1, h2;
double sqrt_dt, t, mul, jp1, jp2;
double one = 1.0, half = 0.25;
long q;
if ((M-1)/2 != (M/2)) printf("* ERROR NUMBER OF TIME STEPS IS NOT EVEN\n");
def V(i, j) = V(i) * dt + dv(j)
def UU = 0
def UD = 1
def DD = 2
dt = (double)M;
sqrt_dt = sqrt(dt);
jpl1 = sqrt_dt;
jpl2 = sqrt_dt;
mul1 = r - q1 - sigma1*half;
mul2 = r - q2 - sigma2*half;
u = opt_type; // assign the jump sizes */
u = exp(jp1);nu = exp(jp2);
d1 = exp(-jp1);
d2 = exp(-jp2);
p[U] = quarter * (one + sqrt_dt * ((mul1/signal) + (mul2/sigma2)) - rho); // set up the jump_
probabilities *";
p[D] = quarter * (one + sqrt_dt * (-(mul1/signal) + (mul2/sigma2)) - rho);
p[DD] = quarter * (one + sqrt_dt * (-(mul1/signal) - (mul2/sigma2)) - rho);
for (i = 0; i < j; i++)
if ((p[i] < 0) || ((p[i] > 1.0)) printf("* ERROR p out of range\n");
discount = exp(-r*dt);
```

Code 6.4 Function to calculate the value of a European put or call on the maximum or minimum of two assets using a standard binomial lattice.