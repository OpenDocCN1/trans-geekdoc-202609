![](bbox=[0.18, 0.08, 0.82, 0.23])

Figure 29.21: Illustration of Bayesian online changepoint detection (BOCPD). (a) Hypothetical segmentation of a univariate time series divided by changepoints on the mean into three segments of lengths g1 = 4, g2 = 6, and an undetermined length for g3 (since it the third segment has not yet ended). From Figure 1 of [AM07]. Used with kind permission of Ryan Adams.

where \(H(\tau)\) is a hazard function:

\(H(\tau) = \frac{p_g(\tau)}{\sum_{t=\tau}^{\infty} p_g(t)}\) (29.64)

where \(p_g(t)\) is the probability of a segment of length \(t\). See Figure 29.21 for an illustration. If we set \(p_g\) to be a geometric distribution with parameter \(\lambda\), then the hazard function is the constant \(H(\tau) = 1/\lambda\).

The advantage of the run-length representation is that we can define the observation model for a segment in a causal way (that only depends on past data):

\(p(\mathbf{y}_t | \mathbf{y}_{1:t-1}, r_t = r, z_t = k) = p(\mathbf{y}_t | \mathbf{y}_{t-r:t-1}, z_t = k) = \int p(\mathbf{y}_t | \boldsymbol{\eta}) p(\boldsymbol{\eta} | \mathbf{y}_{t-r:t-1}, z_t = k) d\boldsymbol{\eta}\) (29.65)

where \(\boldsymbol{\eta}\) are the parameters that are “local” to this segment. This called the **underlying predictive model** or **UPM** for the segment. The posterior over the UPM parameters is given by

\(p(\boldsymbol{\eta} | \mathbf{y}_{t-r:t-1}, z_t = k) \propto p(\boldsymbol{\eta} | z_t = k) \prod_{i=t-r}^{t-1} p(\mathbf{y}_i | \boldsymbol{\eta})\) (29.66)

where we initialize the prior for \(\boldsymbol{\eta}\) using hyper-parameters chosen by state \(k\). If the model is conjugate exponential, we can compute this marginal likelihood in closed form, and we have

\(\pi_t^{r,k} = p(\mathbf{y}_t | \mathbf{y}_{t-r:t-1}, z_t = k) = p(\mathbf{y}_t | \psi_t^{r,k})\) (29.67)

where \(\psi_t^{r,k}\) are the parameters of the posterior predictive distribution at time \(t\) based on the last \(r\) observations (and using a prior from state \(k\)).

In the special case in which we have \(K = 1\) hidden states, then each segment is modeled independently, and we get a **product partition model** [BH92]:

\(p(\mathbf{y} | \mathbf{r}) = p(\mathbf{y}_{s_1:e_1}) \dots p(\mathbf{y}_{s_N:e_N})\) (29.68)

where \(s_i\) and \(e_i\) are the start and end of segment \(i\), which can be computed from the run lengths \(\mathbf{r}\). (We initialize with \(r_0 = 0\).) Thus there is no information sharing between segments. This can be