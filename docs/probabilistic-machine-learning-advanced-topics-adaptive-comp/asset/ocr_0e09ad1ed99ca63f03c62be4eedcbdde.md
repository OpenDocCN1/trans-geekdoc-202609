which has the closed form update

```
$$\boldsymbol{e}_i = \frac{1}{n_i} \sum_{j=1}^{n_i} \boldsymbol{z}_{i,j} \tag{21.80}$$
```

This is like the M step of the EM algorithm when fitting the mean vectors of a GMM. In the minibatch setting, we replace the above operations with an exponentially moving average, as follows:

```
$$N_i^t = \gamma N_i^{t-1} + (1 - \gamma)n_i^t \tag{21.81}$$ 
$$\boldsymbol{m}_i^t = \gamma \boldsymbol{m}_i^{t-1} + (1 - \gamma) \sum_j \boldsymbol{z}_{i,j}^t \tag{21.82}$$ 
$$\boldsymbol{e}_i^t = \frac{\boldsymbol{m}_i^t}{N_i^t} \tag{21.83}$$
```

The authors found $\gamma = 0.9$ to work well.

The above procedure will learn to update the codebook vectors so it matches the output of the encoder. However, it is also important to ensure the encoder does not "change its mind" too often about what codebook value to use. To prevent this, the authors propose to add a third term to the loss, known as the **commitment loss**, that encourages the encoder output to be close to the codebook values. Thus we get the final loss:

```
$$\mathcal{L} = -\log p(\boldsymbol{x}|\boldsymbol{z}_q(\boldsymbol{x})) + ||\text{sg}(\boldsymbol{z}_e(\boldsymbol{x})) - \boldsymbol{e}||_2^2 + \beta ||\boldsymbol{z}_e(\boldsymbol{x}) - \text{sg}(\boldsymbol{e})||_2^2 \tag{21.84}$$
```

The authors found $\beta = 0.25$ to work well, although of course the value depends on the scale of the reconstruction loss (NLL) term. (A probabilistic interpretation of this loss can be found in [Hen+18].) Overall, the decoder optimizes the first term only, the encoder optimizes the first and last term, and the embeddings optimize the middle term.

# ## 21.6.3 Learning the prior

After training the VQ-VAE model, it is possible to learn a better prior, to match the aggregated posterior. To do this, we just apply the encoder to a set of data, \(\{\boldsymbol{x}_n\}\), thus converting them to discrete sequences, \(\{\boldsymbol{z}_n\}\). We can then learn a joint distribution \(p(\boldsymbol{z})\) using any kind of sequence model. In the original VQ-VAE paper [OVK17], they used the causal convolutional PixelCNN model (Section 22.3.2). More recent work has used transformer decoders (Section 22.4). Samples from this prior can then be decoded using the decoder part of the VQ-VAE model. We give some examples of this in the sections below.

# ## 21.6.4 Hierarchical extension (VQ-VAE-2)

In [ROV19], they extend the original VQ-VAE model by using a hierarchical latent code. The model is illustrated in Figure 21.17. They applied this to images of size $256 \times 256 \times 3$. The first latent layer maps this to a quantized representation of size $64 \times 64$, and the second latent layer maps this to a quantized representation of size $32 \times 32$. This hierarchical scheme allows the top level to focus on high level semantics of the image, leaving fine visual details, such as texture, to the lower level. (See Section 21.5 for more discussion of hierarchical VAEs.)