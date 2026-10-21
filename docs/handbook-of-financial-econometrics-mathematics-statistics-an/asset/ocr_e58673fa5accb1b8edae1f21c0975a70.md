In binomial model settings, stock price S either goes up with Increase Factor (u) to arrive uS or down with Decrease Factor (d) to arrive dS at each period, where u = 1 + percentage of increase, d = 1 − percentage of decrease.

Let i = interest rate; r = 1 + i; C_u = max[uS − X, 0], call option price after stock price increases; C_d = max[dS − X, 0], call option price after stock price decreases.

To intuitively grasp the underlying concept of option pricing, here we set up a *risk-free portfolio* — a combination of assets that produces the same return in every state of the world over the investment horizon. The investment horizon here is assumed to be one period. We buy h shares of the stock and sell the call option at its current price of C to set up the portfolio.² Moreover, we choose the value of h such that our portfolio after one period will yield the same payoff whether the stock goes up or down, which is shown as follows:

$h(uS) - C_u = h(dS) - C_d.$  (102.1)

By solving h, we can obtain the number of shares of stock we should buy for each call option we sell, as the following equation shows:

$h = \frac{C_u - C_d}{(u - d)S}.$  (102.2)

Here h is called the *hedge ratio*. Because our portfolio yields the same return under either of the two possible states for the stock price without risk, then it should yield the risk-free rate of return, which is equal to the risk-free borrowing and lending rate. This condition must hold; otherwise, there would be a chance to earn a risk-free profit, which is known as an arbitrage opportunity. Therefore, the ending portfolio value must be equal to r (1 + risk-free rate) times the beginning portfolio value, as defined in the following equation:

$r(hS - C) = h(uS) - C_u = h(dS) - C_d.$  (102.3)

Note that S and C represent the stock price and the option price at period 0, respectively. Substituting h as equation (102.2) shows, we get the