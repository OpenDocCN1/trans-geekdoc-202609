# ### 8.2.3.3 Two-filter smoothing

Note that the backwards pass of the Kalman smoother does not need access to the observations, \( y_{1:T} \), but does need access to the filtered belief states from the forwards pass, \( p(z_t | y_{1:t}) = \mathcal{N}(z_t | \mu_{t|t}, \Sigma_{t|t}) \). There is an alternative version of the algorithm, known as **two-filter smoothing** [FP69; Kit04], in which we compute the forwards pass as usual, and then separately compute backwards messages \( p(y_{t+1:T} | z_t) \propto \mathcal{N}(z_t | \mu_{t|t}^b, \Sigma_{t|t}^b) \), similar to the backwards filtering algorithm in HMMs (Section 9.2.3). However, these backwards messages are conditional likelihoods, not posteriors, which can cause numerical problems. For example, consider \( t = T \); in this case, we need to set the initial covariance matrix to be \( \Sigma_T^b = \infty \mathbf{I} \), so that the backwards message has no effect on the filtered posterior (since there is no evidence beyond step \( T \)). This problem can be resolved by working in information form. An alternative approach is to generalize the two-filter smoothing equations to ensure the likelihoods are normalizable by multiplying them by artificial distributions [BDM10]. In general, the RTS smoother is preferred to the two-filter smoother, since it is more numerically stable, and it is easier to generalize it to the nonlinear case.

# ### 8.2.3.4 Time and space complexity

In general, the Kalman smoothing algorithm takes \( O(N_y^3 + N_z^2 + N_y N_z) \) per step, where there are \( T \) steps. This can be slow when applied to long sequences. In [SGF21], they describe how to reduce this to \( O(\log T) \) steps using a **parallel prefix scan** operator that can be run efficiently on GPUs. In addition, we can reduce the space from \( O(T) \), to \( O(\log T) \) using the same algorithm as in Section 9.2.5.

# ### 8.2.3.5 Forwards filtering backwards sampling

To draw posterior samples from the LG-SSM, we can leverage the following result:

```
\( p(z_t | z_{t+1}, y_{1:T}) = \mathcal{N}(z_t | \tilde{\mu}_t, \tilde{\Sigma}_t) \) \\
\( \tilde{\mu}_t = \mu_{t|t} + \mathbf{J}_t (z_{t+1} - \mathbf{F}_t \mu_{t|t}) \) \\
\( \tilde{\Sigma}_t = \Sigma_{t|t} - \mathbf{J}_t \Sigma_{t+1|t} \mathbf{J}_t^\mathsf{T} = \Sigma_{t|t} - \Sigma_{t|t} \mathbf{F}_t^\mathsf{T} \Sigma_{t+1|t}^{-1} \Sigma_{t+1|t} \mathbf{J}_t^\mathsf{T} \) \\
\( = \Sigma_{t|t} (\mathbf{I} - \mathbf{F}_t^\mathsf{T} \mathbf{J}_t^\mathsf{T}) \)
```

where \( \mathbf{J}_t \) is the backwards Kalman gain defined in Equation (8.67).

# ### 8.2.4 Information form filtering and smoothing

_This section is written by Giles Harper-Donnelly._

In this section, we derive the Kalman filter and smoother algorithms in information form. We will see that this is the "dual" of Kalman filtering/smoothing in moment form. In particular, while computing marginals in moment form is easy, computing conditionals is hard (requires a matrix inverse). Conversely, for information form, computing marginals is hard, but computing conditionals is easy.