# 132 Computational Finance Using C and C#

```
void bbs_lattice(double *value, double greks[], double S0, double X, double sigma, double T,
    double r,
    double q, long M, long *iflag)
{
    // Input parameters:
    ===================
    S0 - the current price of the underlying asset
    X  - the strike price
    sigma - the volatility
    T - the time to maturity
    r -- the interest rate
    q -- the continuous dividend yield
    put - if put is 0 a call option, otherwise a put option
    M -- the number of time steps
    Output parameters:
    ===================
    value - the value of the option, greks[] - the hedges output as follows:
        greks[0] is gamma,
        greks[1] is delta, greks[2] is theta,
        iflag - an error indicator.
}
/* allocates the arrays s[(M*(M+1))/2], and v[M+1] */
    dt = T/double(M);
ti = sqrt(dt);
    u = exp(ti);
    d = exp(-ti);
    r = exp(-r*dt);
    p = (d)/(u-d); if (p < 0) || (p > 1.0) /* Invalid probability */
    discount = exp(-r*dt);
    pu = p*discount;
    pd = (1.0-p)*discount;
j = 0;
s[0] = S[0];
/* the higher value of v[j], at a given time, the lower value of the-
asset price * */
    for (int j=1; j<=M; j++) { /* Asset values up to (M-1) time step */
        for (int i=0; i<j; i++) {
            s[j][i] = u*s[j-1][i-1];
            s[j][i] = d*s[j-1][i];
        }
    }
for (int n=0; n<M; n++) { /* Use Black-Scholes for the final step */
    black_scholes(n,NULL,s,X,sigma,dt,r,put,&iflag);
    v[n] = temp;
}
for (int m=M; m>0; m--) { /* work backwards through the lattice */
    for (int n=0; n<=m; n++) {
        if ((v[n] == 0) && (v[n+1] == 0)) {
            hold = 0;
        }
        else {
            hold = pd*v[n] + pu*v[n+1];
            if (ix_american) {
                if (put)
                    v[n] = MAX(hold,s[j][j]);
                else
                    v[n] = MAX(hold,s[j]-X);
            }
            else
                v[n] = hold;
        }
    }
}
/* Values v[0], v[1] & v[2] correspond to the nodes for m=2, v1 & v2 correspond to-
the nodes for m=1 and the
option value *value corresponds to the node for m = 0. For a given time step v[0] corresponds to-
v1 to the next lowest etc.. */
```

# Code excerpt 5.13.