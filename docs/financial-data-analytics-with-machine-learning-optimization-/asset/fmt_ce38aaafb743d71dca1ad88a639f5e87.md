
Furthermore, the `delta` of a European call option is expected to be positive as the price of a call option increases with the current price of the underlying asset. When `S_t << K`, i.e. when the call option is far out-of-the-money, call options are mostly worthless, and they have deltas close to 0. On the other hand, managers can construct a portfolio with a positive delta so as to bet on the greater increase in the price of the underlying asset. More specifically, to calculate the Greeks of a European call option under the Black–Scholes framework, we first recall their celebrated formula (also see [Example 5.6](#c05.xhtml#c05-fea-0026)): at time `t`, its price is

`C_t = S_t Φ(d_+) - e^(-r(T-t)) K Φ(d_-)`

where `Φ(·)` is the cdf of the standard normal distribution, `d_+ := (ln(S_t/K) + (r + σ²/2)(T-t)) / (σ√(T-t))` and `d_- := d_+ - σ√(T-t)`. We can compute various Greeks of a European call option as follows:
