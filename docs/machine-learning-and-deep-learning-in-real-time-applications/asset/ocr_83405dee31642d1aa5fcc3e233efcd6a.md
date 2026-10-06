# An Introduction to Deep Convolutional Neural Networks With Keras

Figure 25. Subtraction of two layers builds by Keras API

| input: (None, 16) | input: (None, 32) |
| --- | --- |
| input_35: InputLayer | input_36: InputLayer |
| output: (None, 16) | output: (None, 32) |
| |

| input: (None, 16) | input: (None, 32) |
| --- | --- |
| dense_31: Dense | dense_32: Dense |
| output: (None, 8) | output: (None, 8) |
| |

| input: {(None, 8), (None, 8)} |
| --- |
| subtract_4: Subtract |
| output: (None, 8) |
|

| input: (None, 8) |
| --- |
| dense_33: Dense |
| output: (None, 4) |
|

Figure 26. Multiplication of two layers

![](bbox=[0.203, 0.453, 0.796, 0.626])

out = keras.layers.Dense(4)(subtracted)
model = keras.models.Model(inputs=[input1, input2], outputs=out)
model.summary()

| Layer (type) | Output Shape | Param # | Connected to |
| --- | --- | --- | --- |
| input_39 (InputLayer) | (None, 16) | 0 | |
| input_40 (InputLayer) | (None, 32) | | |
| dense_37 (Dense) | (None, 8) | 136 | input_39[0][0] |
| dense_38 (Dense) | (None, 8) | 264 | input_40[0][0] |