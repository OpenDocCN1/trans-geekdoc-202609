# CellPress

# Neuron
NeuroScience

(2) providing a mapping between stimuli (internal or external) and latent variables. For instance, a probabilistic model adaptable to various data types can capture neural response logic and temporal sparsity, through neural impulses. This interpretability relies on domain knowledge, which structure data or hypotheses. The method should be scalable and practical for analyzing large-scale neuroscience datasets.

Most statistical neural data methods are primarily designed for dimensionality reduction to find a low-rank structure that governs the neural data, which makes them suitable for deconvolution. Examples include principal-component analysis (PCA)$^{25-27}$, non-negative matrix factorization (NMF)$^{28-30}$, sparse component analysis (SCA)$^{31}$, v-MIF$^{32}$, and ICA deconvolution methods which recover low-rank structures with the data methods.

generalized linear model (GLM)$^{36}$ and point processes for neural sequences-$^{37}$ point out data with low-rank structures and offer interpretability by separating data activity from noise. However, none of these methods fully meet all of the discussed requirements, such as scalability or adherence to the statistics of the signal.

The limitations of methods and the scalability of deep learning have motivated the exploration of approaches for neural data. Prior work has many desiderata—extracting high-dimensional latent spaces from neural data using non-deep architectures$^{38}$. However, these methods lack a direct link between latent variables and neural counts, making deconvolution difficult due to the "black-box" nature of such models$^{39-41}$.

Here, we propose a novel framework, deconvolved neural learning (DNL), combining convolutional sparse coding (dictionary, learning), which provides a flexible framework to deconvolve single-trial activity into interpretable, localized components. This is enabled by the use of convolutional sparse coding as our generative model. Our model is designed to be flexible, user-friendly, and adaptable through simple modifications to the neural network's non-linearities and training loss functions, without requiring users to redefine an optimization algorithm for their specific application.

To showcase DNL's versatility, we applied it to five experiments. First, we decoded stable and reward prediction (RPE) events from multiplexed reward signals in dopamine neurons. Second, we deconvolved outcomes from low calcium spikes during associative learning. Third, we performed simulations of decoding and prediction in the thalamus using high signal-to-noise ratio (SNR) conditions. Fourth, we extracted neural responses from the piriform with low SNR conditions without overlapping pulses. Fifth, we characterized axonal dopamine activity in

the striatum during a realistic experiment. Finally, we evaluated DUNL, highlighting its strengths: local interpretability, scalability, and generalization in data-limited scenarios.

# RESULTS

Sparse deconvolution learns uncovers structures in single-trial, single-neuron activity
We aim to decompose single-trial activity into pulse-like responses, to recurring events, by identifying low-rank structures in neural data. Observed neural activity is represented as convolution of sparse codes and a "dictionary" with varying shapes and magnitudes. Our goal is to reconstruct data by learning these kernels through model optimization. We want to account for the sparsity of spikes by modeling the mean activity through a passed function like the nonparametric exponential (e.g., Gaussian, Binomial, or Poisson) (see Table S1) for spiking activity and Gaussian with mean $\mu$.

Neural activity $y_t$ is modeled as the convolution of kernels $h_k$ and sparse codes $x_{ki}$, along with a baseline activity $b_t$ (Figure 1B). Deconvolution identifies local temporal patterns and discovers low-rank structures (but) can only capture long-term features). Kernel learning goes beyond the pre-defined methods by learning them automatically. The learned kernels and sparse codes are interpretable: kernels represent shared characteristics across trials, and sparse codes represent individual responses.

indices indicate time events associated with kernel $k$, with amplitudes $x_{ki}$ representing neural response strength. In functional system identification, this method captures cause-effect relationships: sparse codes represent the timing of the effect, while kernels represent the response strength. However, the kernels in the model are non-parametric and fully learned from data, without adhering to a user-parametric form, and codes are sparse. We learn the kernels and $x_{ki}$ by minimizing the loss $\sum (y - \hat{y})^2$, regularized by desired properties in the kernels and codes. Specifically, we use a sparsity prior to promote a few activations in time, and optionally, a second-order covariance structure to capture dedependencies among kernels (e.g., discouraging simulating)

1152 Number 17, 1151–1168, April 16, 2023

Wei Ting Wei with