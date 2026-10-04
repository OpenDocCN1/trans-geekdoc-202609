# Featured Examples

```
curDir = pwd;
unzip('MerchData.zip');
imds = imageDatastore('MerchData', ...
'IncludeSubfolders',imds,true, ...n'LabelSource','foldername');
[imdsTrain,imdsValidation] = splitLabel(imds,0.7,'randomized');
```

# Replace Layers

The fully connected and classification layer of the pretrained network are not configured for 1000 classes. These two layers fc1000 and ClassificationLayer_predictions for ResNet-18, contain information on how to combine the features that the network extracts into class probabilities and predicted labels. These two layers must be fine-tuned for the new classification problem. Except all layers, the last two, from the pretrained network.

```
lgraph = LayerGraph(snet)
lgraph = LayerGraphWithProperties(
Layers: {[71x1 nnet.cnn.Layer]}
Connections: {[78x2 table]}
InputNames:{data'}
OutputNames:{ClassificationLayer_predictions})
```

numClasses = num(category(classes))
numClasses = 5

```
newLearnableLayer = fullyConnectedLayer(numClasses,
'Name','new fc',
'WeightLearnRateFactor',10,
'BiasLearnRateFactor',10);
lgraph = replaceLayer(lgraph, 'fc1000',newLearnableLayer)
newLayer = classificationLayer('Name','new.classout')
lgraph = replaceLayer(lgraph,'ClassificationLayer_predictions',newLayer);
```

# Train Network

The network requires input images of size 224-by-22-by-3, but the images have different sizes. Use an augmented image datastore to automatically resize the training images. Specify additional augmentation operations to perform on the training images, such as randomly flipping the images along the vertical axis and randomly translating them up to 30 pixels horizontally and vertically. Data augmentation helps prevent the network from overfitting and memorizing the exact details of the training images.

```
pixelRange = [-30 30];
imageAugmenter = augmenter('RandReflection',true,
'RandTranslation',pixelRange,
'RandRotation',pixelRange);
```

To automatically resize the validation images without performing further data augmentation, use an augmented image datastore without specifying any preprocessing operations.

```
augdsTrain = augmentedImageDatastore(inputSize(2),imdsTrain, ...
'DataAugmentation',imageAugmenter);
augdsValidation = augmentedImageDatastore(inputSize(2),imdsValidation);
```

10-148