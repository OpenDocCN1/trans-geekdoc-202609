# ### Loading weights to FC Processor.

### FC Weights loaded. Current time is 11-Jan-2021 11:26:16

# Load Image for Prediction

Load the example image.

```
imgFile = fullfile(pwd,'MerchData','MathWorks Cube','Mathworks cube_0.jpg');
inputImg = imresize(imread(imgFile),[224 224]);
imshow(inputImg)
```

![](bbox=[0.251, 0.273, 0.526, 0.563])

# Run Prediction for One Image

Execute the predict method on the dlhl.Workflow object and then show the label in the MATLAB command window.

```
[prediction, speed] = hw.predict(single(inputImg),'Profile','on');
```

### Finished writing input activations.
### Running single input activations.

# Deep Learning Processor Profiler Performance Results

| Network | LastFrameLatency(cycles) | LastFrameLatency(seconds) | TotalFrames |
|---|---|---||
| conv1 | 732615 | 0.02929 | 1 |
| pool1 | 1111619 | 0.04445 | |
| pool2 | 235563 | 0.00094 | |
| res2a2brancha | 268736 | 0.01007 | |
| res2a2branchb | 269631 | 0.01008 | |
| res2a | 94319 | 0.00338 | |
| res2b2brancha | 268877 | 0.01007 | |
| res2b2branchb | 268863 | 0.01008 | |
| res2b | 94255 | 0.00338 | |