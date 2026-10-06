# 108 CHAPTER | 5 Single Asset American Options

```
}
A_1 = -(S*gamma_1)*(1.0 - exp(-q*T)*cum_norm(-di))
if (S < 5*star)
templ_i = 5*star;
black_scholes(&temp_i,S,X,sigma,T,r,q,puts&iflag);
opt_value = A_1*pow(templ_i,gamma_i);
elelse {
opt_value = X - 5;
}
*critical_value = 5*star;
```

Code excerpt 5.4 (Continued).

Mention that Tables 5.2 and 5.3 are results obtained by using the computer code given above.

# 5.3 LATTICE METHODS FOR VANILLA OPTIONS

# 5.3.1 Binomial Lattice

In this section, we will derive equations for a binomial lattice that describes the GBM movement of asset price changes. The approach that we will adopt

| TABLE 5.2 The Macmillan, Barone-Adesi, and Whaley Method for American Options Value Computed by the Routine MBW_approx. The Parameters used were r = 0.5, X = 100.0, q = 0.1, σ = 0.06, and σ = 0.2 The Accurate Value was Calculated using a Standard Lattice with 2000 Time Steps, and the Error was the Macmillan, Barone-Adesi, and Whaley Estimate Minus the Accurate Value |
| Stock price | Accurate value | Error | Accurate value | Error |
|---|---|---|---||}{
| 86.0 | 1.2064 | 5.54 × 10⁻⁴ | 14.0987 | -3.66 × 10⁻² |
| 89.0 | 1.8838 | 1.95 × 10⁻⁴ | 11.5120 | -4.85 × 10⁻² |
| 92.0 | 2.7890 | 7.03 × 10⁻⁴ | 9.2478 | -3.58 × 10⁻² |
| 95.0 | 3.9427 | 1.16 × 10⁻³ | 7.3031 | -1.66 × 10⁻² |
| 98.0 | 5.3522 | 1.15 × 10⁻³ | 5.6674 | 7.19 × 10⁻⁴ |
| 101.0 | 7.0119 | 1.10 × 10⁻³ | 4.3209 | 1.35 × 10⁻² |
| 104.0 | 8.9043 | 2.21 × 10⁻³ | 3.2362 | 2.22 × 10⁻² |
| 107.0 | 11.0072 | 2.63 × 10⁻³ | 2.3823 | 2.63 × 10⁻² |
| 110.0 | 13.2905 | 4.20 × 10⁻³ | 1.7235 | 2.80 × 10⁻² |
| 113.0 | 15.7264 | 4.77 × 10⁻³ | 1.2272 | 2.66 × 10⁻² |