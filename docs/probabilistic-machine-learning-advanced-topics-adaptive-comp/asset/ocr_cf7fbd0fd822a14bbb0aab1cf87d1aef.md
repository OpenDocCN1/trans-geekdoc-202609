# # 20 Generative models: an overview

# ## 20.1 Introduction

A **generative model** is a joint probability distribution \(p(\boldsymbol{x})\), for \(\boldsymbol{x} \in \mathcal{X}\). In some cases, the model may be conditioned on inputs or covariates \(\boldsymbol{c} \in \mathcal{C}\), which gives rise to a **conditional generative model** of the form \(p(\boldsymbol{x}|\boldsymbol{c})\).

There are many kinds of generative model. We give a brief summary in Section 20.2, and go into more detail in subsequent chapters. See also [Tom22] for a recent book on this topic that goes into more depth.

# ## 20.2 Types of generative model

There are many kinds of generative model, some of which we list in Table 20.1. At a high level, we can distinguish between **deep generative models** (DGM) — which use deep neural network to learn a complex mapping from a single latent vector \(\boldsymbol{z}\) to the observed data \(\boldsymbol{x}\) — and more "classical" **probabilistic graphical models** (PGM), that map a set of interconnected latent variables \(\boldsymbol{z}_1, \dots, \boldsymbol{z}_L\) to the observed variables \(\boldsymbol{x}_1, \dots, \boldsymbol{x}_D\) using simpler, often linear, mappings. Of course, many hybrids are possible. For example, PGMs can use neural networks, and DGMs can use structured state spaces. We discuss PGMs in general terms in Chapter 4, and give examples in Chapter 28, Chapter 29, Chapter 30. In this part of the book, we mostly focus on DGMs.

The main kinds of DGM are: **variational autoencoders (VAE)**, **autoregressive models (ARM)** models, **normalizing flows**, **diffusion models**, **energy based models (EBM)**, and **generative adversarial networks (GAN)**. We can categorize these models in terms of the following criteria (see Figure 20.1 for a visual summary):

+   - Density: does the model support pointwise evaluation of the probability density function \(p(\boldsymbol{x})\), and if so, is this fast or slow, exact, approximate or a bound, etc? For **implicit models**, such as GANs, there is no well-defined density \(p(\boldsymbol{x})\). For other models, we can only compute a lower bound on the density (VAEs), or an approximation to the density (EBMs, UPGMs).

+   - Sampling: does the model support generating new samples, \(\boldsymbol{x} \sim p(\boldsymbol{x})\), and if so, is this fast or slow, exact or approximate? Directed PGMs, VAEs, and GANs all support fast sampling. However, undirected PGMs, EBMs, ARM, diffusion, and flows are slow for sampling.

+   - Training: what kind of method is used for parameter estimation? For some models (such as AR, flows and directed PGMs), we can perform exact maximum likelihood estimation (MLE), although