
An intimate limitation of hyperspectral remote sensing is that a single pixel often records a mixed spectral signature of different distinct materials, due to the low spatial resolution of the remote sensor. This raises the need for spectral unmixing (SU) [37], which is a very important step in hyperspectral image processing that has recently attracted strong scientific interest. SU is the procedure of decomposing the measured spectrum of an observed pixel into a collection of constituent spectral signatures (or `endmembers`) and their corresponding proportions (or `abundances`). A widely used model to perform SU is the linear mixing model.

Assume a remotely sensed hyperspectral image consisting of `M` spectral bands, and let `y ∈ ℝ^M` be the vector containing the measured spectral signature (i.e., the radiance values in all spectral bands) of a single pixel (specific earth patch). Also let `X = [x[1], x[2], …, x[l]]` stand for the `M × l` endmember signature matrix, where `x[i] ∈ ℝ^M, i = 1, 2, …, l`, comprises the spectral signatures of the `i`th endmember, and `l` is the total number of (possible) distinct endmembers (earth surface/material types) present in the scene. Finally, let `θ = [θ[1], θ[2], …, θ[l]]^T` be the `abundance vector` associated with `y`, where `θ[i]` denotes the abundance fraction of `x[i]` in `y`. The linear mixing model assumes that there is a linear relationship between the spectra of the measured pixel and the endmembers, expressed as

```
y = Xθ + η
```

where `η` stands for the additive noise values, which are assumed to be samples of a zero mean Gaussian distributed random vector, with (i.i.d.) elements, that is, `η ∼ N(η|0, β^(−1)I[M])`, where `β` denotes the inverse of the noise variance (precision), and `I[M]` is the `M × M` identity matrix. Note that the model in Eq. (13.143) is a typical regression model in its multivariate formulation, because now the output for each measurement is a vector and not a scalar (see also Section 4.9 of Chapter 4). The output variables are measured and the matrix `X` is assumed known, and indeed there are methods to estimate its elements.

Treating such a model to recover the abundance coefficients would be a straightforward application of what has been said so far in the current and previous chapters of this book. However, there is a physical constraint that has to be considered and that makes the task more interesting. The abundance coefficients are nonnegative, that is,

```
θ[i] ≥ 0,  i = 1, 2, …, l.
```

Additionally, a valid assumption is that only a few of the endmembers present in the image will contribute to the spectrum of a single pixel `y`. In other words, the abundance vector `θ` accepts a `sparse` representation in `X`.
