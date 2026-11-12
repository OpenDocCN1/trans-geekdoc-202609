Target: The matrix that the student succeeds in the subject of deep learning is given by (targets) the following:

```
$$y_{N \times K} = \begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix}$$
```

where 1 represents the student who succeeds, and 0 represents the student who does not succeed in deep learning.

Our objective is to perform multi-class classification using the sigmoid activation function. Weights are defined as follows:

```
$$w_{D \times M} = \begin{bmatrix} 0.5 & 0.1 & -0.3 \\ 0.7 & -0.3 & 0.2 \end{bmatrix}$$
```

Taking transpose of the preceding matrix:

```
$$w_{M \times D}^T = \begin{bmatrix} 0.5 & 0.7 \\ 0.1 & -0.3 \\ -0.3 & -.2 \end{bmatrix}$$
```

The previous matrix denotes input to the neural network. Then we train the network. The purpose of training is to make predictions close to the targets.

Also, we have a bias at Z1, Z2, Z3 as follows.

```
$$b = \begin{bmatrix} b_1 = 0.4 \\ b_2 = 0.1 \\ b_3 = 0 \end{bmatrix}$$
```

The feed-forward neural network for this case is given as follows:

![](bbox=[0.22, 0.64, 0.78, 0.93])