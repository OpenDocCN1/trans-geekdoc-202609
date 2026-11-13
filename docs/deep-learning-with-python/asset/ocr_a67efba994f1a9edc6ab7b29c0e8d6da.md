```
```python
if pooling:
    x = layers.MaxPooling2D(2, padding="same")(x)
    x = layers.Conv2D(filters, 1, strides=2)(residual)
elif filters != residual.shape[-1]:
    residual = layers.Conv2D(filters, 1)(residual)
x = layers.add([x, residual])
return x

x = residual_block(x, filters=32, pooling=True)
x = residual_block(x, filters=64, pooling=True)
x = residual_block(x, filters=128, pooling=False)

x = layers.GlobalAveragePooling2D()(x)
outputs = layers.Dense(1, activation="sigmoid")(x)
model = keras.Model(inputs=inputs, outputs=outputs)
model.summary()
```
```

First block

If we use max pooling, we add a strided convolution to project the residual to the expected shape.

If we don't use max pooling, we only project the residual if the number of channels has changed.

Second block; note the increasing filter count in each block.

The last block doesn't need a max pooling layer, since we will apply global average pooling right after it.

This is the model summary we get:

Model: "model"

| Layer (type) | Output Shape | Param # | Connected to |
|---|---|---|---|
| input_1 (InputLayer) | [(None, 32, 32, 3)] | 0 | |
| rescaling (Rescaling) | (None, 32, 32, 3) | 0 | input_1[0][0] |
| conv2d (Conv2D) | (None, 32, 32, 32) | 896 | rescaling[0][0] |
| conv2d_1 (Conv2D) | (None, 32, 32, 32) | 9248 | conv2d[0][0] |
| max_pooling2d (MaxPooling2D) | (None, 16, 16, 32) | 0 | conv2d_1[0][0] |
| conv2d_2 (Conv2D) | (None, 16, 16, 32) | 128 | rescaling[0][0] |
| add (Add) | (None, 16, 16, 32) | 0 | max_pooling2d[0][0] conv2d_2[0][0] |
| conv2d_3 (Conv2D) | (None, 16, 16, 64) | 18496 | add[0][0] |
| conv2d_4 (Conv2D) | (None, 16, 16, 64) | 36928 | conv2d_3[0][0] |
| max_pooling2d_1 (MaxPooling2D) | (None, 8, 8, 64) | 0 | conv2d_4[0][0] |
| conv2d_5 (Conv2D) | (None, 8, 8, 64) | 2112 | add[0][0] |
| add_1 (Add) | (None, 8, 8, 64) | 0 | max_pooling2d_1[0][0] conv2d_5[0][0] |
| conv2d_6 (Conv2D) | (None, 8, 8, 128) | 73856 | add_1[0][0] |
| conv2d_7 (Conv2D) | (None, 8, 8, 128) | 147584 | conv2d_6[0][0] |