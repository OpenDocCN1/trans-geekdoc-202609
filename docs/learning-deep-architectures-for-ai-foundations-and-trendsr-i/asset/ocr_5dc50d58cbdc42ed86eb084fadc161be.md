# # 7
## Variants of RBMs and Auto-Encoders

We review here some of the variations that have been proposed on the basic RBM and auto-encoder models to extend and improve them.
We have already mentioned that it is straightforward to generalize the conditional distributions associated with visible or hidden units in RBMs, e.g., to any member of the exponential family [200]. Gaussian units and exponential or truncated exponential units have been proposed or used in [17, 51, 99, 201]. With respect to the analysis presented here, the equations can be easily adapted by simply changing the domain of the sum (or integral) for the $h_i$ and $x_i$. Diagonal quadratic terms (e.g., to yield Gaussian or truncated Gaussian distributions) can also be added in the energy function without losing the property that the free energy factorizes.

# ### 7.1 Sparse Representations in Auto-Encoders and RBMs

Sparsity has become a concept of great interest recently, not only in machine learning but also in statistics and signal processing, in particular with the work on compressed sensing [30, 47], but it was introduced earlier in computational neuroscience in the context of sparse coding in