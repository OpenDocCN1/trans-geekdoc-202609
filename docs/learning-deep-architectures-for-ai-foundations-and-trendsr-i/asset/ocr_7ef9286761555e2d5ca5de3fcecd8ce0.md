# Variants of RBMs and Auto-Encoders

similar to those observed in area V2 of visual cortex (i.e., the area that follows V1 in the main chain of processing of the visual cortex of primates).

In the compressed sensing literature sparsity is achieved with the $\ell_1$ penalty on the codes, i.e., given bases in matrix $W$ (each column of $W$ is a basis) we typically look for codes $\mathbf{h}$ such that the input signal $\mathbf{x}$ is reconstructed with low $\ell_2$ reconstruction error while $\mathbf{h}$ is sparse:

```
$$\min ||\mathbf{x} - W\mathbf{h}||_2^2 + \lambda ||\mathbf{h}||_1,$
```

where $|\mathbf{h}||_1 = \sum_i |h_i|$. The actual number of non-zero components of $\mathbf{h}$ would be given by the $\ell_0$ norm, but minimizing it is combinatorially difficult, and the $\ell_1$ norm is the $p$-norm that is also convex, making the overall minimization in Equation (7.1) convex. As is well understood [30, 47], the $\ell_1$ norm is a very good proxy for the $\ell_0$ norm and naturally induces sparse results, and it can even be shown to *recover* the true sparse code (if there is one), under mild conditions. Note that the $\ell_1$ penalty corresponds to a Laplace prior, and that the posterior does not have a point at 0, but because of the properties, the *mode* of the posterior (which is recovered when minimizing Equation (7.1)) is often at 0. Although minimizing Equation (7.1) is convex, minimizing jointly the codes and the decoder bases $W$ is not convex, but has been done successfully with many different algorithms [46, 58, 116, 121, 139, 148]:

(7.1)

Like directed graphical models (as the sigmoid belief networks discussed in Section 4.4), sparse coding performs a kind of *explaining away*; it chooses one configuration (among many) of the hidden codes that could explain the input. These different configurations compete, and when one is selected, the others are completely turned off. This can be seen as both an advantage and as a disadvantage. The advantage is that if a cause is more probable than the other, it is the one we want to highlight. The disadvantage is that it makes the resulting codes somewhat unstable, in the sense that small perturbations of the input $\mathbf{x}$ could give rise to very different values of the optimal code $\mathbf{h}$. This instability could spell trouble for higher levels of learned transformations or a trained classifier that would take $\mathbf{h}$ as input. Indeed it could make generalization more difficult if very similar inputs can