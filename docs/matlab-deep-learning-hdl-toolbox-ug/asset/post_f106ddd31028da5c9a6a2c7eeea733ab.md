
# 10 Featured Examples

| | | | | |
|---|---|---|---|
| 53 | 'bn5a branch2a' | Batch Normalization | Batch normalization with 512 channels |
| 54 | 'res5a branch2a_relu' | ReLU | ReLU |
| 55 | 'res5a branch2b' | Convolution | 512 3x3 convolutions with stride 1 |
| 56 | 'bn5a branch2b' | Batch Normalization | Batch normalization with 512 channels |
| 57 | 'res5a' | Addition | Element-wise addition of 2 inputs |
| 58 | 'res5a_relu' | ReLU | ReLU |
| 59 | 'res5a branch1' | Convolution | 512 1x256 convolutions with stride 1 |
| 60 | 'bn5a branch1' | Batch Normalization | Batch normalization with 512 channels |
| 61 | 'res5b branch2a' | Convolution | 512 3x3 convolutions with stride 1 |
| 62 | 'bn5b branch2a' | Batch Normalization | Batch normalization with 512 channels |
| 63 | 'res5b branch2a_relu' | ReLU | ReLU |
| 64 | 'res5b branch2b' | Convolution | 512 3x3 convolutions with stride 1 |
| 65 | 'bn5b branch2b' | Batch Normalization | Batch normalization with 512 channels |
| 66 | 'res5b' | Addition | Element-wise addition of 2 inputs |
| 67 | 'res5b_relu' | ReLU | ReLU |
| 68 | 'pool5' | Global Average Pooling | Global average pooling |
| 69 | 'new_fc' | Fully Connected | 5 fully connected layer |
| 70 | 'prob' | Softmax | softmax |
| 71 | 'new_classout' | Classification Output | crossentropy with 'MathWorks Cap' |

```
### Optimization settings network: Fused 'cnn.layer.BatchNormalization' into 'net.cnn.layer'
5 Memory regions created.
Skipping: data:
Compiling leg: conv1->pool1
Compiling leg: conv1->pool1 ... complete.
Compiling leg: res5a branch2a=>res5a branch2b
Compiling leg: res5a branch2a=>res5a branch2b ... complete.
Compiling leg: res5b branch2a=>res5b branch2b
Compiling leg: res5b branch2a=>res5b branch2b ... complete.
Compiling leg: res5a branch1
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch3=>res5a branch2b
Compiling leg: res5a branch3=>res5a branch2b ... complete.
Compiling leg: res5b branch3=>res5b branch2b
Compiling leg: res5b branch3=>res5b branch2b ... complete.
Compiling leg: res5a branch1
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch4=>res5a branch2b
Compiling leg: res5a branch4=>res5a branch2b ... complete.
Compiling leg: res5b branch4=>res5b branch2b
Compiling leg: res5b branch4=>res5b branch2b ... complete.
Compiling leg: res5a branch1
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch5=>res5a branch2b
Compiling leg: res5a branch5=>res5a branch2b ... complete.
Compiling leg: res5b branch5=>res5b branch2b
Compiling leg: res5b branch5=>res5b branch2b ... complete.
Compiling leg: pool5
Compiling leg: pool5 ... complete.
Compiling leg: new_fc ... complete.
Skipping: prob
Skipping: new_classout
Creating Schedule...

Creating Schedule...
Creating Table Status...
```

10-152

# Classify Images on an FPGA Using a Quantized DAG Network

...
Creating Status Table...complete.
Emitting Schedule...

Emitting Schedule..complete.
Emitting Status Table...

Emitting Status Table...complete.

### ### Allocating external memory buffers:

| offset_name | offset_address | allocated_space |
|---|---|---|
| InputDataOffset | 0x00000000 | 24.0 MB |
| OutputResultOffset | 0x01800000 | 4.0 MB |
| SchedulerDataOffset | 0x01c00000 | 4.0 MB |
| SystemBufferOffset | 0x02000000 | 28.0 MB |
| InstructionDataOffset | 0x03c00000 | 4.0 MB |
| ConvweightDataOffset | 0x04000000 | 16.0 MB |
| FCweightDataOffset | 0x05000000 | 4.0 MB |
| EndOffset | | Total: 84.0 MB |

# ### Network complete.
```
dn = struct with fields:
  weights: [1]
  instructions: [1]
  registers: [1]
```

### Program Bitstream on FPGA
To deploy the network on the Xilinx ZCU102 hardware, run the deploy function of the workflow object. This function uses the output of the complete function to program the FPGA board by using the programming file. It also downloads the network weights and biases. The deploy function starts programming the FPGA device, displays progress messages, and the time to deploy the network.

### Programming Bitstream through Ethernet...
Downloading FPGA configuration over Ethernet to SD card ...
Copied /tmp/data_rd to /mnt/data_rd
Copying data.bit to /mnt/data_rd
Setting data.bit to /mnt/data_rd/data.bit
Setting up to /mnt/data_rd
Set up for Reference Design: AXI-Stream Memory Access
This system will now reboot... FPGA bitstream has been completed successfully.

### Loading weights to Conv Processor.
Current time is 11-Jan-2021 12:26:16

### Loading weights to FC Processor.
Current time is 11-Jan-2021 11:26:16

### Load Image for Prediction
Load the example image.
```matlab
imgFile = fullfile(pwd,'MathData','Mathcube_0.jpg');
inputImg = imresize(imread(imgFile),[224 224]);
imshow(inputImg)
```

### Run Prediction for One Image
Execute the predict method on the workflow object and then show the label in MATLAB window.
```matlab
[prediction, speed] = hw.predict(inputImg),'on');
```

### Finished writing input activations.
Running single input activations.

### Deep Learning Profiler Performance Results

| Network | LastFrameLatency(cycles) | LastFrameLatency(seconds) | TotalFrames |
|---|---|---|---|
| conv1 | 732615 | 0.02929 | 1 |
| pool1 | 1111619 | 0.04445 | |
| pool2 | 235563 | 0.00094 | |
| res2a2brancha | 268736 | 0.01007 | |
| res2a2branchb | 269631 | 0.01008 | |
| res2a | 94319 | 0.00338 | |
| res2b2brancha | 268877 | 0.01007 | |
| res2b2branchb | 268863 | 0.01008 | |
| res2b | 94255 | 0.00338 | |

# Classify Images on an FPGA Using a Quantized DAG Network

| | | | |
|---|---|---|---|
| res3a branch1 | 155156 | 0.00062 | |
| res3a branch2a | 226445 | 0.00091 | |
| res3a branch2b | 243593 | 0.00097 | |
| res3a | 47248 | 0.00019 | |
| res3b branch2a | 243461 | 0.00097 | |
| res3b branch2b | 243501 | 0.00097 | |
| res3b | 47232 | 0.00019 | |
| res4a branch1 | 133899 | 0.00054 | |
| res4a branch2a | 134402 | 0.00054 | |
| res4a branch2b | 234104 | 0.00094 | |
| res4a | 236628 | 0.00090 | |
| res4b branch2a | 234058 | 0.00094 | |
| res4b branch2b | 234648 | 0.00094 | |
| res4b | 23756 | 0.00010 | |
| res5a branch1 | 310730 | 0.00124 | |
| res5a branch2a | 310810 | 0.00124 | |
| res5a branch2b | 310890 | 0.00124 | |
| res5b branch1 | 310970 | 0.00124 | |
| res5b branch2a | 311050 | 0.00124 | |
| res5b branch2b | 311130 | 0.00124 | |
