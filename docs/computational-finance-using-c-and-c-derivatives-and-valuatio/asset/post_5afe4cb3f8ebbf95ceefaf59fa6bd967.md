
# 194 CHAPTER | Multi-asset Options

$P_{udd} = \frac{1}{8} \left\{ 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} \right) - \rho_{12} - \rho_{13} - \rho_{23} \right\}$

$P_{dud} = \frac{1}{8} \left\{ 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} \right) + \rho_{12} - \rho_{13} - \rho_{23} \right\}$

$P_{ddl} = \frac{1}{8} \left\{ 1 - \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} - \frac{\mu_3}{\sigma_3} \right) + \rho_{12} + \rho_{13} + \rho_{23} \right\}$

```cpp
void standard_d3_binomial_double(double s1, double s2, double s3, double x,
double signal1, double signal2, double signal3, double rho_12, double rho_13, double rho_23,
 double T, double r, long m, long type, long is_american, int *flag)
{
// Input parameters:
s1 // the current price of the underlying asset 1
s2 // the current price of the underlying asset 2
s3 // the current price of the underlying asset 3
sigma1 // the volatility of asset 1
sigma2 // the volatility of asset 2
sigma3 // the volatility of asset 3
rho_12 // the correlation coefficient between asset 1 and asset 2
rho_13 // the correlation coefficient between asset 1 and asset 3
rho_23 // the correlation coefficient between asset 2 and asset 3
 T // the time to maturity
put // if put is 1 then a call option, otherwise a put option
opt_type // if opt_type is 1 then an exercise option, otherwise an european option
is_american // if is_american is 1 then a European option, otherwise an American option.

value // the value of the option
iflag // an error indicator

double double_count, dt1, dt2, dt3, d1, d2, u3;
long i, j, k; flags = 0;
double price = 0.0;
double dsv1, dsv2, dsv3, bvh, tmp1, tmp1, tmp2, tmp3;
long P1, P2, P3, tdv, mu1, mu2, mu3, jp1, jp2, jp3;
double one = 1.0, half = 0.625;
hall = 0;

if ((m/2) != (m/2)) printf("THE ERROR OF TIME STEPS IS NOT EVEN\n");
tdv = T/m;
tdv2 = sqrt(tdv);
#define V(i,j,k) v(i) * tdv + (j) * (k)
#define U0 0
#define U1 1
#define U2 2
#define U3 3
#define U4 4
#define U5 5
#define U6 6
#define U7 7
dt = sqrt(tdv);
pj1 = sigma1*sqrt(tdv);
pj2 = sigma2*sqrt(tdv);
pj3 = sigma3*sqrt(tdv);
mu1 = r - sigma1*half;
mu2 = r - sigma2*half;
mu3 = r - sigma3*half;
u1 = exp(mu1); // assign the jump sizes *
nu2 = exp(mu2);
u3 = exp(mu3);
d1 = exp(-jp1);
d2 = exp(-jp2);
d3 = exp(-jp3);
// set up the jump probabilities /
pU[0] = eighth(one + sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
pU[1] = eighth(one - sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
pU[2] = eighth(one + sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
pU[3] = eighth(one + sqrt(tdv) * (mu1)/(sigma1) / (sigma2) / (sigma3)) * rho_12 * rho_13 * rho_23;
```

Code example 6.5 Standard 3-dimensional binomial lattice.

# Three-asset Options Section | 6 195

```cpp
d[DUD] = eighth(one + sqrt_dt * (-mu1/sigma1) + (mu2/sigma2) - (mu3/sigma3)) - rho_12 + rho_13 - rho_23);
p[dUD] = eighth(one + sqrt_dt * (-mu1/sigma1) - (mu2/sigma2) + (mu3/sigma3)) + rho_12 - rho_13 + rho_23);
p[dD] = eighth(one + sqrt_dt * (-mu1/sigma1) - (mu2/sigma2) + (mu3/sigma3)) + rho_12 - rho_13 + rho_23;
for (i = 0; i < 8; i++) {
    if (g[i] < 0 || g[i] > 1.0) printf("P error %d: %.1f out of range %s\n", i, g[i]);
}
for (i = 0; i < 8; i++) {
    p[i] = discount[i];
}
// Allocate the arrays (V(M*(M+1)), M[i], s2(2*M+1), and s3(2*M+1))
s[M];
for (i = 0; i < M; i++) {
    s1[i] = u*M[i]; // the 2*M+1 asset values for s1
    s1[i] = d/M[i];
}
s2[2*M+1];
for (i = 0; i < M; i++) {
    s2[i] = u*M[i]; // the 2*M+1 asset values for s2
    s2[i] = d/M[i];
}
s3[2*M+1];
for (i = 0; i < M; i++) {
    s3[i] = u*M[i]; // the 2*M+1 asset values for s3
    s3[i] = d/M[i];
}
/* Calculate the option values at maturity */
P1[M];
for (i = 0; i < M; i++) {
P2[M];
for (j = 0; j < M; j++) {
P3[M];
for (k = 0; k < M; k++) {
    if (put) { /* Maximum of 3 assets */
        tmp = MAX(s1[i], s2[j], s3[k]);
        V(i,j,k) = MAX(tmp, p3[k]);
    } else if (opt_type == 1) { /* Minimum of 3 assets */
        tmp = MIN(s1[i], s2[j], s3[k]);
        V(i,j,k) = MIN(tmp, p3[k]);
    } else { /* Call option */
        ** Insert call code using the supplied option code as a template **
P3 = P3 + P2;
P2 = P2 + P1;
P1[M];
for (i = M-1; i >= 0; i--) { /* work backwards through the lattice to calculate the option value */
P2[M];
for (j = 0; j < M; j++) {
P3[M];
for (k = 0; k < M; k++) {
    V(i,j,k) = p[DUD](i,j,k) + p[DUD](i,j+1,k) + p[DUD](i,j,k+1) + p[DUD](i+1,j+1,k+1);
    if (is_american) {
        if (opt_type == 0) { /* Maximum of 3 assets */
            tmp = MAX(s1[i], s2[j], s3[k]);
            tmp1 = MAX(tmp, p1[i]);
            tmp2 = MAX(tmp1, p2[j]);
            V(i,j,k) = MAX(tmp2, zero);
        } else if (opt_type == 1) { /* Minimum of 3 assets */
            tmp = MIN(s1[i], s2[j], s3[k]);
            tmp1 = MIN(tmp, p1[i]);
            tmp2 = MIN(tmp1, p2[j]);
            V(i,j,k) = MIN(tmp2, zero);
        } else { /* Call option */
        ** Insert call code using the supplied option code as a template **
    }
    } else { /* European option */
        V(i,j,k) = ...;
    }
}}
```
Code except 6.5 (Continued). **Note**

# 196 CHAPTER | Multi-asset Options

```cpp
P1 = P3 + 2;
P2 = P2 + 2;
P1 = P1 + 2;
}
value = V(9,0);
```

Code except 6.5 (Continued).

# 6.7 FOUR-ASSET OPTIONS

The results for four assets are presented in Tables 6.9 and 6.10. We have the following jump probabilities:

P_{uuuu} = \frac{1}{16} \left( 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} + \frac{\mu_4}{\sigma_4} \right) \right) + \rho_{12} + \rho_{13} + \rho_{14} + \rho_{23} + \rho_{24},$

$P_{uuud} = \frac{1}{16} \left( 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} + \frac{\mu_2}{\sigma_2} - \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4} \right) \right) + \rho_{12} - \rho_{13} - \rho_{14} + \rho_{23} - \rho_{24},$

$P_{uduu} = \frac{1}{16} \left( 1 + \sqrt{\Delta t} \left( \frac{\mu_1}{\sigma_1} - \frac{\mu_2}{\sigma_2} + \frac{\mu_3}{\sigma_3} - \frac{\mu_4}{\sigma_4} \right) \right) - \rho_{12} - \rho_{13} + \rho_{14} - \rho_{23} - \rho_{24},$

# TABLE 6.5 The Computed Values and Absolute Errors for European Options on the Maximum of Three Assets. A Binomial Lattice was used and We Show the Accuracy of the Results Depends on the Number of Steps. The Parameters are $E = 100.0, S_1 = S_2 = S_3 = 100.0, r = 0.1, \tau = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = 0.2, \rho_{12} = \rho_{13} = 0.5,$ and $q_1 = q_2 = q_3 = 0.0$. The Accurate Values are 0.996 for Put and 2.672 for a Call, See Table 2 (Boyle and Gibbs, 1989)

| | Put | Error | Call | Error |
|---|---|---|---|---|
| 10 | 0.9112 | $2.485 \times 10^{-2}$ | 2.8601 | $8.119 \times 10^{-1}$ |
| 20 | 0.9192 | $1.678 \times 10^{-2}$ | 2.2807 | $3.919 \times 10^{-1}$ |
| 30 | 0.9232 | $1.276 \times 10^{-2}$ | 2.4137 | $2.583 \times 10^{-1}$ |
| 40 | 0.9254 | $1.056 \times 10^{-2}$ | 2.4792 | $1.928 \times 10^{-1}$ |
| 50 | 0.9268 | $9.180 \times 10^{-3}$ | 2.5182 | $1.538 \times 10^{-1}$ |
| 60 | 0.9278 | $8.236 \times 10^{-3}$ | 2.5441 | $1.279 \times 10^{-1}$ |

# TABLE 6.6 The Computed Values and Absolute Errors for European Options on the Minimum of Three Assets. A Binomial Lattice was used and We How the Accuracy of the Results Depends on the Number of Time Steps. The Parameters are $E = 100.0, S_1 = S_2 = S_3 = 100.0, r = 0.1, \tau = 1.0, \sigma_1 = \sigma_2 = \sigma_3 = 0.2, \rho_{12} = \rho_{13} = \rho_{23} = 0.5, q_1 = q_2 = q_3 = 0.0$. The Accurate Values are 7.403 for Put and 5.249 for Call, See Table 2 (Boyle and Gibbs, 1989)

| nsteps | Computed value | Error | Computed value | Error |
|---|---|---|---|---|
| 10 | 7.0759 | $3.271 \times 10^{-1}$ | 5.2072 | $4.176 \times 10^{-2}$ |
| 20 | 7.2402 | $1.628 \times 10^{-1}$ | 5.2263 | $2.269 \times 10^{-2}$ |
| 30 | 7.2953 | $1.077 \times 10^{-1}$ | 5.2334 | $1.560 \times 10^{-2}$ |
| 40 | 7.3229 | $8.015 \times 10^{-2}$ | 5.2371 | $1.192 \times 10^{-2}$ |
| 50 | 7.3394 | $6.357 \times 10^{-2}$ | 5.2393 | $9.665 \times 10^{-2}$ |
| 60 | 7.3505 | $5.211 \times 10^{-2}$ | 5.2409 | $8.143 \times 10^{-2}$ |
