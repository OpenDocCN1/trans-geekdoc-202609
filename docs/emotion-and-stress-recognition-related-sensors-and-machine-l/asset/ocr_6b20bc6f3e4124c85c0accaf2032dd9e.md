substantially reduced to a total of 100 convolutional layers (instead of as the VGG16 model), the number of convolutional filters is gradually increased from one convolutional block to the next starting from 8 filters until a maximum of 64 filters. The activation function in each convolutional layer consists of the elu activation function (instead of rectified unit (relu)) activation function as in the VG16 model. Max-pooling and Batch Normalisation [68] are performed after each convolutional block. A detailed description of the feature embedding CNN architecture can be seen in Table 1. The CoupledBiLSTM layers of two LSTMs with 64 units each. The resulting representation of spatio-temporal features is further fed into the attention to generate a single aggregated representation of the input. The classification of the model model is described in Table 2. The exact same architecture is used for both Equation (8) and Equation (9). The whole architecture is subsequently trained in an end-to-end manner, using the Adaptive Moment Estimation (Adam) [69] optimization algorithm with a fixed learning rate set to 10⁻⁵. The categorical cross entropy loss function is used for each network (L_{mhi} = L_{ofi} = L_{agg}) and is defined as follows:

```
$\mathcal{L} = - \sum_{j=1}^{c} y_j \log(\hat{y}_j)$
```

where $\hat{y}_j$ represents the classifier's output, $y_j$ is the ground-truth label value and $c \in N$ is the number of classes for a specific classification task.

# Table 1. Feature embedding CNN architecture.

| Layer | No. Filters |
|---|---|
| 2 × Conv2D | 8 |
| MaxPooling2D | -- |
| Batch Normalisation | -- |
| 2 × Conv2D | 16 |
| MaxPooling2D | -- |
| Batch Normalisation | -- |
| 3 × Conv2D | 32 |
| MaxPooling2D | -- |
| Batch Normalisation | -- |
| 3 × Conv2D | 64 |
| MaxPooling2D | -- |
| Batch Normalisation | -- |
| Flatten | -- |

The size of 1 × 1 kernels is ideal for all convolutional layers and is set to 3 × 3, with the convolutional stride set to 1 performed after each convolutional layer over a 2 × 2 window, with a 2 x 2 stride.

The regularisation parameters of the loss function in Equation (10) are set as follows: $\lambda_{mhi}=\lambda_{ofi} = 0.2$ and $\lambda_{agg} = 0.6$. The value of the regularisation parameter specific to the aggregation layer's loss is higher than the others in order to enable the architecture to compute robust aggregation weights. The whole architecture is trained for a total of 20 epochs with the batch size set to 40 for the BVBD and 60 for the SEDB. The implementation and evaluation of the whole architecture is done with the Python libraries Keras [70], Tensorflow [71] and Scikit-learn [72].