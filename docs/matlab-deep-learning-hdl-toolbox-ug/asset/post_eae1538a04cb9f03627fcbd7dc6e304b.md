
# 10 Featured Examples

```
fc 19441 0.00009
* The clock frequency of the DL processor is: 220MHz
-, idx2] = max(scores, [], 2);
predTestLabelBatch = classnames(idx2);
% The micro-doppler signatures along with the ground truth and
% predictions.
for k = 1:num
index = listIndex(k);
imagesc(testDataNoCar(:, :, index));
axis xy;xlabel('Time (s)')
ylabel('Frequency (Hz)');title(['Ground Truth: '+string(testLabelNoCar(index))+', Prediction FPGA: '+string(TestLabel)
drawnow;
pause(3);
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_129_0.png)

The image shows the micro-Doppler signatures of two bicyclists (bic+bic) which is the ground truth. The ground truth is the classification of the image against which the network prediction is compared. The network prediction retrieved from the FPGA correctly predicts that the image has two bicyclists.

10-50

# Visualize Activations of a Deep Learning Network by Using LogoNet

This example shows how to feed an image to a convolutional neural network and display the activations of the different layers of the network. Examine the activations and discover which features the network learns by comparing areas of activation to the original image. Channels in earlier layers learn features like color and edges, while channels in the deeper layers learn complex features. Identifying features in this way can help you understand what the network has learned.

## Logo Recognition Network

Logos assist in brand identification and recognition. Many companies incorporate their logos in advertising, documentation materials, and promotions. The logo recognition network (LogoNet) was developed in MATLAB and can recognize 32 logos under various lighting conditions and camera motions. Because this network focuses only on recognition, you can use it in applications where localization is not required.

## Prerequisites

- Arria10 SoC development kit
- Deep Learning HDL Toolbox™ Support Package for Intel FPGA and SoC
- Deep Learning Toolbox™
- Deep Vision HDL Toolbox™
- Computer Vision Toolbox™

## Load Pretrained Series Network

To load the pretrained series network LogoNet, enter:

```
snet = getLogoNetwork();
```

## Create Target Object

Create a target object that has a custom name for your target device and an interface to connect your target device to the host computer. Interface options are JTAG and Ethernet. To use JTAG, install Intel™ Quartus Prime Standard Edition 18.1. Use the path to your installed Intel Quartus Prime executable if it is not already set up. For example, to set the include, enter:

```
% hdlsetuptoolath('TargetName', 'Altera Quartus II', 'ToolPath', 'C:\alera\18.1\quartus\bin64');
```

To create the target object, enter:

```
hTarget = dhhdl.Target('Intel', 'Interface', 'JTAG');
```

## Create Workflow Object

Create an object of the dhdl.Workflow class. When you create the object, specify the network and the bitstream name. Specify the saved pretrained LogoNet neural network, snet, as well. Make sure that the bitstream name matches the data type and the FPGA board that you are targeting. In this example, the target FPGA board is the Intel Arria10 SOC board. The bitstream uses a single data type.

```
hW = dlhdl.Workflow('network', snet, 'Bitstream', 'arrialsoc_single', 'Target',hTarget);
```

Read and show an image. Save its size for future use.

```
im = imread('ferari.jpg');
imshow(im)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_131_0.png)

```
imgSize = size(im);
imgSize = imgSize(1:2);
```

## View Network Architecture

Analyze the network to see which layers you can view. The convolutional layers perform convolutions by learning parameters. The network learns to identify useful features, often including one feature per channel. The first convolutional layer has 64 channels.

```
analyzeNetwork(snet)
```

The Input layer specifies the input size. Before passing the image through the network, you can resize it. The network can also process larger images. If you feed the network larger images, the activations become larger. Because the network is trained on images of size 227-by-227, it is not trained to recognize larger objects or features.

## Show Activations of First Maxpool Layer

Investigate features by observing which areas in the maxpool layers activate on an image and comparing that to the corresponding areas in the original images. Each layer of a convolutional neural network consists of many 2-D arrays called channels. Pass the image through the network and examine the activations of the maxpool_1 layer.

```
act1 = hW.activations(single(im),'maxpool_1','Profiler','on');
```

| offset_name | offset_address | allocated_space |
| :--- | :--- | :--- |
| InputDataOffset | 0x00000000 | 24.0 MB |
| OutputResultOffset | 0x01000000 | 136.0 MB |
| SystemBufferOffset | 0x0a000000 | 64.0 MB |
| InstructionDataOffset | 0x0e000000 | 8.0 MB |
| ConvWeightDataOffset | 0x0e000000 | 4.0 MB |
| EndOffset | 0x0e000000 | Total: 236.0 MB |

```

### Programming FPGA Bitstream by JTAG...
### Programming the FPGA bitstream has been completed successfully.

### Finished writing input activations.
### Running single input activations.
```

Deep Learning Processor Profiler Results

| | LastLatency(cycles) | LastLatency(seconds) | FramesNum |
| :--- | :--- | :--- | :--- |
| Network | 10182024 | 0.06788 | 1 |
| conv_module | 10182024 | 0.06788 | |
| conv_1 | 7088885 | 0.04726 | |
| maxpool_1 | 3093166 | 0.02062 | |

* The clock frequency of the DL processor is: 150MHz

The activations are returned as a d-3-array, with the third dimension indexing the channel on the maxpool_1 layer. To show these activations using the itmile function, reshape array to 4-D. The third dimension in the input itmile represents the image color. The third dimension to have size 1 because the activations do not have color. The fourth dimension indexes the channel.

```
sz = size(act1)
act1 = reshape(act1,sz(1) sz(2) 1 sz(3));
```

Display the activations. Each activation can take any value, normalize the output using the mat2gray. All activations are scaled so that the minimum activation is 0 and the maximum activation is 1. Display the 96 images on an 12-by-8 grid, for each channel in the layer.

```
I = itmile(mat2gray(act1), 'GridSize',[12 8]);
imshow(I)
```

# 10 Featured Examples

![](img/747bfd4f288a7e0917a1f27637cc5c2d_133_0.png)

10-54

## Investigate Activations in Specific Channels

Each tile in the activations grid is the output of a channel in the maxpool_1 layer. White pixels represent strong positive activations and black pixels represent strong negative activations. A channel that is mostly gray does not activate as strongly as the input image. The position of a pixel in the activation of a channel corresponds to the same position in the original image. A white pixel at a location indicates the channel is strongly activated there.

Resize the activations in channel 33 to be the same size as the original image and display the activations.

```
actl33 = actl(:,:,22);
actlch33 = mat2gray(actl33);
actlch33 = imresize(actlch33,imgSize);
```

```
I = ittile({{im,actlch33}});
imshow(I)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_134_0.png)

# Find Strongest Activation Channel

Find interesting channels by programmatically investigating channels with large activations. Find the channel that has the largest activation using the max function, resize the channel output, and display the activations.

```
[maxValue,Index] = max(max(max(actl)));
actlchMax = actl(:,:,:,maxValue);
actlchMax = mat2gray(actlchMax);
actlchMax = imresize(actlchMax,imgSize);
```

```
I = ittile({{im,actlchMax}});
imshow(I)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_135_0.png)

Compare the strongest activation channel image to the original image. This channel activates on edges. It activates positively on light left/dark right edges and negatively on dark left/light right edges.

# See Also

# More About

- activations
