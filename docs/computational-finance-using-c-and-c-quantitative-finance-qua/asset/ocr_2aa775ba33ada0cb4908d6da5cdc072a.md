# Single American options

```
/ Solve the upper (n-2)*(n-2) triangular system Ux = y (where x = vold) /
opt_vals[n-2]=work[n-2]/u[n-2]
for (i = n-2; i >= 0; --i)
    opt_vals[i]=(work[i] - c*opt_vals[i+1])/u[i];
if (j==0)
    for (i=0; i <= n; ++i)
        opt_vals[i]=opt_vals[i];
```

```
// Store option values so that can compute theta *
if ((j==1)|(j==2)|(j=-1)|(j=-2))
    temp[ind]=opt_vals[n];
    ind++;
```

```
// Compute theta (4th order accuracy)
greeks[2] = (temp[0]+8.0*temp[1]-temp[3])/(12.0*dt);
// could also compute theta as: gereeks[2] = (-temp[0]+4.0*temp[1]-3.0*vals[n-1])/(2.0*dt);
```

option_value = vals[n];

# Code 5.20 Code 5.25 Function to compute the value and Greeks of a European double knockout call on a nonuniform grid and a logarithmic transformation.

# Table 5.8 Estimated value of a European double knockout call

| Time steps (n) | Estimated value | Boyle and Tian (1998) |
|---|---|--|
| 50 | 1.4569 | 1.4238 |
| 100 | 1.4578 | 1.4437 |
| 200 | 1.4583 | 1.4495 |
| 300 | 1.4583 | 1.4524 |
| 400 | 1.4584 | 1.4542 |
| 500 | 1.4584 | 1.4553 |
| 600 | 1.4584 | 1.4557 |
| 700 | 1.4584 | 1.4559 |
| 800 | 1.4584 | 1.4563 |
| 900 | 1.4584 | 1.4563 |
| 1000 | 1.4584 | 1.4566 |
| 2000 | 1.4584 | 1.4576 |
| 3000 | 1.4584 | 1.4578 |
| 4000 | 1.4584 | 1.4580 |
| 5000 | 1.4584 | 1.4581 |

The columns two were computed by the function dko_call, and in column three are the results reported in Table 2 of Boyle and Tian (1998). The model parameters were: current asset price S = 95.0, exercise E = 100.0, volatility sigma = 0.25, tau r = 1.0, interest rate r = 0.1, dividend yield q = 0.0. The upper barrier is set at 140 and the lower barrier is set at 90.0. The other parameters used by the function dko_call were: nt = n, ns_below_S0 = n/2, ns_above_S0 = n/2, and $\Theta_m = 0.5$ (the Crank-Nicolson method).

*