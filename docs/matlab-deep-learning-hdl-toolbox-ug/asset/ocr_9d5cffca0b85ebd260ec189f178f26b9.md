# Deep Learning Processor IP Core User Guide

+   - Batch normalization layer (batchNormalizationLayer) and 2-D convolution layer (convolution2DLayer).
- 2-D zero padding layer (nnet.keras.ZeroPadding2DLayer) and 2-D convolution layer (convolution2DLayer).
- 2-D zero padding layer (nnet.keras.ZeroPadding2DLayer) and 2-D max pooling layer (maxPooling2Layer).

This code output is an compiler optimization in the compiler log.
Optimizing series network: Used 'nnet.keras.Layer.BatchNormalizationLayer' into 'nnet.cnn.Convolution20Layer'.

# Leg Compilations

The compile function splits a network into legs during compilation. A leg is a subset of the network that you can convert into a series network. The compile function groups the legs based on the output format of layers. The layer output format is defined as the data format of the deep learning process module that processes conv, fc, or adder. For example, in this image, the compile function groups all the layers in Leg 2 because they have a common output format. To learn about the output formats, see "Supported Layers" on page 70.

![](bbox=[0.068, 0.423, 0.931, 0.663])

This image shows the legs of the ResNet-18 network created by the compile function and those legs highlighted on the ResNet-18 layer architecture.

![](bbox=[0.142, 0.733, 0.903, 0.883])

# 2-4