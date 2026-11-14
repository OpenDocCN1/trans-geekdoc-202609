```
**Algorithm 13.2:** Sequential importance sampling with resampling (SISR)
1 Initialization: \( z_1^i \sim q_1(z_1), \tilde{w}_1^i = \frac{\tilde{\gamma}_1(z_1^i)}{q_1(z_1^i)}, W_1^i = \frac{\tilde{w}_1^i}{\sum_j \tilde{w}_1^j}, \hat{\pi}_1(z_1) = \sum_{i=1}^{N_s} W_1^i \delta(z_1 - z_1^i) \)
2 for \( t=2:T \) do
3 Compute ancestors \( \mathbf{a}_{t-1}^{1:N_s} = \text{resample}(\tilde{w}_{t-1}^{1:N_s}) \)
4 Select \( \mathbf{z}_{t-1}^{1:N_s} = \text{permute}(\mathbf{a}_{t-1}^{1:N_s}, \mathbf{z}_{t-1}^{1:N_s}) \)
5 Reset unnormalized weights \( \tilde{w}_{t-1}^{1:N_s} = 1/N_s \)
6 for \( i=1:N_s \) do
7 Sample \( z_t^i \sim q_t(z_t | \mathbf{z}_{1:t-1}^i) \)
8 Compute unnormalized weight \( \tilde{w}_t^i = \alpha_t^i = \frac{\tilde{\gamma}_t(z_{1:t}^i)}{\tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1}^i) q_t(z_t^i | \mathbf{z}_{1:t-1}^i)} \)
9 Compute normalized weights \( W_t^i = \frac{\tilde{w}_t^i}{\sum_j \tilde{w}_t^j} \) for \( i=1:N_s \)
10 Compute MC posterior \( \hat{\pi}_t(z_{1:t}) = \sum_{i=1}^{N_s} W_t^i \delta(z_{1:t} - \mathbf{z}_{1:t}^i) \)
```

We can sample from Equation (13.22) in two steps. First we resample \( N_s \) samples from \( \hat{\pi}_{t-1}(\mathbf{z}_{1:t-1}) \) to get a _uniformly weighted_ set of new samples \( \mathbf{z}_{1:t-1}^i \). (See Section 13.2.4 for details on how to do this.) Then we extend each sample using \( z_t^i \sim q_t(z_t | \mathbf{z}_{1:t-1}^i) \), and concatenate \( \mathbf{z}_t^i \) to \( \mathbf{z}_{1:t-1}^i \).
After making a proposal, we compute the unnormalized weights. We use the standard SNIS method, except we "pretend" that the proposal is given by \( \tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1}^i) q_t(\mathbf{z}_t^i | \mathbf{z}_{1:t-1}^i) \) even though we used \( \hat{\pi}_{t-1}(\mathbf{z}_{1:t-1}^i) q_t(\mathbf{z}_t^i | \mathbf{z}_{1:t-1}^i) \). The intuitive reason why this is valid is because the previous weighted approximation, \( \hat{\pi}_{t-1}(\mathbf{z}_{1:t-1}^i) \), was an unbiased estimate of the previous target distribution, \( \tilde{\gamma}_{t-1}(\mathbf{z}_{1:t-1}) \). (See e.g., [CP20b] for more theoretical details.) We then compute the unnormalized weights, which are the same as the incremental weights, since the resampling step sets \( \tilde{w}_{t-1}^i = 1 \). We then normalize these weights and compute the new approximatioong to the target posterior \( \hat{\pi}_t(\mathbf{z}_{1:t}) \). See Algorithm 13.2 for the pseudocode.

# 13.2.3.1 Bootstrap filter

We now consider a special case of SISR, in which the model is an SSM, and the proposal distribution is equal to the dynamical prior:

```
\( q_t(\mathbf{z}_t | \mathbf{z}_{1:t-1}) = p(\mathbf{z}_t | \mathbf{z}_{1:t-1}) \) (13.24)
```

In this case, the corresponding incremental weight in Equation (13.21) simplifies to

```
\( \alpha_t(\mathbf{z}_{1:t}) = \frac{p(\mathbf{y}_t | \mathbf{z}_{1:t}) p(\mathbf{z}_t | \mathbf{z}_{1:t-1})}{q(\mathbf{z}_t | \mathbf{z}_{1:t-1})} = \frac{p(\mathbf{y}_t | \mathbf{z}_t) p(\mathbf{z}_t | \mathbf{z}_{1:t-1})}{p(\mathbf{z}_t | \mathbf{z}_{1:t-1})} = p(\mathbf{y}_t | \mathbf{z}_{1:t}) \) (13.25)
```

This special case is called the **bootstrap filter** [Gor93] or the **survival of the fittest** algorithm [KKR95]. (In the computer vision literature, this is called the **condensation** algorithm, which stands for "conditional density propagation" [IB98].) See Figure 13.2b for an illustration of how this algorithm works, and Figure 13.1b for some sample results on real data.