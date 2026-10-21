![](bbox=[0.15, 0.12, 0.85, 0.44])

Figure 85.3: American call option price as a function of the ex-dividend stock price immediately prior to the ex-dividend instant. Early exercise may be optimal.

we get

$C(S,T;X) \ge \max[0, S - X e^{-rt}, S - D e^{-rt} - X e^{-rT}].$ (85.83a)

The last two terms on the right-hand side of (85.83a) provide important guidance in deciding whether to exercise the American call option early, just prior to the ex-dividend instant. The second term in the squared brackets is the present value of the early exercise proceeds of the call. If the amount is less than the lower price bound of the call that expires normally, that is, if

$S - X e^{-rt} \le S - D e^{-rT} - X e^{-rt},$ (85.84)

the American call option will not be exercised just prior to the ex-dividend instant. To see why, simply rewrite (85.84) so it reads

$D < X[1 - e^{-r(T-t)}].$ (85.85)

In other words, the American call will not be exercised early if the dividend captured by exercising prior to the ex-dividend date is less than the interest implicitly earned by deferring exercise until expiration.

Figure 85.3 depicts a case in which early exercise could occur at the ex-dividend instant, t. Just prior to ex-dividend, the call option may be exercised yielding proceeds $S_t + D - X$, where $S_t$ is the ex-dividend stock price. An instant later, the option is left unexercised with value $c(S_t, T - t; X)$, where $c(\bullet)$ is the European call option formula. Thus, if the ex-dividend stock price, $S_t$ is above the critical ex-dividend stock price where the two functions intersect, $S_t^*$, the option holder will choose to exercise his or her option early just prior to the ex-dividend instant. On the other hand, if $S_t \le S_t^*$, the option holder will choose to leave her position open until the option's expiration.