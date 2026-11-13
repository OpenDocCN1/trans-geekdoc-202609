As a reminder, this is what our convolutional base looks like:

```
>>> conv_base.summary()
Model: "vgg16"
```

| Layer (type) | Output Shape | Param # |
|---|---|---|
| input_19 (InputLayer) | [(None, 180, 180, 3)] | 0 |
| block1_conv1 (Conv2D) | (None, 180, 180, 64) | 1792 |
| block1_conv2 (Conv2D) | (None, 180, 180, 64) | 36928 |
| block1_pool (MaxPooling2D) | (None, 90, 90, 64) | 0 |
| block2_conv1 (Conv2D) | (None, 90, 90, 128) | 73856 |
| block2_conv2 (Conv2D) | (None, 90, 90, 128) | 147584 |
| block2_pool (MaxPooling2D) | (None, 45, 45, 128) | 0 |
| block3_conv1 (Conv2D) | (None, 45, 45, 256) | 295168 |
| block3_conv2 (Conv2D) | (None, 45, 45, 256) | 590080 |
| block3_conv3 (Conv2D) | (None, 45, 45, 256) | 590080 |
| block3_pool (MaxPooling2D) | (None, 22, 22, 256) | 0 |
| block4_conv1 (Conv2D) | (None, 22, 22, 512) | 1180160 |
| block4_conv2 (Conv2D) | (None, 22, 22, 512) | 2359808 |
| block4_conv3 (Conv2D) | (None, 22, 22, 512) | 2359808 |
| block4_pool (MaxPooling2D) | (None, 11, 11, 512) | 0 |
| block5_conv1 (Conv2D) | (None, 11, 11, 512) | 2359808 |
| block5_conv2 (Conv2D) | (None, 11, 11, 512) | 2359808 |
| block5_conv3 (Conv2D) | (None, 11, 11, 512) | 2359808 |
| block5_pool (MaxPooling2D) | (None, 5, 5, 512) | 0 |

```
Total params: 14,714,688
Trainable params: 14,714,688
Non-trainable params: 0
```

We'll fine-tune the last three convolutional layers, which means all layers up to block4_pool should be frozen, and the layers block5_conv1, block5_conv2, and block5_conv3 should be trainable.