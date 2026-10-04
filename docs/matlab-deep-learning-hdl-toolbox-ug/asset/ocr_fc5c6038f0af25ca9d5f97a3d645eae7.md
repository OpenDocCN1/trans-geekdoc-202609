# Classify ECG Signals Using DAG Network Deployed To FPGA

# Program Bitstream onto FPGA and Download Network Weights

To deploy the network on the Xilinx ZCU102 hardware, run the deploy function of the dlhl.Workflow object. This function uses the output of the compile function to program the FPGA board using the programming file. It also downloads the network weights and biases. The deploy function starts programming the FPGA device, displays progress messages, and the time it takes to deploy the network.

```
HW.deploy

### FPGA bitstream programming has been skipped as the same bitstream is already loaded on the t
### Conv Weights loaded. Current time is 12-Jan-2021 16:28:17
```

# Load Image for Prediction and Run prediction

```
idx=randi(32);
testim=reimage(imgsValidation,idx);
im=resize(testim,[227 227]);
imshow(testim)
```

![](bbox=[0.15, 0.433, 0.53, 0.703])

```
[YPred1,probs1] = classify(trainedSN,im);
accuracy1 = (YPred1==imgsValidation.Labels);
[YPred2,probs2] = hW.predict(single(im), profile', 'on');

### Finished writing input activations.
### Running single input activations.
```

Deep Learning Processor Profiler Performance Results

| Network | LastFrameLatency(cycles) | LastFrameLatency(seconds) | FrameNum |
|---|---|---|--|
| conv1 | 8847610 | 0.04022 | 1 |
| | 626502 | 0.00285 | |

10-167