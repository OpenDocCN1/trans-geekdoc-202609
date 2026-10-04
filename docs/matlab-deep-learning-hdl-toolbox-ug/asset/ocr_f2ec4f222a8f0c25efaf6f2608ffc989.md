# Image Classification Using DAG Network Deployed to FPGA

| 48 | res4b_branch2b | Convolution | 256 3x3x256 convolutions with stride |
| 49 | bn4b branch2b | Batch Normalization | Batch normalization with 256 channels |
| 50 | res4b* | Addition | Element-wise addition of 2 inputs |
| 51 | res4a relu | ReLU | ReLU |
| 52 | res5a branch2a | Convolution | 512 3x3x256 convolutions with stride [ |
| 53 | bn5a branch2a | Batch Normalization | Batch normalization with 512 channels |
| 54 | res5a branch2a_relu | ReLU | ReLU |
| 55 | res5a branch2b | Convolution | 512 3x3x256 convolutions with stride [ |
| 56 | bn5a branch2b | Batch Normalization | Batch normalization with 512 channels |
| 57 | res5a* | Addition | Element-wise addition of 2 inputs |
| 58 | res5a relu | ReLU | ReLU |
| 59 | res5a branch1 | Convolution | 512 1x1x256 convolutions with stride [ |
| 60 | bn5a branch1 | Batch Normalization | Batch normalization with 512 channels |
| 61 | res5b branch2a | Convolution | 512 3x3x256 convolutions with stride [ |
| 62 | bn5b branch2a | Batch Normalization | Batch normalization with 512 channels |
| 63 | res5b branch2a_relu | ReLU | ReLU |
| 64 | res5b branch2b | Convolution | 512 3x3x256 convolutions with stride [ |
| 65 | bn5b branch2b | Batch Normalization | Batch normalization with 512 channels |
| 66 | res5b* | Addition | Element-wise addition of 2 inputs |
| 67 | res5b relu | ReLU | Global Average pooling |
| 68 | pool5* | Fully Connected | 5 connected layer |
| 69 | new_fc | Softmax | softmax |
| 70 | prob* | | |
| 71 | new_classout | Classification Output | crosentropyex with'MathWorks' Cap and

```
### Optimizing series network: fused 'resnet.cnn.layer.BatchNormalizationLayer into 'resnet.cnn..
Skipping data:
Compiling leg: conv1->pool1 ... complete.
Compiling leg: conv1->pool1 ... complete.
Compiling leg: res2a branch2a->res2a branch2b...
Compiling leg: res2a branch2a->res2a branch2b ... complete.
Compiling leg: res2b branch2a->res2b branch2b...
Compiling leg: res2b branch2a->res2b branch2b ... complete.
Compiling leg: res3a branch1 ... complete.
Compiling leg: res3a branch1 ... complete.
Compiling leg: res3a branch2a->res3a branch2b...
Compiling leg: res3a branch2a->res3a branch2b ... complete.
Compiling leg: res3b branch2a->res3b branch2b...
Compiling leg: res3b branch2a->res3b branch2b ... complete.
Compiling leg: res4a branch1 ... complete.
Compiling leg: res4a branch1 ... complete.
Compiling leg: res4a branch2a->res4a branch2b...
Compiling leg: res4a branch2a->res4a branch2b ... complete.
Compiling leg: res4b branch2a->res4b branch2b...
Compiling leg: res4b branch2a->res4b branch2b ... complete.
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch2a->res5a branch2b...
Compiling leg: res5a branch2a->res5a branch2b ... complete.
Compiling leg: res5b branch2a->res5b branch2b...
Compiling leg: res5b branch2a->res5b branch2b ... complete.
Compiling leg: pool5 ... complete.
Compiling leg: pool5 ... complete.
Compiling leg: new_fc ... complete.
Compiling leg: new_fc ... complete.
Skipping: prob
```

10-143