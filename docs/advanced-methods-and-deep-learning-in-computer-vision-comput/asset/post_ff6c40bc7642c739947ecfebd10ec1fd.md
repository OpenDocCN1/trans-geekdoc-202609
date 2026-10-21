
## Regularization-based approaches

In regularization-based approaches, networks are trained with an additional regularization term along with the cross-entropy loss for the source domain. One common regularization function is entropy minimization (Vu et al., 2019) in which entropy of the target logits is minimized. This enforces target samples to produce high confidence predictions. Other forms of regularization include adversarial dropout regularization (Saito et al., 2017b) and maximum classifier discrepancy (Saito et al., 2018) in which feature network is trained to minimize the discrepancy in logits arising from different classifier models that are trained in combination.

## Extension to multisource adaptation

In multisource adaptation, the objective is to adapt from multiple source distributions to the target distribution. Multisource adaptation is a very useful setting in practice as real-world datasets typically contain a mixture of multiple latent domains. The domain adversarial training objective can be extended to the multisource setting using a k-way domain classifier as done in Xu et al. (2018). In Yang et al. (2020), a curriculum-based weighting mechanism is used for selecting the best source domain samples to adapt for the given target domain. In cases where domain labels are available, latent domain discovery can be used for mining the unknown domain labels for multiway adversarial adaptation (Mancini et al., 2018).

## 7.4.2 Generative approaches for domain adaptation

In generative approaches, the objective is to use generative models to estimate source and target distributions. The learnt generative models are then used in the adaptation process to learn domain-invariant representations. Deep neural networks can be a popular choice for learning the generative models due to their high expressive power. Three popular choices of deep generative models are Generative Adversarial Networks (GANs) (Goodfellow et al., 2014), Variational Autoencoders (VAEs) (Kingma and Welling, 2013) and normalizing flows (Papamakarios et al., 2019). GANs have been extensively used for domain adaptation as they have been very successful in generating high fidelity samples.

### Generative adversarial networks

Let {x_i}_{i=1:N} be samples corresponding to the input distribution. The objective of GANs (Goodfellow et al., 2014) is to train a model that enables generating samples that resemble the input distribution. To do this, GANs train a model G that maps samples from latent space to the space of input images. The latent space is typically modeled using a known tractable distribution such as multivariate isotropic Gaussian. Once the model G is trained, we can synthesize samples by sampling from the latent distribution and passing it through the generative model G.

To train the generator G, we utilize a second model called the discriminator (D) or the critic network. The objective of the discriminator is to discriminate if the samples come from real or generated distribution. This is posed as a binary classification problem, with real samples treated as one class while the generated samples are treated as the second class. The generator model G is then trained to make the discriminator fail at this task. Both models G and D are implemented using deep neural networks as shown in Fig. 7.8.

![](img/fe161b7f6e96e35e7e853eece52c6dce_284_0.png)

FIGURE 7.8 GAN framework.

The objective of GANs can then be written as

min_G max_D [ E_{x ~ p_data} log D(x) + E_{z ~ p_z} log (1 - D(G(z))) ] (7.30)

The term inside the parentheses is the negative of the binary classification loss for classifying samples as being drawn from the real distribution p_data or the generated distribution G(p_z). While the discriminator D maximizes the objective, the generator minimizes it, leading to a 2-player minimax game. The overall objective is to find the saddle point of this 2-player game. At convergence, the generator network synthesizes realistic samples and the discriminator is maximally confused between the real and the generated distribution.

Training GANs is extremely challenging due to the min-max nature of the training objective. Several stabilization tricks are used in practice to make the GANs converge to good solutions (Liu et al., 2020). Some of these tricks include the use of Wasserstein (Arjovsky et al., 2017) or hinge-loss based objective (Miyato et al., 2018), using spectral normalization in network architecture (Miyato et al., 2018), regularization techniques such as weight decay (Liu et al., 2020), gradient penalty (Gulrajani et al., 2017) and feature matching losses (Liu et al., 2020).

### Conditional image synthesis

In the previous section, we focused on unconditional image synthesis where the objective was simply to generate images that resemble the input distribution. In conditional image synthesis, we are interested in generating samples conditioned on some variables of interest. One example is class-conditional synthesis where we are required to generate samples belonging to one specific class. When the conditioning variable is itself an image, the task is called image-to-image translation. Here, we are interested in transforming an image belonging to one domain to a different one. In conditional image synthesis, the conditioning variable is used as input in addition to the latent vector.

In domain adaptation, image-to-image translation models are a popular choice of generative models. Since we are interested in unsupervised domain adaptation, we use unpaired image-to-image translation models in which source and target images do not have any correspondences. The idea is to translate source domain images to look like target, and then train a classifier on the translated source domain samples using source labels as ground truth. The trained classifier can then be used for making test-time predictions on the target domain.

**CycleGAN:** CycleGAN is a popular model for unpaired image-to-image translation. Let X and Y denote two domains between which we need to train the image translation models. In CycleGAN, we use two models – a forward model G which translates images from a domain X to domain Y, and a reverse model F which translates images from domain Y to domain X. A discriminator network D_X is used to obtain adversarial loss to ensure that samples produced by F are indistinguishable from real distribution X. Similarly, a second discriminator D_Y encourages samples produced by G to be indistinguishable from the domain Y. Fig. 7.9 shows an overview of CycleGAN framework.

![](img/fe161b7f6e96e35e7e853eece52c6dce_285_0.png)

FIGURE 7.9 (a) CycleGAN framework, (b) Adversarial and cycle consistency loss for the forward model, (c) Adversarial and cycle-consistency losses for the reverse model.

While the discriminator losses encourage realism in generated samples, there is no term in the objective to enforce content preservation. That is, there is no way to prevent a sample from one domain (e.g. Cat) from mapping to a different semantic class in the other domain (e.g. Dog). To prevent this, a cycle-consistent term is used in the objective. The idea is to ensure that applying both forward and reverse maps to the same sample produces back the input, i.e., F(G(x)) ≈ x and G(F(y)) ≈ y. L1 loss is typically used for cycle consistency.

L_cyc(G, F) = E_{x~p_data(x)}[|| F(G(x)) - x ||] + E_{y~p_data(y)}[|| G(F(y)) - y ||] (7.31)

The CycleGAN model is trained using a combination of adversarial losses and cycle-consistency losses.

L = L_adv1 + L_adv2 + λ L_cyc (7.32)

![](img/fe161b7f6e96e35e7e853eece52c6dce_286_0.png)

FIGURE 7.10 CycleGAN results. Input images are shown in the left panel, while the translation of the forward model and back-translation is shown in the middle and right panel respectively.

First, a CycleGAN model is trained to translate between the source and the target domains. Then, a task model (classifier / segmentation model) is trained on the translated source images using source labels as ground truth. For the task model to train well, an additional discriminator loss is used on the feature maps of translated source images and true target images. This ensures that the feature distribution of translated source images and target images is aligned. The training framework of this approach, also known as CyCADA (Hoffman et al., 2018), is shown in Fig. 7.11.

### Distributional distance minimization with generative models

An alternative approach to generative domain adaptation is by utilizing GANs for guiding distributional distance minimization. Recall from Section 7.4.1 that domain adaptation is posed as a distributional distance minimization problem between source and target feature distributions. Instead of directly performing distance minimization in the feature space, the idea is to project the features back into pixel-space using GANs and perform distributional distance minimization in this projected image space (Fig. 7.12). The authors of Sankaranarayanan et al. (2018b) called this approach “Generate to Adapt”.

Projecting features back into image space has two main benefits: First, the capacity of the discriminator network is effectively increased due to the projection step. Second, the projection step helps preserve semantic content in the generated features. That is, it prevents target
