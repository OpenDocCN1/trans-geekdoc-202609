# 6 Iterative reconstruction

Previous chapters dealt with analytic image reconstruction algorithms. This chapter, on the other hand, introduces iterative image reconstruction algorithms. Due to high-speed computers, iterative algorithms get more and more attention in medical image reconstruction. This chapter describes the imaging problem as a system of linear equations and reconstructs an image by minimizing an objective function. Many algorithms are available to solve the system of linear equations or to minimize an objective function. The objective function can be set up by using the likelihood function and can also include the prior knowledge about the image. The likelihood function models the noise distribution in the projection measurements. The maximum-likelihood expectation-maximization (ML-EM) algorithm or ordered-subset expectation-maximization (OS-EM) algorithm is the most popular iterative image reconstruction algorithm in emission tomography, and this chapter has devoted significant efforts to it. Many strategies for noise control are discussed. This chapter also presents a research hot spot – image reconstruction with highly undersampled data, which is often referred to as compressed sensing and is, in fact, nothing but another application of Bayesian image reconstruction.

# 6.1 Solving a system of linear equations

Instead of using an analytical algorithm to reconstruct an image, image reconstruction can also be obtained by solving a system of linear equations. In doing so, the image is first discretized into pixels or voxels (volumetric pixels) as illustrated in Figure 6.1.

Here, the image pixels xj (j = 1, 2, ...) are labeled in a 1D sequential order, as are all projections pi (i = 1, 2, ...). For the simple example in Figure 6.1, we can relate the image pixels and the projections using a system of linear equations:

```
x1 + x2 + x3 = p1,
x4 + x5 + x6 = p2,
x7 + x8 + x9 = p3,
x3 + x6 + x9 = p4,
x2 + x5 + x8 = p5,
x1 + x4 + x7 = p6,
2(√2 − 1)x4 + (√2 − 1)x7 + 2(√2 − 1)x8 = p7,
√2x1 + √2x5 + √2x9 = p8,
2(√2 − 1)x2 + (√2 − 1)x3 + 2(√2 − 1)x6 = p9.
(6.1)
```

This system can be rewritten in the matrix form as