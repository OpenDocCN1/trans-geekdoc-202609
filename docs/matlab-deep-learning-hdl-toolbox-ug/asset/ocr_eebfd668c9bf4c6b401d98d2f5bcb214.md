# 10 Featured Examples

Use the validate function to quantize the parameters in the convolution layers of the network. The validate function simulates the quantized network in MATLAB. The validate function uses the metric function defined in the dquantizationOptions object to compare the results of the single data type network object to the results of the quantized network.

```
prediction_solution = dQuantOutObj.validate(validationData_simulation,options:)

### Network: (Layer 1) The layer 'imageinput' with type 'nnet.cnn.layer.ImageInput' is imple
### Network: (Layer 2) The layer 'imageinput' with type 'nnet.cnn.layer.RegressionOutputLayers is imp
Compiling leg: conv 1->maxpool...
### Network: (Layer 1) The layer 'imageinput' with type 'nnet.cnn.layer.ImageInput' is imple
### Network: (Layer 14) The layer 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is imp
Compiling leg: conv 1->maxpool 4 ... complete.
### Network: (Layer 4) The layer 'maxpool 4' with type 'nnet.cnn.layer' is imple
### Network: (Layer 7) The layer 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is imp
### Should not enter. It means a connection is unaccounted for in MATLAB Edition.
### Network: (Layer 1) The layer 'conv 3' with type 'nnet.cnn.layer.ImageInput' is implemented
### Network: (Layer 2) The layer 'softmax' with type 'nnet.cnn.layer.SoftmaxLayer' is implemented
### Network: (Layer 3) The layer 'classoutout' with type 'nnet.cnn.layer.ClassificationOutputLayer
```

```
prediction_solution = struct with fields:
NumSamples: 5
Metrics:[1x1]
```

For an FPGA validation, the validate function uses the output of the compile function to program the FPGA board by the programming function. It also downloads the networks and biases. The validate function uses the metric function defined in the dquantizationOptions object to compare the output of the network before and after quantization.

```
prediction_FPGA = dQuantOutObj_FPGA.validate(validationData_FPGA, options_FPGA) ...

### Compiling network for Deep Learning prototyping
### Targeting FPGA bitstream zcu102 into
### The network includes the following:
```

| | Image Input | | |
|---|---|---|-|
| 1 | 'imageinput' | | 227x227x3 images with 'zerocenter' normalization |
| 2 | 'conv 1' | Convolution | 96 5x3 convolutions with stride [1 1] and padding |
| 3 | 'relu 1' | ReLU | |
| 4 | 'maxpool 1' | Max Pooling | 3x3 max pooling with stride [2 2] and padding |
| 5 | 'conv 2' | Convolution | 128 3x3 convolutions with stride [1 1] and padding |
| 6 | 'relu 2' | ReLU | |
| 7 | 'maxpool 2' | Max Pooling | 3x3 max pooling with stride [2 2] and padding |
| 8 | 'conv 3' | Convolution | 384 3x3x128 convolutions with stride [1 1] and padding |
| 9 | 'relu 3' | ReLU | |
| 10 | 'maxpool 3' | Max Pooling | 3x3 max pooling with stride [2 2] and padding |
| 11 | 'conv 4' | Convolution | 128 3x3x384 convolutions with stride [2 2] and padding |
| 12 | 'relu 4' | ReLU | |
| 13 | 'maxpool 4' | Max Pooling | 3x3 max pooling with stride [2 2] and padding |
| 14 | 'fc 1' | Fully Connected | 2048 fully connected layer |
| 15 | 'relu 5' | ReLU | |
| 16 | 'dropout 1' | Dropout | 50% dropout |
| 17 | 'fc 2' | Fully Connected | 2048 fully connected layer |
| 18 | 'relu 6' | ReLU | |
| 19 | 'dropout 2' | Dropout | 50% dropout |
| 20 | 'fc 3' | Fully Connected | 32 fully connected layer |

10-112