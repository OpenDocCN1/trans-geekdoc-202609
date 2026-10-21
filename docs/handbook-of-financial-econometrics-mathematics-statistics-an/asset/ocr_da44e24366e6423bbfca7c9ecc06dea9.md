yields the value of option C_uud in period 0 as C_uud = max[u^2 d S - X, 0]. Similarly, we can determine all the option values under different stock price at expiration date.

Similarly, the binomial model can be generalized into n periods. Lee et al. (2013b) defined the pricing of a call option in a binomial OPM with n periods as equation (102.12).

C = 1/r^n sum_{j=0}^n n!/(j!(n-j)!) p^j (1-p)^{n-j} max[(u)^j (d)^{n-j} S - X, 0]. (102.12)

We can rewrite equation (102.12) as

C = S [ sum_{j=a}^n n!/(j!(n-j)!) p^j (1-p)^{n-j} u^j d^{n-j} / r^n ] - X/r^n [ sum_{j=a}^n n!/(j!(n-j)!) p^j (1-p)^{n-j} ], (102.13)

where a denotes the minimum integer value of j for which u^j d^{n-j} - X will be positive.

It is easy to observe that the second term in brackets in equation (102.13) is a cumulative binomial distribution with parameters n and p. If we define p' ≡ (u/r)p and 1 - p' ≡ (d/r)(1 - p), then the first term in the brackets can also become a cumulative binomial distribution with parameters n and p', as shown in equation (102.14):

p^j (1-p)^{n-j} u^j d^{n-j} / r^n = p'^j (1-p')^{n-j}. (102.14)

Therefore, equation (102.13) can be simplified as

C = S B1(a; n, p') - X/r^n B2(a; n, p), (102.15a)

where

B1(a; n, p') = sum_{j=a}^n C_n^j p'^j (1-p')^{n-j}, (102.15b)

B2(a; n, p) = sum_{j=a}^n C_n^j p^j (1-p)^{n-j}. (102.15c)

# 102.2.2 Black-Scholes model

Black and Scholes (1973) and Merton (1973) have used stochastic Ito calculus to derive an option pricing model. However, if we assume risk-neutral, Lee et al. (2013b) proposed a lognormal distribution approach to derive the