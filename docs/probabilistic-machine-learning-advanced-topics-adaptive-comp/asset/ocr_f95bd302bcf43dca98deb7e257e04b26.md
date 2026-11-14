updates the posterior from the previous time step into the prior for the current step. 2
The update step is just Bayes' rule:

p(\mathbf{z}_t|\mathbf{y}_{1:t}) = \frac{1}{Z_t} p(\mathbf{y}_t|\mathbf{z}_t) p(\mathbf{z}_t|\mathbf{y}_{1:t-1}) (8.5)

where the normalization constant is

Z_t = \int p(\mathbf{y}_t|\mathbf{z}_t) p(\mathbf{z}_t|\mathbf{y}_{1:t-1}) d\mathbf{z}_t = p(\mathbf{y}_t|\mathbf{y}_{1:t-1}) (8.6)

We can use the normalization constants to compute the log likelihood of the sequence as follows:

\log p(\mathbf{y}_{1:T}) = \sum_{t=1}^T \log p(\mathbf{y}_t|\mathbf{y}_{1:t-1}) = \sum_{t=1}^T \log Z_t (8.7)

where we define p(\mathbf{y}_1|\mathbf{y}_0) = p(\mathbf{y}_1). This quantity is useful for computing the MLE of the parameters.

# 8.1.3 Bayesian smoothing equations

In the offline setting, we want to compute p(\mathbf{z}_t|\mathbf{y}_{1:T}), which is the belief about the hidden state at time t given all the data, both past and future. This is called (fixed interval) smoothing. We first perform the forwards or filtering pass, and then compute the smoothed belief states by working backwards, from right (time t = T) to left (t = 1), as we explain below. Hence this method is also called forwards filtering backwards smoothing or FFBS.

Suppose, by induction, that we have already computed p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T}). We can convert this into a joint smoothed distribution over two consecutive time steps using

p(\mathbf{z}_t, \mathbf{z}_{t+1}|\mathbf{y}_{1:T}) = p(\mathbf{z}_t|\mathbf{z}_{t+1}, \mathbf{y}_{1:T}) p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T}) (8.8)

To derive the first term, note that from the Markov properties of the model, and Bayes' rule, we have

p(\mathbf{z}_t|\mathbf{z}_{t+1}, \mathbf{y}_{1:T}) = p(\mathbf{z}_t|\mathbf{z}_{t+1}, \mathbf{y}_{1:t}, \mathbf{y}_{t+1:T}) (8.9)

= \frac{p(\mathbf{z}_t, \mathbf{z}_{t+1}|\mathbf{y}_{1:t})}{p(\mathbf{z}_{t+1}|\mathbf{y}_{1:t})} (8.10)

= \frac{p(\mathbf{z}_{t+1}|\mathbf{z}_t) p(\mathbf{z}_t|\mathbf{y}_{1:t})}{p(\mathbf{z}_{t+1}|\mathbf{y}_{1:t})} (8.11)

Thus the joint distribution over two consecutive time steps is given by

p(\mathbf{z}_t, \mathbf{z}_{t+1}|\mathbf{y}_{1:T}) = p(\mathbf{z}_t|\mathbf{z}_{t+1}, \mathbf{y}_{1:T}) p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T}) = \frac{p(\mathbf{z}_{t+1}|\mathbf{z}_t) p(\mathbf{z}_t|\mathbf{y}_{1:t}) p(\mathbf{z}_{t+1}|\mathbf{y}_{1:T})}{p(\mathbf{z}_{t+1}|\mathbf{y}_{1:t})} (8.12)

2. The prediction step is not needed at t = 1 if p(\mathbf{z}_1) is provided as input to the model. However, if we just provide p(\mathbf{z}_0), we need to compute p(\mathbf{z}_1|\mathbf{y}_{1:0}) = p(\mathbf{z}_1) by applying the prediction step.