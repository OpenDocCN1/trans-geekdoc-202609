
![](img/fe161b7f6e96e35e7e853eece52c6dce_215_0.png)

FIGURE 5.3 A simple illustration of difference between descriptive models and generative models in terms of the desk object. Compared to descriptive models, generative models introduce hidden variables to model the strong dependency within the observed images.

Typical generative models include sparse coding (Roweis and Ghahramani, 1999; Hoyer and Hyvärinen, 2002; Mairal and Zhang, 1993), wavelet image representation (Do and Vetterli, 2003; Lu et al., 1992), principal component analysis (PCA) (Kambhatla and Leen, 1997; Kong et al., 2005), independent component analysis (ICA) (Hyvärinen, 1999; Hyvärinen and Oja, 2000) and the restricted Boltzmann machine (Lee et al., 2001). Such models assume an image can be represented by a series of bases. In this way, the representation dimension can be greatly reduced by projecting the original image space to the hidden space. Therefore, the computation cost becomes less intensive. In the literature, generative models are often inseparable from descriptive models, as the hidden variables are often characterized by a descriptive model. For instance, the sparse coding scheme is a two-layer generative model and assumes that the image bases are independent and identically distributed hidden variables. And the hidden layer in the hidden Markov models for speech and motion modeling is a Markov chain.

Recently, benefiting from large scale datasets and high-end computation devices, deep learning has achieved great success in many artificial intelligence tasks, like visual recognition (Szegedy et al., 2015; He et al., 2016) and object detection (Girshick, 2015; Ren et al., 2015). Similarly, many deep neural networks based generative models have been proposed, including pixel CNN (Van den Oord et al., 2016), variational auto-encoder (VAE) (Doersch, 2016), and generative adversarial networks (Goodfellow et al., 2014). Essentially, in order to generate high-quality images, such deep models must learn to memorize the visual patterns and underlying structures in their weight space. To some extent, better generation quality is equivalent to better pattern learning. In the following parts, we will briefly introduce the fundamentals of classical generative models and deep generative models.

## 5.3 Classical generative models

From the mathematical perspective (Hua, 2020), classic generative models are statistical models which target modeling the joint probability distribution p(X, z|Θ), where X is an observed multivariate variable, z is the aforementioned hidden variable, and Θ are the parameters of the model to optimize. The hidden variable Z could represent different confounders. For example, if Z are the class labels, generative models can also be used for classification tasks. But the modeling objectives of generative models are different from discriminative models, which directly model the conditional distribution p(Z|X, Θ).

As it is the case for any statistical models, learning and inference are two fundamental problems to be addressed in generative models. Learning refers to the process of estimating the parameters of these generative models from the data. When the data is complete where X and Z are both observed as a sample pair, parameter estimation is often formalized as a standard Maximum Likelihood estimation problem. A more common setting in real world applications is to estimate the parameters from incomplete data, where only X is observed and the target variable Z is not observed in the data sample. This is a problem of maximum likelihood with incomplete data. Such a problem is often approached by the seminal Expectation-Maximization (EM) algorithm (Dempster et al., 1977), where an E-step and a M-step are iteratively conducted to maximize the likelihood of the incomplete data. From the perspective of optimization, such an iterative process can be regarded as a surrogate optimization process.

The E-Step, by definition, computes the expectation of the data likelihood over the distribution of the hidden or target variables. This is done by first conducting an inference step, i.e., calculating the posterior probability p(Z|X, Θ_c) given the current parameter setting Θ_c. Then we have

E(Θ|Θ_c) = ∫_Z p(X, Z|Θ) p(Z|X, Θ_c) dZ. (5.1)

Then the M-Step maximizes E(Θ|Θ_c) to obtain updated parameters

Θ_c^{new} = arg max_Θ E(Θ|Θ_c). (5.2)

These two steps iterate until convergence. This iteration represents a surrogate maximization process of L(X|Θ), which is monotonically nondecreasing. Since it is obviously upper bounded, the process is guaranteed to converge. Ghahramani (Ghahramani and Beal, 2001) derived a Bayesian EM algorithm by leveraging probabilistic variational analysis. Indeed, the M-Step does not need to fully solve the maximization problem. Instead it only needs to find a new parameter Θ_c^{new}, which has higher E(Θ_c^{new}|Θ_c) than E(Θ_c|Θ_c). This is also referred to the generalized EM algorithm.

The inference of the posterior probability p(Z|X, Θ_c) would have a closed-form solution under limited cases. For example, when the prior distribution p(Z) and likelihood distribution p(X|Z) are conjugated, then the posterior would take the same form as the prior. Such conjugate priors are common when the distributions are confined to the conjugate-exponential family (Ghahramani and Beal, 2001). However, for more general distributions, it is often intractable to calculate the posterior in closed-form.

When closed-form inference is intractable, one can often resort to numerical solution, such as using Markov chain Monte Carlo (MCMC) methods, e.g., the Gibbs sampling, to produce samples from this distribution and then compute the integral in Eq. (5.1) numerically. Hinton et al. (Hinton, 2002) presented a method, namely contrastive divergence to use one step sampling to replace the full MCMC sampling. It could significantly speed up the learning process with a certain guarantee of convergence.

![](img/fe161b7f6e96e35e7e853eece52c6dce_217_0.png)

FIGURE 5.4 The simple illustration of the typical deep generative model “auto-encoder”, which first encodes the input image into a hidden latent code, then reconstruct the original image from the latent code with the decoder.

## 5.4 Deep generative models

Following a similar methodology, deep generative models also aim to model the distribution of X with the hidden variables Z. But different from the above traditional generative methods which often use a handcrafted model like wavelet and sparse coding, deep neural networks are utilized instead, whose learning capacity is demonstrated to be much more powerful.

### Auto-encoder

We start our discussion with the vanilla auto-encoders (Wang et al., 2016), though strictly speaking, they are not typical generative models, because it facilitates the understanding of other deep generative models. As shown in Fig. 5.4, it usually consists of two parts: an encoder and a decoder part. Both of them are stacked by a series of fully connected or convolutional layers. The encoder continually reduces the dimensionality to a smaller latent representation z (code), and the decoder then reconstructs the input image from the latent representation to the original resolution symmetrically. Need to note that the goal of auto-encoder is not simply to reconstruct the original images with a trivial identity function, but to learn the underlying visual patterns so that we can even generate some new unseen images from the learned latent space. To achieve this goal, a lot of auto-encoder variants have been proposed. The first typical one is the undercomplete auto-encoder (Zhai et al., 2018), which requires the dimension of latent code to be significantly smaller than that of the input. In this way, the latent code should be informative enough to represent the input image, otherwise the reconstruction loss will be very large. The second popular variant is denoising auto-encoder (Vincent et al., 2008), which deliberately adds some noises into the training dataset so that the auto-encoder needs to learn how to denoise. Instead of changing the training dataset, the third variant sparse auto-encoder (Ng et al., 2011) imposes a sparsity constraint on its loss and encourages the number of active units in the code layer to be minimal and learn a sparse representation of the dataset.

### Variational auto-encoder

Though the above auto-encoders can successfully map the training image to an embedding space, there is no explicit probabilistic model associated with the embedding space. Therefore, randomly sampling from this embedding space can not guarantee that we meaningfully sample from the image space when feeding the sampled code to the decoder. To
