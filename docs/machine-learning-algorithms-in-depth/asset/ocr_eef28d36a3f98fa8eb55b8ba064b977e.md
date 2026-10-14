recursive pass to compute the alphas. It's a real-time algorithm suitable (with appropriate features) for applications such as handwriting or speech recognition. However, we can improve our estimates of the marginals by considering all the data up to time T. Let's figure out how we can do that by introducing the backward pass. The basic idea of the forward–backward algorithm is to partition the Markov chain into past and future by conditioning on z_t. Let T be the time our time series ends. Let's define the marginal probability over all observed data as the following.

γ_t(j) = p(z_t = j | x_{1:T}) = p(z_t = j | x_{1:t}, x_{t+1:T})
= (1/Z_t) p(z_t = j | x_{1:t}) p(x_{t+1:T} | z_t = j)
∝ α_t(j) β_t(j)  (7.17)

Here, we defined β_t(j) = p(x_{t+1:T} | z_t = j) and used conditional independence of the past and future chain conditioned on state z_t. But our question remains: how can we compute β_t(j)? We can use a similar recursion going backward from time t = T.

β_{t-1}(i) = p(x_{t:T} | z_{t-1} = i) = Σ_j p(z_t = j, x_t, x_{t+1:T} | z_{t-1} = i)
= Σ_j p(x_{t+1:T} | z_t = j, x_t, z_{t-1} = i) p(z_t = j, x_t | z_{t-1} = i)
= Σ_j p(x_{t+1:T} | z_t = j) p(z_t = j, x_t | z_{t-1} = i)
= Σ_j p(x_{t+1:T} | z_t = j) p(x_t | z_t = j, z_{t-1} = i) p(z_t = j | z_{t-1} = i)
= Σ_j β_t(j) E_t(j) A(i, j)  (7.18)

We can summarize our derivation in the matrix notation as follows.

β_{t-1} = A(E_t β_t)  (7.19)

Here, the base case is given by the following.

β_T(i) = p(X_{T+1:T} | z_T = i) = 1  (7.20)

This is true since the sequence ends at time T and X_{T+1:T} is a nonevent with probability 1. Having computed both alpha and beta messages, we can combine them to produce our smoothed marginals: γ_t(j) ∝ α_t(j) β_t(j).