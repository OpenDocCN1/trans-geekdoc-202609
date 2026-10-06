# CHAPTER | 5 Single Asset American Options

The iterative algorithm for the American put is therefore

```
$S_{i}^{**} = \frac{E - RHS(S_{i}^{**}, E, 	au)}{1 + b_i} + b_i S_{i}^{**} \quad (5.2.37)
```

where we can use $S_{0}^{**} = E$ for the initial estimate of the critical asset value (see the computer code except below).

# The Expression for $b_i$

Here, we derive an expression for the term $b_i$ which is used in equation (5.2.37). Since

```
$b_i = \frac{\partial}{\partial S_{i}^{**}} p(S_{i}^{**}, E, \tau) - \frac{S_{i}^{**}}{\gamma_1} (1 - \exp(-q\tau)) + N_1(d_1(S_{i}^{**})) \exp(-q\tau))$
```

we have

```
$b_i = \frac{\partial p(S_{i}^{**}, E, \tau)}{\partial S_{i}^{**}} - \frac{1}{\gamma_1} \{1 - \exp(-q\tau)\} - \frac{1}{\gamma_1} \exp(-q\tau) N_1(d_1(S_{i}^{**})) \\frac{\exp(-q\tau) N_1(d_1(S_{i}^{**})) \\partial d_1(S_{i}^{**})}{\gamma_1} \frac{\partial d_1(S_{i}^{**})}{\partial S_{i}^{**}}$
```

We now quote the following results which are derived in Appendix A:

+   - Appendix A, equation (A.1.3): $\frac{N(d_1(S_{i}^{**}))}{\partial d_1(S_{i}^{**})} = n(d_1(S_{i}^{**}))$

+   - Appendix A, equation (A.1.6): $\frac{1}{\partial S_{i}^{**}} = \frac{1}{S_{i}^{**}} \sigma \sqrt{\tau}$

+   - Appendix A, equation (A.3.4): $\Delta_p = \frac{\partial p(S_{i}^{**}, E, \tau)}{\partial S_{i}^{**}} = \exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\}$

Substituting these results into the above expression, we obtain obtain

```
$b_i = \exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\} - \frac{1}{\gamma_1} \{\exp(-q\tau) + N_1(d_1(S_{i}^{**})) \exp(-q\tau)\} \\fracfrac{\exp(-q\tau) N_1(d_1(S_{i}^{**})) \\partial d_1(S_{i}^{**})}{\gamma_1} \frac{\partial d_1(S_{i}^{**})}{\partial S_{i}^{**}}$
```

```
$=\exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\} - \frac{1}{\gamma_1} \{\exp(-q\tau) + N_1(d_1(S_{i}^{**})) \exp(-q\tau)\}$
```

```
$-\frac{S_{i}^{**} \exp(-q\tau) n(d_1(S_{i}^{**}))}{\gamma_1 \sigma \sqrt{\tau}},
```

which can be rearranged to yield

```
$b_i = \exp(-q\tau) \{N_1(d_1(S_{i}^{**})) - 1\} \frac{1}{\gamma_1} \\ + \frac{1}{\gamma_1} \{\exp(-q\tau) - 1 - \frac{\exp(-q\tau) n(d_1(S_{i}^{**}))}{\sigma \sqrt{\tau}}} \exp(-q\tau)\} \quad (5.2.38)
```