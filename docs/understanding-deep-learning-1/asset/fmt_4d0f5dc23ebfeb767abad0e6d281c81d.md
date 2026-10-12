
[Figure 18.9](#c018.xhtml#c18-fig-0012a) U-Net as used in diffusion models for images. The network aims to predict the noise that was added to the image. It consists of an encoder which reduces the scale and increases the number of channels and a decoder which increases the scale and reduces the number of channels. The encoder representations are concatenated to their partner in the decoder. Connections between adjacent representations consist of residual blocks, and periodic global self-attention in which every spatial position interacts with every other spatial position. A single network is used for all time steps, by passing a sinusoidal time embedding (figure 12.5) through a shallow neural network and adding the result to the channels at every spatial position at every stage of the U-Net.

A large number of time steps are needed as the conditional probabilities `q(z[t-1]|z[t])` become closer to normal when the hyperparameters `β[t]` are close to zero, matching the form of the decoder distributions `Pr(z[t-1]|z[t], ϕ[t])`. However, this makes sampling slow. We might have to run the U-Net model through `T = 1000` steps to generate good images.

### 18.6.2 Improving generation speed

The loss function (equation 18.39) requires the diffusion kernel to have the form `![c18-fig-5060.jpg](images/c18-fig-5060.jpg)`. The same loss function will be valid for *any* forward process with this relation, and there is a family of such compatible processes. These are all optimized by the same loss function but have different rules for the forward process and different corresponding rules for how to use the estimated noise `g[z[t], ϕ[t]]` to predict `z[t-1]` from `z[t]` in the reverse process ([figure 18.10](#c018.xhtml#c18-fig-0013)).

![Figure 18.10 Different diffusion processes that are compatible with the same model. a) Five sampled trajectories of the reparameterized model superimposed on the ground truth marginal distributions. Top row represents Pr(x) and subsequent rows represent q(xt). b) Histogram of samples generated from reparameterized model plotted alongside ground truth density curve Pr(x). The same trained model is compatible with a family of diffusion models (and corresponding updates in the opposite direction), including the denoising diffusion implicit (DDIM) model, which is deterministic and does not add noise at each step. c) Five trajectories from DDIM model. d) Histogram of samples from DDIM model. The same model is also compatible with accelerated diffusion models that skip inference steps for increased sampling speed. e) Five trajectories from accelerated model. f) Histogram of samples from accelerated model.](images/c18-fig-0010.jpg)

[Figure 18.10](#c018.xhtml#c18-fig-0013a) Different diffusion processes that are compatible with the same model. a) Five sampled trajectories of the reparameterized model superimposed on the ground truth marginal distributions. Top row represents `Pr(x)` and subsequent rows represent `q(x[t])`. b) Histogram of samples generated from reparameterized model plotted alongside ground truth density curve `Pr(x)`. The same trained model is compatible with a family of diffusion models (and corresponding updates in the opposite direction), including the denoising diffusion implicit (DDIM) model, which is deterministic and does not add noise at each step. c) Five trajectories from DDIM model. d) Histogram of samples from DDIM model. The same model is also compatible with accelerated diffusion models that skip inference steps for increased sampling speed. e) Five trajectories from accelerated model. f) Histogram of samples from accelerated model.

Among this family are *denoising diffusion implicit models*, which are no longer stochastic after the first step from `x` to `z[1]`, and *accelerated sampling* models, where the forward process is defined only on a sub-sequence of time steps. This allows a reverse process that skips time steps and hence makes sampling much more efficient; good samples can be created with 50 time steps when the forward process is no longer stochastic. This is much faster than before but still slower than most other generative models.

---

**Notebook 18.4**

Families of diffusion models

---

### 18.6.3 Conditional generation

If the data has associated labels `c`, these can be exploited to control the generation. Sometimes this can improve generation results in GANs, and we might expect this to be the case in diffusion models as well; it's easier to denoise an image if you have some information about what that image contains. One approach to conditional synthesis in diffusion models is *classifier guidance*. This modifies the denoising update from `z[t]` to `z[t-1]` to take into account class information `c`. In practice, this means adding an extra term into the final update step in algorithm 18.2 to yield:

`![c18-fig-5061.jpg](images/c18-fig-5061.jpg)`

 (18.40)

The new term depends on the gradient of a classifier `Pr(c|z[t])` that is based on the latent variable `z[t]`. This maps features from the downsampling half of the U-Net to the class `c`. Like the U-Net, it is usually shared across all time steps and takes time as an input. The update from `z[t]` to `z[t-1]` now makes the class `c` more likely.

*Classifier-free guidance* avoids learning a separate classifier `Pr(c|z[t])` but instead incorporates class information into the main model `g[t][z[t], ϕ[t], c]`. In practice, this usually takes the form of adding an embedding based on `c` to the layers of the U-Net in a similar way to how the time step is added (see [figure 18.9](#c018.xhtml#c18-fig-0012)). This model is jointly trained on conditional and unconditional objectives by randomly dropping the class information during training. Hence, it can both generate unconditional or conditional data examples at test time or any weighted combination of the two. This brings a surprising advantage; if the conditioning information is over-weighted, the model tends to produce very high quality but slightly stereotypical examples. This is somewhat analogous to the use of truncation in GANs (figure 15.10).

---

**Problem 18.12**

---

### 18.6.4 Improving generation quality

As for other generative models, the highest quality results result from applying a combination of tricks and extensions to the basic model. First, it's been noted that it also helps to estimate the variances `![c18-fig-5062.jpg](images/c18-fig-5062.jpg)` of the reverse process as well as the mean (i.e., the widths of the brown normal distributions in [figure 18.7](#c018.xhtml#c18-fig-0007)). This particularly improves the results when sampling with fewer steps. Second, it's possible to modify the noise schedule in the forward process so that `β[t]` varies at each step, and this can also improve results.

Third, to generate high-resolution images, a cascade of diffusion models is used. The first creates a low-resolution image (possibly guided by class information). The subsequent diffusion models generate progressively higher-resolution images. They condition on the lower-resolution image by resizing this and appending it to the layers of the constituent U-Net, as well as any other class information ([figure 18.11](#c018.xhtml#c18-fig-0014)).

![Figure 18.11 Cascaded conditional generation based on a text prompt. a) A diffusion model consisting of a series of U-Nets is used to generate a 64×64 image. b) This generation is conditioned on a sentence embedding computed by a language model. c) A higher resolution 256×256 image is generated and conditioned on the smaller image and the text encoding. d) This is repeated to create a 1024×1024 image. e) Final image sequence. Adapted from Saharia et al. (2022b).](images/c18-fig-0011.jpg)
