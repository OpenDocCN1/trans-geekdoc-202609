# 64.5.2 The mixture Kalman filter

certain probabilistic structure. With discrete indicator variables, the model can be used to deal with outliers, sudden jumps, system failures, environmental changes and clutters. If the λ_t follows a Markov chain regime-switching process with transition probabilities p_ij = Prob[λ_t = j|λ_{t-1}= i], the above state-space model becomes state-space model with regime switching.

Chen and Liu (2000) propose a special sequential Monte Carlo method, the mixture Kalman filter (MKF), which uses a random mixture of the Gaussian distributions to approximate a target distribution. The MKF can be used to filter and estimate the state-space model with regime switching. We introduce the algorithm of the MKF in this following part.

Let y_{1:t} = (y_1,...,y_t) be the observation and λ_{1:t} = (λ_1,...,λ_t) be the regime indicator up to time t. We observe that p(x_t|y_{1:t}) = ∫ p(x_t|λ_{1:t}, y_{1:t})p(λ_{1:t}|y_{1:t})dλ_{1:t}, where p(x_t|λ_{1:t}, y_{1:t}) ~ N{μ_t(λ_{1:t}), Σ_t(λ_{1:t})}, in which, {μ_t(λ_{1:t}), Σ_t(λ_{1:t})} can be obtained by running the Kalman filter with given trajectory λ_{1:t}. The main idea of the MKF is to use a weighted Monte Carlo sample of the indicators,

$$S_t = \{ (λ_{1:t}^{(1)}, w_t^{(1)}), ..., (λ_{1:t}^{(m)}, w_t^{(m)}) \}$$

to represent the distribution p(λ_{1:t}|y_{1:t}). In detail, we sample λ_{1:t}^{(j)}, j = 1,...,N from a pre-selected trial distribution q(λ_{1:t}|y_{1:t}, x_{1:t}) and assign w_t^{(j)} = p(λ_{1:t}|y_{1:t})/q(λ_{1:t}|y_{1:t}, x_{1:t}). Following an importance sampling logic, the mixture of Gaussian distribution

$$\frac{1}{W_t} \sum_{j=1}^N w_t^{(j)} N\{ μ_t(λ_{1:t}^{(j)}), Σ_t(λ_{1:t}^{(j)}) \}$$

where W_t = ∑_{j=1}^N w_t^{(j)}, approximates the target distribution p(x_t|y_{1:t}). For any integrable function h(·), we can estimate the quantity of interest E{h(x_t)|y_{1:t}} as

$$\hat{E}\{h(x_t)|y_{1:t}\} = \frac{1}{W_t} \sum_{j=1}^N w_t^{(j)} \int h(x) \phi\{x; μ_t(λ_{1:t}^{(j)}), Σ_t(λ_{1:t}^{(j)})\} dx,$$

where φ is the Gaussian density function.

Set KF_t^{(j)} = (μ_t(λ_{1:t}^{(j)}), Σ_t(λ_{1:t}^{(j)})), which records the posterior mean and covariance matrix of x_t, conditional on y_{1:t} and a given trajectory λ_{1:t}^{(j)}. This can be obtained by the Kalman filter. Then the MKF updating scheme consists of recursive applications of the following steps. For j = 1,...,N: