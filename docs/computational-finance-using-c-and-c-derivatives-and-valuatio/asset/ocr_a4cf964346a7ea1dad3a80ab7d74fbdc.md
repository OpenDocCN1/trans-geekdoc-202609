# Approximations for Vanilla American Options Section | 5.2 97

**TABLE 5.1** Comparison of the Computed Values for American Call Options with Dividends, using the Roll, Geske, and Whaley Approximation, and the Black Approximation. The Parameters used $E = 100.0, 	au = 0.04, \sigma = 0.2, 	au = 2.0$, and there is One Cash Dividend of Value 5.0 at Time $t = 1.0$. The Current Stock Price, $S$, is Varied from 80.0 to 120.0. The Results are in agreement with European calls: Table 1 of Whaley (1981)

| Stock price | Critical price, $S^*$ | RGW approximation | Black approximation |
|---|---|---|--|
| 80.0 | 123.582 | 3.212 | 3.208 |
| 85.0 | 123.582 | 4.818 | 4.808 |
| 90.0 | 123.582 | 6.839 | 6.820 |
| 95.0 | 123.582 | 9.276 | 9.239 |
| 100.0 | 123.582 | 12.111 | 12.048 |
| 105.0 | 123.582 | 15.316 | 15.215 |
| 110.0 | 123.582 | 18.851 | 18.703 |
| 115.0 | 123.582 | 22.676 | 22.470 |
| 120.0 | 123.582 | 26.748 | 26.476 |

$D_i, i = 1, \dots, n$, at times $t_i, i = 1, \dots, n$, it involves calculating the prices of European options that mature at times $T$, and $t_n$, and then setting the option price to the greater of these two values, for example, Hull (2003).

The Black approximation, $C_{BL}$, can be expressed more concisely in terms of our previously defined notation

> $C_{BL}(S, E, T) = \max(v_1, v_2)$.

where $v_1$ and $v_2$ are European calls:

$v_1 = c(S, E, 	au)$ and $v_2 = c(S_D, E, 	au_1), 	au = T - t, 	au_1 = T - t_n$,

and

$SD = S - \sum_{i=1}^{n} D_i$ and $S_D^* = S - \sum_{i=1}^{n} D_i$.

**Code excerpt 5.2** computes the Black approximation.

```
void black_approx(double value, long n, double dividends[], double Divs_T[]) {
    double d59, double x, double sigma, double T, double r, long put, long "iscall"
    // Input parameters:
    n_divs
// the number of dividends
```

**Code excerpt 5.2** Function to compute the value of the Black approximation for the value of an American call option with discrete dividends.