calculated dynamically as the exponential moving average of || J_w^T y ||_2 as the training progresses.

The authors find that this additional term makes exploring the latent space more reliable and consistent. Moreover, the regularization terms in the loss function are only applied once every 16 minibatches, for efficiency. This technique, called lazy regularization, does not cause a measurable drop in performance.

# No Progressive Growing

Another major update is in how StyleGAN2 is trained. Rather than adopting the usual progressive training mechanism, StyleGAN2 utilizes skip connections in the generator and residual connections in the discriminator to train the entire network as one. It no longer requires different resolutions to be trained independently and blended as part of the training process.

Figure 10-12 shows the generator and discriminator blocks in StyleGAN2.

![](bbox=[0.13, 0.4, 0.9, 0.78])

Figure 10-12. The generator and discriminator blocks in StyleGAN2