![](bbox=[0.19, 0.08, 0.83, 0.28])

Figure 2.21: A smooth witness function for comparing two distributions which are (a) different and (b) similar. From a figure from [GSJ19]. Used with kind permission of Arthur Gretton.

The IPM in this case is equal to the **Wasserstein-1 distance**

```
$$W_1(P, Q) \triangleq \sup_{\|f\|_L \le 1} | \mathbb{E}_{p(x)} [f(x)] - \mathbb{E}_{q(x')} [f(x')] |$$
```

See Section 6.8.2.4 for details.

# ## 2.7.3 Maximum mean discrepancy (MMD)

In this section, we describe the **maximum mean discrepancy** or **MMD** method of [Gre+12], which defines a discrepancy measure \(D(P, Q)\) using samples from the two distributions. The samples are compared using positive definite kernels (Section 18.2), which can handle high-dimensional inputs. This approach can be used to define two-sample tests, and to train implicit generative models (Section 26.2.4).

# ### 2.7.3.1 MMD as an IPM

The MMD is an integral probability metric (Section 2.7.2) of the form

```
$$\text{MMD}(P, Q; \mathcal{F}) = \sup_{f \in \mathcal{F}: \|f\| \le 1} [\mathbb{E}_{p(x)} [f(x)] - \mathbb{E}_{q(x')} [f(x')]]$$
```

where \(\mathcal{F}\) is an RKHS (Section 18.3.7.1) defined by a positive definite kernel function \(\mathcal{K}\). We can represent functions in this set as an infinite sum of basis functions

```
$$f(x) = \langle f, \phi(x) \rangle_{\mathcal{F}} = \sum_{l=1}^{\infty} f_l \phi_l(x)$$
```

We restrict the set of witness functions \(f\) to be those that are in the unit ball of this RKHS, so \(\|f\|_{\mathcal{F}}^2 = \sum_{l=1}^{\infty} f_l^2 \le 1\). By the linearity of expectation, we have

```
$$\mathbb{E}_{p(x)} [f(x)] = \langle f, \mathbb{E}_{p(x)} [\phi(x)] \rangle_{\mathcal{F}} = \langle f, \mu_P \rangle_{\mathcal{F}}$$
```