# # 21 Variational autoencoders

# ## 21.1 Introduction

In this chapter, we discuss generative models of the form

```
z ~ p_\theta(z)                                                    (21.1)
x|z ~ Expfam(x|d_\theta(z))                                        (21.2)
```

where _p_(_z_) is some kind of prior on the latent code _z_, \(d_\theta(z)\) is a deep neural network, known as the **decoder**, and \(\text{Expfam}(x|\eta)\) is an exponential family distribution, such as a Gaussian or product of Bernoullis. This is called a **deep latent variable model** or **DLVM**. When the prior is Gaussian (as is often the case), this model is called a **deep latent Gaussian model** or **DLGM**.

Posterior inference (i.e., computing \(p_\theta(z|x)\)) is computationally intractable, as is computing the marginal likelihood

```
p_\theta(x) = \int p_\theta(x|z)p_\theta(z) dz                                          (21.3)
```

Hence we need to resort to approximate inference. For most of this chapter, we will use **amortized inference**, which we discussed in Section 10.1.5. This trains another model, \(q_\phi(z|x)\), called the **recognition network** or **inference network**, simultaneously with the generative model to do approximate posterior inference. This combination is called a **variational autoencoder** or **VAE** [KW14; RMW14b; KW19a], since it can be thought of as a probabilistic version of a deterministic autoencoder, discussed in Section 16.3.3.

In this chapter, we introduce\(^\dagger\) the basic VAE, as well as some extensions. Note that the literature on VAE-like methods is vast\(^\dagger\), so we will only discuss a small subset of the ideas that have been explored.

# ## 21.2 VAE basics

In this section, we discuss the basics of variational autoencoders.