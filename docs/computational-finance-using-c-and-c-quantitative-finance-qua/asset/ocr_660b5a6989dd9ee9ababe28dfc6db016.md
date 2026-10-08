# Other financial derivatives

It can be seen from Eqs. (4.4.31), (4.4.32) and (7.5.20) that this forward price is:

```
$S^f(t, T) = S^f(t) \exp((r^f - \sigma_s\sigma_f\rho_{sf})(T-t)) \quad (7.5.21)$
```

where $S^f(t)$ is the current price of the foreign equity and $T$ is the maturity of the forward.

In an equity quantum the payoff is in foreign currency but it is converted to domestic currency at a predetermined exchange rate (which we denote here by X). The value equity quantum is:

```
$QF(t, T) = DF^f\{S^f(t, T) - K^f\}X$
```

where $X$ is the exchange rate, $K^f$ is the strike in units of foreign currency, and $S^f(t, T)$ is the foreign equity price.

# Equity quantum option

In Chapter 4 Eqs. (4.4.58) and (4.4.59) expressed the value of vanilla European put and call options are:

where we have used superscripts to denote the domestic currency, and the current equity quantum forward price with maturity T is:

```
$S^d(t, T) = S^d(t)\exp(r^d(T-t)), \quad t \le T$
```

The value of an equity quantum option can be found by substituting $S^f$ for $S^d$ in the above expression.

where $E^f$ is the strike in foreign currency units, $S^f(t, T)$ is the foreign equity forward price (obtained from Eq. (7.5.21)) and $X$ is the prespecified exchange rate (number of units of domestic currency per foreign currency unit).