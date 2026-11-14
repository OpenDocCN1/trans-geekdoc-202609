
We now derive the induced Gaussian approximation to \(\mathbf{y} = g(\mathbf{x})\). The mean is given by

\(\mathbb{E}[\mathbf{y}] \approx \mathbb{E}[g(\boldsymbol{\mu}) + \mathbf{G}(\boldsymbol{\mu})\boldsymbol{\delta}] = g(\boldsymbol{\mu}) + \mathbf{G}(\boldsymbol{\mu})\mathbb{E}[\boldsymbol{\delta}] = g(\boldsymbol{\mu})\)

The covariance is given by

\(\text{Cov}[\mathbf{y}] = \mathbb{E}[(g(\mathbf{x}) - \mathbb{E}[g(\mathbf{x})])(g(\mathbf{x}) - \mathbb{E}[g(\mathbf{x})])^\mathsf{T}]\)
\(\approx \mathbb{E}[(g(\mathbf{x}) - g(\boldsymbol{\mu}))(g(\mathbf{x}) - g(\boldsymbol{\mu}))^\mathsf{T}]\)
\(\approx \mathbb{E}[(g(\boldsymbol{\mu}) + \mathbf{G}(\boldsymbol{\mu})\boldsymbol{\delta} - g(\boldsymbol{\mu}))(g(\boldsymbol{\mu}) + \mathbf{G}(\boldsymbol{\mu})\boldsymbol{\delta} - g(\boldsymbol{\mu}))^\mathsf{T}]\)
\(= \mathbb{E}[(\mathbf{G}(\boldsymbol{\mu})\boldsymbol{\delta})(\mathbf{G}(\boldsymbol{\mu})\boldsymbol{\delta})^\mathsf{T}]\)
\(= \mathbf{G}(\boldsymbol{\mu})\mathbb{E}[\boldsymbol{\delta}\boldsymbol{\delta}^\mathsf{T}] \mathbf{G}(\boldsymbol{\mu})^\mathsf{T}\)
\(= \mathbf{G}(\boldsymbol{\mu}) \boldsymbol{\Sigma} \mathbf{G}(\boldsymbol{\mu})^\mathsf{T}\)

```
Algorithm 8.3: Linearized approximation to a joint Gaussian distribution.
def LinearizedMoments(\(\boldsymbol{\mu}\), \(\boldsymbol{\Sigma}\), g, \(\Omega\)):
    \(\hat{\mathbf{y}}\) = g(\(\boldsymbol{\mu}\))
    G = Jac(g)(\(\boldsymbol{\mu}\))
    S = G\(\boldsymbol{\Sigma}\)G† + \(\Omega\)
    C = \(\boldsymbol{\Sigma}\)G†
    Return (\(\hat{\mathbf{y}}\), S, C)
```

When deriving the EKF, we need to compute the joint distribution \(p(\mathbf{x}, \mathbf{y})\) where

\(\mathbf{x} \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma}), \quad \mathbf{y} = g(\mathbf{x}) + \mathbf{q}, \quad \mathbf{q} \sim \mathcal{N}(\mathbf{0}, \boldsymbol{\Omega})\)

where \(\mathbf{q}\) is independent of \(\mathbf{x}\). We can compute this by defining the augmented function \(\tilde{g}(\mathbf{x}) = [\mathbf{x}, g(\mathbf{x})]\) and following the procedure above. The resulting linear approximation to the joint is

\(\begin{pmatrix} \mathbf{x} \\ \mathbf{y} \end{pmatrix} \sim \mathcal{N}\left( \begin{pmatrix} \boldsymbol{\mu} \\ \hat{\mathbf{y}} \end{pmatrix}, \begin{pmatrix} \boldsymbol{\Sigma} & \mathbf{C} \\ \mathbf{C}^\mathsf{T} & \mathbf{S} \end{pmatrix} \right) = \mathcal{N}\left( \begin{pmatrix} \boldsymbol{\mu} \\ g(\boldsymbol{\mu}) \end{pmatrix}, \begin{pmatrix} \boldsymbol{\Sigma} & \boldsymbol{\Sigma}\mathbf{G}^\mathsf{T} \\ \mathbf{G}\boldsymbol{\Sigma} & \mathbf{G}\boldsymbol{\Sigma}\mathbf{G}^\mathsf{T} + \boldsymbol{\Omega} \end{pmatrix} \right)\)

where the parameters are computed using Algorithm 8.3. We can then condition this joint Gaussian on the observed value \(\mathbf{y}\) to get the posterior.

It is also possible to derive an approximation for the case of non-additive Gaussian noise, where \(\mathbf{y} = g(\mathbf{x}, \mathbf{q})\). See [SS23, Sec 7.1] for details.

## 8.3.2 The extended Kalman filter (EKF)

We now derive the extended Kalman filter for performing approximate inference in the model given by Equation (8.15). We first linearize the dynamics model around \(\boldsymbol{\mu}_{t-1|t-1}\) to get an approximation to the one-step-ahead predictive distribution \(p(\mathbf{z}_t|\mathbf{y}_{1:t-1}, \mathbf{u}_{1:t}) = \mathcal{N}(\mathbf{z}_t|\boldsymbol{\mu}_{t|t-1}, \boldsymbol{\Sigma}_{t|t-1})\). We then linearize the observation model around \(\boldsymbol{\mu}_{t|t-1}\), and then perform a Gaussian update. (In Section 8.3.2.2, we consider linearizing around a different point that gives better accuracy.)

We can write one step of the EKF algorithm using the notation from Section 8.2.2.5 as follows:

```
(\boldsymbol{\mu}_{t|t-1},\boldsymbol{\Sigma}_{t|t-1},-) = \textbf{LinearizedMoments}(\boldsymbol{\mu}_{t-1|t-1},\boldsymbol{\Sigma}_{t-1|t-1},f(\cdot,\boldsymbol{u}_t),\mathbf{Q}_t) (8.136)
(\hat{\mathbf{y}}_t,\mathbf{S}_t,\mathbf{C}_t) = \textbf{LinearizedMoments}(\boldsymbol{\mu}_{t|t-1},\boldsymbol{\Sigma}_{t|t-1},h(\cdot,\boldsymbol{u}_t),\mathbf{R}_t) (8.137)
(\boldsymbol{\mu}_{t|t},\boldsymbol{\Sigma}_{t|t},\ell_t) = \textbf{GaussCondition}(\boldsymbol{\mu}_{t|t-1},\boldsymbol{\Sigma}_{t|t-1},\hat{\mathbf{y}}_t,\mathbf{S}_t,\mathbf{C}_t,\mathbf{y}_t) (8.138)
```

Spelling out the details more explicitly, we can write the predict step as follows:

```
\boldsymbol{\mu}_{t|t-1} = f(\boldsymbol{\mu}_{t-1},\boldsymbol{u}_t) (8.139)
\boldsymbol{\Sigma}_{t|t-1} = \mathbf{F}_t \boldsymbol{\Sigma}_{t-1} \mathbf{F}_t^\mathsf{T} + \mathbf{Q}_t (8.140)
```

where \(\mathbf{F}_t \equiv \text{Jac}(f(\cdot,\boldsymbol{u}_t))(\boldsymbol{\mu}_{t|t-1})\) is the \(N_z \times N_z\) Jacobian matrix of the dynamics model. The update step is as follows:

```
\hat{\mathbf{y}}_t = h(\boldsymbol{\mu}_{t|t-1},\boldsymbol{u}_t) (8.141)
\mathbf{S}_t = \mathbf{H}_t \boldsymbol{\Sigma}_{t|t-1} \mathbf{H}_t^\mathsf{T} + \mathbf{R}_t (8.142)
\mathbf{K}_t = \boldsymbol{\Sigma}_{t|t-1} \mathbf{H}_t^\mathsf{T} \mathbf{S}_t^{-1} (8.143)
\boldsymbol{\mu}_{t|t} = \boldsymbol{\mu}_{t|t-1} + \mathbf{K}_t(\mathbf{y}_t - \hat{\mathbf{y}}_t) (8.144)
\boldsymbol{\Sigma}_{t|t} = \boldsymbol{\Sigma}_{t|t-1} - \mathbf{K}_t \mathbf{H}_t \boldsymbol{\Sigma}_{t|t-1} = \boldsymbol{\Sigma}_{t|t-1} - \mathbf{K}_t \mathbf{S}_t \mathbf{K}_t^\mathsf{T} (8.145)
```

where \(\mathbf{H}_t \equiv \text{Jac}(h(\cdot,\boldsymbol{u}_t))(\boldsymbol{\mu}_{t|t-1})\) is the \(N_y \times N_z\) Jacobian matrix of the observation model and \(\mathbf{K}_t\) is the \(N_z \times N_y\) Kalman gain matrix. See Supplementary Section 8.2.1 for the details of the derivation.

### 8.3.2.1 Accuracy

The EKF is widely used because it is simple and relatively efficient. However, there are two cases when the EKF works poorly [IX00; VDMW03]. The first is when the prior covariance is large. In this case, the prior distribution is broad, so we end up sending a lot of probability mass through different parts of the function that are far from \(\boldsymbol{\mu}_{t-1|t-1}\), where the function has been linearized. The other setting where the EKF works poorly is when the function is highly nonlinear near the current mean (see Figure 8.5a).

A more accurate approach is to use a second-order Taylor series approximation, known as the second order EKF. The resulting updates can still be computed in closed form (see [SS23, Sec 7.3] for details). We can further improve performance by repeatedly re-linearizing the equations around \(\boldsymbol{\mu}_t\) instead of \(\boldsymbol{\mu}_{t|t-1}\); this is called the iterated EKF (see Section 8.3.2.2). In Section 8.4.2, we will discuss an algorithm called the unscented Kalman filter (UKF) which is even more accurate, and is derivative free (does not require computing Jacobians).

### 8.3.2.2 Iterated EKF

Another way to improve the accuracy of the EKF is by repeatedly re-linearizing the measurement model around the current posterior, \(\boldsymbol{\mu}_{t|t}\), instead of \(\boldsymbol{\mu}_{t|t-1}\); this is called the iterated EKF [BC93]. See Algorithm 8.4 for the pseudocode. (If we set the number of iterations to \(J=1\), we recover the standard EKF.)

### Algorithm 8.4: Iterated extended Kalman filter.

```
def IEKF(f, Q, h, R, y_{1:T}, \mu_{0|0}, \Sigma_{0|0}, J) :
  foreach t = 1 : T do
    Predict step:
    (\mu_{t|t-1}, \Sigma_{t|t-1}, -) = LinearizedMoments(\mu_{t-1|t-1}, \Sigma_{t-1|t-1}, f(\cdot, u_t), Q_t)
    Update step:
    \mu_{t|t} = \mu_{t|t-1}, \Sigma_{t|t} = \Sigma_{t|t-1}
    foreach j = 1 : J do
      (\hat{y}_t, S_t, C_t) = LinearizedMoments(\mu_{t|t}, \Sigma_{t|t}, h(\cdot, u_t), R_t)
      (\mu_{t|t}, \Sigma_{t|t}, \ell_t) = GaussCondition(\mu_{t|t-1}, \Sigma_{t|t-1}, \hat{y}_t, S_t, C_t, y_t)
Return (\mu_{t|t}, \Sigma_{t|t})_{t=1}^T
```

![](img/ca72c1626f4850f058a9edc138c1ac73_403_0.png)

Figure 8.4: Illustration of filtering applied to a 2d nonlinear dynamical system. (a) True underlying state and observed data. (b) Extended Kalman filter estimate. Generated by ekf_spiral.ipynb. (c) Unscented Kalman filter estimate. Generated by ukf_spiral.ipynb.

The IEKF can be interpreted as a Gauss–Newton method for finding MAP estimate of the state at each step [BC93]. Specifically it minimizes the following objective:

\(\mathcal{L}(\mathbf{z}_t) = \frac{1}{2}(\mathbf{y}_t - \mathbf{h}(\mathbf{z}_t))^\top \mathbf{R}_t^{-1}(\mathbf{y}_t - \mathbf{h}(\mathbf{z}_t)) + \frac{1}{2}(\mathbf{z}_t - \boldsymbol{\mu}_{t|t-1})^\top \boldsymbol{\Sigma}_{t|t-1}^{-1}(\mathbf{z}_t - \boldsymbol{\mu}_{t|t-1})\) (8.146)

See [SS23, Sec 7.4] for details.

Unfortunately the Gauss-Newton method can sometimes diverge. Various robust extensions — including Levenberg-Marquardt, line search, and quasi-Newton methods — have been proposed in [SHA15; SS20a]. See [SS23, Sec 7.5] for details.

### 8.3.2.3 Example: Tracking a point spiraling in 2d

In Section 8.2.1.1, we considered an example of state estimation and tracking of an object moving in 2d under a linear dynamics model with a linear observation model. However, motion and observation models are often nonlinear. For example, consider an object that is moving along a curved trajectory,
