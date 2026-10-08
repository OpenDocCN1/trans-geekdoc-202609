# 7.3 Foreign exchange derivatives

We consider derivatives based on the exchange rate between a domestic currency and a foreign currency. We will use the convention that quantities relating to the domestic currency will have the superscript $d$, while for the foreign currency will have the superscript $f$. The notation for the various exchange rates is as follows:

+   * $X_d^f(t)$ is the spot value of one unit of foreign currency in domestic currency at time $t$
* $X_b^f(t)$ is the spot value of one unit of foreign currency in base currency at time $t$
* $X_b^d(t)$ is the spot value of one unit of domestic currency in base currency at time $t$
* $X_d^f(t, T)$ is the (time $t$) forward value of one unit of foreign currency in domestic currency at time $T$.

# Covered interest arbitrage

If the current spot exchange rate $X_d^f(t)$, is known then using covered interest arbitrage it is possible to obtain a value for the future spot exchange rate—we denote this forward exchange rate by $X_d^f(t, T)$, where $T > t$.
Let us consider the following two scenarios:

# Scenario A

At time $t$ an investor deposits one unit of foreign currency which grows at the (constant) foreign free interest rate $r^f$. By time $T$ the initial amount will have increased $1/DF^f(t, T)$ units of foreign currency, where $DF^f(t, T) = \exp(-r^f(T-t))$. The foreign currency is converted into domestic currency at the time $T$ forward forward exchange rate $X_d^f(t, T)$, and thus yields $X_d^f(t, T)/DF^f(t, T)$ units of domestic currency.

# Scenario B

At time $t$ an investor deposits $X_d^f(t)$ units of domestic currency (the sum is equivalent to one unit of foreign currency), and which grows at the (constant) domestic free interest rate $r^d$. At time $T$ the initial sum will have increased to $X_d^f(t)/DF^d(t, T)$ units of domestic currency, where $DF^d(t, T) = \exp(-r^d(T-t))$.

For no arbitrage to occur the final amount of domestic currency in both scenarios must be the same—we have assumed that there is no charge in converting one currency into another.
We have thus:

```
$$\frac{X_d^f(t, T)}{DF^f(t, T)} = \frac{X_d^f(t, T)}{DF^d(t, T)}$
```