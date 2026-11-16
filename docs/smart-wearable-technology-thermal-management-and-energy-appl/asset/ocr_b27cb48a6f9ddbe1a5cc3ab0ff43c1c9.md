however, allows the initial input to bypass any processing and pass directly to the output. At the end of the process, the values from both the main path and the skip connection are combined through residual mapping, which helps mitigate the vanishing gradient problem and allows deeper networks to perform better. The equation for this process is as follows:

```
X + F(X)
```

where X is the input value and F(X) is the value that passes through the main path. Additionally, the residual block where residual mapping occurs can be illustrated as shown in Figure 4.

![](bbox=[0.27, 0.26, 0.76, 0.55])

The 1D-ResNet model in this study, as depicted in Figure 5, consists of three residual blocks. Each convolutional layer has a kernel size of 3 × 3, with 64 filters in the first block, 128 filters in the second block, and 256 filters in the third block. Following the residual blocks, a global average pooling layer is used to reduce the dimensionality while retaining important features. This is followed by two fully connected layers, a dropout layer with a dropout rate of 0.5 to prevent overfitting, and a softmax layer for calculating class probabilities. The final classification layer then recognizes the workout based on these features. The algorithm was trained using Root Mean Square Propagation (RMSprop) as the solver, chosen for its ability to adapt the learning rate during training, which helps in improving convergence. The model was trained for 200 epochs (800 iterations) with a batch size of 128, an initial learning rate of 0.001 and decrease factor of 0.5 per 25 epochs, allowing for a balance between learning speed and stability. Furthermore, we conducted the same training and validation processes with 3D input data comprising X-, Y-, and Z-axis dimensions to investigate the performance differences compared to the 1D ResNet model.

To validate the performance of the trained 1D ResNet algorithm, we utilized 301 test data samples as input to generate predictions. These predictions were then used to calculate not only the overall accuracy but also key classification metrics such as precision, recall, and F1-score. These metrics were calculated as follows:

```
Precision = \frac{TP}{TP + FP}
```