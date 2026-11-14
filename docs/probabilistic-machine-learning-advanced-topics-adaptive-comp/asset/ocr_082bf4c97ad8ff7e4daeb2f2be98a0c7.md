model to get the one-step-ahead state predictions, \(\mathbf{z}_{t|t-1}^s = \mathbf{f}(\mathbf{z}_{t-1|t-1}^s, \mathbf{q}_t^s)\), from which we get \(\mathbf{Z}_{t|t-1} = \{\mathbf{z}_{t|t-1}^s\}\), which has size \(N_z \times N_s\). Next we draw \(N_s\) observation noise variables \(\mathbf{r}_t^s \sim \mathcal{N}(\mathbf{0}, \mathbf{R}_t)\), and use them to compute the one-step-ahead observation predictions, \(\mathbf{y}_{t|t-1}^s = \mathbf{h}(\mathbf{z}_{t|t-1}^s, \mathbf{r}_t^s)\) and \(\mathbf{Y}_{t|t-1} = \{\mathbf{y}_{t|t-1}^s\}\), which has size \(N_y \times N_s\). Finally we compute the measurement update using

```
\(\mathbf{Z}_{t|t} = \mathbf{Z}_{t|t-1} + \tilde{\mathbf{K}}_t (\mathbf{y}_t \mathbf{1}^\mathsf{T} - \bar{\mathbf{Y}}_{t|t-1})\) (8.191)
```

which is the analog of Equation (8.29).

We now discuss how to compute \(\bar{\mathbf{K}}_t\), which is the analog of the Kalman gain matrix in Equation (8.28). First note that we can write the exact Kalman gain matrix (in the linear-Gaussian case) as \(\mathbf{K}_t = \unknown_{t|t-1} \mathbf{H}^\mathsf{T} \mathbf{S}_t^{-1} = \mathbf{C}_t \mathbf{S}_t^{-1}\), where \(\mathbf{S}_t\) is the covariance of the measurements, and \(\mathbf{C}_t\) is the crosscovariance between the state and output predictions. In the EnKF, we approximate \(\mathbf{S}_t\) and \(\mathbf{C}_t\) empirically as follows. First we compute the anomalies

```
\(\tilde{\mathbf{Z}}_{t|t-1} = \mathbf{Z}_{t|t-1} - \bar{\mathbf{z}}_{t|t-1} \mathbf{1}^\mathsf{T}, \quad \bar{\mathbf{Y}}_{t|t-1} = \mathbf{Y}_{t|t-1} - \bar{\mathbf{y}}_{t|t-1} \mathbf{1}^\mathsf{T}\) (8.192)
```

Then we compute the sample covariance matrices

```
\(\tilde{\mathbf{C}}_t = \frac{1}{N_s - 1} \tilde{\mathbf{Z}}_{t|t-1} \tilde{\mathbf{Y}}_{t|t-1}^\mathsf{T}, \quad \tilde{\mathbf{S}}_t = \frac{1}{N_s - 1} \tilde{\mathbf{Y}}_{t|t-1} \tilde{\mathbf{Y}}_{t|t-1}^\mathsf{T}\) (8.193)
```

Finally we compute

```
\(\bar{\mathbf{K}}_t = \tilde{\mathbf{C}}_t \tilde{\mathbf{S}}_t^{-1}\) (8.194)
```

which has the same form as a multivariate least squares problem. For models with additive noise, we can reduce the variance of this procedure by eliminating the sampling of the predicted observations. Thus we replace \(\bar{\mathbf{Y}}_{t|t-1}\) with its deterministic version, \(\bar{\mathbf{Y}}_{t|t-1} = \mathbf{H} \mathbf{Z}_{t|t-1}\) (assuming a linear observation model for notational simplicity. We then use \(\tilde{\mathbf{C}}_t = \frac{1}{N_s - 1} \tilde{\mathbf{Z}}_{t|t-1} \tilde{\mathbf{O}}_{t|t-1}^\mathsf{T}\), and \(\tilde{\mathbf{S}}_t = \frac{1}{N_s - 1} \tilde{\mathbf{O}}_{t|t-1} \tilde{\mathbf{O}}_{t|t-1}^\mathsf{T} + \mathbf{R}_t\). (It is also possible to eliminate the sampling for the latent states, by using the **ensemble square root filter** [Tip+03], although this may be less robust.)

We now compare the computational complexity to the KF algorithm. Recall that \(N_z\) is the number of latent dimensions, \(N_y\) is the number of observed dimensions, and \(N_s\) is the number of samples. We will assume \(N_z > N_s > N_y\), as occurs in most geospatial problems. The EnKF time update takes \(O(N_z^2 N_s)\) time to propagate the samples though the model (assuming a linear model, for simplicity), whereas the KF takes \(O(N_z^3)\) time to compute \(\mathbf{F}_t \unknown_{t-1} \mathbf{F}_t + \mathbf{Q}_t\). The EnKF measurement update takes \(O(N_z N_y N_s)\) time to compute \(\tilde{\mathbf{C}}_t\), \(O(N_y^2 N_s)\) time to compute \(\tilde{\mathbf{S}}_t\), \(O(N_y^3)\) time to compute \(\tilde{\mathbf{S}}_t^{-1}\), \(O(N_z N_y^2)\) to compute \(\bar{\mathbf{K}}_t\), and \(O(N_z N_y N_s)\) time to compute \(\mathbf{Z}_{t|t}\). By contrast, in the KF, the measurement update takes \(O(N_z^2 N_y)\) to compute \(\mathbf{C}_t\), \(O(N_z^2 N_y)\) to compute \(\mathbf{S}_t\), \(O(N_y^3)\) to compute \(\mathbf{S}_t^{-1}\), \(O(N_z N_y^2)\) to compute \(\mathbf{K}_t\), and \(O(N_z N_y)\) to compute \(\boldsymbol{\mu}_{t|t}\). In summary, EnKF is \(O N_z N_s)\), but EKF is \(O(N_z^2)\), if we ignore the dependency on \(N_y\) for simplicity.

Unfortunately, if \(N_s\) is too small, the EnKF can become overconfident, and the filter can diverge. A common heuristic to reduce this is known as **covariance inflation**, in which we replace \(\tilde{\mathbf{Z}}_{t|t-1}\) with \(\bar{\mathbf{Z}}_{t|t-1} = \frac{1}{c} (\mathbf{Z}_{t|t-1} - \tilde{\mathbf{z}}_{t|t-1} \mathbf{1}^\mathsf{T})\) for some fudge factor \(c < 1\).

Unlike the particle filter, the EnKF is not guaranteed to converge to the correct posterior. However, hybrid PF/EnKF approaches have been developed (see e.g., [LGMT11; FK13b; Rei13]) with better theoretical foundations.