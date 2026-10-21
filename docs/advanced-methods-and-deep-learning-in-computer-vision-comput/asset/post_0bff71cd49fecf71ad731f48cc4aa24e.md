
![](img/fe161b7f6e96e35e7e853eece52c6dce_226_0.png)

FIGURE 5.15 The reconstruction result of the encoder and decoder with (right) and without (middle) the reconstruction branch during the training stage. Obviously, involving the reconstruction branch helps guarantee no style information to be absorbed in the encoder and decoder part and almost perfect reconstruction. The figures are by courtesy of Chen et al. (2017b).

![](img/fe161b7f6e96e35e7e853eece52c6dce_226_1.png)

FIGURE 5.16 The disentanglement enables fast incremental learning for new styles. For each case, the left and right are the stylization results of incremental training and fresh training respectively. The figures are by courtesy of Chen et al. (2017b).

![](img/fe161b7f6e96e35e7e853eece52c6dce_226_2.png)

FIGURE 5.17 Stylization results by linear combination of two style filter banks. By adopting different fusing weights, we change the proportion of each style accordingly. The figures are by courtesy of Chen et al. (2017b).

obtain comparable stylization results to those from fresh training, which retrains the whole network with the new styles.

The second advantage is enabling style fusion in two different ways: linear fusion and region-specific fusion. For linear fusion, since different styles are encoded into different filter banks {K_i^1, ..., K_i^m}, we can linearly fuse multiple styles by linearly fusing filter banks in the StyleBank layer. Then the fused filter bank is used to convolve with the content feature F:

F̃ = (∑_{i=1}^m w_i * K_i) ⊗ F   ∑_{i=1}^m w_i = 1,   (5.12)

where m is the number of styles, K_i is the filter bank of style i. F̃ is then fed to the decoder to get the final stylization result. Fig. 5.17 shows such linear fusion results of two different styles with variant fusion weight w_i.

For region-specific style fusion, suppose that the image is decomposed into n disjoint regions in the feature space, and M_i denotes every region mask, then the feature maps can be

![](img/fe161b7f6e96e35e7e853eece52c6dce_227_0.png)

FIGURE 5.18 Region-specific style fusion results with two paintings by applying different filterbanks onto different image regions. The left two paintings are from Picasso and Van Gogh respectively, while the right two are both from Van Gogh. The figures are by courtesy of Chen et al. (2020c).

![](img/fe161b7f6e96e35e7e853eece52c6dce_227_1.png)

FIGURE 5.19 The simple illustration figure to show the general idea of FusedGAN, which fuses an unconditional GAN and a conditional GAN and trains them in a semisupervised way. The figures are by courtesy of Bodla et al. (2018).

described as $F = \sum_{i=1}^{m} (M_i \times F)$ and region-specific style fusion can be formulated as:

$$\tilde{F} = \sum_{i=1}^{m} K_i \otimes (M_i \times F), \qquad (5.13)$$

Fig. 5.18 shows such two region-specific style fusion results. The left case borrows styles from two famous paintings of Picasso and Van Gogh, while the right two styles are both from Van Gogh.

## 5.6.2 Disentangle structure and style

Different from the above style transfer task, where the semantic content structure and style elements are directly specified by the input content and style image, it is more difficult to achieve fine-grained disentanglement in general image synthesis. For example, in the classical text-to-image method StackGAN (Zhang et al., 2017), we can control only over the styles by feeding the text descriptions but cannot achieve the fine-grained controllability upon both structure and styles. Here, the structures mainly denote the semantic shape and posture, and the styles denote the fine-grained visual patterns/textures.

To address the above limitation, Bodla et al. (2018) design a new cascaded generative model FusedGAN to achieve the disentanglement of structure and style in a semisupervised way. The general idea of FusedGAN is shown in Fig. 5.19, which basically combines an unconditional GAN to produce the structure prior and another conditional GAN to match the

![](img/fe161b7f6e96e35e7e853eece52c6dce_228_0.png)

FIGURE 5.20 The disentangled learning framework for FusedGAN, where blue and orange blocks are the unconditional and conditional image generation pipelines respectively. The figures are by courtesy of Bodla et al. (2018).

### Disentanglement by sharing the structure prior

Based on the above motivation, an end-to-end disentangled learning framework is designed in Fig. 5.20, where the blue and orange blocks correspond to the unconditional and conditional image generation branches respectively. In details, the unconditional branch consists of a generator network G1 and a discriminator network Du, which are trained in a similar adversarial way as other GAN models. In order to provide the structure prior for the conditional generation branch, G1 is split into two modules: Gs and Gu. Gs takes a random noise vector z as the input, and generates a structure prior Ms after a series of convolution and upsampling operations. Then the structure prior Ms is fed into Gu to generate the final image after another series of convolution and upsampling operations.

Different from the traditional conditional generation framework, which often takes one condition and one random noise vector as inputs, the conditional generator network Gc in FusedGAN instead takes the structure prior Ms and the condition vector My as inputs. That is to say, the unconditional generation branch and the conditional generation branch share the same structure prior Ms. To encourage the disentanglement of the structure and style, the unconditional and the conditional generation branch adopt different training datasets, i.e., unlabeled dataset for G1 and a dataset labeled with conditional descriptions for Gc. According to different tasks, the condition vector My may have different formats. For example, in the text-to-image task, the original text description is first encoded into an embedding representation y and then fed into the encoder E to generate a new condition tensor My as shown in Fig. 5.20. Note that, in order to generate diverse results, conditional augmentation is performed to sample latent vector ĉ from an independent Gaussian distribution N(μ(y), Σ(y)) around the text embedding, and ĉ is then spatially repeated to match the spatial dimension of Ms to produce My.

This bird has a bright yellow body, with brown on its crown and wings.

This bird is completely red with black wings and pointy beak.

This bird has wings that are brown and has a white body.

A bird with bright yellow belly, and colors of orange on it tail and back.

A small colorful bird that contains bright blue feathers covering most of its body except on its black tail.

![](img/fe161b7f6e96e35e7e853eece52c6dce_229_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_229_1.png)

FIGURE 5.21 Synthesized results of FusedGAN. The left part are the synthesis results of different styles (rows) and structures (columns), and the right part are the style interpolation results of different styles under a fixed structure. The figures are by courtesy of Bodla et al. (2018).

To guide the learning of the unconditional and conditional generation branch, the discriminator Du takes the generated image xuf of Gu or the real image xr as input and discriminate whether it is real or fake, while the discriminator Dc takes the generated image xcf of Gc or the real image xr and the corresponding condition as inputs to ensure that Gc generates images that match the condition. In the training stage, these two pipelines are trained end-to-end in an alternative way. And the model parameters are updated by optimizing the combined GAN and CGAN objectives, i.e.,

```
LG_u = log Du(G_u(z)), LDu = log Du(x), LDc = log Dc(x, y),
LG_c = log Dc(G_c(M_y, M_s), y) + λDKL (N(μ(y), Σ(y)) || N(0, I))
```

where z is the sampled noise vector from a normal distribution N(0, I). To summarize, the key disentanglement design in this work is sharing the structure prior but training the two branches with different objectives.

During inference, to generate a conditional image, a random sample z is first drawn and passed through Gs to generate the structure prior. Ms then takes two paths, one through the generator Gu to produce an unconditional image xuf. In the second path, the input text description is fed into the encoder E and draws a sample from the Gaussian around the text embedding. The output of E and Ms are concatenated together and passed through Gc to generate the conditional image xcf. That is to say, in one inference step, two images are synthesized: xcf the conditional image and xuf the unconditional image, a byproduct of the model which helps to analyze and better understand the proposed model and the results.

### Synthesis results

To verify whether the structure and style are well decoupled, some synthesis results are presented in Fig. 5.21. In the left part, the last row displays the unconditional generation
