where \(\kappa\) is similar to the condition number of matrix \(A\), and \(\kappa\) is defined as the ratio
of the largest singular value \(\sigma_1\) over the cutoff singular value \(\sigma_n\). This simplification is
reasonable because the “worst” noise influence comes from the frequency compo-
nents (i.e., the singular vector) corresponding to the current smallest singular value
\(\sigma_n\). In the SVD pseudo-inverse method, the reconstructed image is a sum of many
terms. Each term is a product of a component (i.e., the singular vector) and the recip-
rocal of its corresponding singular value \(1/\sigma\). The largest gain comes from \(1/\sigma_n\), which
corresponds to a singular vector with very high frequencies.

![](bbox=[0.178, 0.266, 0.755, 0.362])

Fig. 6.11: Application of a window function to the ramp filter.

In your mind, you can imagine that \(\lambda_n(\omega)\) is a windowed ramp filter (see Figure 6.11).
The width of the window increases as the iteration number increases. We immedi-
ately see that one way to control noise is to control the iteration number.

This analogy between an iterative reconstruction and an SVD pseudo-inverse is
not mathematically correct, but it is a way of showing the similarity of these two ap-
proaches. This analogy can give us some insight of an iterative algorithm.

Stopping early is the simplest way to regulate the noise. However, iterative algo-
rithms do not have a uniform convergence rate throughout the image. After an itera-
tive algorithm is stopped, the resultant image will have nonuniform resolution. If you
would like your reconstructed image to have uniform resolution, one remedy is to
over-iterate (i.e., not to stop early) and then apply a post-filter to suppress the noise.

# 6.6.3 Iterative methods: choosing pixels

The second way to reduce image noise is to reduce the errors in the data. This ap-
proach of regularization is a unique feature for the iterative algorithm. The errors
between the projections \(P\) and the model \(AX\), Error\(_{data}\), consist of two parts: determi-
nisitic errors and random errors. The deterministic errors are generated from the non-
ideal system model \(AX\). First of all, discretizing the continuous object into pixels (or
voxels) may cause errors. One must consider the trade-offs when deciding pixel size.
Smaller pixels give a more accurate model but increase the number of unknowns to
be solved. Larger pixels make the image model less accurate, but fewer unknowns
can make the inverse problem more stable.