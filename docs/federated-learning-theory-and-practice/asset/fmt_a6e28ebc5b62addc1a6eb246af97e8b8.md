
## AAE Training

We introduce AAE training as follows. Instead of training the noisy generator as in GAN, AAE leverages an autoencoder-based regression model to minimize a reconstruction loss between input data (`x`) and decoded output (`x'`). The bottleneck vector (latent space `z`) is modeled as a variational autoencoder [34] but uses a discriminator to refine `z` closer to a real vector (`η`) sampled from a fixed Gaussian distribution as shown in Fig. 20.5(a). This discriminative training resulted in a better test-likelihood on synthetic samples [13, 39].

Let `x` and `z` be the input and the bottleneck latent vector of an encoder-decoder model, respectively. The universal approximator posterior `q(z)` introduced [39] is

```
q(z|x) = ∫[η] q(z|x, η) p[η](η) dη
```
(20.8)

```
⇒ q(z) = ∫[x]∫[η] q(z|x, η) p[d](x) p[η](η) dη dx,
```
(20.9)

where the stochasticity in `q(z)` comes from both the data distribution `x` and the random noise `η` with a fixed Gaussian distribution at the input of the encoder. The adversarial training procedure can match `q(z)` to `p(z)` by back-propagation through the encoder network directly. The encoder encodes an input data `x` into latent vector, `z'[i] ~ N(μ[i](x), σ[i](x))`, by variational inference used in [34]. Therefore, a training objective for reconstructing input `x` is computed by minimizing the following upper-bound on the negative log-likelihood of `x`:

```
E[x][E[q(z|x)][-log(p(x|z))]] + E[x][KL(q(z|x) || p(z))].
```
(20.10)

![Figure 20.5 The PATE-AAE [69] vertical training framework does not require sufficient non-sensitive data to train a DP-preserving speech model, where its AAE module has been recognized as a generative modeling process without text labels and speech data.](OEBPS/images/B9780443190377000302/gr005_u8.jpg)

**Figure 20.5** The PATE-AAE [69] vertical training framework does not require sufficient non-sensitive data to train a DP-preserving speech model, where its AAE module has been recognized as a generative modeling process without text labels and speech data.

Makhzani et al. [39] further introduce a discriminative update into the second term of (20.10) that makes `q(z)` match the distribution of `p(z)` to train an AAE. The discriminative training objective between the latent vector `z'` (denoted as a fake sample as 0) and the sampling noise `η` is computed by BCE loss and back-propagated gradients to input data (`x`) for updating encoder's parameters (Fig. 20.5(a)).

### Teacher Model Training

Next, for training teacher models, we partition the sensitive dataset into `n` subsets, `D[1], …, D[I]`, with `|D_i| = |D|/I` for `∀q`. Each teacher model (`T[i]`) is trained with discriminator loss:

```
L_Ti = - ( Σ_{q ∈ D} log T_i(q(z)) + Σ_{j=1}^{I} log(1 - T_i(q(z'_j))) ).
```
(20.11)

### Student Model Training

To generate synthetic samples for training the student model, we take `I` samples of Gaussian distribution, `η[1], …, η[I]`, using the trained AAE decoder network (`G`) to synthesize sample `û_j = G(η_j)` for each class. Following the PATE mechanism for knowledge transfer, the aggregated noisy output from the teacher models in (20.11) labels the synthetic data for training a differentially private student model, where noisy label refers `r_j = PATE(û_j, λ)` from (20.7). Finally, we train the student model to maximize the standard cross-entropy loss on this teacher-labeled data:

```
L_S = Σ_{j=1}^{I} r_j log S(û_j) + (1 - r_j) log(1 - S(û_j)).
```
(20.12)
