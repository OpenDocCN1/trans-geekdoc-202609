
# Code excerpt 5.12 uses the of the control variate technique in a standard binomial lattice to provide improved estimates for both the value and the hedge statistics of an American option.

```cpp
/* Set up the arrays in the standard lattice */
```

```cpp
for (int i = 0; i < (M+1)/2; i++) { /* Calculate the option values at maturity */
    if (put) {
        a_v[M-i] = MAX(X - S(P1,i), 0);
        a_v[i] = MAX(X - S(P2,i), 0);
    } else {
        a_v[M-i] = MAX(S[P1]-X, 0);
        a_v[i] = MAX(S[P2]-X, 0);
    }
    e_v[i] = a_v[i];
    e_v[M-i] = a_v[i];
    P1 = P2;
    P2 = P2 + 2;
}
```

```cpp
/* work backwards through the lattice to calculate current option value */
P2 = 0;
for (int ml = M-1; ml >= 0; ml--) {
    P1 = P2;
    P2 = P2 + 1;
    for (int n = 0; n <= ml; n++) {
        if ((a_v[n] == 0) && (a_v[n+1] == 0)) {
            hold = 0;
        } else {
            hold = p*d_a[n] + q*u_a[n+1];
            if (put) {
                a_v[n] = MAX(hold,S[P1]);
            } else {
                a_v[n] = MAX(hold,S[P1]-X);
            }
            e_v[n] = p*d_e[n] + q*u_e[n+1];
        }
    }
}
```

```cpp
/* The American values are stored in the array a_v, and the European values in the array e_v. The indexing is the same as the standard lattice */
for (int jj = 2; jj >= 1; jj--) {
    ind = ml-1;
    for (int n = 0; n <= ml; n++) {
        hold = p*d_a[jj-1] + q*u_a[jj-1];
        if (put) {
            a_v[jj] = MAX(hold,S[ind]);
        } else {
            a_v[jj] = MAX(hold,S[ind]-X);
        }
        e_v[jj] = p*d_e[jj-1] + q*u_e[jj-1];
    }
    ind = ind + 2;
}
```

```cpp
/* American binomial approximation, v2 = European Binomial approximation, temp = exact (American) black_scholes(4,Sigma,T,q,put,flag) */
value = a_v[5] + temp; /* return the variate approximation */
```

```cpp
/* assign the value of delta (obtained from model 1) */
a_delta = (a_v[4]-a_v[3])/(S[M]-S[1]);
e_delta = (a_v[5]-a_v[4])/(S[M]-S[1]);
greeks[1] = a_delta - e_delta + bs_reeks[1];
/* assign the value of gamma (use the values at time step ml=2) */
dvi = a_v[2] - a_v[1];
```

# Code excerpt 5.12. Single American asset options

```cpp
ds = s[v2] - s[M];
dv = a[v1] - a[0];
ds2 = s[M] - s[M-2];
h = 0.5*s[M+2] - (dv2/ds2);
dvi = e[v1] - e[0];
dv = e[1] - e[0];
gamma = (dv1/ds1) - (dv2/ds2);
greeks = (a_gamma - gamma) + bs_reeks[0];
/* assign the value of theta */
theta = (e[v1]-e[v5])/(2.0*dt);
theta = (e[v1]-e[v5])/(2.0*dt);
theta = (a_theta - theta) + bs_reeks[2];
```

**Code excerpt 5.12** Lattice to compute the value of an American option using a binomial lattice with a control variate.

Finally we should mention that the control variate technique does not just apply to American vanilla options. The method is general and can be used to obtain improved estimates for any integral (or exotic option) so long as an accurate (closed form) solution of a similar integral is known. One common use of the control variate method is to improve the accuracy of Monte Carlo estimates.

## 5.3.4 The Binomial lattice with BBS and BSSR

Here we consider the Binomial-Scholes (BBS) method and also the Binomial-Scholes method with Richardson extrapolation (BSSR) (see Broadie and DeTemple (1996)). As with the control variate method discussed in the previous section, both of these techniques can be used in conjunction with a standard binomial lattice to improve the computed results. We will first discuss the BBS method.

## The bbs method

The bbs method is identical to the standard binomial lattice except that in the last step (that is just before option maturity) the Black–Scholes formula is used to calculate the option values at maturity. For an $n$ step binomial lattice this involves evaluating the Black–Scholes formula at each of the $n$ nodes in the penultimate step; see Fig. 5.1. In Code excerpt 5.13 we define the function bs_lattice incorporates the BBS method into a standard binomial lattice. The reader will have noticed that bbs_lattice is rather lack the amount of storage that is required; see Section 5.3.2. It uses an array of size $L_N$ rather than $L_S$, to store the asset prices; the modification to use an array of size $L_S$, is left as an exercise.

The benefits of using the BBS approach to price an American call are illustrated in Fig. 5.3. Here we compare the results obtained using the function bbs_lattice, the standard binomial lattice of Code excerpt 5.11. It can be clearly seen that the BBS method is significantly more accurate than the standard binomial lattice approach, in which option pricing error exhibits pronounced oscillations.

# 132 Computational Finance Using C and C#

```cpp
void bbs_lattice(double *value, double greks[], double S0, double X, double sigma, double T,
    double r, double q, int M, int flag) {
    // Input parameters:
    S0 - current asset price
    X - strike price
    sigma - volatility
    T - time to maturity
    r - interest rate
    q - dividend yield
    M - number of steps
    flag - 0 for call, 1 for put
    // Output parameters:
    value - value of the option
    greks[0] - gamma
    greks[1] - delta
    greks[2] - theta
}
```
