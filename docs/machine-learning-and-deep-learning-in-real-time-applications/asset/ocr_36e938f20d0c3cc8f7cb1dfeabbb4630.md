# An Introduction to Deep Convolutional Neural Networks With Keras

| dense_21 (Dense) | (None, 4) | 36 | add_6[0][0] |
|---|---|---|---|

Total params: 828
Trainable params: 828
Non-trainable params: 0

Figure 23. Addition of three layers build by Keras API

| input: (None, 32) | input: (None, 32) | input: (None, 32) | input: (None, 32) |
|---|---|---|---||
| input_25: InputLayer | input_26: InputLayer | input_27: InputLayer | |
| output: (None, 32) | output: (None, 32) | output: (None, 32) | output: (None, 32) |

| input: (None, 32) | input: (None, 32) | input: (None, 32) |
|---|---|---||
| dense_18: Dense | dense_19: Dense | dense_20: Dense |
| output: (None, 8) | output: (None, 8) | output: (None, 8) |

| input: [(None, 8), (None, 8), (None, 8)] | |
|---||
| add_6: Add | |
| output: (None, 8) | |

| input: (None, 8) | |
|---||
| dense_21: Dense | |
| output: (None, 4) | |

# Subtraction of Two Keras Layers

The subtraction function of Keras tensor takes as an input a list of tensors with size 2 and has both the shape and provides a single tensor output with the same shape. The command is used for this purpose is keras.layers.Subtract(). Figure 24 shows the subtraction of two layers. Figure 25 shows the subtraction of two layers builds by Keras API.

Figure 24. Subtraction of two layers

![](bbox=[0.172, 0.699, 0.858, 0.903])