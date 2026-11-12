| Layer | Input Size | No. of Filters ($n_l$) | Filter Size ($F$) | Padding ($P$) | Stride ($S$) | Output Size | Number of parameters (size of filter * number of filters) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Convolution Layer 12 | 14 * 14 * 512 | 512 | (3 * 3 * 512) | Same | 1 | 14 * 14 * 512 | (3 * 3 * 512) * 512 |
| Convolution Layer 13 | 14 * 14 * 512 | 512 | (3 * 3 * 512) | Same | 1 | 14 * 14 * 512 | (3 * 3 * 512) * 512 |
| Pooling Layer 5 (Max Pooling.) | 14 * 14 * 512 | 1 | (2 * 2) | 0 | 2 | 7 * 7 * 512 | 0 |
| Fully Connected Layer 1 | 7 * 7 * 512 = 25088 | NA | NA | NA | NA | 4096 | (7 * 7 * 512) * 4096 |
| Fully Connected Layer 2 | 4096 | NA | NA | NA | NA | 4096 | (4096 * 4096) |
| Fully Connected Layer 3 | 1000 | NA | NA | NA | NA | 1000 | (4096 * 1000) |
| Summation of parameters | 28 Million | NA | NA | NA | NA | - | 138 Million |

Table 4.4: VGGNet parameters [INPUT:]

# Different types of model-fitting and dropout in neural networks

Model fitting is a method to measure how well a deep learning model shows the results on new testing data after being trained with the training data. Model fitting is divided into three parts: under-fitting, balanced-fitting, and over-fitting, as shown in figure 4.175: