# Generator

# Discriminator

![](bbox=[0.275, 0.095, 0.715, 0.55])

Figure 10-2. The generator and discriminator architectures for the first stage of the ProGAN training process

In the paper, the authors train this pair of networks until the discriminator has seen 800,000 real images. We now need to understand how the generator and discriminator are expanded to work with 8 × 8-pixel images.

To expand the generator and discriminator, we need to blend in additional layers. This is managed in two phases, transition and stabilization, as shown in Figure 10-3.