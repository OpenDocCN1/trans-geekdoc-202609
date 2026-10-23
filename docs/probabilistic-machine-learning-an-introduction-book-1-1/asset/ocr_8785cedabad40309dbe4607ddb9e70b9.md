![](bbox=[0.425, 0.111, 0.636, 0.244])

*Figure 20.11: Mixture of factor analysers as a PGM.*

This is called **nonlinear factor analysis**. Unfortunately we can no longer compute the posterior or the MLE exactly, so we need to use approximate methods. In Sec. **20.3.5**, we discuss variational autoencoders, which is the most common way to approximate a nonlinear FA model.

# ## 20.2.6 Mixtures of factor analysers

The factor analysis model (Sec. **20.2**) assumes the observed data can be modeled as arising from a linear mapping from a low-dimensional set of Gaussian factors. One way to relax this assumption is to assume the model is only locally linear, so the overall model becomes a (weighted) combination of FA models; this is called a **mixture of factor analysers**. The overall model for the data is a mixture of linear manifolds, which can be used to approximate an overall curved manifold.

More precisely, let latent indicator \(c_n \in \{1,\ldots,K\}\), specifying which subspace (cluster) we should use to generate the data. If \(c_n=k\), we sample \(z_n\) from a Gaussian prior and pass it through the \(W_k\) matrix and add noise, where \(W_k\) maps from the \(L\)-dimensional subspace to the \(D\)-dimensional visible space. More precisely, the model is as follows:

\[
p(x_n\mid z_n,c_n=k,\theta)=\mathcal{N}(x_n\mid\mu_k+W_kz_n,\Psi_k) \tag{20.67}
\]
\[
p(z_n\mid\theta)=\mathcal{N}(z_n\mid 0,I) \tag{20.68}
\]
\[
p(c_n\mid\theta)=\operatorname{Cat}(c_n\mid\pi) \tag{20.69}
\]

This is called a **mixture of factor analysers (MFA)** [GH96]. The corresponding distribution in the visible space is given by

\[
p(x\mid\theta)=\sum_k p(c=k)\int dz\,p(z\mid c)p(x\mid z,c)=\sum_k\pi_k\int dz\;\mathcal{N}(z\mid\mu_k,I)\mathcal{N}(x\mid W_kz,\sigma^2I) \tag{20.70}
\]

In the special case that \(\Psi_k=\sigma^2I\), we get a mixture of PPCA models (although it is difficult to ensure orthogonality of the \(W_k\) in this case). See Fig. **20.12** for an example of the method applied to some 2d data.

We can think of this as a low-rank version of a mixture of Gaussians. In particular, this model needs \(O(KLD)\) parameters instead of the \(O(KD^2)\) parameters needed for a mixture of full covariance Gaussians. This can reduce overfitting.

4. If we allow \(z_n\) to depend on \(c_n\), we can let each subspace have a different dimensionality, as suggested in [KS15].