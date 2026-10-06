# Foreign Exchange Derivatives Section | 7.3 221

When $K = 0$ we have $d_1 = 0, N_1(d_1) = 1, N_1(-d_1) = 0$, which means that the value of the foreign leg payment

$FloatLeg(t_0) = P	au D^f(t_0, t_k) E^f(t_k, t_{k-1}) \exp(\alpha(t_{k-1} - t_0)), \quad (7.2.95)$

where as $\alpha = -\sigma_x \sigma_f 	au_{x,f}$.
Using equation (7.2.95), the value of a quanto swap with (pay) fixed domestic rate and (receive) foreign floating rate

$QSwaplet(t_0) = P	au D^f(t_0, t_k) \{ F^f(t_0, t_{k-1}, t_k) \exp(\alpha(t_{k-1} - t_0)) \} - K$.

# 7.3 FOREIGN EXCHANGE DERIVATIVES

Here, we consider derivatives based on the exchange rate between a domestic currency and a foreign currency. We will use the convention that quantities relating to the domestic currency will have the superscript $d$, while those for the foreign currency will have the superscript $f$. The notation for the various exchange rates is as follows:

+   $X_t^f(t)$ is the spot value of one unit of foreign currency in domestic currency at time $t$,
$X_t^b(t)$ is the spot value of one unit of foreign currency in base currency at time $t$,
$X_t^d(t)$ is the spot value of one unit of domestic currency in base currency at time $t$,
$X_t^f(t,T)$ is the (time $t$) forward value of one unit of foreign currency in domestic currency at time $T$.

Covered Interest Arbitrage
When the current spot rate, $X_t^f(t)$, is known as Covered Interest Arbitrage, it is possible to obtain a value for future spot exchange rate – we denote this foreign exchange rate by $X_t^f(t,T)$, where $T > t$.

Let us consider the following scenarios:

Scenario A
At time $t$ an investor deposits one unit of foreign currency which grows at the (constant) foreign risk-free interest rate $r^f$. By time $T$ the initial amount will have increased to $1/DF^f(t,T)$ units of foreign currency, where $DF^f(t,T) = \exp(-r^f(T-t))$. The foreign currency is converted into domestic currency at the time $T$ forward exchange rate $X_t^f(t,T)$ and yields $X_t^f(t,T)/DF^f(t,T)$ units of domestic currency.

Scenario B
At time $t$ an investor deposits $X_t^f(t)$ units of domestic currency (the scheme is equivalent to one unit of foreign currency), and this grows at the (constant) domestic risk-free interest rate $r^d$. At time $T$ the initial sum will have