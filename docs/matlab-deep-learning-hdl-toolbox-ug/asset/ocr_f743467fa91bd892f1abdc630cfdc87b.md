# 10 Featured Examples

# Compile the netTransfer DAG network, run the compile method of the dlhdl.Workflow

To compile the netTransfer DAG network, you can optionally specify the maximum number of inputs.

```
dn = hw.compile('InputFrameNumberLimit',15)
```

### Compilation network for Deep Learning FPGA prototyping ...
### Targeting FPGA bitstream zcu102_single ...
nThe network includes the following layers:

| | | | |
|---|---||
| 1 | 'data' | Image Input | 222x224x3 images with 'z' normalization |
| 2 | 'conv1' | Convolution | 64 7x3 convolutions with stride [2 |
| 3 | 'bn_conv1' | Batch Normalization | |
| 4 | 'conv1_relu' | ReLU | |
| 5 | 'pool1' | Max Pooling | 3x3 max pooling with stride [2] and |
| 6 | 'res2a_branch2a' | Convolution | 64 3x4 convolutions with stride [1 |
| 7 | 'bn2a_branch2a' | Batch Normalization | Batch normalization with 64 channels |
| 8 | 'res2a_branch2a_relu' | ReLU | |
| 9 | 'res2a_branch2b' | Convolution | 64 3x4 convolutions with stride [1 |
| 10 | 'bn2a_branch2b' | Batch Normalization | Batch normalization with 64 channels |
| 11 | 'res2a' | Addition | Element-wise addition of 2 inputs |
| 12 | 'res2a_relu' | ReLU | |
| 13 | 'res2b_branch2a' | Convolution | 64 3x4 convolutions with stride [1 |
| 14 | 'bn2b_branch2a' | Batch Normalization | Batch normalization with 64 channels |
| 15 | 'res2b_branch2a_relu' | ReLU | |
| 16 | 'res2b_branch2b' | Convolution | 64 3x4 convolutions with stride [1] |
| 17 | 'bn2b_branch2b' | Batch Normalization | Batch normalization with 64 channels |
| 18 | 'res2b' | Addition | Element-wise addition of 2 inputs |
| 19 | 'res2b_relu' | ReLU | |
| 20 | 'res3a' | Convolution | 128 3x64 convolutions with stride [2] |
| 21 | 'bn3a_branch2a' | Batch Normalization | Batch normalization with 128 channels |
| 22 | 'res3a_branch2a_relu' | ReLU | |
| 23 | 'res3a_branch2b' | Convolution | 128 3x64 convolutions with stride [2] |
| 24 | 'bn3a_branch2b' | Batch Normalization | Batch normalization with 128 channels |
| 25 | 'res3a' | Addition | Element-wise addition of 2 inputs |
| 26 | 'res3a_relu' | ReLU | |
| 27 | 'res3a_branch1' | Convolution | 128 1x64 convolutions with stride [2] |
| 28 | 'bn3a_branch1' | Batch Normalization | Batch normalization with 128 channels |
| 29 | 'res3b_branch2a' | Convolution | 128 3x64 convolutions with stride [2] |
| 30 | 'bn3b_branch2a' | Batch Normalization | Batch normalization with 128 channels |
| 31 | 'res3b_branch2a_relu' | ReLU | |
| 32 | 'res3b_branch2b' | Convolution | 128 3x64 convolutions with stride [2] |
| 33 | 'bn3b_branch2b' | Batch Normalization | Batch normalization with 128 channels |
| 34 | 'res3b' | Addition | Element-wise addition of 2 inputs |
| 35 | 'res3b_relu' | ReLU | |
| 36 | 'res4a' | Convolution | 256 3x128 convolutions with stride [2] |
| 37 | 'bn4a_branch2a' | Batch Normalization | Batch normalization with 256 channels |
| 38 | 'res4a_branch2a_relu' | ReLU | |
| 39 | 'res4a_branch2b' | Convolution | 256 3x256 convolutions with stride [2] |
| 40 | 'bn4a_branch2b' | Batch Normalization | Batch normalization with 256 channels |
| 41 | 'res4a' | Addition | Element-wise addition of 2 inputs |
| 42 | 'res4a_relu' | ReLU | |
| 43 | 'res4a_branch1' | Convolution | 256 1x128 convolutions with stride [2] |
| 44 | 'bn4a_branch1' | Batch Normalization | Batch normalization with 256 channels |
| 45 | 'res4b_branch2a' | Convolution | 256 3x256 convolutions with stride [2] |
| 46 | 'bn4b_branch2a' | Batch Normalization | Batch normalization with 256 channels |
| 47 | 'res4b_branch2a_relu' | ReLU |

10-142