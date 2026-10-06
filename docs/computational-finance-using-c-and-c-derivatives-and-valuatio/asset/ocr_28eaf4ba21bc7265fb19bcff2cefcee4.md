# 124 CHAPTER |5 Single Asset American Options

option, we can achieve an improved estimate for the value of the American option.
When applied to the valuation of an American put option, this can be expressed as follows:

European pricing error, $\Delta_E = p^{BS}(S,E,	au) - p^L(S,E,	au)$,
American pricing error, $\Delta_A = p^*(S,E,	au) - p^L(S,E,	au)$,
where usual $S$ is the current value of the asset, $E$ is the strike price, and $	au$ is the maturity of the option. $p^{BS}(S,E,	au)$ is the Black–Scholes value of the European put option, $p^*(S,E,	au)$ is the accurate (unknown) value estimate of the American put option, and $p^L(S,E,	au)$ is the binomial lattice estimate of the American option.

Setting $\Delta_E = \Delta_A$, we then have

> $p^{BS}(S,E,	au) - p^L(S,E,	au) = p^*(S,E,	au) - p^L(S,E,	au)$

> $p^*(S,E,	au) = p^{BS}(S,E,	au) - p^l(S,E,	au) + p^L(S,E,	au)$

We use $p^*(S,E,	au)$ as the improved, control variate estimate for the value of American put option. Of exactly the same approach can be used to obtain an improved estimate for the value of an American call.

Code excerpt 5.12 shows the use of the control variate technique in provide improved estimates for both the value and the hedge statistics of an American option.

```
/* Set the arrays in the standard lattice */
for (i = 0; i <= M; i++) { /* Calculate the values at maturity */
if (put) {
    u[i] = MAX(X-s[i],0);
    d[i] = MAX(s[i]-X,0);
} else {
    u[i] = MAX(s[i]-X,0);
    d[i] = MAX(X-s[i],0);
}
  nv[i] = u[i];
  nv[M-i] = d[i];
}

/* work backwards through the lattice to calculate the control option value */
for (i = M-1; i >= 2; i--) {
    P1 = P2;
    P2 = p[i];
    if (c[i] == zero && (nv[i+1] == zero)) {
        hold = true;
    }
    if (put) {
        p[i] = p*u*nv[i+1]+q*d*nv[i];
    } else {
        p[i] = p*d*nv[i+1]+q*u*nv[i];
    }
}
```

**Code excerpt 5.12** Function to compute the value and hedge statistics of an American option using a binomial lattice with a control variate.