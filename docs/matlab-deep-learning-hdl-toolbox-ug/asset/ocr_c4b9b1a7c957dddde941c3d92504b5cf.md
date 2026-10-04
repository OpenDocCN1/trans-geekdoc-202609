# Featured Examples

disp(['Number of validation images: ',num2str(numel(imgsValidation.Files))]);
Number of validation images: 32

# SqueezeNet

SqueezeNet is a deep CNN whose architecture supports images of size 227-by-227-3. Even though the image dimensions are different for GoogleLeNet, you do not have to generate new RGB images at the SqueezeNet dimensions. You can use the original RGB images.

# Load

Load a custom SqueezeNet neural network.

```
sqz = squeezenet;
```

Extract the graph from the network. Confirm SqueezeNet has fewer layers than GoogleLeNet. Also confirm if SqueezeNet is configured for images of size 227-by-227-3

```
lGraphSqz = layerGraph(sqz);
disp('Number of Layers: ',num2str(numel(lGraphSqz.Layers)));
Number of Layers: 68
disp(lGraphSqz.Layers(1).InputSize)
227 227 3
```

# Modify SqueezeNet Network Parameters

To retain SqueezeNet to classify new images, make changes similar to those made for GoogleLeNet.
Inspect the last six network layers.

```
lGraphSqz.Layers(end-5:end)
ans =
1 'drop9' Dropout 50% dropout
2 'conv10' Convolution 1000x1x512 convolutions v
3 'relu_conv10' ReLU ReLU
4 'pool10' Global Average Pooling Global pooling
5 'prob' Softmax softmax
6 'ClassificationLayer_predictions' Classification Output crosstropyex with tech
```

Replace the 'drop9' layer, the last dropout layer in the network, with a dropout layer of probability 0.6.

```
tmpLayer = lGraphSqz.Layers(end);
newDropoutLayer = dropoutLayer(0.6,'Name',new dropout);
lGraphSqz = replaceLayer(lGraphSqz,tmpLayer.Name,newDropoutLayer);
```

Unlike GoogleLeNet, the learnable layer in SqueezeNet is a 1-by-1 convolutional layer, 'conv10', and not fully connected. Replace the 'conv10' with a new convolutional layer with a number of filters equal to the number of classes. As done with GoogleLeNet, increase the learning rate of the new layer.

```
numClasses = numel(categories(imgsTrain.Labels));ntmpLayer = lGraphSqz.Layers(end-4);
```

# 10-***