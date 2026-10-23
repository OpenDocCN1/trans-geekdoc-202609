by training with the squared error criterion

$$\|g(f(\tilde{x}))-x\|^2 \tag{14.16}$$

and corruption

$$C(\tilde{x}=\tilde{x}\mid x)=\mathcal{N}(\tilde{x};\mu=x,\Sigma=\sigma^2I) \tag{14.17}$$

with noise variance $\sigma^2$. See figure **14.5** for an illustration of how this works.

In general, there is no guarantee that the reconstruction $g(f(x))$ minus the input $x$ corresponds to the gradient of any function, let alone to the score. That is why the early results (Vincent, 2011) are specialized to particular parametrizations, where $g(f(x))-x$ may be obtained by taking the derivative of another function. Kamyshanska and Memisevic (2015) generalized the results of Vincent (2011) by identifying a family of shallow autoencoders such that $g(f(x))-x$ corresponds to a score for all members of the family.

So far we have described only how the denoising autoencoder learns to represent a probability distribution. More generally, one may want to use the autoencoder as a generative model and draw samples from this distribution. This is described in section **20.11**.

# 14.5.1.1 Historical Perspective

The idea of using MLPs for denoising dates back to the work of LeCun (1987) and Gallinari et al. (1987). Behnke (2001) also used recurrent networks to denoise images. Denoising autoencoders are, in some sense, just MLPs trained to denoise. The name “denoising autoencoder,” however, refers to a model that is intended not merely to learn to denoise its input but to learn a good internal representation as a side effect of learning to denoise. This idea came much later (Vincent et al., 2008, 2010). The learned representation may then be used to pretrain a deeper unsupervised network or a supervised network. Like sparse autoencoders, sparse coding, contractive autoencoders, and other regularized autoencoders, the motivation for DAEs was to allow the learning of a very high-capacity encoder while preventing the encoder and decoder from learning a useless identity function.

Prior to the introduction of the modern DAE, Inayoshi and Kurita (2005) explored some of the same goals with some of the same methods. Their approach minimizes reconstruction error in addition to a supervised objective while injecting noise in the hidden layer of a supervised MLP, with the objective to improve generalization by introducing the reconstruction error and the injected noise. Their method was based on a linear encoder, however, and could not learn function families as powerful as the modern DAE can.