Combining (65.8) with (65.7) the pdf of W1 is

f(w1)=c sigma/(sqrt(2) sqrt(T)) (sqrt(2) sigma / sqrt(T))^{(T-1)/2} sum_{r=0}^{infty} ( mu/(sigma^2/T) w1 - 1/2 )^r * 1/r! (sqrt(2) sigma / sqrt(T))^r Gamma((2r+T+1)/4) (1/w1^2)^{(2r+T+1)/4}, -infty < w1 < infty. (65.9)

Now transform from W1 to U = (T - 1)W1/sigma^2, since U = Ybar / S^2 and it is U whose distribution we are seeking. From (65.9) the pdf of U is, after combining terms and simplifying, say

f(mu)=c1 sum_{r=0}^{infty} Gamma((2r+T+1)/4) 1/r! ( 2 mu T u - (T-1) / (sqrt(2T) sigma) )^r (1/u^2)^{(2r+T+1)/4}, -infty < u < infty. (65.10)

where

c1 = e^{-T mu^2 / (2 sigma^2)} / [ sqrt(pi) 2^{(T+3)/4} ( sigma sqrt(T)/(T-1) )^{(T-1)/2} Gamma((T-1)/2) ] > 0,

and with parameters -infty < mu < infty, sigma > 0, and sample size T > 1.

Equation (65.10), therefore, gives the exact sampling distribution of the statistic U = Ybar / S^2 in terms of T, mu, and sigma. That is, (65.10) gives the exact pdf of the statistic we are interested in, with parameters T, mu, and sigma. It is possible to define a function of U, say U' = 2 sqrt(T) sigma U/(T - 1), which is not a statistic when sigma is unknown, but whose pdf is parameterized by T and the ratio mu sqrt(T)/sigma. This is equivalent to finding the pdf of the ratio of, say V1 = sqrt(T) Z1/sigma to V2 = Z2/2, instead of Z1/Z2. However, we are actually interested in the pdf of a different function of U, namely beta_hat_ML. Indeed, given the exact sampling distribution of U = Ybar / S^2, from (65.10), the exact sampling distribution of beta_hat_ML = Ybar / S^2 + 1/2 can be found easily. However, it is interesting to consider the uniformly minimum variance unbiased (MVU) estimator of beta for the lognormal assumption considered by Brown and Gibbons (1985). First we shall give another representation of the