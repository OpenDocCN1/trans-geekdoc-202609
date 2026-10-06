# 7.5.2 Equity Quantos

The Black Shoes equation can also be used to price Equity quanto options (Reiner, 1992). We have the following processes:

```
$dS^f = \mu_{S^f} dt + \sigma_{S^f} dW_{S^f},\ndX^f = \mu_{X^f} dt + \sigma_{X^f} dW_{X^f},\ndB^f = r^B dt,\\ndB^d = r^d dt.$
```

Here, $S^f$ is the price (in foreign currency units) of the foreign stock, $B^d$ the domestic money market account where money grows at the (constant) risk-free interest rate $r^d, Bf$ the foreign money market account where money grows at the (constant) risk-free rate $r^f$, and $X^f$ the foreign exchange rate, which is the value of one unit of foreign currency in units of domestic currency.
The tradables for the domestic money market account priced in domestic currency units (is, $X^f B^d$) and the foreign stock priced in domestic currency, $X^f S^f$.

We know from (4.4.30) that there is a probability (the neutral measure) $Q$ under which the relative price of tradables such as equities are martingales. We also established that under $Q$ the process followed by these tradables is GBM with constant drift $r^d$. For the process of the equity $S^d$

```
$dS^d = r^d S^d dt + \sigma_{S^d} dW_{S^d}.$
```

Similarly, the process followed by the price of a foreign equity $S^f$ under the foreign risk neutral measure $F$ is

```
$dS^f = r^f S^f dt + \sigma_{S^f} dW_{S^f}.$
```

However, the process followed by the price of a foreign equity $S^f$ under the domestic risk neutral measure $Q$ is

```
$dS^f = S^f (r^f + \alpha) dt + \sigma_{S^f} dW_{S^f},$
```

where $\alpha$ (the quanto adjustment) is to be determined.
We will derive the value for $\alpha$ and then use this to price both forwards and quanto options.

# Determining the Quanto Adjustment, $\alpha$

Since $X^f_d B^f$ and $X^f_d S^f$ are domestic tradables, it means that the relative prices $(X^f_d B^f/B^d)$ and $(X^f_d S^f/B^d)$ are also martingales under the probability measure $Q$.
Since $(X^f_d B^f/B^d)$ is a martingale,

```
$$\frac{d}{dt}\left(\frac{X^f_d B^f}{B^d}\right) = \sigma_X dW_{Q^X}.$
```