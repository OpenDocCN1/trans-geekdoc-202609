+   - **Density estimation:** Given an input $x$, the machine learning system returns an estimate of the true density $p(x)$ under the data-generating distribution. This requires only a single output, but it also requires a complete understanding of the entire input. If even one element of the vector is unusual, the system must assign it a low probability.

+   - **Denoising:** Given a damaged or incorrectly observed input $\tilde{x}$, the machine learning system returns an estimate of the original or correct $x$. For example, the machine learning system might be asked to remove dust or scratches from an old photograph. This requires multiple outputs (every element of the estimated clean example $x$) and an understanding of the entire input (since even one damaged area will still reveal the final estimate as being damaged).

+   - **Missing value imputation:** Given the observations of some elements of $x$, the model is asked to return estimates of or a probability distribution over some or all of the unobserved elements of $x$. This requires multiple outputs. Because the model could be asked to restore any of the elements of $x$, it must understand the entire input.

+   - **Sampling:** The model generates new samples from the distribution $p(x)$. Applications include speech synthesis, that is, producing new waveforms that sound like natural human speech. This requires multiple output values and a good model of the entire input. If the samples have even one element drawn from the wrong distribution, then the sampling process is wrong.

For an example of a sampling task using small natural images, see figure 16.1. Modeling a rich distribution over thousands or millions of random variables is a challenging task, both computationally and statistically. Suppose we wanted to model only binary variables. This is the simplest possible case, and yet already it seems overwhelming. For a small 32 × 32 pixel color (RGB) image, there are $2^{3072}$ possible binary images of this form. This number is over $10^{800}$ times larger than the estimated number of atoms in the universe.

In general, if we wish to model a distribution over a random vector $\mathbf{x}$ containing $n$ discrete variables capable of taking on $k$ values each, then the naive approach of representing $P(\mathbf{x})$ by storing a lookup table with one probability value per possible outcome requires $k^n$ parameters!

This is not feasible for several reasons:

+   - *Memory—the cost of storing the representation:* For all but very small values of $n$ and $k$, representing the distribution as a table will require too many values to store.