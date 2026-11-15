
functions, as is suggested in Ref. [11]. Gaussian mixtures have proved to be an effective way for modeling heterogeneous populations [12]. Intuitively, Eq. (9.3) can be rewritten in the following form:

$$g(e|\omega, \theta)=\sum_{i=1}^{N} \omega_i f_i(e_i|\theta_i)$$ (9.4)

In the particular case in which the f(e_i | \theta_i) are all normal distributions, \theta = (\mu_1, \sigma_1 ... \mu_N, \sigma_N) represents each client's belief. f(e_i | \theta_i) is the density of a Gaussian distribution with mean \mu_i and variance \sigma_i. \theta denotes the unknown mean and variance for global distribution. The purpose is to find the parameter \omega and \theta so that the global data distribution can be obtained. Since the parameters are unknown, from the Bayesian perspective, Eq. (9.4) can be interpreted as to infer the posterior probability distribution of the model parameters given the measurement or observations e. Then, the estimated distribution parameter will be broadcast to all the clients. In this way, the client can be aware of the difference between a local distribution and global distribution. The overall scenario is illustrated in Figure 9.1.

![](img/0dd4397c67b063014553965e4f1cf7e4_173_0.png)

**FIGURE 9.1** Scenario description: we consider there are multiple users taking part in a federated analytics task to obtain the whole dataset distribution. Each user can only have partial observations among the whole dataset due to the limitation of sensing and mobility range. For each user, the on-device private data analysis will be performed locally because of privacy concern. After individual evaluation is done, all the participants will upload their dataset features to the aggregator, which is done by an edge server covering this area. By doing aggregation, the estimation of distribution regarding the whole dataset can be obtained. Then, the estimated distribution will be broadcast to all the clients to make them aware of the difference between a local distribution and global distribution. This process will be performed iteratively to keep the global distribution updated with more samples observed from the user side.

## 9.3 Methodology

In this section, the concept of the missing data approach is introduced in Section 9.3.1. Then, the MCMC and standard MH is introduced in detail in Section 9.3.2. Finally, the delayed rejection technique is elaborated in Section 9.3.3, and the proposed FMCMC-DR algorithm is given accordingly.

### 9.3.1 Missing Data Approach

As is discussed in the previous section, the main challenge to obtain the global distribution is to estimate and calculate the unknown parameters, i.e., \(\omega\) and \(\theta\). Assume the kernel functions are convex, the expectation of Eq. (9.3) is also a convex combination of expectations, i.e.,

\( E[e] = \sum_{i=1}^N \omega_i E[e_i] \)
\( = \sum_{i=1}^N \omega_i E[e_i | \theta_i] \)

Therefore, deriving an expectation estimator of a Gaussian mixture can be an effective way to solve Eq. (9.3).

However, the form of the mixture model denoted by Eq. (9.3) is disadvantageous to derive a Bayesian estimator. Therefore, in order to obtain the parameters \(\omega\) and \(\theta\), the corresponding posterior expectation Eq. (9.5) can be rewritten as the structure of likelihood expansions containing \(N^K\) terms, i.e.,

\( L(\omega, \theta | e) = \sum_{j=1}^K \sum_{i=1}^N \omega_i \phi_i(e_j | \theta_i). \)

As we can see, since the likelihood is given by \(N^K\) components, this will lead to a huge computation cost, even when the number of devices \(N\) is not very large. Therefore, a way to reduce the complexity of Eq. (9.6) has to be applied, where one of common but effective approach is missing data approach.

One interpretation of the mixture model is that the observation happens among a dataset that is made up of several strata, while the allocation of observation to a specific group is lost. Therefore, for each evidence \(e_i\), it has a probability of \(\omega_i\) to be allocating into sub-group \(\varphi_i\). Because the structure is not clear or lost, an auxiliary variable can be introduced, which aims at identifying the specific sub-group or mixture component each observation is generated from. This is also the reason why this method is named as the missing data approach. Here, we denote this auxiliary variable as \(z_j\). To construct $z_j$ the association of observations $e$ from $N$ mixture components and $z_j$ is

\(e_j|z_j = i \sim \phi(e_j|\theta_i)\) (9.7)

and

\(p(z_j = i) = \omega_i\) (9.8)

This auxiliary variable $z_j$ identifies to which component the observation $e_j$ belongs to [13]. In other words, for each sample of data $e = (e_1, ..., e_N)$, we assume a missing dataset $z = (z_1, ..., z_N)$, rendering the corresponding labels to indicate the specific mixture sub-population from which the observation has been generated.

By utilizing the constructed auxiliary random variable, the likelihood in Eq. (9.6) can be simplified into:

\( L(\omega, \theta|e, Z) = \prod_{j=1}^K \omega_{z_j} \phi(e_j|\theta_{z_j}) \\
= \prod_{i=1}^N \omega_i^{k_i} \left[ \prod_{j:z_j=i} \phi(e_j|\theta_i) \right] \) (9.9)

where \(k_i\) equals to the number of \(z_j=i\) and \(\sum_i k_i = K\). Then, the posterior probability that the observation \(e_j\) belongs to the \(i\)-th mixture component is:

\( p(z_j=i|e_j, \omega, \theta) = \frac{\omega_i \phi(e_j|\theta_i)}{\sum_{i=1}^N \omega_i \phi(e_j|\theta_i)} \) (9.10)

Since we assume the kernel functions are Gaussian, the corresponding estimated likelihood can be further written as the following:

\( L(\omega, \mu, \sigma|e, z) \propto \prod_{i=1}^N \omega_i \exp \left( - \frac{\sigma_i}{2} (e_j - \mu_i)^2 \right) \) (9.11)

Accordingly, the posterior probability is:

\( P(z_j=i|e_j, \omega, \mu, \sigma) = \frac{\omega_i \exp \left( - \frac{\sigma_i}{2} (e_j - \mu_i)^2 \right)}{\sum_{l=1}^N \omega_l \left( \exp \left( - \frac{\sigma_l}{2} (e_j - \mu_l)^2 \right) \right)} \) (9.12)

### 9.3.2 Markov Chain Monte Carlo Method

In order to obtain the posterior probability, we firstly introduce the MCMC method, which utilizes the properties of the Monte Carlo method and Markov chain. Generally, parameter distribution cannot be obtained analytically. Therefore, the Monte Carlo aims to conduct repeated random sampling and use the expectation of sampling to estimate or approximate parameters. Therefore, how to perform high-volume sampling efficiently is challenging, which motivates the utilization of the Markov chain. The definition of a Markov chain is as follows.

### Definition 9.1

A Markov chain is a sequence of random variables Q_1, Q_2, Q_3..., where the probability of moving to the next state is dependent on the current state while independent on the previous states:

$$P(Q_{t+1} = q \mid Q_1 = q_1, Q_2 = q_2, ..., Q_t = q_t) = P(Q_{t+1} = q \mid Q_t = q_t).$$ (9.13)

By this definition, for each Markov chain, there exists a state transition matrix that describes the probabilities of the transition for any two states in this chain, which can be written as:

$$T = \begin{bmatrix} p_{11} & p_{12} & ... & p_{1n} \\ p_{21} & p_{22} & ... & p_{2n} \\ \vdots & \vdots & \vdots & \vdots \\ p_{n1} & p_{n2} & ... & p_{nn} \end{bmatrix}$$ (9.14)

With regard to matrix T, there are several properties.

### Theorem 9.1

For an irreducible, aperiodic Markov chain, with finite or infinite state space, the existence of a stationary distribution $\pi$ ensures that the Markov chain will converge to $\pi$ as t approaches $\infty$, i.e.,

$$\lim_{t \to \infty} P_{ij}^t = \pi(j)$$ (9.15)

where the stationary distribution can be described as $\pi = [\pi_1, \pi_2, ... \pi_n]$ and the summation of all the elements equals to one, i.e., $\sum_{j=1}^n \pi(j) = 1$.

Another important property of the Markov chain is the detailed balance, which is defined as follows.

### Definition 9.2

Let \(Q_1, Q_2...\) be a Markov chain with stationary distribution \(\pi\). The chain is said to be reversible with respect to \(\pi\) or satisfy detailed balance with respect to \(\pi\) if

\(\pi_i P_{ij} = \pi_j P_{ji}, \forall i, j \quad (9.16)\)

Intuitively, if the stationary distribution of the Markov chain is exactly the posterior probability distribution, the problem can be solved. The Monte Carlo method utilizes the property of the Markov chain for sampling. Suppose a random sample \(q_0\) is given. According to the convergence property of the Markov chain, after \(t\) times sampling, the probability distribution converges to a stationary state \(\pi(q)\).

Then, suppose sampling starts from \(t + 1\), the newly obtained \(\pi_{t+1}\) needs to be equal to \(\pi_t\). With the detailed balance property, we can derive \(\pi T = \pi\). If we can obtain the matrix \(T\), the sampling can be proceeded through random walk. Now the problem is how to get \(T\), where the Metropolis-Hastings algorithm is the effective method.

The purpose is to construct transition probability matrix \(T\). In the Metropolis-Hastings algorithm, the acceptance rate is employed to evaluate the feasibility to adopt the newly obtained sample from \(Q(q^*|q_i)\). Therefore, to interpret this, we can consider these two parts contributes to form \(T\) together, i.e., \(T(q^*|q_i) \Rightarrow Q(q^*|q_i) \times \min\left(1, \frac{\pi(q^*)Q(q_i|q^*)}{\pi(q_i)Q(q^*|q_i)}\right)\). When the acceptance rate equals to 1, \(u\) is smaller than 1, which indicates that \(Q(q^*|q_i)\) is the value of \(T\). On the contrary, when the acceptance is less than one, the value \(\frac{\pi(q^*)Q(q_i|q^*)}{\pi(q_i)Q(q^*|q_i)}\) is the required \(T\) [14].

However, for the mixture model, there are multiple parameters to estimate, where a Federated MCMC algorithm is proposed to solve this problem. In order to model parameters, \(\omega, \mu\) and \(\sigma\), we assume conjugate prior and posterior pairs as the following:

- 1. \([\omega \sim D(\delta_1, ..., \delta_n), \omega | e, z \sim D(\delta_1^*, ..., \delta_n^*)]\)

- 2. \([\sigma_i \sim G(\frac{\alpha}{2}, \frac{\beta}{2}), \sigma_i | e, z \sim G(\frac{\alpha^*}{2}, \frac{\beta^*}{2})]\)

- 3. \([\mu_i | \sigma_i \sim N(m_i, \frac{1}{a_i \sigma_i}), \mu_i | e, z, \sigma_i \sim N(m_i^*, \frac{1}{a_i^* a_i})]\)
