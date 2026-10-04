# Deploy Quantized Network Example

# Program Bitstream onto FPGA and Download Network Weights

Deploy the network on the Xilinx ZCU102 SoC hardware, run the deploy function of the dhldl.Workflow object. This function uses the output of the compile function to program the FPGA board using the programming file. It also downloads the network weights and biases. The deploy function starts programming the FPGA device, displays progress messages, and the time it takes to deploy the network.

HW.deploy

```
### FPGA bitstream programming has been skipped as the same bitstream is already loaded on the
### Loading weights to Conv Processor.
### Current weights loaded. Current time is 17-Dec-2020 11:06:56
### Loading weights to FC Processor.
### 33% finished, current time is 17-Dec-2020 11:06:57.
### 67% finished, current time is 17-Dec-2020 11:06:59.
### FC Weights loaded. Current time is 17-Dec-2020 11:06:59
```

# Load Example Images and Run the Prediction

To load the example image, execute the predict function of the dhldl.Workflow object, and to deploy the FPGA result, execute:

```
idx = randperm(numel(imdsValidation.Files),4)
figure
for i = 1:4
    subplot(2,2,i)
    I = readimage(imdsValidation,idx(i))
    imshow(I)
    [prediction, speed] = HW.predict(single(I), 'Profile','on')
    [val, index] = max(prediction)
    netTransfer.Layers(end).ClassNames(index)
    label = netTransfer.Layers(end).ClassNames(index)
    title(string(label))
end
```

### Finished writing input activations.
### Running simple input activations.

# Deep Learning Profiler Performance Results

| | LastLatency(cycles) | LastLatency(seconds) | FramesNum |
|---|---|---|-|
| Network | 9008267 | 0.04131 | 1 |
| conv1 | 713071 | 0.00324 | |
| norm1 | 460546 | 0.00209 | |
| pool1 | 88791 | 0.00040 | |
| conv2 | 911059 | 0.00414 | |
| norm2 | 270238 | 0.00123 | |
| pool2 | 92782 | 0.00042 | |
| conv3 | 297066 | 0.00135 | |
| conv4 | 238155 | 0.00108 | |
| conv5 | 166248 | 0.00076 | |
| pool5 | 19576 | 0.00080 | |
| fc6 | 3955696 | 0.01798 | |
| fc7 | 1757863 | 0.00799 | |

10-105