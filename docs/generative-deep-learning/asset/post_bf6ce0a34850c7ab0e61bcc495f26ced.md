
![](img/f0f0f5d89818fdddf117bbe758ac8143_201_0.png)

Figure 6-4. The two moons dataset in two dimensions

The code for creating this dataset is given in Example 6-1.

## Example 6-1. Creating a moons dataset

```
data = datasets.make_moons(3000, noise=0.05)[0].astype("float32")
norm = layers.Normalization()
norm.adapt(data)
normalized_data = norm(data)
```

- ① Make a noisy, unnormalized moons dataset of 3,000 points.
- ② Normalize the dataset to have mean 0 and standard deviation 1.

We will build a RealNVP model that can generate points in 2D that follow a similar distribution to the two moons dataset. Whilst this is a very simple example, it will help us understand how a normalizing flow model works in practice, in fine detail.

First, however, we need to introduce a new type of layer, called a coupling layer.

## Coupling Layers

A coupling layer produces a scale and translation factor for each element of its input. In other words, it produces two tensors that are exactly the same size as the input, one for the scale factor and one for the translation factor, as shown in Figure 6-5.

![](img/f0f0f5d89818fdddf117bbe758ac8143_201_1.png)

Figure 6-5. A coupling layer outputs two tensors that are the same shape as the input: a scaling factor (s) and a translation factor (t)

To build a custom Coupling layer for our simple example, we can stack Dense layers to create the scale output and a different set of Dense layers to create the translation output, as shown in Example 6-2.

![](img/f0f0f5d89818fdddf117bbe758ac8143_202_0.png)

For images, Coupling layer blocks use Conv2D layers instead of Dense layers.

## Example 6-2. A Coupling layer in Keras

```
def Coupling():
    input_layer = layers.Input(shape=2) ①

    s_layer_1 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(input_layer) ②
    s_layer_2 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_1)
    s_layer_3 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_2)
    s_layer_4 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_3)
    s_layer_5 = layers.Dense(
        2, activation="tanh", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_4) ③

    t_layer_1 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(input_layer) ④
    t_layer_2 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_1)
    t_layer_3 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_2)
    t_layer_4 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_3)
    t_layer_5 = layers.Dense(
        2, activation="linear", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_4) ⑤

    return models.Model(inputs=input_layer, outputs=[s_layer_5, t_layer_5]) ⑥
```

① The input to the Coupling layer block in our example has two dimensions.

- ② The scaling stream is a stack of Dense layers of size 256.
- ③ The final scaling layer is of size 2 and has tanh activation.
- ④ The translation stream is a stack of Dense layers of size 256.
- ⑤ The final translation layer is of size 2 and has linear activation.
- ⑥ The Coupling layer is constructed as a Keras Model with two outputs (the scaling and translation factors).

Notice how the number of channels is temporarily increased to allow for a more complex representation to be learned, before being collapsed back down to the same number of channels as the input. In the original paper, the authors also use regularizers on each layer to penalize large weights.

## Passing data through a coupling layer

The architecture of a coupling layer is not particularly interesting—what makes it unique is the way the input data is masked and transformed as it is fed through the layer, as shown in Figure 6-6.

![](img/f0f0f5d89818fdddf117bbe758ac8143_203_0.png)

Figure 6-6. The process of transforming the input x through a coupling layer

Notice how only the first d dimensions of the data are fed through to the first coupling layer—the remaining D − d dimensions are completely masked (i.e., set to zero). In our simple example with D = 2, choosing d = 1 means that instead of the coupling layer seeing two values, (x₁, x₂), the layer sees (x₁, 0).

The outputs from the layer are the scale and translation factors. These are again masked, but this time with the *inverse* mask to previously, so that only the second halves are let through—i.e., in our example, we obtain (0, s₂) and (0, t₂). These are then applied element-wise to the second half of the input x₂ and the first half of the input x₁ is simply passed straight through, without being updated at all. In summary, for a vector with dimension D where d < D, the update equations are as follows:

$$z_{1:d} = x_{1:d}$$
$$z_{d+1:D} = x_{d+1:D} \odot \exp(s(x_{1:d})) + t(x_{1:d})$$

You may be wondering why we go to the trouble of building a layer that masks so much information. The answer is clear if we investigate the structure of the Jacobian matrix of this function:

$$\frac{\partial z}{\partial x} = \begin{bmatrix} \mathbf{I} & 0 \\ \frac{\partial z_{d+1:D}}{\partial x_{1:d}} & \text{diag}(\exp[s(x_{1:d})]) \end{bmatrix}$$

The top-left d × d submatrix is simply the identity matrix, because z₁:₍d₎ = x₁:₍d₎. These elements are passed straight through without being updated. The top-right submatrix is therefore 0, because z₁:₍d₎ is not dependent on x₍d+1:D₎.

The bottom-left submatrix is complex, and we do not seek to simplify this. The bottom-right submatrix is simply a diagonal matrix, filled with the elements of exp(s(x₁:₍d₎)), because z₍d+1:D₎ is linearly dependent on x₍d+1:D₎ and the gradient is dependent only on the scaling factor (not on the translation factor). Figure 6-7 shows a diagram of this matrix form, where only the nonzero elements are filled in with color.

Notice how there are no nonzero elements above the diagonal—for this reason, this matrix form is called *lower triangular*. Now we see the benefit of structuring the matrix in this way—the determinant of a lower-triangular matrix is just equal to the product of the diagonal elements. In other words, the determinant is not dependent on any of the complex derivatives in the bottom-left submatrix!

J = ∂z/∂x =

![](img/f0f0f5d89818fdddf117bbe758ac8143_205_0.png)

Figure 6-7. The Jacobian matrix of the transformation—a lower triangular matrix, with determinant equal to the product of the elements along the diagonal

Therefore, we can write the determinant of this matrix as follows:

det(J) = exp[∑_j s(x_{1:d})_j]

This is easily computable, which was one of the two original goals of building a normalizing flow model.

The other goal was that the function must be easily invertible. We can see that this is true as we can write down the invertible function just by rearranging the forward equations, as follows:

x_{1:d} = z_{1:d}
x_{d+1:D} = (z_{d+1:D} - t(x_{1:d})) ⊙ exp(-s(x_{1:d}))

The equivalent diagram is shown in Figure 6-8.

![](img/f0f0f5d89818fdddf117bbe758ac8143_206_0.png)

Figure 6-8. The inverse function x = g(z)

We now have almost everything we need to build our RealNVP model. However, there is one issue that still remains—how should we update the first d elements of the input? Currently they are left completely unchanged by the model!

## Stacking coupling layers

To resolve this problem, we can use a really simple trick. If we stack coupling layers on top of each other but alternate the masking pattern, the layers that are left unchanged by one layer will be updated in the next. This architecture has the added benefit of being able to learn more complex representations of the data, as it is a deeper neural network.

The Jacobian of this composition of coupling layers will still be simple to compute, because linear algebra tells us that the determinant of a matrix product is the product of the determinants. Similarly, the inverse of the composition of two functions is just the composition of the inverses, as shown in the following equations:

det(A · B) = det(A)det(B)
$(f_b \circ f_a)^{-1} = f_a^{-1} \circ f_b^{-1}$

Therefore, if we stack coupling layers, flipping the masking each time, we can build a neural network that is able to transform the whole input tensor, while retaining the essential properties of having a simple Jacobian determinant and being invertible. Figure 6-9 shows the overall structure.
