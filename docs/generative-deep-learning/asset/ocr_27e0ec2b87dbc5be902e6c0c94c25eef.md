The full architectures of the encoder and decoder are shown in Tables 3-5 and 3-6, respectively.

# Table 3-5. Model summary of the VAE faces encoder

| Layer (type) | Output shape | Param # | Connected to |
|---|---|---|---|
| InputLayer (input) | (None, 32, 32, 3) | 0 | [] |
| Conv2D (conv2d_1) | (None, 16, 16, 128) | 3,584 | [input] |
| BatchNormalization (bn_1) | (None, 16, 16, 128) | 512 | [conv2d_1] |
| LeakyReLU (lr_1) | (None, 16, 16, 128) | 0 | [bn_1] |
| Conv2D (conv2d_2) | (None, 8, 8, 128) | 147,584 | [lr_1] |
| BatchNormalization (bn_2) | (None, 8, 8, 128) | 512 | [conv2d_2] |
| LeakyReLU (lr_2) | (None, 8, 8, 128) | 0 | [bn_2] |
| Conv2D (conv2d_3) | (None, 4, 4, 128) | 147,584 | [lr_2] |
| BatchNormalization (bn_3) | (None, 4, 4, 128) | 512 | [conv2d_3] |
| LeakyReLU (lr_3) | (None, 4, 4, 128) | 0 | [bn_3] |
| Conv2D (conv2d_4) | (None, 2, 2, 128) | 147,584 | [lr_3] |
| BatchNormalization (bn_4) | (None, 2, 2, 128) | 512 | [conv2d_4] |
| LeakyReLU (lr_4) | (None, 2, 2, 128) | 0 | [bn_4] |
| Flatten (flatten) | (None, 512) | 0 | [lr_4] |
| Dense (z_mean) | (None, 200) | 102,600 | [flatten] |
| Dense (z_log_var) | (None, 200) | 102,600 | [flatten] |
| Sampling (z) | (None, 200) | 0 | [z_mean, z_log_var] |

Total params 653,584
Trainable params 652,560
Non-trainable params 1,024

# Table 3-6. Model summary of the VAE faces decoder

| Layer (type) | Output shape | Param # |
|---|---|---|
| InputLayer | (None, 200) | 0 |
| Dense | (None, 512) | 102,912 |
| BatchNormalization | (None, 512) | 2,048 |
| LeakyReLU | (None, 512) | 0 |
| Reshape | (None, 2, 2, 128) | 0 |
| Conv2DTranspose | (None, 4, 4, 128) | 147,584 |
| BatchNormalization | (None, 4, 4, 128) | 512 |
| LeakyReLU | (None, 4, 4, 128) | 0 |
| Conv2DTranspose | (None, 8, 8, 128) | 147,584 |