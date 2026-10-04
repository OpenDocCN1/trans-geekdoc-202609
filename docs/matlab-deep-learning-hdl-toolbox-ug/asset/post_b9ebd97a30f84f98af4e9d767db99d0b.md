
## 10 Featured Examples

Use the validate function to quantize the parameters in the convolution layers of the network. The validate function simulates the quantized network in MATLAB. The validate function uses the metric function defined in the dquantizationOptions object to compare the results of the single data type network object to the results of the quantized network.

```matlab
prediction_solution = dQuantOutObj.validate(validationData_simulation,options:)
```

### Network: (Layer 1) The layer 'imageinput' with type 'nnet.cnn.layer.ImageInput' is implemented
### Network: (Layer 2) The layer 'imageinput' with type 'nnet.cnn.layer.RegressionOutputLayers is implemented
Compiling leg: conv 1->maxpool...
### Network: (Layer 1) The layer 'imageinput' with type 'nnet.cnn.layer.ImageInput' is implemented
### Network: (Layer 14) The layer 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is implemented
Compiling leg: conv 1->maxpool 4 ... complete.
### Network: (Layer 4) The layer 'maxpool 4' with type 'nnet.cnn.layer' is implemented
### Network: (Layer 7) The layer 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is implemented
### Should not enter. It means a connection is unaccounted for in MATLAB Edition.
### Network: (Layer 1) The layer 'conv 3' with type 'nnet.cnn.layer.ImageInput' is implemented
### Network: (Layer 2) The layer 'softmax' with type 'nnet.cnn.layer.SoftmaxLayer' is implemented
### Network: (Layer 3) The layer 'classoutout' with type 'nnet.cnn.layer.ClassificationOutputLayer' is implemented
```

```matlab
prediction_solution = struct with fields:
NumSamples: 5
Metrics: [1x1]
```

For an FPGA validation, the validate function uses the output of the compile function to program the FPGA board by the programming function. It also downloads the networks and biases. The validate function uses the metric function defined in the dquantizationOptions object to compare the output of the network before and after quantization.

```matlab
prediction_FPGA = dQuantOutObj_FPGA.validate(validationData_FPGA, options_FPGA) ...
```

### Compiling network for Deep Learning prototyping
### Targeting FPGA bitstream zcu102 into
### The network includes the following:

| | | Image Input | | |
| :--- | :--- | :--- | :--- |
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

## Quantize Network for FPGA Deployment

21 'softmax' softmax
22 'classoutput' Classification Output entropy with 'adidas' and 31 other class

3 Memory Regions created.
Skipping: imageinput
Compiling leg: conv 1->maxpool 4 ...
Compiling leg: conv 1->maxpool 4 ... complete.
Compiling leg: fc 1->fc 3 ...
Compiling leg: fc 1->fc 3 ... complete.
Skipping: softmax
Skipping: classout
Creating Schedule...
...
Creating Schedule...complete.
Creating Status Table...
...
Creating Status Table...complete.
Emitting Schedule...
...
Emitting Schedule...complete.
Emitting Status Table...
...
Emitting Table...complete.

### Allocating external memory buffers:

| name | offset address | allocated_space |
| :--- | :--- | :--- |
| "InputDataOffset" | 0x00000000 | 48.0 MB |
| "OutputResultOffset" | 0x03000000 | 4.0 MB |
| "SchedulerDataOffset" | 0x03400000 | 4.0 MB |
| "SystemBufferOffset" | 0x03800000 | 60.0 MB |
| "InstructionDataOffset" | 0x07400000 | 8.0 MB |
| "ConvWeightDataOffset" | 0x07C00000 | 12.0 MB |
| "FCWeightDataOffset" | 0x08000000 | 12.0 MB |
| "EndOffset" | 0x09400000 | Total: 148.0 MB |

### Network completion complete.
### FPGA bit programming has been skipped as the same bitstream already loaded on the target
### Deep learning network programming has been skipped as the Finished writing input activations.

### Deep Learning Processor Results

| LastFrame(cycles) | LastFrame(seconds) | Frames |
| :--- | :--- | :--- |
| conv 1 | 127297 | 0.00578 | 1 |
| conv 2 | 281362 | 0.00217 | 1 |
| conv 3 | 535330 | 0.00243 | 1 |
| conv 4 | 504820 | 0.00229 | 1 |
| maxpool 1 | 8965 | 0.00004 | 1 |
| maxpool 2 | 68762 | 0.00313 | 1 |
| maxpool 3 | 58721 | 0.00200 | 1 |
| maxpool 4 | 47786 | 0.00217 | 1 |
| fc 1 | 341132 | 0.00569 | 1 |
| fc 2 | 246293 | 0.00112 | 1 |
| fc 3 | 129631 | 0.00156 | 1 |
