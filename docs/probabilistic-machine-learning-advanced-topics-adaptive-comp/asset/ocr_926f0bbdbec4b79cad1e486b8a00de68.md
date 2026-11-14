# 13.3.2 Proposals based on the extended and unscented Kalman filter

One way to approximate the locally optimal proposal distribution is based on the extended Kalman filter (Section 8.3.2) or the unscented Kalman filter (Section 13.3.2), which gives rise to the extended particle filter [DGA00] and unscented particle filter [Mer+00] respectively. To explain these methods, we follow the presentation of [NLS19, p36]. As usual, we assume the dynamical system can be written as \(\mathbf{z}_t = \mathbf{f}(\mathbf{z}_{t-1}) + \mathbf{q}_t\) and \(\mathbf{y}_t = \mathbf{h}(\mathbf{z}_t) + \mathbf{r}_t\), where \(\mathbf{q}_t\) is the system noise and \(\mathbf{r}_t\) is the observation noise. The EKF and UKF approximations assume that the joint distribution over neighboring time steps, given the \(i'\)th history, is Gaussian:

\(p(\mathbf{z}_t, \mathbf{y}_t | \mathbf{z}_{1:t-1}^i) \approx \mathcal{N} \left( \begin{pmatrix} \mathbf{z}_t \\ \mathbf{y}_t \end{pmatrix} ; \hat{\boldsymbol{\mu}}^i, \hat{\boldsymbol{\Sigma}}^i \right)\) (13.43)

where

\(\hat{\boldsymbol{\mu}}^i = \begin{pmatrix} \hat{\boldsymbol{\mu}}_z^i \\ \hat{\boldsymbol{\mu}}_y^i \end{pmatrix}, \hat{\boldsymbol{\Sigma}}^i = \begin{pmatrix} \hat{\boldsymbol{\Sigma}}_{zz}^i & \hat{\boldsymbol{\Sigma}}_{zy}^i \\ \hat{\boldsymbol{\Sigma}}_{yz}^i & \hat{\boldsymbol{\Sigma}}_{yy}^i \end{pmatrix}\) (13.44)

(See Section 8.5.1 for details.)

The EKF and UKF compute \(\hat{\boldsymbol{\mu}}^i\) and \(\hat{\boldsymbol{\Sigma}}^i\) differently. In the EKF, we linearize \(\mathbf{f}\) and \(\mathbf{h}\), and assume the noise terms are Gaussian. We then compute \(p(\mathbf{z}_t, \mathbf{y}_t | \mathbf{z}_{1:t-1}^i)\) exactly for this linearized model (see Section 8.3.1). In the UKF, we propagate sigma points through \(\mathbf{f}\) and \(\mathbf{h}\), and approximate the resulting means and covariances using the unscented transform, which can be more accurate (see Section 8.4). Once we have computed \(\hat{\boldsymbol{\mu}}^i\) and \(\hat{\boldsymbol{\Sigma}}^i\), we can use standard rules for Gaussian conditioning to compute the approximate proposal as follows:

\(q(\mathbf{z}_t | \mathbf{z}_{1:t-1}^i, \mathbf{y}_t) \approx \mathcal{N}(\mathbf{z}_t | \boldsymbol{\mu}_t^i, \boldsymbol{\Sigma}_t^i)\) (13.45)
\(\boldsymbol{\mu}_t^i = \hat{\boldsymbol{\mu}}_z^i + \hat{\boldsymbol{\Sigma}}_{zy}^i (\hat{\boldsymbol{\Sigma}}_{yy}^i)^{-1} (\mathbf{y}_t - \hat{\boldsymbol{\mu}}_y^i)\) (13.46)
\(\boldsymbol{\Sigma}_t^i = \hat{\boldsymbol{\Sigma}}_{zz}^i - \hat{\boldsymbol{\Sigma}}_{zy}^i (\hat{\boldsymbol{\Sigma}}_{yy}^i)^{-1} \hat{\boldsymbol{\Sigma}}_{yz}^i\) (13.47)

Note that the linearization (or sigma point) approximation needs to be performed for each particle sepatately.

# 13.3.3 Proposals based on the Laplace approximation

To handle non-Gaussian likelihoods in an SSM, we can use the Laplace approximation (Section 7.4.3), as suggested in [DGA00]. In particular, consider an SSM with linear-Gaussian latent dynamics and a GLM likelihood. At each step, we compute the maximum \(\mathbf{z}_t^* = \text{argmax} \log p(\mathbf{y}_t | \mathbf{z}_t)\) as step \(t\) (e.g., using Newton-Raphson), and then approximate the likelihood using

\(p(\mathbf{y}_t | \mathbf{z}_t) \approx \mathcal{N}(\mathbf{z}_t | \mathbf{z}_t^*, -\mathbf{H}_t^*)\) (13.48)

where \(\mathbf{H}_t^*\) is the Hessian of the log-likelihood at the mode. We now compute \(p(\mathbf{z}_t | \mathbf{z}_{t-1}^i, \mathbf{y}_t)\) using the update step of the Kalman filter, using the same equations as in Section 13.3.2. This combination is called the Laplace Gaussian filter [Koy+10]. We give an example in Section 13.3.3.1.