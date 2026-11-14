| Layer | Output Shape | Param # | Connected to |
| :--- | :--- | :--- | :--- |
| dropout_5 (Dropout) | (None, 16, 16, 256) | 0 | batch_normalization_9[0][0] |
| conv2d_10 (Conv2D) | (None, 16, 16, 256) | 590080 | dropout_5[0][0] |
| batch_normalization_10 (BatchNo | (None, 16, 16, 256) | 1024 | conv2d_10[0][0] |
| conv2d_transpose_1 (Conv2DTrans | (None, 32, 32, 128) | 131200 | batch_normalization_10[0][0] |
| concatenate_1 (Concatenate) | (None, 32, 32, 256) | 0 | conv2d_transpose_1[0][0] batch_normalization_8[0][0] |
| conv2d_11 (Conv2D) | (None, 32, 32, 128) | 295040 | concatenate_1[0][0] |
| batch_normalization_11 (BatchNo | (None, 32, 32, 128) | 512 | conv2d_11[0][0] |
| dropout_6 (Dropout) | (None, 32, 32, 128) | 0 | batch_normalization_11[0][0] |
| conv2d_12 (Conv2D) | (None, 32, 32, 128) | 147584 | dropout_6[0][0] |
| batch_normalization_12 (BatchNo | (None, 32, 32, 128) | 512 | conv2d_12[0][0] |
| conv2d_transpose_2 (Conv2DTrans | (None, 64, 64, 64) | 32832 | batch_normalization_12[0][0] |
| concatenate_2 (Concatenate) | (None, 64, 64, 128) | 0 | conv2d_transpose_2[0][0] batch_normalization_6[0][0] |
| conv2d_13 (Conv2D) | (None, 64, 64, 64) | 73792 | concatenate_2[0][0] |
| batch_normalization_13 (BatchNo | (None, 64, 64, 64) | 256 | conv2d_13[0][0] |
| dropout_7 (Dropout) | (None, 64, 64, 64) | 0 | batch_normalization_13[0][0] |
| conv2d_14 (Conv2D) | (None, 64, 64, 64) | 36928 | dropout_7[0][0] |
| batch_normalization_14 (BatchNo | (None, 64, 64, 64) | 256 | conv2d_14[0][0] |
| conv2d_transpose_3 (Conv2DTrans | (None, 128, 128, 32) | 8224 | batch_normalization_14[0][0] |
| concatenate_3 (Concatenate) | (None, 128, 128, 64) | 0 | conv2d_transpose_3[0][0] batch_normalization_4[0][0] |
| conv2d_15 (Conv2D) | (None, 128, 128, 32) | 18464 | concatenate_3[0][0] |
| batch_normalization_15 (BatchNo | (None, 128, 128, 32) | 128 | conv2d_15[0][0] |
| dropout_8 (Dropout) | (None, 128, 128, 32) | 0 | batch_normalization_15[0][0] |
| conv2d_16 (Conv2D) | (None, 128, 128, 32) | 92488 | dropout_8[0][0] |
| batch_normalization_16 (BatchNo | (None, 128, 128, 32) | 128 | conv2d_16[0][0] |
| conv2d_transpose_4 (Conv2DTrans | (None, 256, 256, 16) | 2064 | batch_normalization_16[0][0] |
| concatenate_4 (Concatenate) | (None, 256, 256, 32) | 0 | conv2d_transpose_4[0][0] batch_normalization_2[0][0] |

Fig. (5). Summary of the Keras model implemented in the system.

In between down sampling and up sampling dropout, maxpooling2d, convolution layers are being used whose functions are as followed:

+   * Dropout: The dropout layer is simply used to avoid overfitting. It subsamples the output layer randomly thus avoiding reducing capacity or thinning of the network.
+   * Maxpooling2d: It proved the feature map after scanning input by a fixed size filter containing the most prominent features. Its filter selects maximum elements from the region of the feature map.
+   * Convolution: The convolution layer is the soul of any neural network. Its simple application of filter over input results in the activation of features. Moreover,