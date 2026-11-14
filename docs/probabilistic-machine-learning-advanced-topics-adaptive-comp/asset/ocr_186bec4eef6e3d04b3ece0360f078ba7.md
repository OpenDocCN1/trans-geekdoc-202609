from which we get the new smoothed marginal distribution:

\(p(\mathbf{z}_t|\mathbf{y}_{1:T}) = p(\mathbf{z}_t|\mathbf{y}_{1:t}) \int \left[ \frac{p(\mathbf{z}_{t+1}|\mathbf{z}_t)p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T})}{p(\mathbf{z}_{t+1}|\mathbf{y}_{1:t})} \right] d\mathbf{z}_{t+1}\)

\(= \int p(\mathbf{z}_t, \mathbf{z}_{t+1}|\mathbf{y}_{1:t}) \frac{p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T})}{p(\mathbf{z}_{t+1}|\mathbf{y}_{1:t})} d\mathbf{z}_{t+1}\)

Intuitively we can interpret this as follows: we start with the two-slice filtered distribution, \(p(\mathbf{z}_t, \mathbf{z}_{t+1}|\mathbf{y}_{1:t})\), and then we divide out the old \(p(\mathbf{z}_{t+1}|\mathbf{y}_{1:t})\) and multiply in the new \(p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T})\), and then marginalize out \(\mathbf{z}_{t+1}\).

# ## 8.1.4 The Gaussian ansatz

In general, computing the integrals required to implement Bayesian filtering and smoothing is intractable. However, there are two notable exceptions: if the state space is discrete, as in an HMM, we can represent the belief states as discrete distributions (histograms), which we can update using the forwards-backwards algorithm, as discussed in Section 9.2; and if the SSM is a linear-Gaussian model, then we can represent the belief states by Gaussians, which we can update using the Kalman filter and smoother, which we discuss in Section 8.2.2 and Section 8.2.3. In the nonlinear and/or non-Gaussian setting, we can still use a Gaussian to represent an approximate belief state, as we discuss in Section 8.3, Section 8.4, Section 8.5 and Section 8.6. We discuss some non-Gaussian approximations in Section 8.7.

For most of this chapter, we assume the SSM can be written as a nonlinear model subject to additive Gaussian noise:

\(\mathbf{z}_t = \mathbf{f}(\mathbf{z}_{t-1}, \mathbf{u}_t) + \mathcal{N}(\mathbf{0}, \mathbf{Q}_t)\)
\(\mathbf{y}_t = \mathbf{h}(\mathbf{z}_t, \mathbf{u}_t) + \mathcal{N}(\mathbf{0}, \mathbf{R}_t)\)

where \(\mathbf{f}\) is the transition or dynamics function, and \(\mathbf{h}\) is the observation function. In some cases, we will further assume that these functions are linear.

# ## 8.2 Inference for linear-Gaussian SSMs

In this section, we discuss inference in SSMs where all the distributions are linear Gaussian. This is called a **linear Gaussian state space model (LG-SSM)** or a **linear dynamical system (LDS)**. We discuss such models in detail in Section 29.6, but in brief they have the following form:

\(p(\mathbf{z}_t|\mathbf{z}_{t-1}, \mathbf{u}_t) = \mathcal{N}(\mathbf{z}_t|\mathbf{F}_t\mathbf{z}_{t-1} + \mathbf{B}_t\mathbf{u}_t + \mathbf{b}_t, \mathbf{Q}_t)\)
\(p(\mathbf{y}_t|\mathbf{z}_t, \mathbf{u}_t) = \mathcal{N}(\mathbf{y}_t|\mathbf{H}_t\mathbf{z}_t + \mathbf{D}_t\mathbf{u}_t + \mathbf{d}_t, \mathbf{R}_t)\)

where \(\mathbf{z}_t \in \mathbb{R}^{N_z}\) is the hidden state, \(\mathbf{y}_t \in \mathbb{R}^{N_y}\) is the observation, and \(\mathbf{u}_t \in \mathbb{R}^{N_u}\) is the input. (We have allowed the parameters to be time-varying, for later extensions that we will consider.) We often assume the means of the process noise and observation noise (i.e., the bias or offset terms) are zero, so \(\mathbf{b}_t = \mathbf{0}\) and \(\mathbf{d}_t = \mathbf{0}\). In addition, we often have no inputs, so \(\mathbf{B}_t = \mathbf{D}_t = \mathbf{0}\). In this case, the model