# Classify ECG Signals Using DAG Network Deployed To FPGA

| 55 | fire8-concat | Depth concatenation | Depth concatenation of 2 inputs |
| 56 | fire9-squeezelx1 | Convolution | 64 1x512 convolutions with stride |
| 57 | fire9-relu squeezelx1 | ReLU | ReLU |
| 58 | fire9-expand1x1 | ReLU | 256 1x64 convolutions with stride |
| 59 | fire9-relu expand1x1 | ReLU | ReLU |
| 60 | fire9-expand3x3 | Convolution | 256 3x64 convolutions with stride |
| 61 | fire9-relu expand3x3 | ReLU | ReLU |
| 62 | fire9-concat | Depth concatenation | Depth concatenation of 2 inputs |
| 63 | new-dropout | Dropout | 60% dropout |
| 64 | new-conv | ReLU | 3 1x512 convolutions with stride |
| 65 | new-conv10 | Global Average Pooling | Global average pooling |
| 66 | pool10 | Softmax | softmax |
| 67 | prob | Classification Output |

Memory Regions created.

```
Skipping: data
Compiling: conv1>>fire2-relu_squeezelx1
Compiling: conv1>>fire2-relu_squeezelx1 ... complete.
Compiling: fire2-expand1x1>>fire2-relu expand1x1
Compiling: fire2-expand1x1>>fire2-relu expand1x1 ... complete.
Compiling: fire2-expand3x3>>fire2-relu expand3x3
Compiling: fire2-expand3x3>>fire2-relu expand3x3 ... complete.
Do nothing: fire2-concat
Compiling: fire3-squeezelx1>>fire3-relu_squeezelx1
Compiling: fire3-squeezelx1>>fire3-relu_squeezelx1 ... complete.
Compiling: fire3-expand1x1>>fire3-relu expand1x1
Compiling: fire3-expand1x1>>fire3-relu expand1x1 ... complete.
Compiling: fire3-expand3x3>>fire3-relu expand3x3
Compiling: fire3-expand3x3>>fire3-relu expand3x3 ... complete.
Do nothing: fire3-concat
Compiling: fire4-squeezelx1>>fire4-relu_squeezelx1
Compiling: fire4-squeezelx1>>fire4-relu_squeezelx1 ... complete.
Compiling: fire4-expand1x1>>fire4-relu expand1x1
Compiling: fire4-expand1x1>>fire4-relu expand1x1 ... complete.
Compiling: fire4-expand3x3>>fire4-relu expand3x3
Compiling: fire4-expand3x3>>fire4-relu expand3x3 ... complete.
Do nothing: fire4-concat
Compiling: fire5-squeezelx1>>fire5-relu_squeezelx1
Compiling: fire5-squeezelx1>>fire5-relu_squeezelx1 ... complete.
Compiling: fire5-expand1x1>>fire5-relu expand1x1
Compiling: fire5-expand1x1>>fire5-relu expand1x1 ... complete.
Compiling: fire5-expand3x3>>fire5-relu expand3x3
Compiling: fire5-expand3x3>>fire5-relu expand3x3 ... complete.
Do nothing: fire5-concat
Compiling: fire6-squeezelx1>>fire6-relu_squeezelx1
Compiling: fire6-squeezelx1>>fire6-relu_squeezelx1 ... complete.
Compiling: fire6-expand1x1>>fire6-relu expand1x1
Compiling: fire6-expand1x1>>fire6-relu expand1x1 ... complete.
Compiling: fire6-expand3x3>>fire6-relu expand3x3
Compiling: fire6-expand3x3>>fire6-relu expand3x3 ... complete.
Do nothing: fire6-concat
Compiling: fire7-squeezelx1>>fire7-relu_squeezelx1
Compiling: fire7-squeezelx1>>fire7-relu_squeezelx1 ... complete.
Compiling: fire7-expand1x1>>fire7-relu expand1x1
Compiling: fire7-expand1x1>>fire7-relu expand1x1 ... complete.
Compiling: fire7-expand3x3>>fire7-relu expand3x3
```

10-165