# Merged Batch Normalization

As described in Section 2.1.3, batch normalization is used to accelerate the training and to make the gradient propagation in the network more stable. Therefore, the network activations are normalized to zero mean and unit variance and transformed through the learned parameters γ_i and β_i as defined in eq. (2.8) and eq. (2.9), respectively, which can be rewritten as:

$$\tilde{\mathbf{h}}_i^{BN} = \gamma_i \frac{(\mathbf{W}_i \mathbf{h}_{i-1} + \mathbf{b}_i) - \mu_B \mathbf{e}}{\sqrt{\sigma_B^2 + \epsilon}} + \beta_i \mathbf{e.}$$ (7.1)

As μ, σ², γ_i and β_i are constant during inference, they can be merged into the weights and biases of the previous convolutional layer as proposed in [Fu17]. Note that μ and σ² are the average of the mean and variance values computed for each batch during training. The new convolutional layer can then be written as eq. (7.4), where Ŵ_i and b̂_i are the rescaled weights and biases of layer i given in eq. (7.2) and eq. (7.3), respectively.

$$\hat{\mathbf{W}}_i = \gamma_i\left(\frac{\mathbf{W}_i}{\sqrt{\sigma^2 + \epsilon}}\right)$$ (7.2)

$$\hat{\mathbf{b}}_i = \gamma_i\left(\frac{\mathbf{b}_i - \mu \mathbf{e}}{\sqrt{\sigma^2 + \epsilon}}\right) + \beta_i \mathbf{e}$$ (7.3)

$$\tilde{\mathbf{h}}_i^{BN} = \hat{\mathbf{W}}_i \mathbf{h}_{i-1} + \hat{\mathbf{b}}_i$$ (7.4)

Merging batch normalization related variables into the weights and biases of the previous convolutional layers leads to improved inference time, as the additional computational costs of the batch normalization layers are removed.

# Computation-Efficient Classification Heads

As described in Section 7.1.1, (c + 4)k convolutional filters with kernel size 3 × 3 are applied at each feature map location to predict c confidence scores