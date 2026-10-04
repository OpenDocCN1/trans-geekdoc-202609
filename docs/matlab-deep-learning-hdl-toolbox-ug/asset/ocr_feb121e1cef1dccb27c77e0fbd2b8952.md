# Compile YOLO v2 Object Detector

To compile the snet series, run the compile function of the dlhdl.Workflow object

dn = HW.compile

### Compiling network for Deep Learning FPGA prototyping ...
### Targeting FPGA bitstream zcul02_single ...
### The network includes the following layers:

| 'data' | Image Input | 222x224x3 images with 'zerocenter' |
| 'conv1' | Convolution | 96 11x3 convolutions with stride |
| 'relu1' | ReLU | ReLU |
| 'norm1' | Cross Normalization | cross normalization with 5 |
| 'pool1' | Max Pooling | 3x3 max pooling with stride [2 2] |
| 'conv2' | Grouped Convolution | 2 groups of 128 5x5x48 convolutions |
| 'relu2' | ReLU | ReLU |
| 'norm2' | Cross Normalization | cross normalization with 5 |
| 'pool2' | Max Pooling | 3x3 max pooling with stride [2 2] |
| 'conv3' | Convolution | 384 3x3x256 convolutions with stride |
| 'relu3' | ReLU | ReLU |
| 'conv4' | Grouped Convolution | 2 groups of 192 3x3x192 convolutions |
| 'relu4' | ReLU | ReLU |
| 'conv5' | Grouped Convolution | 2 groups of 128 3x3x192 convolutions |
| 'yolov2Conv1' | Convolution | 256 3x3x256 convolutions with stride |
| 'yolov2Batch1' | Batch Normalization | Batch normalization with 256 channel |
| 'relu5' | ReLU | ReLU |
| 'yolov2Conv2' | Convolution | 256 3x3x256 convolutions with stride |
| 'yolov2Batch2' | Batch Normalization | Batch normalization with 256 channel |
| 'relu6' | ReLU | ReLU |
| 'yolov2ClassConv' | Convolution | 42 1x1x256 convolutions with stride |
| 'yolov2Transform' | YOLO v2 Transform Layer | YOLO v2 Transform Layer with 7 anchor |
| 'yolov2Output' | YOLO v2 Output | YOLO v2 Output with 7 anchors.

### Optimizing network network: Fused 'snet.cnn.layer.BatchNormalizationLayer' into 'snet.cnn.
Memory regions created
Skipping: data
Compiling leg: conv1->yolov2ClassConv
Compiling leg: conv1->yolov2ClassConv ... complete.
Skipping: yolov2OutputLayer
Creating Schedule...
Creating Schedule...complete.
Creating Table...
Creating Status Table...
Creating Status Table...complete.
Emitting Schedule...complete.
Emitting Status Table...
itting Status...complete.
### Allocating external memory buffers: