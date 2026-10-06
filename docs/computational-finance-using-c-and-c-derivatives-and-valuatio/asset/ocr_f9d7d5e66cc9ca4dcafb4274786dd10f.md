# 172 CHAPTER | 5 Single Asset American Options

```
opt_val = hold;
}
opt_val[v[j]][1] = opt_val;
v[j] = j - 1;
}
opt_total_vals = opt_total_vals + opt_val[v[1]]; // Sum the option values for each simulation
}
opt_value = opt_total_vals/(double)n_simulations; // compute the average option value
printf("The estimated option value = %3.4f\n", opt_value);
```

Code example 5.21. (Continued).

**In Table 5.13**, we computed values of an American option with maturity $	au$ can only be exercised at the following four times: $t, t+	au/3, 2	au/3$, and $t+	au$, where $t$ is the current time.

The column labelled $MC_{50}^{100}$ are the results obtained using 100 simulations of a stochastic lattice with 50 branches per node, and the column labelled $MC_{250}^1$.

**TABLE 5.13** American Option Values, Computed using the Stochastic Lattice in Code excerpt **5.21**, with the Four Exercise Times $t,t+	au/3,t+2	au/3$, and $t+	au$. Option Parameters used were $r=0.1, q=0.05, 	au=1.0, \sigma=0.2$, and $t=50$. The Column $MC^{100}_{50}$ Refers to the Results obtained using $d=4, b=50, n\_simulations=100$, and the Column Labelled $MC_{250}$ Refers to the Results obtained using $d=4, b=5$. The True values are Given in Broadie et al. (1997) and Computed with the Formula in Gekson and Johnson (1984). The Absolute Error, ABS(stochastic\_lattice\_value-true\_value), is Given in Brackets. The Last Column Gives the Values Computed using an Accurate (6000 time step) Binomial Lattice

| X | $MC_{50}^{100}$ | $MC_{250}^1$ | True | Binomial lattice |
|---|---|---|---|---||
| 70 | 0.118 (0.003) | 0.123 (0.002) | 0.121 | 0.126 |
| 80 | 0.663 (0.007) | 0.672 (0.002) | 0.670 | 0.696 |
| 90 | 2.317 (0.014) | 2.307 (0.004) | 2.303 | 2.389 |
| 100 | 5.830 (0.099) | 5.720 (0.011) | 5.731 | 5.928 |
| 110 | 11.564 (0.223) | 11.361 (0.020) | 11.341 | 11.770 |
| 120 | 20.205 (0.205) | 20.000 (0.000) | 20.000 | 20.052 |
| 130 | 30.054 (0.054) | 30.000 (0.000) | 30.000 | 30.000 |