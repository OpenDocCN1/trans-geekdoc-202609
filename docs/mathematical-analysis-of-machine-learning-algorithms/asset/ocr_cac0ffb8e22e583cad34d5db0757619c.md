Note that the random choice of the returned predictor in the perceptron algorithm is for the purpose of online to batch conversion, which we will discuss later. In the following, we first state the mistake bound of perceptron as follows.

# Theorem 14.1

Consider the perceptron algorithm in algorithm 14.1. Consider γ > 0 and weight vector w_* such that for all t

$$w_*^\top X_t Y_t \ge \gamma.$$

Then we have the following mistake bound:

$$\sum_{t=1}^T \mathbf{1}(w_{t-1}^\top X_t Y_t \le 0) \le \frac{\|w_*\|_2^2 \sup\{\|X_t\|_2^2\}}{\gamma^2}.$$

Proof Let M = sup_t ||X_t||_2, and let η = γ / M^2. Assume that we have a mistake at time step t, then we have

$$(\eta w_{t-1} - w_*)^\top X_t Y_t \le 0 - w_*^\top X_t Y_t \le -\gamma.$$

This implies that

$$\|\eta w_t - w_*\|_2^2 = \|\eta w_{t-1} + \eta X_t Y_t - w_*\|_2^2 = \|\eta w_{t-1} - w_*\|_2^2 + 2\eta(\eta w_{t-1} - w_*)^\top X_t Y_t + \eta^2 \|X_t\|_2^2 \le \|\eta w_{t-1} - w_*\|_2^2 - 2\eta\gamma + \eta^2 M^2 \le \|\eta w_{t-1} - w_*\|_2^2 - \frac{\gamma^2}{M^2}.$$

Note also that $\|\eta w_t - w_*\|_2^2 = \|\eta w_{t-1} - w_*\|_2^2$ if there is no mistake at time step t. Therefore by summing over t = 1 to t = T, we obtain

$$0 \le \|\eta w_t - w_*\|_2^2 \le \|\eta w_0 - w_*\|_2^2 - \frac{\gamma^2}{M^2} k,$$

where k is the number of mistakes. This implies the bound.

The perceptron mistake bound can be regarded as an online version of the margin bound discussed in Chapter 9, where empirical process was used to obtain similar margin bounds for the ERM method. The technique required for analyzing the ERM method is much more complicated.