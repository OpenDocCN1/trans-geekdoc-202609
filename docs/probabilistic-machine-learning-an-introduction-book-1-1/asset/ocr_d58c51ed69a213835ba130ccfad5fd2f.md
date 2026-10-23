![](bbox=[0.25, 0.08, 0.82, 0.3])

*Figure 19.21: Diagram of the semi-supervised GAN framework. The discriminator is trained to output the class of labeled datapoints (red), a “fake” label for outputs from the generator (yellow), and any label for unlabeled data (green).*

They consist of a generator network, which maps samples from a simple latent distribution to the data space, and a critic network, which attempts to distinguish between the outputs of the generator and samples from the true data distribution. The generator is trained to generate samples that the critic classifies as “real”.

Since standard GANs do not produce a learned latent representation of a given datapoint and do not learn an explicit model of the data distribution, we cannot use the same approaches as were used for VAEs. Instead, semi-supervised learning with GANs is typically done by modifying the critic so that it outputs either a class label or “fake” instead of simply classifying real vs. fake [Sal+16; Ode16]. For labeled real data, the critic is trained to output the appropriate class label, and for unlabeled real data, it is trained to raise the probability of any of the class labels. As with standard GAN training, the critic is trained to classify outputs from the generator as fake and the generator is trained to fool the critic.

In more detail, let $p_\theta(y|\mathbf{x})$ denote the critic with $C + 1$ outputs corresponding to $C$ classes plus a “fake” class, and let $G(\mathbf{z})$ denote the generator which takes as input samples from the prior distribution $p(\mathbf{z})$. Let us assume that we are using the standard cross-entropy GAN loss as originally proposed in [Goo+14]. Then the critic’s loss is

```
$-\mathbb{E}_{\mathbf{x},y\sim p(\mathbf{x},y)} \log p_\theta(y|\mathbf{x}) - \mathbb{E}_{\mathbf{x}\sim p(\mathbf{x})} \log[1 - p_\theta(y = C + 1|\mathbf{x})] - \mathbb{E}_{\mathbf{z}\sim p(\mathbf{z})} \log p_\theta(y = C + 1|G(\mathbf{z})) \quad (19.56)$
```

This tries to maximize the probability of the correct class for the labeled examples, to minimize the probability of the fake class for real unlabeled examples, and to maximize the probability of the take class for generated examples. The generator’s loss is simpler, namely

```
$\mathbb{E}_{\mathbf{z}\sim p(\mathbf{z})} \log p_\theta(y = C + 1|G(\mathbf{z})) \quad (19.57)$
```

A diagram visualizing the semi-supervised GAN framework is shown in Fig. 19.21.

# 19.6.6.3 Normalizing flows

**Normalizing flows** (described in more detail in the sequel to this book, [Mur22]) are a tractable way to define deep generative models. More precisely, they define an invertible mapping $f_\theta : \mathcal{X} \to \mathcal{Z}$,