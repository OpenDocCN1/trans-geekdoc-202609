

(10.17) `y_i = \sum_{j=1}^{K} \alpha_j \tilde{f}_j(\mathbf{x}_i) + \epsilon_i, i = 1, \dots, n`

where `α_j`, to be determined, is the coefficient serving as a kind of “weight” associated with `\tilde{f}_j(\cdot)`. We essentially consider `(\tilde{f}_1(\mathbf{x}), \dots, \tilde{f}_K(\mathbf{x}))^T` as a `K`‐dimensional random input vector. Generally speaking, `K` is mostly large, so we use a PCA approach to these `\tilde{f}_j(\mathbf{x}_i)`'s to reduce the input data dimension, at the same time also removing the collinearity (if present). With a sample of size `n`, consider the following `K × n` data matrix:

`\tilde{D} := (\tilde{f}_{\cdot}(\mathbf{x}_1) \dots \tilde{f}_{\cdot}(\mathbf{x}_n)), where \tilde{f}_{\cdot}(\mathbf{x}_i) := (\tilde{f}_1(\mathbf{x}_i) \dots \tilde{f}_K(\mathbf{x}_i))^T,`

