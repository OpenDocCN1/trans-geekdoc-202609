have

\(\begin{pmatrix} z_t - \mu \\ z_{t-1} - \mu \end{pmatrix} = \begin{pmatrix} \rho_1 & \rho_2 \\ 1 & 0 \end{pmatrix} \begin{pmatrix} z_{t-1} - \mu \\ z_{t-2} - \mu \end{pmatrix} + \begin{pmatrix} q_t \\ 0 \end{pmatrix} \tag{29.133}\)

where \(q_t \sim \mathcal{N}(0, \sigma_z^2)\). Thus we have

\(z_t = \mu + \rho_1(z_{t-1} - \mu) + \rho_2(z_{t-2} - \mu) + q_t \tag{29.134}\)

# 29.11.3 Posterior inference

Inferring the states of an NGSSM model is in general computationally difficult. Fortunately, there are a variety of approximate inference schemes that can be used, which we discuss in Chapter 8 and Chapter 13.

# 29.12 Structural time series models

In this section, we discuss **time series forecasting**, which is the problem of computing the predictive distribution over future observations given the data up until the present, i.e., computing \(p(\mathbf{y}_{t+h} | \mathbf{y}_{1:t})\). (The model may optionally be conditioned on known future inputs, to get \(p(\mathbf{y}_{t+h} | \mathbf{y}_{1:t}, \mathbf{u}_{1:t+h})\).) There are many approaches to this problem (see e.g., [HA21]), but in this section, we focus on **structural time series (STS)** models, which are defined in terms of linear-Gaussian SSMs.

Many classical time series methods, such as the **ARMA** (autoregressive moving average) method, can be represented as STS models (see e.g., [Har90; CK07; DK12; PFW21]). However, the STS approach has much more flexibility. For example, we can create nonlinear, non-Gaussian, and even hierarchical extensions, as we discuss below.

# 29.12.1 Introduction

The basic idea of an STS model is to represent the observed scalar time series as a sum of \(C\) individual components:

\(f(t) = f_1(t) + f_2(t) + \cdots + f_C(t) + \epsilon_t \tag{29.135}\)

where \(\epsilon_t \sim \mathcal{N}(0, \sigma^2)\). For example, we might have a seasonal component that causes the observed values to oscillate up and down, and a growth component, that causes the observed values to get larger over time. Each latent process \(f_c(t)\) is modeled by a linear Gaussian state-space model, which (in this context) is also called a **dynamic linear model (DLM)**. Since these are linear, we can combine them altogether into a single LG-SSM. In particular, in the case of scalar observations, the model has the form

\(p(\mathbf{z}_t | \mathbf{z}_{t-1}, \boldsymbol{\theta}) = \mathcal{N}(\mathbf{z}_t | \mathbf{F}\mathbf{z}_{t-1}, \mathbf{Q}) \tag{29.136}\)

\(p(y_t | \mathbf{z}_t, \boldsymbol{\theta}) = \mathcal{N}(y_t | \mathbf{H}\mathbf{z}_t + \boldsymbol{\beta}^\top \mathbf{u}_t, \sigma_y^2) \tag{29.137}\)

where \(\mathbf{F}\) and \(\mathbf{Q}\) are block structured matrices, with one block per component. The vector \(\mathbf{H}\) then adds up all the relevant pieces from each component to generate the overall mean. Note that the