Gradients obtained by back-propagation may then be used with any general-purpose gradient-based techniques to train an RNN.

To gain some intuition for how the BPTT algorithm behaves, we provide an example of how to compute gradients by BPTT for the RNN equations above (equation 10.8 and equation 10.12). The nodes of our computational graph include the parameters **U**, **V**, **W**, **b** and **c** as well as the sequence of nodes indexed by t for **x**^(t), **h**^(t), **o**^(t) and L^(t). For each node **N** we need to compute the gradient ∇_**N** L recursively, based on the gradient computed at nodes that follow it in the graph. We start the recursion with the nodes immediately preceding the final loss:

$$\frac{\partial L}{\partial L^{(t)}} = 1.\tag{10.17}$$

In this derivation we assume that the outputs **o**^(t) are used as the argument to the softmax function to obtain the vector **ŷ** of probabilities over the output. We also assume that the loss is the negative log-likelihood of the true target y^(t) given the input so far. The gradient ∇_**o**(t) L on the outputs at time step t, for all i, t, is as follows:

$$(\nabla_{\boldsymbol{o}^{(t)}}L)_i = \frac{\partial L}{\partial o_i^{(t)}} = \frac{\partial L}{\partial L^{(t)}} \frac{\partial L^{(t)}}{\partial o_i^{(t)}} = \hat{y}_i^{(t)} - \mathbf{1}_{i=y^{(t)}}.\tag{10.18}$$

We work our way backward, starting from the end of the sequence. At the final time step τ, **h**^(τ) only has **o**^(τ) as a descendent, so its gradient is simple:

$$\nabla_{\boldsymbol{h}^{(\tau)}}L = \boldsymbol{V}^\top \nabla_{\boldsymbol{o}^{(\tau)}}L.\tag{10.19}$$

We can then iterate backward in time to back-propagate gradients through time, from t = τ − 1 down to t = 1, noting that **h**^(t) (for t < τ) has as descendents both **o**^(t) and **h**^(t+1). Its gradient is thus given by

$$\nabla_{\boldsymbol{h}^{(t)}}L = \left(\frac{\partial \boldsymbol{h}^{(t+1)}}{\partial \boldsymbol{h}^{(t)}}\right)^\top (\nabla_{\boldsymbol{h}^{(t+1)}}L) + \left(\frac{\partial \boldsymbol{o}^{(t)}}{\partial \boldsymbol{h}^{(t)}}\right)^\top (\nabla_{\boldsymbol{o}^{(t)}}L)\tag{10.20}$$

$$= \boldsymbol{W}^\top \text{diag}\left(1 - \left(\boldsymbol{h}^{(t+1)}\right)^2\right) (\nabla_{\boldsymbol{h}^{(t+1)}}L) + \boldsymbol{V}^\top (\nabla_{\boldsymbol{o}^{(t)}}L),\tag{10.21}$$

where diag\(1 - (\boldsymbol{h}^{(t+1)})^2\) indicates the diagonal matrix containing the elements 1 - (h_i^{(t+1)})^2. This is the Jacobian of the hyperbolic tangent associated with the hidden unit i at time t + 1.

Once the gradients on the internal nodes of the computational graph are obtained, we can obtain the gradients on the parameter nodes. Because the