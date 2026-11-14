distribution at step \( t \) is

\(\tilde{\gamma}_t(\mathbf{z}_{1:t}) = p(\mathbf{z}_1)p(\mathbf{y}_1|\mathbf{z}_1) \prod_{s=1}^t p(\mathbf{z}_s|\mathbf{z}_{1:s-1})p(\mathbf{y}_s|\mathbf{z}_{1:s}) \qquad (13.5)\)

For example, consider a 1d Gaussian sequence model where the dynamics are first-order Markov, but the observations depend on the entire past sequence (this is example 1.2.1 from [NLS19]):

\(p(z_t|\mathbf{z}_{1:t-1}) = \mathcal{N}(z_t|\phi z_{t-1}, q)\)
\(p(y_t|\mathbf{z}_{1:t}) = \mathcal{N}(y_t| \sum_{s=1}^t \beta^{t-s} z_s, r) \qquad (13.6)\)

If we set \(\beta = 0\), we get \(p(y_t|\mathbf{z}_{1:t}) = \mathcal{N}(y_t|z_t, r)\) (where we define \(0^0 = 1\)), so the model becomes a linear-Gaussian SSM. As \(\beta\) gets larger, the dependence on the past increases, making the inference problem harder. (We will revisit this example below.)

# 13.1.3 SMC samplers for static parameter estimation

Now consider the problem of parameter estimation from a fixed dataset, \(\mathcal{D} = \{ \mathbf{y}_n : n = 1 : N \}\). We suppose the observations are conditionally iid, so the posterior has the form \(p(\mathbf{z}|\mathcal{D}) \propto p(\mathbf{z}) \prod_{n=1}^N p(\mathbf{y}_n|\mathbf{z}) \), where \(\mathbf{z}\) is the unknown parameter. It is not immediately obvious how to approximate \(p(\mathbf{z}|\mathcal{D}) \) using SMC, since we just have one distribution. However, we can convert this into a sequential inference problem in several different ways. One approach, known as **data tempering**, defines the (marginal) target distribution at step \( t \) as \(\tilde{\gamma}_t(\mathbf{z}_t) = p(\mathbf{z}_t)p(\mathbf{y}_{1:t}|\mathbf{z}_t) \). In this case, the number of time steps \( T \) is the same as the number of data samples, \( N \). Another approach, known as **likelihood tempering**, defines the (marginal) target distribution at step \( t \) as \(\tilde{\gamma}_t(\mathbf{z}_t) = p(\mathbf{z}_t)p(\mathcal{D}|\mathbf{z}_t)^{\tau_t} \), where \( 0 = \tau_t < \cdots < \tau_T = 1 \) is a temperature parameter. In this case, the number of steps \( T \) depends on how quickly we anneal the distribution from the initial prior \( p(\mathbf{z}_1) \) to the final target \( p(\mathcal{Z}_T)p(\mathcal{D}|\mathbf{z}_T) \). Once we have defined the marginal target distributions \(\tilde{\gamma}_t(\mathbf{z}_t) \), we need a way to expand this to a joint target distribution over a *sequence* of variables, \(\tilde{\gamma}_t(\mathbf{z}_{1:t}) \), so the distributions become connected to each other. We explain how to do this in Section 13.6. We can then treat the model as an SSM and apply particle filtering. At the end, we extract the final joint target distribution, \(\tilde{\gamma}_T(\mathbf{z}_{1:T}) = p(\mathbf{z}_{1:T})p(\mathcal{D}|\mathbf{z}_T) \), from which we can compute the marginal target distribution \(\tilde{\gamma}_T(\mathbf{z}_T) = p(\mathbf{z}_T, \mathcal{D}) \), from which we can get the posterior \(p(\mathbf{z}|\mathcal{D}) \) by normalizing. We give the details in Section 13.6.

# 13.2 Particle filtering

In this section, we cover the basics of SMC for state space models, culminating in a method known as the **particle filter**.

# 13.2.1 Importance sampling

We start by reviewing the self-normalized importance sampling method (**SNIS**), which is the foundation of the particle filter. (See also Section 11.5.)