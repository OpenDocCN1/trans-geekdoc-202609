from 10% to 30% when AUROR is used to preprocess the input. And the accuracy drop remains negligible for malicious ratios from 10% to 30%.

# ## 4.4　A NEW CDL ATTACK: GAN ATTACK

Hitaj et al. [12] developed a new attack on an indirect CDL based on generative adversarial networks (GANs). He proved that the privacy-preserving feature of indirect CDL makes the model more susceptible than direct CDL. In Hitaj et al.’s model, the attacker runs a GAN and pretends to be a user; then he or she infers the privacy information from the victim’s device by downloading gradient vectors. The attacker can influence not only the local data but also the learning process of the global model and deceive the victim into releasing more personal information.

# ### 4.4.1　Generative Adversarial Network (GAN)

Unlike the normal deep learning model, the goal of GANs is to generate “new” images that have similar distributions as the target images. As shown in Figure 4.4, the generative network is first initialized with random noise. At each iteration, it is trained to minimize the distance between the generated images and training images, while the discriminator is trained to distinguish generated images from the original dataset. This iteration continues until the discriminator cannot identify the generated images. In other words, the generator is trying to fool the discriminator.

![](bbox=[0.117, 0.669, 0.824, 0.901])