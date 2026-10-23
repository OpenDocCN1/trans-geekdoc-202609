# 17.4 Scaling GPs to large datasets

The main disadvantage of GPs (and other kernel methods, such as SVMs, which we discuss in Sec. 17.5) is that inverting the N × N kernel matrix takes O(N³) time, making the method too slow for big datasets. Many different approximate schemes have been proposed to speedup GPs (see e.g., [Liu+18a] for a review). In this section, we briefly mention some of them.

# 17.4.1 (Sparse) variational inference

In this section, we approximate the posterior p(f|y) using variational inference. This approach is known as the variational free energy (VFE) method for GPs [Tit09; Mat+16].

In more detail, the VFE approach tries to find an approximate posterior q(f) to minimize J(q) = 𝔼KL(q(f)||p(f|y)), where q is the variational distribution that we choose, and f = (f*, f_X, f_Z) is a vector of function values at any set of testing points *, the training points X, and a set of M artificially introduced inducing points or pseudo-inputs Z. The function values at these inducing points are denoted by u = f_Z.

The key idea is that we will optimize these inducing points so that (Z, f_Z) acts as a “bottleneck” to store the information from the training set, so that we can then make the approximation

p(f|y) ≈ q(f) = q(f*, f_X, f_Z) = p(f*, f_X | f_Z) q(f_Z) (17.67)

where p(f*, f_X | f_Z) is computed exactly using the GP. We can marginalize out f_X from the conditional prior to get p(f*|f_Z), since it is jointly Gaussian. If we choose q(f_Z) = 𝒩(f_Z | m, S), then we can compute q(f*) = 𝔼_{q(f_Z)} [p(f*|f_Z)] efficiently as well, from which we can compute the predictions q(y*|X*, D). Hence this method is often called a “sparse GP”, because it makes predictions using just a sparse set of points, namely f_Z, instead of the whole training set, f_X. We give the details below.

# 17.4.1.1 Prediction

Suppose we have already computed the variational posterior q(f_Z) = 𝒩(f_Z | m, S). Now consider the induced variational distribution over an arbitrary set of inputs T, which could be training or test points. We have