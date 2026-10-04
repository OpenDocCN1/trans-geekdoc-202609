
# 10 Featured Examples

![](img/747bfd4f288a7e0917a1f27637cc5c2d_113_0.png)

# Quantize and Deploy trainedBlemNet Network

The trainedBlemNet network improves performance to 45 frames per second. The target performance of the deployed network is 100 frames per second while staying within the target resource utilization budget. The resource utilization budget takes into consideration parameters such as memory size, board IO, and so on. Increasing the resource utilization could mean choosing a larger board which could cost more. Increase deployed network performance and stay within resource utilization budget by quantizing the network. To quantize and deploy the trainedBlemNet:

- Load the dataset as an imageastore. The imageData labels images based on folder names and stores the data. Divide the data into calibration and validation sets. Use 50% of the images for calibration and 50% of the images for validation. Expedite the calibration and validation process by using a subset of the calibration and validation image sets.

```matlab
if -isfile 'dataset.zip'
  url = 'https://www.mathworks.com/supportfiles/dlhdl/dataset.zip';
  websave('dataset.zip',url)
end
unzip('dataset.zip')
imageData = imageDatastorefullfile('dataset',
    'IncludeFolders',true, 'FileExtensions',''.PNG', 'LabelSource','foldernames'),
[calibrationData, validationData] = splitLabel(imageData, 0.5, 'randomized');
calibrationData_reduced = calibrationData.subset(1:20);
validationData_reduced = validationData.subset(1:1);
```

- Create a quantized network using the dlquantizer object. Set the target execution environment to FPGA.

```matlab
dlQuantObj = dlquantizer(snet_blemdenet, 'ExecutionEnvironment', 'FPGA')
```

# Defect Detection

dlQuantObj =
dlquantizer with properties:

NetworkObject: [1xSeriesNetwork]
ExecutionEnvironment: 'FPGA'

- Use the calibrate function to execute the network with sample inputs and collect the information. The calibrate function exercises the network and collects the dynamic ranges of the weights and biases in the convolution and fully connected layers of the network and the dynamic ranges of the activations in all layers of the network. The calibrate function returns a table. Each row of the table contains range information for a learnable parameter of the quantized network.

```matlab
dlQuantObj.calibrate(calibrationData_reduced)
```

| ans=21x5 table | Network Layer Name | Learnable / Activations | MinValue |
| :--- | :--- | :--- | :--- |
| 'conv1 Weights' } | { 'conv1' } | "Weights" | -0.29022 |
| 'conv1 Bias' } | { 'conv1' } | "Bias" | -0.02187 |
| 'conv2 Weights' } | { 'conv2' } | "Weights" | -0.10499 |
| 'conv2 Bias' } | { 'conv2' } | "Bias" | -0.01018 |
| 'fc1 Weights' } | { 'fc1' } | "Weights" | -0.05159 |
| 'fc1 Bias' } | { 'fc1' } | "Bias" | -0.004897 |
| 'fc2 Weights' } | { 'fc2' } | "Weights" | -0.07156 |
| 'fc2 Bias' } | { 'fc2' } | "Bias" | -0.06286 |
| 'imageinput' } | { 'imageinput' } | "Activations" | 0 |
| 'imageinput_normalization' } | { 'imageinput' } | "Activations" | -184.37 |
| 'relu1' } | { 'relu1' } | "Activations" | -112.18 |
| 'maxpool1' } | { 'maxpool1' } | "Activations" | 0 |
| 'crossnorm' } | { 'crossnorm' } | "Activations" | 0 |
| 'conv2' } | { 'conv2' } | "Activations" | 0 |
| 'relu2' } | { 'relu2' } | "Activations" | -117.79 |

- Create an object of the dlhdl.Workflow class. When you create the object, specify the network and the bitstream. Specify the pretrained trained dberDetObject dlQuantObj as the network. Make sure the bitstream matches the data type and the FPGA board you are targeting. In this example the target FPGA is the Xilinx ZCU102 SOC. The bitstream uses int8 data type.

```matlab
hw = dlhdl.Workflow('Network', dlQuantObj, 'Bitstream', 'zcu102_int8', 'Target', hT);
```

- To compile the quantized network, run the compile function of the dlhdl.Workflow object.

```matlab
hw.compile(InputFrameLength,.30)
```

### Compiling network for Deep Learning FPGA prototyping...
### Targeting FPGA bitstream zcu102_int8 *
### The network includes the following layers:
1 'imageinput' Image Input 128x128x1 images with 'zerocenter' normal
2 'conv1' Convolution 20x5x5 convolutions with stride [1 1]
3 'relu2' ReLU
4 'maxpool_1' Max Pooling 2x2 pooling with stride 2 and
5 'crossnorm' Cross Normalization with stride 5 channel
6 'conv_2' Convolution 20x5x20 convolutions with stride 1
7 'relu_2' ReLU
8 'maxpool_2' Max Pooling 2x2 pooling with stride 2 and
9 'fc_1' Fully Connected 5 fully connected layer
10 'fc_2' Fully Connected 2 fully connected layer
11 'softmax' Softmax
12 'classout' Classification Output with classes 'ng' and 'ok'

Memory Regions created.
Skipping: imageinput
Compiling>>maxpool 2
Compiling>>pool2 complete.
Skipping: softmax
Skipping: classoutput
Creating Schedule...
Creating Schedule...complete.
Creating Status Table...
Creating Status...complete.
Emitting Schedule...
Emitting Schedule...complete.
Emitting Status Table...
Emitting Status Table...complete.

### Allocating memory:

| offset_name | offset_address | allocated_space |
| :--- | :--- | :--- |
| "InputDataOffset" | "0x00000000" | 16.0 MB |
| "OutputOffset" | "0x01000000" | 4.0 MB |
| "SchedulerDataOffset" | "0x01400000" | 4.0 MB |
| "SystemBufferOffset" | "0x01800000" | 28.0 MB |
| "InstructionDataOffset" | "0x02400000" | 4.0 MB |
| "ConvWeightDataOffset" | "0x03800000" | 4.0 MB |
| "FCWeightDataOffset" | "0x03c0000" | 12.0 MB |
| "EndOffset" | "0x04000000" | Total: 72.0 MB |

### Network connection complete.

```matlab
ans = struct with fields:
  weights: [1x struct]
  instructions: [1x struct]
  registers: [1x struct]
  syncInstructions: [1x struct]
```

- To deploy the network on the Xilinx ZCU102 SoC, run the deploy function of the dhldl.Workflow object uses this output of the compile function to program the FPGA board using the programming file. It also downloads the network weights and biases.

deploy function starts the FPGA device, displays progress messages, and the time it takes to deploy the network.

# HW:deploy

```matlab
### Programming FPGA Bitstream using Ethernet...
Downloading target FPGA device configuration over Ethernet to SD card ...
# Copied /tmp/hdlcoder_rd to /mnt/hdlcoder_rd
# Copying Bitstream hdlcoder.system.bit to /mnt/hdlcoder_rd
# Set bitstream to hdlcoder/rd/system.bit
# Copying Devicetree devicetree.dlhl.dtb to /mnt/hdlcoder_rd
# Set Devicetree to hdlcoder_rd/devicetree.dlhl.dtb
# Set up boot for Reference Design: 'AXI-Stream DDR Memory Access : 3-AXIM'
```

Downloading target FPGA device configuration over Ethernet to SD card done. The system will now

System is rebooting.

![](img/747bfd4f288a7e0917a1f27637cc5c2d_116_0.png)

```matlab
### Programming the FPGA bitstream has been completed successfully.
### Loading weights to Conv Processor.
### Conv Weights loaded. Current time is 16-Dec-2020 16:18:03
### Loading weights to FC Processor.
### FC Weights loaded. Current time is 16-Dec-2020 16:18:03
```

- Load an image from the attachedImages folder, resize the image to match the network image input layer dimensions, and run the predict function from the dlhl.Workflow object to retrieve and display the defect prediction from the FPGA.

```matlab
wi = uint32(320);
he = uint32(240);
ch = uint32(3);
```

# 10 Featured Examples

```matlab
filename = fullfile(pwd, 'ok1.png');
img = imread(filename);
img = resize(img, [he, wi]);
img = mat2ocv(img);

% Extract ROI for preprocessing
[Iori, imgPacked, bbox] = myDNNet_Preprocess(img);

% row-major > column-major conversion
imgPacked2 = zeros([128, 128, 4], 'uint8');
for c = 1:4
  for i = 128
    for j = 128
      imgPacked2(i,j,c) = imgPacked((i-1)*128 + (j-1) + (c-1)*128 + 1);
  end
end

% Classify detected objects by CNN
scores = zeros(2,4);
for i = 1:num
  [scores(:,i), speed] = HW.predict(single(imgPacked2), 'Profile', 'on');
```

### Finished writing activations.
Nun running input activations.

Deep Learning Processor Profiler Results

| | LastFrameLatency(cycles) | LastFrameLatency(seconds) | Total |
|---|---|---|---|
| Network | 1754969 | 0.00798 | 1 |
| conv_1 | 271340 | 0.00123 | |
| maxpool_1 | 87533 | 0.00040 | |
| crosshorn | 125737 | 0.00057 | |
| conv_2 | 149972 | 0.00068 | |
| maxpool_2 | 19657 | 0.00009 | |
| fc_1 | 108568 | 0.00043 | |
| fc_2 | 14928 | 0.00007 | |

> * The clock frequency of the DL processor is: 220MHz

```matlab
% Iori = reshape([Iori, [1, he*wi]);
bbox = reshape(bbox, [1,16]);
scores = reshape(scores, [1, 8]);
```

```matlab
% Insert an annotation for postprocessing
out = myDNNet_Postprocess(Iori, num, bbox, wi, he);
```

```matlab
sz = [he wi];
out = ocv2mat(out,sz);
imshow(out)
```
