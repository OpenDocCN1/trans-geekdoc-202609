```
sudo pip install git+https://www.github.com/keras-team/keras-contrib.git
```

Listing 25.1: Example of installing keras-contrib with pip.

Or, if you are using an Anaconda virtual environment, such as on EC2:

```
git clone https://www.github.com/keras-team/keras-contrib.git
cd keras-contrib
sudo ~/anaconda3/envs/tensorflow_p36/bin/python setup.py install
```

Listing 25.2: Example of installing keras-contrib with Anaconda.

The new InstanceNormalization layer can then be used as follows:

```
...
from keras_contrib.layers.normalization.instancenormalization import InstanceNormalization
# define layer
layer = InstanceNormalization(axis=-1)
...
```

Listing 25.3: Example of using the InstanceNormalization layer.

The axis argument is set to -1 to ensure that features are normalized per feature map. The network weights are initialized to Gaussian random numbers with a standard deviation of 0.02, as is described for DCGANs more generally.

Weights are initialized from a Gaussian distribution N (0, 0.02).

> — Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks, 2017.

The discriminator model is updated using a least squares loss (L2), a so-called Least-Squared Generative Adversarial Network, or LSGAN.

... we replace the negative log likelihood objective by a least-squares loss. This loss is more stable during training and generates higher quality results.

> — Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks, 2017.

This can be implemented using mean squared error between the target values of class = 1 for real images and class = 0 for fake images. Additionally, the paper suggests dividing the loss for the discriminator by half during training, in an effort to slow down updates to the discriminator relative to the generator.

In practice, we divide the objective by 2 while optimizing D, which slows down the rate at which D learns, relative to the rate of G.

> — Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks, 2017.

This can be achieved by setting the loss_weights argument to 0.5 when compiling the model. This weighting does not appear to be implemented in the official Torch implementation when updating discriminator models are defined in the fDx_basic() function1. We can tie all

1https://github.com/junyanz/CycleGAN/blob/master/models/cycle_gan_model.lua#L136