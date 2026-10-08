# Single asset American options

**Table 5.1** A comparison of the computed values for American call options with dividends, using the Roll–Geske–Whaley approximation and the Black approximation

| Stock price | Critical price, S* | RGW approximation | Black approximation |
| 80.0 | 123.582 | 3.212 | 3.208 |
| 85.0 | 123.582 | 4.818 | 4.808 |
| 90.0 | 123.582 | 6.839 | 6.820 |
| 95.0 | 123.582 | 9.276 | 9.239 |
| 100.0 | 123.582 | 12.111 | 12.048 |
| 105.0 | 123.582 | 15.316 | 15.215 |
| 110.0 | 123.582 | 18.851 | 18.703 |
| 115.0 | 123.582 | 22.676 | 22.470 |
| 120.0 | 123.582 | 26.748 | 26.476 |

The parameters used were: $E = 100.0, r = 0.04, \sigma, \tau = 2.0$, and there is one cash dividend of 5.0 at time $t = 1.0$. The current stock price, $S$, is varied from 80.0 to 120.0. The results are in agreement with those given in Table 1 of Whaley (1981).

presented in Table 5.1. These compare the Roll–Geske–Whaley approximation with the Black approximation, which we will now briefly discuss. We will now consider the Black approximation.

# The Black approximation

The Black (1973) approximation for an American call with cash dividends is simpler than the Roll–Geske–Whaley method we have just described. For American call option that expires at time $T$, with $n$ discrete cash dividends $D_i, i = 1, \dots, n$, at times $t_i, i = 1, \dots, n$, involves calculating the prices of European options that matures at times $T$ and $t_n$, and then setting the option price to the greater of these two values, see for Hull (2003).

The Black approximation, $C_{BL}$, can be expressed more concisely in terms of our previously defined notation as:

```
$C_{BL}(S, \tau) = \max(v_1, v_2)$
```

where $v_1$ and $v_2$ are the following European calls:

$v_1 = c(S_D, E, \tau)$ and $v_2 = c(S_D^+, E, \tau), \tau = T - t, \tau_1 = T - t_n$

```
$S_D = S - \sum_{i=1}^n D_i \quad \text{and} \quad S_D^+ = S - \sum_{i=1}^{n-1} D_i$
```

Code excerpt 5.2 computes the Black approximation.

Code excerpt 5.3 uses the same values as in Whaley (1981) and compares the Roll–Geske–Whaley approximation with that of Black; the results are presented in Table 5.1.