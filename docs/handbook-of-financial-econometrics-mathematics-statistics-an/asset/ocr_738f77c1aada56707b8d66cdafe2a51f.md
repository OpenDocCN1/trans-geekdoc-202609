![](bbox=[0.22, 0.1, 0.78, 0.42])

Figure 85.4: American call option price as a function of the ex-dividend stock price immediately prior to the ex-dividend instant. Early exercise will not be optimal.

Figure 85.4 depicts a case in which early exercise will not occur at the ex-dividend instant, t. Early exercise will not occur if the functions, S_t + D - X and c(S_t, T - t; X) do not intersect, as is depicted in Figure 85.4. In this case, the lower boundary condition of the European call, S_t - X e^{-r(T-t)}, lies above the early exercise proceeds, S_t + D - X, and hence the call option will not be exercised early. Stated explicitly, early exercise is not rational if

$S_t + D - X < S_t - X e^{-r(T-t)}$

This condition for no early exercise is the same as (85.84), where S_t is the ex-dividend stock price and where the investor is standing at the ex-dividend instant, t. The condition can also be written as

$D < X[1 - e^{-r(T-t)}].\tag{85.85}$

In words, if the ex-dividend stock price decline — the dividend — is less than the present value of the interest income that would be earned by deferring exercise until expiration, early exercise will not occur. When condition (85.85) is met, the value of the American call is simply the value of the corresponding European call.

The lower price bound of an American put option is somewhat different. In the absence of a dividend, an American put may be exercised early. In the presence of a dividend payment, however, there is a period just prior to the ex-dividend date when early exercise is suboptimal. In that period, the interest earned on the exercise proceeds of the option is less than the drop in the stock price from the payment of the dividend. If t_n represents a time prior to the dividend payment at time t, early exercise is suboptimal, where (X - S) e^{-r(t - t_n)} is less than (X - S + D). Rearranging, early exercise