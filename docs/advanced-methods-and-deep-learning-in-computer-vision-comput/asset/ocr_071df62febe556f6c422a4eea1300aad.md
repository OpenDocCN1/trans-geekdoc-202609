![](bbox=[0.12, 0.12, 0.92, 0.35])

FIGURE 7.8 GAN framework.

then be written as

min_G max_D [ E_{x ~ p_data} log D(x) + E_{z ~ p_z} log (1 - D(G(z))) ] (7.30)

The term inside the parenthesis is the negative of the binary classification loss for classifying samples as being drawn from the real distribution p_data or the generated distribution G(p_z). While the discriminator D maximizes the objective, the generator minimizes it leading to a 2-player minimax game. The overall objective is to find the saddle point of this 2-player game. At convergence, the generator network synthesizes realistic samples and discriminator are maximally confused between the real and the generated distribution.

Training GANs are extremely challenging due to the min-max nature of the training objective. Several stabilization tricks are used in practice to make the GANs converge to good solutions (Liu et al., 2020). Some of these tricks include use of Wasserstein (Arjovsky et al., 2017) or hinge-loss based objective (Miyato et al., 2018), using spectral normalization in network architecture (Miyato et al., 2018), regularization techniques such as weight decay (Liu et al., 2020), gradient penalty (Gulrajani et al., 2017) and feature matching losses (Liu et al., 2020).

# Conditional image synthesis:

In the previous section, we focused on unconditional image synthesis where the objective was simply to generate images that resemble the input distribution. In conditional image synthesis, we are interested in generating samples conditioned on some variables of interest. One example is class-conditional synthesis where we are required to generate samples belonging to one specific class. When the conditioning variable is itself an image, the task is called image-to-image translation. Here, we are interested in transforming an image belonging to one domain to a different one. In conditional image synthesis, the conditioning variable is used as input in addition to the latent vector.

In domain adaptation, image-to-image translation models are a popular choice of generative models. Since, we are interested in unsupervised domain adaptation, we use unpaired image-to-image translation models in which source and target images do not have any corre-