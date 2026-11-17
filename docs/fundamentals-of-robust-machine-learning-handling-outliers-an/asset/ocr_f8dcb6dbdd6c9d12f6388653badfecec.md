For $w_{23}$, the same type of formulation is used as for CE except for the use of the LC loss function. The needed partial derivatives for the $i$th row are

```
\(\frac{\partial J^{LC}(\mathbf{w})}{\partial w_{23}} = \frac{\partial J^{LC}(p_i)}{\partial p_i} \frac{\partial p_i}{\partial z_{\text{out},i}} \frac{\partial a_{i3}}{\partial z_{i3}} \frac{\partial z_{i3}}{\partial w_{23}}.\)
```

Then, as before, we can assemble the matrix update equation associated with the first layer parameters as follows (Step 6):

```
\(\begin{bmatrix} w_{11} & w_{21} \\ w_{12} & w_{22} \\ w_{13} & w_{23} \\ w_{14} & w_{24} \end{bmatrix}^{(t+1)} = \begin{bmatrix} w_{11} & w_{21} \\ w_{12} & w_{22} \\ w_{13} & w_{23} \\ w_{14} & w_{24} \end{bmatrix}^{(t)} - \ell \begin{bmatrix} \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{11}} & \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{21}} \\ \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{12}} & \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{22}} \\ \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{13}} & \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{23}} \\ \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{14}} & \frac{\partial J^{LC}(\mathbf{w})}{\partial w_{24}} \end{bmatrix}\)
```

and the biases are updated using

```
\(\begin{bmatrix} b_1 \\ b_2 \\ b_3 \\ b_4 \end{bmatrix}^{(t+1)} = \begin{bmatrix} b_1 \\ b_2 \\ b_3 \\ b_4 \end{bmatrix}^{(t)} - \ell \begin{bmatrix} \frac{\partial J^{LC}(\mathbf{b})}{\partial b_1} \\ \frac{\partial J^{LC}(\mathbf{b})}{\partial b_2} \\ \frac{\partial J^{LC}(\mathbf{b})}{\partial b_3} \\ \frac{\partial J^{LC}(\mathbf{b})}{\partial b_4} \end{bmatrix}.\)
```

When we examine the expressions for gradients required for either CE or LC in this example, it is clear that there is a natural structure and repeated use of partial derivatives as the network is traversed in the reverse direction. This is the core idea of backprop: it relies on the fact that each layer requires partial derivative terms from a previously computed layer. Simply stated, backprop is an efficient implementation of gradient calculations facilitated by the storage and reuse of precomputed partial derivatives. Furthermore, with the advent of graphics processing units (GPUs) in recent years, the matrix-vector operations of forward and backward propagation can be vectorized to greatly reduce computation time. The tasks can also be parallelized to a great extent to further reduce the training time. The combination of backprop, GPUs, and parallelism has made deep learning possible and eventually led to the generative AI capabilities embodied in ChatGPT.

# ## 9.6 Cross-entropy and Log-Cosh Algorithms

We can now combine all the elements discussed thus far into simple algorithms for the cross-entropy neural network (CENN) and the log-cosh neural network (LCNN). The algorithms are provided in Algorithms 9.1 and 9.2.

In the setup phase, the algorithms begin by reading in the training data, \(\mathbf{X}\) and \(\mathbf{y}\). If the dataset is small, we can process all \(n\) rows together as one entity in each iteration. This is called **batch gradient descent** and each iteration is referred to as an **epoch**. For large datasets, especially those encountered in deep learning problems, the whole dataset is not usually processed all at once. Instead, we create small batches of equal-sized subsets of rows of the data and process them one small batch at a time.