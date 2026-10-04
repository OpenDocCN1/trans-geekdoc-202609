# 10 Featured Examples

Network: [1x1 SeriesNetwork]
Bitstream: [zcu102_single]
ProcessorConfig: []
Target: [1x1 dhldl.Target]

# Compile the MNIST Series Network

To compile the MNIST series network, run the compile function in the dhldl.Workflow object.

```
dn = HW.compile(
### Compiling network for Deep Learning FPGA prototyping ...n### Targeting FPGA bitstream zcu102_single ...
### The network includes the following layers:
1 'imageinput'      Image Input             28x28 images with 'zerocenter' normalization
2 'conv 1'          3x3x1 convolutions with stride [1 1] and padded
3 'batchnorm 1'     Batch NormalizationBatch normalization with 8 channels
4 'relu 1'          ReLU                    ReLU
5 'maxpool 1'      Max Pooling             2x2 max pooling with stride [2 2] and padding
6 'conv 2'          Convolution             16 3x3 convolutions with stride [1 1] and padded
7 'batchnorm 2'   Batch NormalizationBatch normalization with 16 channels
8 'relu 2'          ReLU                    ReLU
9 'maxpool 2'      Max Pooling             2x2 max pooling with stride [2 2] and padding
10 'conv 3'         Convolution             32 3x16 convolutions with stride [1 1] and padded
11 'batchnorm 3'   Batch NormalizationBatch normalization with 32 channels
12 'relu 3'         ReLU                    ReLU
13 'fc'             Fully Connected         10 fully connected layer
14 'softmax'        Softmax                 softmax
15 'classoutput'   Classification Output crosentypex with '0' and 9 other classes
```

Memory regions created.

Skipping: compiling conv 1->relu_3
### Optimizing series network: Fused 'nnet.cnn.layer.BatchNormalizationLayer' into 'nnet.cnn.layer...
### Notice: (Layer 1) The 'data' with type 'nnet.cnn.layer.ImageInputLayer' is implemented
### Notice: (Layer 10) The 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is implemented
Compiling: conv 1->relu_3... complete.
Compiling: fc...
### Notice: (Layer 1) The 'data' with type 'nnet.cnn.layer.ImageInputLayer' is implemented
### Notice: (Layer 3) The 'output' with type 'nnet.cnn.layer.RegressionOutputLayer' is implemented
Compiling: fc... complete.
Skipping: softmax
Skipping: classoutput

Creating Schedule...
Creating Status...

Creating Status Table...complete.
Emitting Schedule...

Emitting Schedule...complete.
Emitting Table...

10-6