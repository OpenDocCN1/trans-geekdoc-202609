
distribution at step \( t \) is

\(\tilde{\gamma}_t(\mathbf{z}_{1:t}) = p(\mathbf{z}_1)p(\mathbf{y}_1|\mathbf{z}_1) \prod_{s=1}^t p(\mathbf{z}_s|\mathbf{z}_{1:s-1})p(\mathbf{y}_s|\mathbf{z}_{1:s}) \qquad (13.5)\)

For example, consider a 1d Gaussian sequence model where the dynamics are first-order Markov, but the observations depend on the entire past sequence (this is example 1.2.1 from [NLS19]):

\(p(z_t|\mathbf{z}_{1:t-1}) = \mathcal{N}(z_t|\phi z_{t-1}, q)\)
\(p(y_t|\mathbf{z}_{1:t}) = \mathcal{N}(y_t| \sum_{s=1}^t \beta^{t-s} z_s, r) \qquad (13.6)\)

If we set \(\beta = 0\), we get \(p(y_t|\mathbf{z}_{1:t}) = \mathcal{N}(y_t|z_t, r)\) (where we define \(0^0 = 1\)), so the model becomes a linear-Gaussian SSM. As \(\beta\) gets larger, the dependence on the past increases, making the inference problem harder. (We will revisit this example below.)

### 13.1.3 SMC samplers for static parameter estimation

Now consider the problem of parameter estimation from a fixed dataset, \(\mathcal{D} = \{ \mathbf{y}_n : n = 1 : N \}\). We suppose the observations are conditionally iid, so the posterior has the form \(p(\mathbf{z}|\mathcal{D}) \propto p(\mathbf{z}) \prod_{n=1}^N p(\mathbf{y}_n|\mathbf{z}) \), where \(\mathbf{z}\) is the unknown parameter. It is not immediately obvious how to approximate \(p(\mathbf{z}|\mathcal{D}) \) using SMC, since we just have one distribution. However, we can convert this into a sequential inference problem in several different ways. One approach, known as **data tempering**, defines the (marginal) target distribution at step \( t \) as \(\tilde{\gamma}_t(\mathbf{z}_t) = p(\mathbf{z}_t)p(\mathbf{y}_{1:t}|\mathbf{z}_t) \). In this case, the number of time steps \( T \) is the same as the number of data samples, \( N \). Another approach, known as **likelihood tempering**, defines the (marginal) target distribution at step \( t \) as \(\tilde{\gamma}_t(\mathbf{z}_t) = p(\mathbf{z}_t)p(\mathcal{D}|\mathbf{z}_t)^{\tau_t} \), where \( 0 = \tau_t < \cdots < \tau_T = 1 \) is a temperature parameter. In this case, the number of steps \( T \) depends on how quickly we anneal the distribution from the initial prior \( p(\mathbf{z}_1) \) to the final target \( p(\mathcal{Z}_T)p(\mathcal{D}|\mathbf{z}_T) \). Once we have defined the marginal target distributions \(\tilde{\gamma}_t(\mathbf{z}_t) \), we need a way to expand this to a joint target distribution over a *sequence* of variables, \(\tilde{\gamma}_t(\mathbf{z}_{1:t}) \), so the distributions become connected to each other. We explain how to do this in Section 13.6. We can then treat the model as an SSM and apply particle filtering. At the end, we extract the final joint target distribution, \(\tilde{\gamma}_T(\mathbf{z}_{1:T}) = p(\mathbf{z}_{1:T})p(\mathcal{D}|\mathbf{z}_T) \), from which we can compute the marginal target distribution \(\tilde{\gamma}_T(\mathbf{z}_T) = p(\mathbf{z}_T, \mathcal{D}) \), from which we can get the posterior \(p(\mathbf{z}|\mathcal{D}) \) by normalizing. We give the details in Section 13.6.

## 13.2 Particle filtering

In this section, we cover the basics of SMC for state space models, culminating in a method known as the **particle filter**.

### 13.2.1 Importance sampling

We start by reviewing the self-normalized importance sampling method (**SNIS**), which is the foundation of the particle filter. (See also Section 11.5.)

Suppose we are interested in estimating the expectation of some function \(\varphi_t\) with respect to a target distribution \(\pi_t\), which we denote by

\(\pi_t(\varphi) \triangleq \mathbb{E}_{\pi_t}[\varphi_t(z_{1:t})] = \int \frac{\tilde{\gamma}_t(z_{1:t})}{Z_t} \varphi_t(z_{1:t}) dz_{1:t}\)

where \(Z_t = \int \tilde{\gamma}_t(z_{1:t}) dz_{1:t}\). Suppose we use SNIS with proposal \(q_t(z_{1:t})\). We then get the following approximation:

\(\pi_t(\varphi) \approx \frac{1}{\hat{Z}_t} \frac{1}{N_s} \sum_{i=1}^{N_s} \tilde{w}_t^i(z_{1:t}^i) \varphi_t(z_{1:t}^i)\)

where \(z_{1:t}^i \stackrel{\text{iid}}{\sim} q_t\) are independent samples from the proposal, \(\tilde{w}_t^i\) are the **unnormalized weights** defined by

\(\tilde{w}_t^i = \frac{\tilde{\gamma}_t(z_{1:t}^i)}{q_t(z_{1:t}^i)}\)

and \(\hat{Z}_t\) is the approximate normalization constant defined by

\(\hat{Z}_t \triangleq \frac{1}{N_s} \sum_{i=1}^{N_s} \tilde{w}_t^i\)

To simplify notation, let us define the **normalized weights** by

\(W_t^i = \frac{\tilde{w}_t^i}{\sum_j \tilde{w}_t^j}\)

Then we can write

\(\mathbb{E}_{\pi_t}[\varphi_t(z_{1:t})] \approx \sum_{i=1}^{N_s} W_t^i \varphi_t(z_{1:t}^i)\)

Alternatively, instead of computing the expectation of a specific target function, we can just approximate the target distribution itself, using a sum of weighted samples:

\(\pi_t(z_{1:t}) \approx \sum_{i=1}^{N_s} W_t^i \delta(z_{1:t} - z_{1:t}^i) \triangleq \hat{\pi}_t(z_{1:t})\)

The problem with importance sampling when applied in the context of sequential models is that the dimensionality of the state space is very large, and increases with \(t\). This makes it very hard to define a good proposal that covers the high probability regions, resulting in most samples getting negligible weight. In the sections below, we discuss solutions to this problem.

### 13.2.2 Sequential importance sampling

In this section, we discuss sequential importance sampling or **SIS**, in which the proposal has the following autoregressive structure:

$q_t(\mathbf{z}_{1:t}) = q_{t-1}(\mathbf{z}_{1:t-1})q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})$

We can obtain samples from $q_{t-1}(\mathbf{z}_{1:t-1})$ by reusing the $\mathbf{z}_{1:t-1}^i$ samples, which we then extend by one step by sampling from the conditional $q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1}^i)$. We can think of this as “growing” the chain (sequence of states). The unnormalized weights can be computed recursively as follows:

\begin{aligned}
\tilde{w}_t(\mathbf{z}_{1:t}) &= \frac{\tilde{\gamma}_t(\mathbf{z}_{1:t})}{q_t(\mathbf{z}_{1:t})} = \frac{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})}{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})q_{t-1}(\mathbf{z}_{1:t-1})} \\
&= \frac{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})}{q_{t-1}(\mathbf{z}_{1:t-1})} \frac{\tilde{\gamma}_t(\mathbf{z}_{1:t})}{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})} \\
&= \tilde{w}_{t-1}(\mathbf{z}_{1:t-1}) \frac{\tilde{\gamma}_t(\mathbf{z}_{1:t})}{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})}
\end{aligned}

The ratio factors are sometimes called the **incremental importance weights**:

$\alpha_t(\mathbf{z}_{1:t}) = \frac{\tilde{\gamma}_t(\mathbf{z}_{1:t})}{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})}$

See Algorithm 13.1 for pseudocode for the resulting SIS algorithm. (In practice we compute the weights in log-space, and convert back using the log-sum-exp trick.)

Note that, in the special case of state space models, the weight computation can be further simplified. In particular, suppose we have

\begin{aligned}
\tilde{\gamma}_t(\mathbf{z}_{1:t}) &= p(\mathbf{z}_{1:t}, \mathbf{y}_{1:t}) = p(\mathbf{y}_t|\mathbf{z}_{1:t})p(\mathbf{z}_t|\mathbf{z}_{1:t-1})p(\mathbf{z}_{1:t-1}, \mathbf{y}_{1:t-1}) \\
&= p(\mathbf{y}_t|\mathbf{z}_{1:t})p(\mathbf{z}_t|\mathbf{z}_{1:t-1})\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})
\end{aligned}

Then the incremental weight is given by

$\alpha_t(\mathbf{z}_{1:t}) = \frac{p(\mathbf{y}_t|\mathbf{z}_{1:t})p(\mathbf{z}_t|\mathbf{z}_{1:t-1})\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})}{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1})q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})} = \frac{p(\mathbf{y}_t|\mathbf{z}_{1:t})p(\mathbf{z}_t|\mathbf{z}_{1:t-1})}{q_t(\mathbf{z}_t|\mathbf{z}_{1:t-1})}$

Unfortunately SIS suffers from a problem known as **weight degeneracy** or **particle impoverishment**, in which most of the weights become very small (near zero), so the posterior ends up being approximated by a single particle. This is illustrated in Figure 13.2a, where we apply SIS to the non-Markovian example in Equation (13.6) using $N_s = 5$ particles. The reason for degeneracy is that each particle has to “explain” (generate) the entire sequence of observations. Each sequence of guessed states becomes increasingly improbable over time, due to the product of likelihood terms, and the differences between the weights of each hypothesis will grow exponentially. Of course, there has to be a best sequence amongst the set of candidates, so when we normalize the weights, the best one will get weight 1 and the rest will get weight 0. But this is a waste of most of the particles. We discuss a solution to this in Section 13.2.3.
