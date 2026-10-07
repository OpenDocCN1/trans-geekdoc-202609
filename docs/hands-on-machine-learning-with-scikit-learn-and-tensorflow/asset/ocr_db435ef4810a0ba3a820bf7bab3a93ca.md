+   $\sigma_g$ is the vector of input standard deviations, also evaluated over the whole mini-batch (it contains one standard deviation per input).

+   $m_g$ is the number of instances in the mini-batch.

+   $	ilde{x}^{(i)}$ is the vector of zero-centered and normalized inputs for instance $i$.

+   $\mathbf{y}$ is the output scale vector for the layer (it contains one scale parameter per input).

+   $\otimes$ represents element-wise multiplication (each input is multiplied by its corresponding output scale parameter).

+   $eta$ is the output shift (offset) parameter vector for the layer. Each input is offset by its corresponding shift parameter.

+   $e$ is a tiny number to avoid division by zero (typically $10^{-5}$). This is called a smoothing term.

+   $z^{(i)}$ is the output of the BN: it is rescaled and shifted version of inputs.

So during training, BN just standardizes its inputs then rescales and offsets them. Good! What about test time? Well it is not simple. Indeed, we need to make predictions for individual instances rather than batches of instances: in this case, we have no way to compute each input's mean and standard deviation. Moreover, even if we have a batch of instances, it may be too small, or computing statistics over the batch might be unreliable (during training, the instances may not be independent and identically distributed (IID), the batches should not be too small, if possible more than 30 instances, and all instances should be IID, as we saw in Chapter 4. One solution is to wait until the end of training, then run the whole training set through the neural network, and compute the mean and standard deviation of each BN layer. These "final" input mean and standard deviations can be used instead of the batch mean and standard deviations when making predictions. However, it is often preferred to estimate these final statistics during training using a moving average of the layer's mean and standard deviations. In each batch-normalized layer: $\mathbf{y}$ (the output scale vector) and $eta$ (the output offset vector) are learned through regularization, $\mu$ (the final input mean vector), and $\sigma$ (the final standard deviation vector) are estimated using an exponential moving average. Note that $\mu$ and $\sigma$ are estimated during training, but they are not used at during training, only after training (to replace the batch mean and standard deviations in Equation 11-3).

The authors demonstrated that this technique considerably improved all the deep neural networks they experimented with, leading to a huge improvement in the ImageNet classification task (ImageNet is a large database of images classified into many classes and commonly used to evaluate computer vision systems). The vanish