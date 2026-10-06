# Foreign Exchange Derivatives Section | 7.3 223

# 7.3.2 European FX Option

Foreign exchange option can be priced using the Black Scholes formula, (Garman and Kohlhagen, 1983). There are three processes involved in foreign exchange options and, under the real world probability measure P, they are

```
$dB^F = r^F dB^d,\ndX_d^F = X_d^F \mu dt + X_d^F \sigma dW^P, \quad dW^P \sim N(0,dt),\ndB^d = r^d Bd^d.$
(7.3.5)
```

where $X_d^F$ is the value of one unit of foreign currency in units of domestic currency, $B^d$ is the domestic money account where money grows at the (constant) risk-free rate $r^d$, $B^F$ is the foreign money account where money grows at the (constant) risk-free rate $r^f$ and $\sigma$ is the volatility of $X_d^F$. From a domestic point of view, there are only assets - the money market account $B^d$ and the value of the foreign money market account in domestic currency, $X_d^F$.

From Ito's product rule in Chapter 2 and using equation(2.6.3) with $X_1 = X_d^F$ and $X_2 = B^d$, we have

```
$d(X_d^F B^d) = (X_d^F B^d)\{r^f + \mu\} dt + (X_d^F B^d)\sigma dW^P$.
```

We will now consider $B^d$ as the numeraire and the process for $B_d^F/B^d$ using the Ito rule given in Chapter 2. Substituting $X_1 = B_d^F$ and $X_2 = B^d$ in equation(2.6.8), we obtain

```
$d(\frac{B_d^F}{B^d}) = \frac{B_d^F}{B^d} d(\frac{B_d^F}{B^d}){\{r^f - r^d + \mu\} dt + \frac{B_d^F}{B^d}\sigma dW^P$.
```

If we choose the probability measure Q such that

```
$dW^P = dQ - \frac{r^f - r^d}{\sigma} dt,\quad(7.3.6)
```

then $(B_d^F/B^d)$ is a martingale since

```
$d(\frac{B_d^F}{B^d}) = (frac{B_d^F}{B^d})sigma dW^Q$.
```

Substituting for $dW^P$ in equation(7.3.5) yields

```
$dX_d^F = X_d^F \mu dt + X_d^F \sigma{\frac{r^f - r^d + \mu}{\sigma}} dt,\ndX_d^F = X_d^F \mu dt - X_d^F (r^f - r^d + \mu) dt + X_d^F \sigma dW^Q$.
```